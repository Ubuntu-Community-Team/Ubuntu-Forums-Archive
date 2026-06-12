---
title: "Sudo Su &amp; Oracle"
date: 2006-01-17
forum: Packaging and Compiling Programs
---

### Post by squidward on 2006-01-17
Not the [Phil Collins]("http://en.wikipedia.org/wiki/Sussudio") song.;) 

I wish to start Oracle from my account, vice starting at boot, or starting from the Oracle account.

This command and variants have come close, but not quite:

> [COLOR="Blue"]squid@ubuntu:~$ sudo su - $ORACLE -c "/home/oracle/bin/lsnrctl start listener"
Password:

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 17-JAN-2006 05:47:10

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

TNS-01106: Message 1106 not found; No message file for product=network, facility=TNS       [listener]
squid@ubuntu:~$[/COLOR]

The problems seem to be that the program want's to be started by the home account.  I've tried setting -H Oralce without luck.  Admitting, I may have the syntax wrong.

---

### Post by squidward on 2006-01-17
Not sure how this thread ended up in this section.  Need more AM coffee.

---

### Post by ape on 2006-01-17
The ORACLE_HOME variable is not getting set before running the lsnrctl command.

---

### Post by squidward on 2006-01-18
[QUOTE=ape]The ORACLE_HOME variable is not getting set before running the lsnrctl command.[/QUOTE]

I checked bashrc, it's there.  Is there another place to put it?

On second thought... do my bashrc environment variables apply once sudo su'd to another account name?  I may have to write a more comprehensive shell script to get this done,

---

### Post by ape on 2006-01-19
Because you are passing the '-' to the su command, you are telling su to make the shell a login shell (which reads the resultant users environment, replacing yours).

You can see this by modifying your command to the following:

    sudo su - $ORACLE -c "env"

You won't see the $ORACLE_HOME variable being set unless you are doing it from the $ORACLE users .bashrc.

---

