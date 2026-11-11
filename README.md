# W2-PM5 -- Network Scanning with Zenmap

**Project module:** Week 2 \| Project Module 5\
**Program:** Networkwalks \| Batch B084\
**Author:** Shaik Mahboob Mohiuddin\
**Tool:** Zenmap (Nmap GUI) on Windows\
**Target:** Own local Wi-Fi LAN (`192.168.1.0/24`)

## Overview

This project documents an authorized local-network discovery exercise
using Zenmap. The tasks follow the supplied Networkwalks W2-PM5
practical: install Zenmap, identify the local IP/subnet, discover live
hosts, record IP and MAC information, and create a topology view.

## Objectives

-   Identify the Windows PC's local IPv4 address and subnet.
-   Discover active hosts on the local `/24` network.
-   Record observed IP addresses and hostnames.
-   Record MAC addresses only where the evidence confirms them.
-   Review selected TCP service-scan results and network topology.

## Environment and tools

-   Windows PC
-   Zenmap / Nmap
-   Windows Command Prompt (`ipconfig /all`)
-   Local Wi-Fi network

## Results

The Windows adapter details showed: - IPv4 address: `192.168.1.11` -
Subnet mask: `255.255.255.0` - Subnet: `192.168.1.0/24` - Default
gateway: `192.168.1.1` - Local Wi-Fi adapter MAC: `CC-47-40-F5-7E-B4`

The primary Ping Scan output reported **7 hosts up** out of 256
addresses:

  Host                   IP address
  ---------------------- ----------------
  Router / unnamed       `192.168.1.1`
  Ayesha-s-A36           `192.168.1.4`
  Galaxy-A57-5G          `192.168.1.5`
  Uni.\*20DVR            `192.168.1.6`
  Redmi-Note-9-Pro-Max   `192.168.1.7`
  SHAIK (local PC)       `192.168.1.11`
  V2336                  `192.168.1.13`

A later repeat Ping Scan screenshot showed 5 hosts up. The topology
screenshot includes an iPhone at `192.168.1.8`; these are separate scan
snapshots because device availability can change.

## MAC address evidence

The only MAC address confirmed in the supplied screenshots is the local
Windows Wi-Fi adapter: `192.168.1.11` → `CC-47-40-F5-7E-B4`. MAC
addresses for other hosts were not visible in the supplied Nmap output
and are not guessed.

## Additional port observations

  -----------------------------------------------------------------------
  Host                    Open TCP ports shown    Service labels
  ----------------------- ----------------------- -----------------------
  `192.168.1.1`           53, 80, 443             DNS/domain, HTTP, HTTPS

  `192.168.1.6`           80, 554                 HTTP, RTSP

  `192.168.1.11`          135, 139, 445, 6646     MSRPC, NetBIOS-SSN,
                                                  Microsoft-DS, unknown
  -----------------------------------------------------------------------

An open port is not automatically a vulnerability; further validation is
required.

## Limitations

-   MAC addresses for other discovered devices were not visible in the
    supplied scan output.
-   The initial scan reported 7 hosts; a later repeat scan reported 5.
-   The topology screenshot includes `192.168.1.8`, suggesting a
    different scan snapshot.
-   The exported topology PDF requested in the practical was not
    supplied.

## Repository structure

``` text
W2-PM5-Zenmap-Network-Scanning/
├── README.md
├── report/
│   └── W2-PM5_Network_Scanning_with_Zenmap_Report.pdf
└── evidence/
    ├── CMD.png
    ├── initial-ping-scan.png
    ├── live-hosts-repeat-scan.png
    ├── topology.png
    ├── ports.png
    ├── quick-scan.png
    └── zenmap.png
```

## Run the discovery scan

Only scan networks you own or have explicit permission to assess.

``` bash
nmap -sn 192.168.1.0/24
```

On Windows, run `ipconfig /all` to inspect the local adapter address and
subnet mask.

## Disclaimer

This project is for educational purposes and documents activity on the
author's own local network. Do not scan systems or networks without
authorization.
