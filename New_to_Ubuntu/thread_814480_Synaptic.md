---
title: "Synaptic"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by coubury on 2008-05-31
What setting do i have to make in synaptic to be able to install things trying to install wine and it cant find it! i had to reinstall ubuntu today had all this sorted before but cant remember what to do


root@coubury-desktop:/home/coubury# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

---

### Post by Maestro23 on 2008-05-31
Make sure you have the "Universe" repository enabled in Software Sources.

---

### Post by TeoBigusGeekus on 2008-05-31
Perhaps
```
sudo apt-get update
```
?

---

### Post by IHATEDLINK on 2008-05-31
This is what happens when people are to used to terminal. ;)
Try via Applications>Add/Remove...
**MAKE SURE THAT THE 'SHOW' OPTION IS SET TO 'ALL AVAILABLE APPLICATIONS'.**
Here's a quick demo:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72379&stc=1&d=1212276526[/IMG]

Don't forget to 'Apply Changes' when your done!

Terminal didn't let you download it because, as Maestro23 points out, the 'Universe' repository isn't enabled by default. When you'll try to 'Apply Changes' a dialog box will tell you that you are about to install 'Community Maintained Software' and then it will ask you if you want to enable community maintained software. You just click OK to everything and magically the Universe repository will be enabled. ;)
If this post was helpful don't forgot to thank me by clicking the little star button at the button right of this post ;)

---

