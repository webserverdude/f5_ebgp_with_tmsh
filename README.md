# Configuring BIG-IP for basic BGP routing with tmsh

BIG-IP supports BGP4 and BGP4+, your BIG-IP system must be licensed for the BIG-IP Advanced Routing Module (BIG-IP ARM). 
Since TMOS version 14.0 BGP can be configured with tmsh. The old ZebOS IMI will still exist in read-only mode, but IMI and tmsh/iControl REST are mutually exclusive, therefore **F5 recommends to migrate away from ZebOS configuration.**

The following is a POC configuration between two BIG-IP systems running TMOS v15.1.10.2.
The topology is as shown in this diagram.

![topology_diagram](/assets/topology_diagram.png)

To verify if Advance Routing Module is provisioned run:
```bash
[root@tmos15-bgp01:Active:Standalone] config # tmsh show /sys license | grep "Routing Bundle"
    Routing Bundle, VE
```

Before you recreate a router on the BIG-IP, activate the sys db variable by typing the command (on both BIG-IP systems):
```bash
[root@tmos15-bgp01:Active:Standalone] config # tmsh modify sys db tmrouted.tmos.routing value enable
```