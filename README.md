# victorialogs-sandbox

VictoriaLogs rehearsal environments on Docker Compose, one directory per case.
The cases share host ports, so run one at a time.

- [cluster](cluster/): one production-shaped cluster (3 vlstorage, 3 vlinsert,
  3 vlselect) with Grafana, for the ingest path, the search path, and what
  losing a vlstorage node means.
- [ha](ha/): two independent zones behind a replicating write path (vlagent)
  and a failing-over read path (vmauth), for what VictoriaLogs availability
  actually looks like, since a single cluster keeps no replicas.

Both cases keep the same loopback contract: reads at 127.0.0.1:9471, writes at
127.0.0.1:9481, Grafana at http://127.0.0.1:3000/.

## License

This project is licensed under the [MIT License](./LICENSE).
