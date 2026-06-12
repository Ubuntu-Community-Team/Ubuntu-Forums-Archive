---
title: "Problem with HP Network printing"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by adam s on 2008-11-23
I need to use the network as the printer is in another room to the computer.

When I print, the printer says "printing" and hangs. If I cancel the job, it prints about 1cm of the print
I have installed snmp and I get the following results :

adam@frodo:~$ snmpwalk -Os -c public -v 1 192.168.1.147 1.3.6.1.4.1.11.2.3.9.1.1.7.0
enterprises.11.2.3.9.1.1.7.0 = STRING: "MFG:HP;MDL:Officejet 7300 series;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;1284.4DL:4d,4e,1;CLS:PRINTER;DES:6543;SN:MY633Q717T04HR;S:038080C484001021002c180005ec288004c;J:                    ;Z:0102,0503cbe9014dc9,0600;BT:000000000000,4F66666963656A65742037333030"


I do not know how to test which ports are open as per instructions on HPLIP website.

Please help me get my printer working.

I am running Intrepid, but had the same problem with Hardy.

Thanks,

Adam

---

### Post by adam s on 2008-11-24
I have this logged with launchpad, I will post the solution when/if I have it.

Adam

---

### Post by halitech on 2008-11-24
how do you have the connection to the network printer? (ie. IPP, hp/JetDirect, samba share?) is it connected to a windows computer or does it have an IP address on the network?

---

### Post by adam s on 2008-11-25
It is connected by IP address.

---

### Post by halitech on 2008-11-25
when you installed the driver, which option did you select? IPP, HP/JetDirect or how?

---

### Post by adam s on 2008-11-26
None of the above,

It was found automatically by the "new printer" program.

Adam.

---

