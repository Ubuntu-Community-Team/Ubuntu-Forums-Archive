---
title: "GDM could not write to authorisation file"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Hookheathen on 2008-06-20
[FONT="Arial"]Hi, I am running Feisty very happily for the past couple of years on dual boot IBM X40 laptop, but following downloading recent updates today I got the very disconcerting stop sign with:-

"GDM could not write to your authorisation file. This could mean you are out of disk space or that your home directory could ot be opened for writing. In any case it is not possible to log in. Please contact your system administrator."

Firstly, please help me to login. Thereafter maybe I could address the possible congested disk. Many thanks.[/FONT]

---

### Post by dracayr on 2008-06-20
try booting in single-user-mode:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

or download Knoppix and boot from CD/DVD

dracayr

---

### Post by aquavitae on 2008-06-20
Boot from the live cd or into recovery mode, drop to the command line and delete stuff from there. But that requires some knowledge of the command line. I'd say easiest is to just boot of the live cd.

---

### Post by rockinlinux on 2008-06-20
if you dont know the command line good then boot from a live cd and delete file you do not need. if you dont think you are out of disk space then boot with a live cd and the most easy way to tell is open gparted...it will tell you. you can also look at properties on your /home partition (if it is separate) and your / partition. or if you know the command line you can do it all from there. If you are not out of space post what you find back and we can take it from there.

---

### Post by chrisccoulson on 2008-06-20
There should be no need to boot a live CD or go to recovery mode to fix this. Boot normally, then at the login screen, do CTRL+ALT+F1 to switch to a terminal. Log in via the terminal and check the output of the following commands:
```
df -h
ls -l /home
ls -l ~/.Xauthority
```

This will check whether you have space left on all your disks, allow you to make sure you have write permissions to your home folder (should probably be 755) and allow you to check the permissions on your .Xauthority file (should be 600 and owned by you).

The most likely culprit is being out of disk space unless you've been playing around with permissions. Another possible culprit is running a graphical application with sudo, which might have changed ownership of your Xauthority file to root

---

### Post by Hookheathen on 2008-06-20
Yup, you were correct. disk usage is the problem. On /dev/sda3 it is 100% and on /dev/sda2 94%.

Under Xauthority I have rw authorisations for my own directory (but not for another directory which is redundant and would like to delete to make space). Where do I go to from here?

---

### Post by chrisccoulson on 2008-06-20
I can't tell you what to delete under /home (you'll have to work that out for yourself). To work out where the space is going, try this from the terminal (it's probably going to take a little while):
```
sudo du -h --max-depth=1 /
```
...then post the results (try to post the output from any command that people ask you to use as opposed to describing what you saw, as it makes it easier to help you. I appreciate this might be difficult when you're not running in a graphical environment. For example, I don't know what is mounted on /dev/sda2 or /dev/sda3 from your description, so I can't tell you where to delete files from).

---

### Post by Hookheathen on 2008-06-20
Many thanks for getting me restarted. I successfully deleted sufficient files to access GUI, then did some serious housekeeping. Thank you again for your help.

---

