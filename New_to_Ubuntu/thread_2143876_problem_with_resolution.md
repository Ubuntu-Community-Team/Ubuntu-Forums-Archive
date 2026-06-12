---
title: "problem with resolution"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-10
Hey everyone. I got my gpu driver working(yay,installed the bumbleblee thingy). But i still have one major problem that is an issue to me, i cant change my screen resolution , it is on 1024x768 and my native is 1366x768. Help please.

---

### Post by pogopuschel on 2013-05-10
Create & attach a bugreport please..
```
 sudo bumblebee-bugreport
```

---

### Post by DragonGirl123 on 2013-05-10
[http://www29.zippyshare.com/v/36741254/file.html](http://www29.zippyshare.com/v/36741254/file.html) here is the bug report

---

### Post by pogopuschel on 2013-05-10
Due to your boot option "nomodeset" VESA driver is running instead of Intel, which limits the resolution. Get rid off that boot option ..

---

### Post by DragonGirl123 on 2013-05-10
how do i get rid of that?

---

### Post by cortman on 2013-05-10
See the last section of [this]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

---

### Post by DragonGirl123 on 2013-05-10
i did the last part and the commands ,but it didnt work :(

---

### Post by pogopuschel on 2013-05-10
So you have run
 ```
sudo update-grub
```
after editing /etc/default/grub,  rebooted and resolution still is 1024x768only**?**
Please show your /var/log/Xorg.0.log or create new bugreport.

---

### Post by DragonGirl123 on 2013-05-10
i used this **sudo gedit /etc/default/grub **&#8203;and it said gedit command not found

---

### Post by pogopuschel on 2013-05-10
I see. You are on Lubuntu, that means your text editor is leafpad (or mousepad, dunno), not gedit. Try:
```
gksudo leafpad **/etc/default/grub**
```

---

### Post by raja.genupula on 2013-05-10
you can install gedit if you want with
> sudo apt-get install gedit

---

### Post by DragonGirl123 on 2013-05-10
> **pogopuschel said:**
> I see. You are on Lubuntu, that means your text editor is leafpad (or mousepad, dunno), not gedit. Try:
```
gksudo leafpad **/etc/default/grub**
```
it said premission denied.

---

### Post by pogopuschel on 2013-05-10
Can you please copy and post the whole terminal output, means, the command you gave and the "answer" ;)

---

### Post by DragonGirl123 on 2013-05-10
do you mean to the command **/etc/default/grub **? the answer i got is that bash: /etc/default/grub : Permission denied.

---

### Post by pogopuschel on 2013-05-10
/etc/default/grub is a path, not a command. Thats why I wanted you to copy,paste and post the whole terminal output here using code tags:
to ensure you give the right commands. "Permission denied" cannot be a valid answer when using sudo/gksudo, as long your user belongs to the sudoers group, which is default in Ubuntu.

---

### Post by DragonGirl123 on 2013-05-10
oh sorry ,what do i have to type in the terminal? im little bit confused ,and sorry for my nooby linux skill

---

### Post by pogopuschel on 2013-05-10
Np, its absolute beginner section. I want you to copy& paste the command, not to type.
Paste into the terminal:

```
gksudo leafpad /etc/default/grub
```

hit enter and paste the whole terminal content please.

---

### Post by DragonGirl123 on 2013-05-10
well it opened a new thingy ,thats called grub,do i now remove the nomodeset? also a picture about it [http://postimg.org/image/4ny86ff97/](http://postimg.org/image/4ny86ff97/)

---

### Post by pogopuschel on 2013-05-10
Yes, remove it. Make it look like
GRUB_CMDLINE_LINUX=""
then close the file saving the changes. When closed, run:
```
sudo update-grub
```
Then reboot

---

### Post by DragonGirl123 on 2013-05-11
sorry for the long time it took me to reply. Yay everything works now :D

---

### Post by pogopuschel on 2013-05-11
Fine. Please mark your thread as solved (Threadtools) then ..

---

