# example_blockchain
Blockchain example written in Python with key functionality exposed as Restful APIs

$PORT -> Primary Node (eg 6000)
$NEW_PROT -> Secondary Node (eg 6001)

1. Install the dependencies:
   Install depip install Flask requests

2. Run the script:
   python example_blockchain.py

3. Mine a block:
   curl http://localhost:$PORT/mine

4. Create a new transaction that will be added to a new block to be mined:
   curl -X POST -H "Content-Type: application/json" -d '{
   "sender": "d4ee26eee15148ee92c6cd394edd974e",
   "recipient": "someone-other-address",
   "amount": 25
   }' "http://localhost:$PORT/transactions/new"

5. Inspect the full chain:
   curl http://localhost:$PORT/chain

6. Add a new node to the network (Run the python script on the same machine and inform another port. Execute the command below on the primary node):
   curl -X POST http://localhost:$PORT/nodes/register
   -H 'Content-Type: application/json'
   -d '{"nodes": ["http://127.0.0.1:$NEW_PORT"]}'

7. Mining blocks and creating transactions on secondary node

8. Run the command below on the primary node to see the conflict resolution between the nodes (consensus algorithm):
   curl http://localhost:$PORT/nodes/resolve
