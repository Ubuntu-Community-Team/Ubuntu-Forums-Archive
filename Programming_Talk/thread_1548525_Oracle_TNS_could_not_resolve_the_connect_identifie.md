---
title: "Oracle TNS could not resolve the connect identifier specified"
date: 2010-08-08
forum: Programming Talk
---

### Post by iansane on 2010-08-08
Hi,

I've just installed oracle-xe and am getting an error when trying to connect through sqlplus.

TNS could not resolve the connect identifier specified

I've tried looking at the tnsnames.ora and listener.ora but am a little confused by the host section.

I used a dynamic dns script to give me a fqdn but my server name is different. I changed the server name to mach the first part of my fqdn and then changed tnsnames.ora, listener.ora and all my host files to match but still get the same error.

The web interface works fine and apache2 works but I just can't connect with sqlplus.

Just to be sure, if my host name is "lotus"
Should that be what is in the tnsnames.ora and listener.ora or should that be my fqdn?

Also is "sqlplus system as sysdba" the correct way to connect? And why do I have a new user named "oracle"?

Sorry if this is too many questions at once but this oracle is definately something different when compared to MySql which also works fine.

Thanks

---

### Post by iansane on 2010-08-08
I did an strace and found an error with the password. Apparently !@# at the end of the password was causing a problem so I re-intalled and went throught the oracle-xe configure process again.

Now I get a whole new set of errors.

ORA-01034: ORACLE not available
ORA-27123: unable to attach to shared memory segment
Linux Error: 13: Permission denied

I tried setting the shared mem segment with
echo "kernel.shmmax=1073741824" >> /etc/sysctl.conf

but still get the same error.

This link,
[http://www.idevelopment.info/data/Oracle/DBA_tips/Linux/LINUX_8.shtml](http://www.idevelopment.info/data/Oracle/DBA_tips/Linux/LINUX_8.shtml)
actually uses two gigs but that's all my machine has so I set it at 1.

Does it really require that much memory just to run oracle?

---

### Post by iansane on 2010-08-08
OK,

I finally tried "su oracle" to get terminal as the user oracle and now it works. But then I have to remember to exit out of "oracle" terminal or I could really mess some things up if I run other commands through the wrong user couldn't I?

Is there something I need to set in my own user (lotus@lotus) settings to be able to log in from lotus instead of oracle? Or is the "oracle" user a security measure?

---

