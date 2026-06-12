---
title: "java RxTx permission problems.."
date: 2007-09-10
forum: Programming Talk
---

### Post by machs_fuel42 on 2007-09-10
got a little project i'd like to develop; i need to use java to access the serial port and record the information in a db for web access.

i've got java installed with eclipse ide.  I've got the rxtx libraries installed as well as the java comm stuff.

I followed this guys guide to get this far.
[http://wass.homelinux.net/howtos/Comm_How-To.shtml](http://wass.homelinux.net/howtos/Comm_How-To.shtml)

I've trying to run the simpleRead program that came with the javaComm libs to make sure everything is working.

i'm getting some permission errors, something to due with my user not being part of the uucp group (which it is) I also tryed adding my user to the dailout group, since thats who owns all of the /dev/ttyS* enteries.

```
RXTX WARNING:  This library requires the user running applications to be in
group uucp.  Please consult the INSTALL documentation.  More information is
avaiable under the topic 'How can I use Lock Files with rxtx?'
check_lock_status: No permission to create lock file.

		please see: How can I use Lock Files with rxtx? in INSTALL 
```

I'm out of ideas at this points... anyone have experience using java and the rxtx libraries ?

---

### Post by coffecup1978 on 2007-09-10
I've noticed that the uucp package isn't installed by default, try to apt-get it and see if that helps...

---

### Post by machs_fuel42 on 2007-09-11
hmm your right - i didn't have uucp
however still no joy when running the simpleRead code..

---

### Post by dwhitney67 on 2007-09-12
> **machs_fuel42 said:**
> hmm your right - i didn't have uucp
however still no joy when running the simpleRead code..

Do you have any idea where the lock file is being created?  Perhaps the user's privileges do not allow the lock file to be created.

Also, I presume when you stated that your user is part of the uucp group, an entry in /etc/group appears such as:
```
[FONT="Courier New"]
uucp:x:10:*<user id>*[/FONT]
```

where <user id> is your login id.

---

### Post by Defrector on 2007-11-14
I have uucp installed, I have reinstalled various versions of RXTX, I have triple-checked that I am part of group uucp and it still is returning the lockfile error.

edit: Also part of dialout group. No change.
edit: Reinstalled RXTX using apt-get instead of manual. Just in case there was confusion between JREs, I removed all Java folders except the jdk1.6.0_01. No change.
...Sometimes rebooting is necessary to make group settings kick in. No change.
...Reinstalled java.comm using the solaris/SPARC version instead of the specific linux version, as suggested on the homelinux.net site. No change.

---

### Post by v.korecky on 2008-01-18
Did anybody fix this problem ?
I am in the same situation and I don't know how can I fix it.
I am member of group uucp and package uucp is installed.

Thanks in advance for any help.

---

### Post by Defrector on 2008-02-19
bump.

---

### Post by regomodo on 2008-03-03
anyone got this fixed? I've just got this problem whilst trying to use my Arduino.

I don't want to reinstall Debian again
[edit] I got the error to go away by using these commands. I'm not sure if all of them are required

```
sudo chown uucp /var/lock

sudo nano /etc/group (change *uucp:x:#:{username}*  to *uucp:x:#:uucp,{username}*)

sudo usermod -aG uucp {username}

sudo chgrp uucp /var/lock
sudo chmod 775 /var/lock 
```

Now, i would go with the last 2 commands first before messing around any more.

Hope this helps someone.

---

### Post by azibhai on 2009-04-29
Hii everybody
Please help me for the following......

I am using jdk1.5.0_18 and RXTX .and I have  code to read data from serial port when I login as root . But while I am trying in another user (which is also in group uucp) I can't read the data from port.

the error message which I am getting:

>>
Experimental:  JNI_OnLoad called.
Stable Library
=========================================
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7
gnu.io.NoSuchPortException
Exception in thread "main" java.lang.NullPointerException
    at serialcomm.portopen(serialcomm.java:30)
    at serialcomm.main(serialcomm.java:156)

thanks in advance

---

### Post by Reiger on 2009-04-29
I guess that no serial ports are accessible to non-root users? That is, anything doing raw read/write access to the serial port must run as root? 

Try invoking your program with sudo. :)

---

### Post by amrypma on 2009-06-04
> **dwhitney67 said:**
> Do you have any idea where the lock file is being created?  Perhaps the user's privileges do not allow the lock file to be created.

Also, I presume when you stated that your user is part of the uucp group, an entry in /etc/group appears such as:
```
[FONT="Courier New"]
uucp:x:10:*<user id>*[/FONT]
```

where <user id> is your login id.

or try
```

adduser <user> uucp

```

make for a lot less looking at /etc/passwd and group

---

### Post by gertmul on 2011-02-18
(2 years later, but maybe a similar problem)

I found that RxTx creates a lock file in /var/lock but with the current user's permissions and for some reason the lock file does not get deleted afterwards. (I guess the lock file gets deleted and recreated when you run the program again. Running 'minicom' after your program deletes the lock file and does not create a new one?!?)

So when you try to run the code as another user, the lock file can not get deleted/accessed since the other user does not have permission to delete/modify the lock file the first one created.

---

### Post by zx5000 on 2012-03-28
Another year later another lock problem. Here's a solution.

**Problem**
ls -l /var
...
drwxr-xr-x.  6 root     root     4096 Mar 28 03:49 lock
...

**Solution**
sudo chgrp lock /var/lock
sudo chmod 775 /var/lock

Fixes the permission denied problem.

---

