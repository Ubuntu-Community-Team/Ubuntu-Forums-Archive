---
title: "Need more disk space"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by lennart4 on 2014-12-11
Hello
 I am trying to make a program update on my Laptop which have Lunbuntu 14.04 LTS installed.
 Doing this I got an error message: ”Not enough disk space”.

 The installation needs 61M of free space on the volume  ”/boot”. At least 12 M of free disk space must be free on the volume to continue.

 
 
 The recycle bin is empty, and I have tried the command: sudo apt-get clean
 to clean earlier installation package, but I don't get more disk space.
 
 
 Can somebody help me how I get more space on this disk so I can make my program update?
 
 
 Many thanks in advance!
 Lennart H

---

### Post by nerdtron on 2014-12-11
Looks like your /boot is full due to old kernels. Have a look at the solution here. [http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by lennart4 on 2014-12-11
Thanks for your answer,
 It seems to be very advanced for a newcomer like me to &#8220;play around&#8221; with these kernels and remove &#8220;the right ones&#8221;. :)

 Is this the only way to do it? :oops:

---

### Post by sudodus on 2014-12-11
If it is still possible to install program packages, you can try ***Ubuntu Tweak's janitor***. See this link

[http://blog.ubuntu-tweak.com/2014/04/21/ubuntu-tweak-0-8-7-released-14-04-ready.html](http://blog.ubuntu-tweak.com/2014/04/21/ubuntu-tweak-0-8-7-released-14-04-ready.html)

```
sudo add-apt-repository ppa:tualatrix/ppa

 sudo apt-get update

sudo apt-get install ubuntu-tweak
```

---

### Post by nerdtron on 2014-12-11
And also, when you update, kernel upgrades are optional so you can skip them to prevent this from happening again.

---

### Post by kpatz on 2014-12-11
**sudo apt-get --purge autoremove** should remove all kernels except the two most recent.

---

### Post by lennart4 on 2014-12-11
I tried the command: [B]sudo apt-get --purge autoremove
[/B]and got the message: The package autoremove could not be found  [B]??
[/B]

---

### Post by sudodus on 2014-12-11
Try these commands

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by lennart4 on 2014-12-11
Thanks for your help everybody!!
I installed the ***Ubuntu Tweak's janitor ***program and removed old kernels with this program, and now I got more space to make my upgrade.

Great job from all of you!  Many thanks!
Best regars
Lennart

---

