---
title: "Need Help Understanding Rights for Shares"
date: 2015-07-17
forum: New to Ubuntu
---

### Post by robertzito on 2015-07-17
I am attempting to SNMPGET to my printer to get sysuptime. The mib file sits in /usr/share/snmp/mibs/ when I attempt sudo snmpget, I get an error that I do not have permission to the folder. Without being root is the share supposed to be available to me or this is a protected folder that only root can access? If just for root why use the word share?

---

### Post by Vladlenin5000 on 2015-07-17
By definition, you - the user - have read/write/execute permissions to your userspace only, the folder with your username inside /home. Everything else is "system", hence root needed.

---

### Post by Geoffrey_Arndt on 2015-07-17
The usr/share directory is owned by root . . . to see the ownership, check the folder props or use nautilus to view owner attribute column.

---

### Post by robertzito on 2015-07-18
Thank you for taking the time.

---

