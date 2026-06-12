---
title: "fancontrol help request"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by iwant2 on 2013-12-28
Loaded fancontrol.  Then I get this:

bill@bill-P47G:~$ sudo fancontrol
[sudo] password for bill: 
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
bill@bill-P47G:~$ 
??? What should be done to get fancontrol to work?

---

### Post by varunendra on 2014-01-01
From the man page of "fancontrol" -
> **CONFIGURATION**
       For  easy  configuration,  there's a script named **pwmconfig**(8) which lets you interactively write your configuration file for fancon&#8208;
       trol. Alternatively you can write this file yourself using the information from this manpage.

This script (pwmconfig) is part of fancontrol installation. To run it -
```
sudo pwmconfig
```

To get some basic info about this script before running it, see its own man page -
```
man pwmconfig
```

Hope it helps.

---

