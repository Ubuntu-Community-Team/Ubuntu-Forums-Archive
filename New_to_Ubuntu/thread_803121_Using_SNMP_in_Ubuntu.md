---
title: "Using SNMP in Ubuntu"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-22
Hi Guys,

I am trying to monitor a machine using SNMP & Cacti, however having problems generating the information that im after...

I have installed snmpd, and able to query using the following:

```
$ snmpwalk -c 'communityname' -v 1 localhost
``` 

And receive the following output:

```
sysDescr.0 = STRING: Linux marknotebook 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
sysObjectID.0 = OID: netSnmpAgentOIDs.10
sysUpTimeInstance = Timeticks: (11484170) 1 day, 7:54:01.70
sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)
sysName.0 = STRING: marknotebook
sysLocation.0 = STRING: Unknown (configure /etc/snmp/snmpd.local.conf)
sysORLastChange.0 = Timeticks: (26) 0:00:00.26
sysORID.1 = OID: snmpMIB
sysORID.2 = OID: tcpMIB
sysORID.3 = OID: ip
sysORID.4 = OID: udpMIB
sysORID.5 = OID: vacmBasicGroup
sysORID.6 = OID: snmpFrameworkMIBCompliance
sysORID.7 = OID: snmpMPDCompliance
sysORID.8 = OID: usmMIBCompliance
sysORDescr.1 = STRING: The MIB module for SNMPv2 entities
sysORDescr.2 = STRING: The MIB module for managing TCP implementations
sysORDescr.3 = STRING: The MIB module for managing IP and ICMP implementations
sysORDescr.4 = STRING: The MIB module for managing UDP implementations
sysORDescr.5 = STRING: View-based Access Control Model for SNMP.
sysORDescr.6 = STRING: The SNMP Management Architecture MIB.
sysORDescr.7 = STRING: The MIB for Message Processing and Dispatching.
sysORDescr.8 = STRING: The management information definitions for the SNMP User-based Security Model.
sysORUpTime.1 = Timeticks: (23) 0:00:00.23
sysORUpTime.2 = Timeticks: (23) 0:00:00.23
sysORUpTime.3 = Timeticks: (23) 0:00:00.23
sysORUpTime.4 = Timeticks: (23) 0:00:00.23
sysORUpTime.5 = Timeticks: (23) 0:00:00.23
sysORUpTime.6 = Timeticks: (26) 0:00:00.26
sysORUpTime.7 = Timeticks: (26) 0:00:00.26
sysORUpTime.8 = Timeticks: (26) 0:00:00.26
End of MIB
```

When i attempt to configure SNMP using snmpconf it doesn't appear to list the configuration file that is listed above for SNMP:

/etc/snmp/snmpd.local.conf

Any tips on how to configure SNMP on Ubuntu... Since im not getting any info :(

Thanks!

---

### Post by markbusu on 2008-05-22
Solved, had to define the security names /etc/snmp/snmpd.conf 

####
# Second, map the security names into group names:

# sec.model sec.name
group MyROSystem v1 paranoid
group MyROSystem v2c paranoid
group MyROSystem usm paranoid
group MyROGroup v1 readonly
group MyROGroup v2c readonly
group MyROGroup usm readonly
group MyRWGroup v1 readwrite
group MyRWGroup v2c readwrite
group MyRWGroup usm readwrite

to

group MyROSystem v1 local
group MyROSystem v2c local
group MyROSystem usm local
group MyROGroup v1 localnet
group MyROGroup v2c localnet
group MyROGroup usm localnet
group MyRWGroup v1 local
group MyRWGroup v2c local
group MyRWGroup usm local

Hope this helps!

---

