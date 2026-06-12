---
title: "New to ubuntu install"
date: 2021-11-16
forum: New to Ubuntu
---

### Post by sbadm on 2021-11-16
Hello, I am trying to figure out what ubuntu to download regular or sever. and recommendations?

---

### Post by naxal on 2021-11-17
Hello,

Its very simple.

If you are choosing Ubuntu for regular use, like for example, you want to install it in your PC / Laptop and want to watch movies, browse internet, edit videos or photos, do school work, then download the regular.

Server, as the name suggests, is mainly for servers. For example, I am running Ubuntu Server for my home server running NextCloud backup. Similarly, I am running Ubuntu Desktop (regular as you are referring) on my Dell Laptop for regular usage. 

So ask yourself, what is your need and choose accordingly

Thanks.

---

### Post by grahammechanical on 2021-11-17
There is more than two editions of the Ubuntu distribution of Linux.

Ubuntu Desktop has a desktop environment and a user interface that is point and click. It is appropriate for home/office type of applications. Ubuntu Server only has a command line interface. Applications are loaded by entering commands. It is not suitable for home/office type of applications but for business server applications. Although individuals can also use Ubuntu server for the limited needs of the individual. Then there is Ubuntu Core which is meant for the Internet of Things devices. It is small in size, highly secure and has a command line interface. There are also various cloud based derivatives of Ubuntu.

Ubuntu is Open Source Software. Some developers have taken Ubuntu and installed different desktop environments and user interface. Some have become officially recognized by the sponsor of Ubuntu as official flavors.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

One of these might be to your taste. One of these might be necessary if your hardware is old.

Regards

---

### Post by TheFu on 2021-11-17
> **sbadm said:**
> Hello, I am trying to figure out what ubuntu to download regular or sever. and recommendations?

First - you should use 20.04 releases. This is the current LTS and has no-hassle support for 5 yrs of the core OS and libraries. Non-LTS releases get 9 months of support, which means you should expect to move to a new release every 6 months when they are made available. 21.04 and 21.10 are non-LTS releases.  21.04 support ends next month, so everyone running it must move to 21.10 to stay supported.  21.10 support ends in July, so they must move to 22.04 which will be the next LTS.

The only reason NOT to use 20.04 based release would be if your hardware is extremely new.  However, it should be said that new CPUs can run on older releases. I'm running a Ryzen 5600g on 18.04, for example. The iGPU didn't like the default kernels, but it still works. 20.04 does support this newer Ryzen CPU, BTW.

Server doesn't have a GUI and would not be a good choice for anyone new to Linux/Unix.  Server is meant to be used by admins and programmers to provide network services or data crunching.  No GUI, means no email, no browser, absolutely no mouse or video or audio use.

You probably want a GUI running a "DE" - Desktop Environment.  Unlike Windows, there are 50 choices of GUIs for most flavors of Linux. Each has resource demands, so the physical hardware your computer has will help to decide which DE you should choose.  It is also possible to run without any DE, but still have a GUI, though this isn't something people new to Linux should do.

We can break down the GUIs into three resource requirement groups.
[LIST]
[*]heavy/bloated - all the 'cheese' that a modern OS with new, fast, CPU, GPU and plenty of RAM would expect
[*]medium - a good trade-off between usability and resource use
[*]lite - mainly for 10+ yr old computers
[/LIST]

There is some overlap in each of those groups.  My estimate for resource use in the Ubuntu family of 20.04 releases is this:
[LIST]
[*]Ubuntu (this is the default that Canonical pushes running Gnome3 as the DE). A Core i5+ newer than 2017 with 8G of RAM should handle it.
[*]Kubuntu - this uses KDE and is much lighter than Gnome3+, but is a full-featured and impressive GUI.
[*]Ubuntu-Mate - this is firmly in the "medium" and quite usable range.  Linux Mint would be an alternative, perhaps more usable. Mate is the DE.
[*]Xubuntu - This is a lite-to medium DE and also very usable. I think it uses older, lighter Gnome2 libraries. XFCE4 is the DE.
[*]Ubuntu-Budgie - Lite and very WinXP-like  interface.  Compare to Pop!OS. I've never used this DE.
[*]PopOS ... I've only seen it a few times, but it seems to fit in these slot. It might be lighter than Lubuntu. I'm not sure.
[*]Lubuntu - this is a lite DE using LXQt.  Lubuntu used to be LXDE-based, which I ran for years. Mom used Lubuntu on a Pentium computer.
[/LIST]

Here are the Canonical supported DE flavors: [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Something to consider. You don't need to make a choice this big, unless you are really time limited.  Download all of them and try them out using a Live Boot environment running from a USB3 flash drive. That's one thing Ubuntu does well - plus you'll always want to keep a flash drive with the install on it after you've already done an install just to deal with some boot issues that may happen once every few years. The "Try Ubuntu" capability of flash drives is really excellent and means you can always have a useful computer even if your normal install isn't working for any non-hardware-failure reason.

Even if you have a Core i7 10th gen and 32GB of RAM, Xubuntu or Mate are still really great. Same for Linux Mint. Those 3 are my initial recommendations for new users.  Mint does some things to make it very useful for new users and it limits some complexities that Canonical has forced into Ubuntu.

---

### Post by ActionParsnip on 2021-11-17
Server has no GUI, regular does. It's that simple.

---

