---
title: "Anoyance"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by fishman78 on 2008-07-01
Hi All,

   I am just wondering if there is a way to change my grub/EasyBCD loader.  Currently when ubuntu loads it looks for hdd2,0.  However my ubuntu is on hdd1,0.  I have to change it to hdd1,0 everytime i want to boot into ubuntu (which has become more frequent.)  I change it by pressing e at the menu, change to 1, then b for boot.  Is there a way to change this.  I am using EasyBCD, but i don't see anywhere to change it.  Any help is greatly appreciated.  

Kurt

---

### Post by kuja on 2008-07-01
I would open the file /boot/grub/menu.lst with root in whichever text editor you like, look for a line like: ```
[color=gray]# groot=(hd2,0)[/color]
```
 Change it to ```
[color=gray]# groot=(hd1,0)[/color]
```, and save. Then run the command ```
sudo update-grub
``` and you should be good to go.

---

### Post by fishman78 on 2008-07-01
> **kuja said:**
> I would open the file /boot/grub/menu.lst with root in whichever text editor you like, look for a line like: ```
[color=gray]# groot=(hd2,0)[/color]
```
 Change it to ```
[color=gray]# groot=(hd1,0)[/color]
```, and save. Then run the command ```
sudo update-grub
``` and you should be good to go.

Thanks for the reply.  This looks like the right track, but when I try and save the file it says I don't have permision.  How do i open this file with admin rights.  Thanks!

Kurt

---

### Post by kuja on 2008-07-01
Use gksudo or kdesudo (depending what DE's you have installed) when running the editor command (ie: kdesudo kate or gksudo geditor or sudo vim)

PS: this document is a good read: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by fishman78 on 2008-07-01
> **kuja said:**
> Use gksudo or kdesudo (depending what DE's you have installed) when running the editor command (ie: kdesudo kate or gksudo geditor or sudo vim)

PS: this document is a good read: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Sorry, but I'm still a little new to linux.  In Windows I would just go to the file and then right click __run as admin__ presto!  This doesn't seem to work.  And I don't know the command to open this file in the term with sudo.  I'm sure it's $sudo...somthing...somthing....somthing.  Could you provide me with the easiest way to open this bad boy.  Thanks!

Kurt

---

### Post by kuja on 2008-07-01
Take a look at the examples above, and just tack the file name (/boot/grub/menu.lst) on the end, preceeded by a space.

---

### Post by fishman78 on 2008-07-01
> **kuja said:**
> Take a look at the examples above, and just tack the file name (/boot/grub/menu.lst) on the end, preceeded by a space.

Oh Yeah!

That's the stuff.  My problem was I was typing sudo geditor, but it's sudo gedit.  It works now...perfect!!  Thanks for all your help!!!

Kurt

---

### Post by kuja on 2008-07-01
sudo gedit = bad idea. Use gksudo unless you want to experience what happens when important files in your home folder are changed to being owned by root.

gksudo for graphical things
sudo for console things

---

