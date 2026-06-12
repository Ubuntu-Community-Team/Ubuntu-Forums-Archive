---
title: "HOW TO: Virtualbox 1.6.2 non free in Hardy"
date: 2008-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by chuckyp on 2008-07-31
Okay this how to should work for future versions of virtualbox but this is what I had to go through to get it working for version 1.6.2.

Make sure that you have build-essential and linux-headers installed for your kernel. Open a terminal and:
```

$sudo aptitude install build-essentail linux-headers-`uname -r`

```

Now we need to downloaded the deb for Hardy from [www.virtualbox.org](www.virtualbox.org) and install it.  All you have to do is double click it to install it with gdebi.  It will error out about building the kernel module thats find just keep clicking next and finish.

After its done installing you want to add your user to the vboxusers group. 

Click System > Administration > Users & Groups. Now click on the Unlock button and then Manage Groups.

Scroll all the way down until you see the vboxusers group. Select it and click properties or double click it. You now need to checkbox your users name so that you have access to the virtualbox.

Now open up a terminal and we have to build and install the kernel module that failed. Enter the following commands.
```

$cd /usr/src/vboxdrv-1.6.2
$sudo make KERN_SRC=/usr/src/linux-headers-`uname -r`
$sudo make install KERN_SRC=/usr/src/linux-headers-`uname -r`

```

Now just restart your system and you should be able to run virtual box from Applications > System Tools

---

