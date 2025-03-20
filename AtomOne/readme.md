# Atomone Service by Pathrocknetwork

Welcome to the Atomone Public Good Service provided by Pathrock Network. This service offers essential tools and endpoints for interacting with the Atomone network, including RPC, API, gRPC, seed nodes, and snapshots to help you get started or stay in sync.

## Services

| Service  | URL/Information                                                     | Description                                                         |
|----------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| RPC      | https://rpc.atomone.pathrocknetwork.org/                            | Remote Procedure Call endpoint for interacting with the Atomone blockchain. |
| API      | https://api.atomone.pathrocknetwork.org/                            | RESTful API for accessing Atomone network data.                     |
| gRPC     | https://grpc.atomone.pathrocknetwork.org/                           | gRPC endpoint for efficient, low-latency communication with the Atomone network. |
| Seed     | aab3205c39027b108a004d2261d3b83553c3fa34@seed.atomone.pathrocknetwork.org:36656 | Seed node for peer discovery in the Atomone network.                |
| Snapshot | https://snapshot.atomone.pathrocknetwork.org/atomone_latest.tar.lz4 | Latest snapshot of the Atomone blockchain for quick synchronization. |

## Snapshot Instructions

To quickly synchronize your Atomone node, use the following commands to apply the latest snapshot:

```bash
sudo systemctl stop atomoned
cp $HOME/.atomoned/data/priv_validator_state.json $HOME/.atomoned/priv_validator_state.json.backup
rm -rf $HOME/.atomoned/data
curl https://snapshot.atomone.pathrocknetwork.org/atomone_latest.tar.lz4 | lz4 -dc - | tar -xf - -C $HOME/.atomoned
mv $HOME/.atomoned/priv_validator_state.json.backup $HOME/.atomoned/data/priv_validator_state.json
sudo systemctl restart atomoned && sudo journalctl -u atomoned -f```
