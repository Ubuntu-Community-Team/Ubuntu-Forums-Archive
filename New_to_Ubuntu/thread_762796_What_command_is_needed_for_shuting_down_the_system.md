---
title: "What command is needed for shuting down the system?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by hovzio on 2008-04-22
Hi, I've been learning about shell scripts (More like I've been learning bash basics) lately and have started to (attempt to) write some of my own. So far its been going rather well and I'm having a a great deal of fun with it. 

To my question. Example: So I have this script that runs for a few hours and I'd like to let it run overnight, is it possible to shutdown the computer from within a bash script?(at the end of it) What is the appropriate command to shutdown the pc? I am new to Ubuntu and Linux so it would be really nice if options and so forth are somewhat defined. I appreciate any help, input, ... on the subject.

---

### Post by lizzard on 2008-04-22
Either use "sudo shutdown now -h" or "sudo init 0" to shutdown your system.

---

### Post by teeceegee on 2008-04-22
Try shutdown.

Read the man page "man shutdown" for the options.

Cheers
TCG

---

### Post by hums07 on 2008-04-22
[http://www.mrhope.com/unix/ushutdow.htm]("http://www.mrhope.com/unix/ushutdow.htm")
example to shutdown at 8 o'clock:
sudo shutdown 8:00

---

### Post by Elijah on 2008-04-22
I use 'halt' ;)

---

### Post by hovzio on 2008-04-22
Thanks! Is it possible to use these commands at the end of a shell script?

---

### Post by bobbocanfly on 2008-04-22
Yes you could put these at the end of a bash script but they would need to be run with root priveleges to work.

---

### Post by twright on 2008-04-23
or you could run sudo ./script && halt

---

### Post by tahnok on 2008-04-23
or ./script&&sudo halt if you don't want to give the script root permissions.

---

### Post by eriqjaffe on 2008-04-23
> **bobbocanfly said:**
> Yes you could put these at the end of a bash script but they would need to be run with root priveleges to work....you could also edit the sudoers file so that you can run shutdown -h without having to enter a password.  There are plenty of threads about that around here.

---

### Post by stchman on 2008-04-23
> **hovzio said:**
> Hi, I've been learning about shell scripts (More like I've been learning bash basics) lately and have started to (attempt to) write some of my own. So far its been going rather well and I'm having a a great deal of fun with it. 

To my question. Example: So I have this script that runs for a few hours and I'd like to let it run overnight, is it possible to shutdown the computer from within a bash script?(at the end of it) What is the appropriate command to shutdown the pc? I am new to Ubuntu and Linux so it would be really nice if options and so forth are somewhat defined. I appreciate any help, input, ... on the subject.

I use:

```
sudo reboot
```

This command can be used in a shell script provided the script is being run as root.

---

