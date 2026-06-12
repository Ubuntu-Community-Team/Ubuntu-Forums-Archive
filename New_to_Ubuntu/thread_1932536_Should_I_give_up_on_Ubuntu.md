---
title: "Should I give up on Ubuntu?"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by pjmahar on 2012-02-27
Complete newbie here.
Trying to ressurect an ooold dell inspiron 8000 laptop.
I have had problems with video (apparently not uncommon with this laptop) and also wireless.
I've posted here and on "launchpad" w/no responses.
Tried Xbuntu and same problems
Is there some other version of linux best suited to this type of hardware?
 
Here is a link on the video:
 
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/186153](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/186153)
 
I cant find the link for the wireless but it only works intermittently and the wireless icon on the desktop says that the device is not managed.

---

### Post by snowpine on 2012-02-27
Ubuntu is a delight on modern, well-supported hardware.

You may find these links helpful:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by wildmanne39 on 2012-02-27
Hi, well it is hard to tell with out more information please post the output of:
```
sudo lshw
```
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by mikewhatever on 2012-02-27
You posted this three weeks ago:
> **pjmahar said:**
> I figured it out. 
How to I list this as solved?

...and the launchpad question got several responses.

---

### Post by Mark Phelps on 2012-02-29
> **pjmahar said:**
> Is there some other version of linux best suited to this type of hardware?

That's the great thing about Linux distros -- trying out new ones only requires a small investment of time and effort.

Would recomment looking a Mint 12, and PC Linux OS.  Both of these are available from distrowatch.com.

---

### Post by musicman10489 on 2012-02-29
I might also recommend **Puppy Linux**. That's a great little distro that seems to run on just about anything.

[http://www.puppylinux.com/](http://www.puppylinux.com/)

---

