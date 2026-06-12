---
title: "Ubuntu 8.04 Hard Heron-sudo not working"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by duuchung on 2008-05-01
Dear comrades,

My system has just been upgraded to Ubuntu 8.04 Hard Heron today. The first thing  I noticed is that the images became sharper  on screen. The second thing is that sudo and su are not working. I have not changed any passwords.

I googled and found the above would happen whenever there are upgrades. I have not found the solution yet.What should I do?

regards,
duuchung

---

### Post by Sef on 2008-05-01
Moved to Absolute Beginners.

---

### Post by skymera on 2008-05-01
When you say it's not working.
Do you mean you can't sudo?
or sudo "command not found" ?

---

### Post by Bothered on 2008-05-01
Execute the following commands in a console and post the results:

```
groups
```

Will print a list of groups of which you are a member.

```
sudo echo "Hello World"
```

Attempts to print "Hello World" via sudo.

---

### Post by Oldsoldier2003 on 2008-05-01
> **Bothered said:**
> Execute the following commands in a console and post the results:

```
groups
```

Will print a list of groups of which you are a member.

```
sudo echo "Hello World"
```

Attempts to print "Hello World" via sudo.

actually if sudo was working before the upgrade its probably the hosts file go munged. If there is a . in the hostname sudo gets confused. taking a look at /etc/hosts and making sure the host is listed the same as it is in /etc/hostname is a fast check.

if it is like 127.0.1.1	fred-desktop.somedomain all you need to do is boot to recovery mode and remove the  .somedomain and sudo will start working again.

---

### Post by duuchung on 2008-05-01
I typed "groups".
The output:
xyz adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin

I typed 'sudo echo "Hello World"'
The output:
[sudo] password for xyz: 
I typed my password. A prompt returned and "Hello World" not printed.

My problem is:
I typed sudo. The system asks for my password. I type in my password. It returns a prompt abc@abc-desktop:depot$.
regards

---

