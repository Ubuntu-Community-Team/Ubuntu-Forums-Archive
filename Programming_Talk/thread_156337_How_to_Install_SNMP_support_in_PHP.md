---
title: "How to Install SNMP support in PHP"
date: 2006-04-06
forum: Programming Talk
---

### Post by nick1 on 2006-04-06
Greetings,

I hope I have the right forum.  I'm a bit of a newbie to Linux in general.
I have Apache and PHP installed on my Ubuntu 5.10 computer.
I'm trying to use the snmpwalk function in PHP5.
When I try to run my simple snmpwalk script, I receive the following error:

```
Fatal error: Call to undefined function: snmpwalk() in <filename_here>
```

I've looked around on google and it appears that PHP doesn't come with support for SNMP by default.  How do I go about adding SNMP support to PHP?  Like I said, I'm a bit of a newbie to Linux so I don't know much of anything about compiling things, if that's what it takes to gain SNMP support in PHP.

Any help would be much appreciated.  Thanks,

Nick

---

### Post by John.Michael.Kane on 2006-04-06
[http://us3.php.net/snmp](http://us3.php.net/snmp)
[http://phpbuilder.com/manual/en/function.snmpwalk.php](http://phpbuilder.com/manual/en/function.snmpwalk.php)
[http://www.enseirb.fr/~kadionik/embedded/snmp/english/net-snmp_english.html](http://www.enseirb.fr/~kadionik/embedded/snmp/english/net-snmp_english.html)

---

### Post by nick1 on 2006-04-06
I found a package in Synaptic called "php5-snmp."  Description reads: SNMP module for php5.  I installed it and rebooted the server.  Seems to be working so far.

Nick

---

