---
title: "First Network Client/Server Script)"
date: 2009-02-12
forum: Programming Talk
---

### Post by tomehb on 2009-02-12
Basically I want to get SNMP Data from one host to another....
So far on the server I have the following very simple script:


> 
#!/bin/bash
#----------Settings-------------- 
snmpwalk=/usr/bin/snmpwalk
snmpversion="-v 2c"
snmpcom="-c public"
snmpip="213.xx.xx.xx"
#---------------------------
"`$snmpwalk $snmpversion $snmpcom $snmpip`"



when i telnet to port 6200 this data is returned, however i'm wondering how I can get the client to connect and then pass the following variables snmpversion, snmpcon and snmpip. and then for the server to run the snmpwalk after.

Any help would be greatful even if its pointing me in the right direction :)


Regards

Thomas

---

