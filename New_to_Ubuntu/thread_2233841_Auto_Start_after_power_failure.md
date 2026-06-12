---
title: "Auto Start after power failure"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by harpreet2 on 2014-07-11
Hi 

I am using a set of Ubuntu Machines deployed remotely. These units do not have any monitor or keyboard attached to them. Also these units experience occasional hard reboot due to power failure. Upon reboot, the system gets stuck at grub asking for an option from the user. Unless the option is selected by the user, the system doesn't boot. 

I tried using the solutions posted on the forums - changing the grub file or changing the 00_header file and running update-grub command but that doesn't work. The changes to grub or 00_header file are not saved by system and it gives an error that this is a "Read Only" file. 

Can someone provide a solution for this issue.  I am using Ubuntu 14.4 

Thanks in advance for the help 


harpreet

---

### Post by deadflowr on 2014-07-11
Exactly, those files would be set as read-only for you.
How are you trying to edit them?

---

### Post by harpreet2 on 2014-07-11
tried editing using text editor but that gives a read only notifiation
tried editing the 00_header file using gedit option but that opens a blank file

---

### Post by sotiris2 on 2014-07-11
If you have admin priviledges try 

```
gksu gedit /etc/grub.d/00_header
```
It will ask for **your** password. If you have admin priviledges you will get to edit it else it will fail. 
If it says *program gksu not found* or something similar (but [b] not that you are not authorised) try
```
*pkexec env* DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit /etc/grub.d/00_header
```

---

### Post by deadflowr on 2014-07-11
As I stated, those files are system files, and as such cannot be written to by you, normally.
(If it was so easily written by anyone, imagine the amount of damage one could do to their own system)

That said, the gksu package is most likely not installed on 14.04.
You will need to do two things to get it working.
You need to either find the package in the software center or run
```
sudo apt-get install gksu
```
after which, you will need to make sure the authenication is set for sudo, and not su.
To do so, this must be done in a terminal.
```
gksu-properties
```
if it lists su, and not sudo, click on that and it should give you the option to switch it to sudo.
then close, and now gksu will work to open gedit.

Then you can write to those files to your hearts content.
Be careful, and good luck...

---

### Post by harpreet2 on 2014-07-14
This worked perfectly. thank you !!


harpreet

---

### Post by sandyd on 2014-07-14
Hi, please mark this thread as solved if you have found a solution.
You can do this via thread tools -> Mark as solved.

Thanks!

---

