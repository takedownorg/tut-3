# ns-3 Tutorial

## Build Docker Image

```bash
docker build -t custom-ns3 .
```

## Run Container

Mount `ns3-projects` directory (Windows):

```bash
docker run -it --rm -v .\ns3-projects:/usr/ns3/scratch/my-projects custom-ns3
```

Mount `ns3-projects` directory (Linux/macOS):

```bash
docker run -it --rm -v $(pwd)/ns3-projects:/usr/ns3/scratch/my-projects custom-ns3
```

Run without mounting:

```bash
docker run -it --rm custom-ns3
```

## Access Running Container

```bash
docker exec -it <container_id> bash
```

List project files inside container:

```bash
ls scratch/my-projects
```

## Install Additional Packages

```bash
apt-get update && apt-get install -y vim
```

## NS-3 Commands

Run simulations:

```bash
./ns3 run first
./ns3 run second
./ns3 run third
./ns3 run fourth
./ns3 run fifth
./ns3 run hello-simulator
```

Move output files:

```bash
mv *.cwnd *.pcap *.tr scratch/my-projects/
```

## Tutorial Commands

```bash
cp examples/tutorial/first.cc scratch/my-projects/test0/my-first.cc
./ns3 run "my-first"

cp examples/tutorial/second.cc scratch/my-projects/test1/my-second.cc
./ns3 run "my-second"

cp examples/tcp/tcp-bulk-send.cc scratch/my-projects/test2/my-bulk.cc
./ns3 run "my-bulk"

# Optional: TCP App & Window Tracing
# cp examples/tutorial/fifth.cc scratch/my-projects/test3/my-fifth.cc
# ./ns3 run "my-fifth"
```

## TCP Variants (cwnd)

```bash
./ns3 run "scratch/my-projects/tcp-cwnd-variants --tcpVariant=TcpCubic"
./ns3 run "scratch/my-projects/tcp-cwnd-variants --tcpVariant=TcpBic"
./ns3 run "scratch/my-projects/tcp-cwnd-variants --tcpVariant=TcpNewReno"
```

## Plotting

After exiting the container (can work inside too, if you have the required python libraries installed):

```bash
python plot_cwnd.py
```
