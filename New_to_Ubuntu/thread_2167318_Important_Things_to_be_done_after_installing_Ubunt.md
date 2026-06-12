---
title: "Important Things to be done after installing Ubuntu 12.04"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by sydney2 on 2013-08-13
Hello Everyone
I have just installed Ubuntu 12.04 on my desktop PC.Please suggest me the important tweaks and things to be done to setup a successful Ubuntu System.

Regards...

Sydney.

---

### Post by howefield on 2013-08-13
Apply any updates.

---

### Post by sydney2 on 2013-08-13
How do I apply updates. I know of the command  sudo apt-get update. But what about the system packages,hardware drivers,compilers etc.Please suggest me a specific answer..

---

### Post by leg on 2013-08-13
[Comprehensive Multi-media how to]("http://ubuntuforums.org/showthread.php?t=766683")

Check that you have all the media software you require.

---

### Post by howefield on 2013-08-13
> **sydney2 said:**
> How do I apply updates. I know of the command  sudo apt-get update. But what about the system packages,hardware drivers,compilers etc.Please suggest me a specific answer..

Open the Dash by pressing the Super key (windows flag) or Super + A and start typing Update Manager, check and apply updates.

Then search the Dash for Additional Drivers which will tell you if there are any proprietary drivers that you may wish to install.

---

### Post by ibjsb4 on 2013-08-13
> **sydney2 said:**
> How do I apply updates. I know of the command  sudo apt-get update. But what about the system packages,hardware drivers,compilers etc.Please suggest me a specific answer..

Apt-get update and upgrade is the most important, after that you need to get your AV working with the restricted extras package.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mastablasta on 2013-08-13
if you have DVD drive you will need libdvdcss to play DVD.

and then install what you want/need.

---

### Post by Frogs Hair on 2013-08-13
[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

---

### Post by VMC on 2013-08-13
Most people have their own tweaks that support how they run programs and how it looks. 
I think the most important tweak has already been suggested - update your system. I have an alias just for that:
```
alias upd8='sudo apt-get update && sudo apt-get upgrade'
```
Then again that's just how I run things. I don't prefer the gui updater.

---

