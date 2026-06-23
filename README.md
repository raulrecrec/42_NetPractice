*This project has been created as part of the 42 curriculum by rexposit.*

# NetPractice

## Description

NetPractice is a practical networking project from the 42 curriculum.

The goal of this project is to understand the basics of TCP/IP networking by fixing simulated network configurations. The project is completed through a browser-based training interface where each level contains a broken network diagram.

For each level, the objective is to configure the available fields correctly so that packets can travel from the source host to the required destination. This requires understanding how IP addresses, subnet masks, routes and gateways work together.

The project contains 10 levels. Each solved level must be exported as a configuration file and submitted in the repository.

## Project Goals

The main goals of NetPractice are:

* Understand IPv4 addressing.
* Understand subnet masks and network ranges.
* Identify whether two devices are in the same subnet.
* Configure hosts, routers and routes.
* Understand the role of a default gateway.
* Understand how packets move between networks.
* Read logs to diagnose incorrect configurations.
* Practice solving routing problems step by step.

## Instructions

### Running the training interface

First, download and extract the NetPractice files provided by the project page.

Then, from the extracted folder, run:

```bash
./run.sh
```

This script launches a local web server and opens the NetPractice interface in the browser.

If the script does not work properly, the interface can be launched manually with:

```bash
python3 -m http.server 49242
```

Then open the following address in the browser:

```text
http://localhost:49242
```

The port number can be changed if needed.

### Using the interface

When the interface opens:

1. Enter the 42 login.
2. Start the training mode.
3. Solve each level by modifying the available unshaded fields.
4. Use the `Check again` button to verify the configuration.
5. When a level is correct, use the `Get my config` button to export the solved configuration.
6. Save one exported configuration file per level.
7. Continue until all 10 levels are completed.

The logs at the bottom of the page help identify problems such as:

* Invalid IP addresses.
* Missing gateways.
* Incorrect routes.
* Packets reaching the wrong host.
* Destinations not matching any route.

### Submission requirements

The repository must contain:

* This `README.md` file at the root of the repository.
* 10 exported configuration files, one for each level.
* All exported configuration files must be placed at the root of the repository.

During the defense, only the files inside the repository will be evaluated.

## Networking Concepts Studied

### TCP/IP Addressing

TCP/IP addressing is used to identify devices inside a network. In NetPractice, each host or router interface needs a valid IPv4 address.

An IPv4 address is written as four decimal numbers separated by dots, for example:

```text
192.168.1.10
```

Each part represents one byte, so each value must be between 0 and 255.

### Subnet Masks

A subnet mask defines which part of an IP address identifies the network and which part identifies the host.

For example:

```text
255.255.255.0
```

means that the first three octets identify the network, while the last octet identifies the host.

The same mask can also be written in CIDR notation:

```text
/24
```

A correct configuration requires devices that communicate directly with each other to be in the same subnet.

### Network Address

The network address identifies the subnet itself. It cannot be assigned to a host.

For example, with:

```text
192.168.1.10/24
```

the network address is:

```text
192.168.1.0
```

### Broadcast Address

The broadcast address is the last address of a subnet. It is also not assignable to a host.

For example, in:

```text
192.168.1.0/24
```

the broadcast address is:

```text
192.168.1.255
```

### Host Range

The usable host range is between the network address and the broadcast address.

For example, in:

```text
192.168.1.0/24
```

the usable host range is:

```text
192.168.1.1 - 192.168.1.254
```

### Default Gateway

A default gateway is the device used when the destination IP is outside the local subnet.

If a host wants to communicate with another network, it sends the packet to its gateway. The gateway is usually a router interface inside the same subnet as the host.

A gateway must be reachable directly by the device using it.

### Routers

Routers connect different networks together.

Each router interface belongs to a specific network. A router can forward packets between networks if its interfaces and routes are correctly configured.

In NetPractice, routers are used to move packets from one subnet to another.

### Switches

Switches connect devices inside the same local network.

A switch does not route between different networks. Devices connected through a switch still need compatible IP addresses and subnet masks to communicate directly.

### Routing Tables

Routing tables define where packets should be sent depending on their destination.

A route usually contains:

* A destination network.
* A subnet mask or CIDR range.
* A next hop or gateway.

A default route is commonly represented as:

```text
0.0.0.0/0
```

This means "any destination not matched by a more specific route".

### OSI Layers

NetPractice mainly focuses on concepts related to the network layer.

Relevant OSI layers include:

* Layer 2 — Data Link: local network communication, switches and MAC-level forwarding.
* Layer 3 — Network: IP addressing, subnetting and routing.
* Layer 4 — Transport: TCP and UDP operate above IP, although this project focuses mostly on addressing and routing.

## Solving Strategy

The general approach used to solve each level is:

1. Identify the objective shown at the top of the interface.
2. Locate the source and destination devices.
3. Check whether directly connected interfaces are in the same subnet.
4. Ensure every IP address is valid and not a network or broadcast address.
5. Configure gateways only when the destination is outside the local subnet.
6. Configure router routes so packets can move toward the destination.
7. Ensure the return path is also valid when required.
8. Use the logs to understand where the packet is blocked.
9. Export the configuration before moving to the next level.

## Resources

The following resources are useful to understand the concepts required for this project:

* RFC 791 — Internet Protocol.
* RFC 950 — Internet Standard Subnetting Procedure.
* RFC 1122 — Requirements for Internet Hosts.
* RFC 1812 — Requirements for IPv4 Routers.
* Cisco documentation about IP addressing and subnetting.
* IBM documentation about TCP/IP addressing.
* Practical subnetting tutorials and subnet mask tables.
* General OSI model references.
* Peer explanations and review during project preparation.

The main concepts studied were:

* TCP/IP addressing.
* IPv4 address structure.
* Subnet masks.
* CIDR notation.
* Network addresses.
* Broadcast addresses.
* Host ranges.
* Default gateways.
* Routers.
* Switches.
* Routing tables.
* Default routes.
* OSI layers.

## AI Usage

AI was used as a learning and productivity support tool during this project.

It was used to:

* Summarize the project subject requirements.
* Help structure this README.
* Explain networking concepts such as subnet masks, gateways, routes and CIDR notation.
* Prepare a study plan for learning NetPractice efficiently.
* Review reasoning steps while practicing levels.

AI was not used to blindly submit unexplained answers. All configurations must be understood, tested in the NetPractice interface and reviewed before submission.

During evaluation, the project must be defended without relying on external tools, except for a simple calculator if needed.

## Defense Notes

During the defense, three random levels must be completed successfully within a limited time.

Important points to remember:

* Enter the correct login in the interface.
* Read the objective carefully.
* Check local subnet compatibility first.
* A gateway must be inside the same subnet as the device using it.
* Routers need routes toward the destination network.
* Return paths may also be necessary.
* Exported files must be placed at the repository root.
