---
title: "bash and snmpget to variable"
date: 2017-11-16
forum: Programming Talk
---

### Post by cazz on 2017-11-16
Hi
I was thinking maybe try to make a monitor system for my computers.
I trying to put information from snmpget to a MySQL but I have problem to get the clean information to variable.

When I run this command

```
snmpget -v 1 -c "key" <servername> .1.3.6.1.4.1.2021.10.1.3.1  .1.3.6.1.4.1.2021.4.5.0 .1.3.6.1.4.1.2021.4.6.0 .1.3.6.1.2.1.1.3.0
```

I get to much information 
UCD-SNMP-MIB::laLoad.1 = STRING: 0.11
UCD-SNMP-MIB::memTotalReal.0 = INTEGER: 1007000 kB
UCD-SNMP-MIB::memAvailReal.0 = INTEGER: 245912 kB
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (18477320) 2 days, 3:19:33.20

I only need 
0.11
1007000
245912
2 days, 3:19:33

so I easy can put the information in my MySQL database
Not sure how to do that, I need somehow split the four information to four variable, maybe somehow use \n to split but not sure.

/UPDATE
Have found this for python that works nice
[http://easysnmp.readthedocs.io/en/latest/](http://easysnmp.readthedocs.io/en/latest/)

Going to try to use that.

---

