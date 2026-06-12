---
title: "How to start/stop one program from another"
date: 2009-11-09
forum: Programming Talk
---

### Post by Juggler00 on 2009-11-09
Here's what I'm trying to do (Jaunty server edition):

I would like to be able to start/stop one program from another. Specifically, I have installed Asterisk that runs as non-root user asterisk. I would like Asterisk (the program) to be able to launch a bash script with the following:

```
#!/bin/bash
sudo /etc/init.d/motion start

```
Motion is another program installed, running as non-root user motion. 

What is the best way to accomplish this? I don't want to hard-code any passwords into the script.

cheers,
   J.

---

### Post by A_Fiachra on 2009-11-09
The problem is that sudo will ask for your password.


Another approach is to just call the program from a shell script and set a sticky bit on the shell script.

[Sticky bit]("http://www.beginlinux.org/mod/resource/view.php?id=347")

---

### Post by Arndt on 2009-11-09
> **A_Fiachra said:**
> The problem is that sudo will ask for your password.


Another approach is to just call the program from a shell script and set a sticky bit on the shell script.

[Sticky bit]("http://www.beginlinux.org/mod/resource/view.php?id=347")

The link is fine, but you mean the SUID bit, not the sticky bit.

There have been security issues with setting the suid bit on a shell script in the past. Ubuntu may have solved them, I don't know. In case it hasn't, the thing to do is to write a small wrapper in for example C, and set the suid bit on it instead.

---

### Post by Juggler00 on 2009-11-09
How does setting the SUID bit on the script help? In Asterisk, I am calling the bash script... should I change the permissions on it?

Can you point to any examples of this?

cheers,
  J.

---

### Post by matt1985 on 2009-11-09
Can you point to any examples of this?

---

### Post by A_Fiachra on 2009-11-09
man chmod

---

### Post by Juggler00 on 2009-11-10
Thank you for your suggestions. I looked into SUID/SGID and found sites that related to adding a specific exception in the sudoers file. 

Using [FONT=Courier New]sudo visudo[/FONT], I appended the following line:
[FONT=Courier New]asterisk ALL = (root) NOPASSWD: /usr/share/asterisk/agi-bin/motion_start.sh[/FONT]

The script is as follows:
[FONT=Courier New]-rwxr-xr-x 1 asterisk asterisk   40 2009-11-10 08:42 motion_start.sh[/FONT]

and contains:
[FONT=Courier New]#!/bin/bash
/etc/init.d/motion restart [/FONT]

When I try to run the script: 
[FONT=Courier New]$ sudo -u asterisk ./motion_start.sh[/FONT]

I get the following error message:
[FONT=Courier New] * Starting motion detection daemon : motion
start-stop-daemon: Unable to set gid to 1003 (Operation not permitted)[/FONT]

What am I missing?

---

