---
title: "LTSP Clients super slow."
date: 2018-01-03
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-01-03
I don't expect them to be speed demons for desktop use. And admittedly maybe I've been spoiled by the ssd I put in my laptop.

I have been thinking about deploying LTSP in my house awhile now and finally been doing some test runs. It works, but painfully slow. Minecraft runs great, once it loads. Stopwatch at 1 min 6 seconds from the time you click Play on the loader to the time you can pick a world. Other apps run fine, but again take a long time. Makemkv clocks in at 36 seconds to load. Handbrake same. Chromium is surprisingly quick to load. Using fat clients.

Is that normal load times for a spinning hard drive (which is close to same i/o as gigabit network?) Or am I expecting to much from a network boot solution?

---

### Post by DuckHook on 2018-01-03
Conceptually, there is no reason that LTSP clients would be inherently slow. In the real world, however, performance is dependent on a large number of factors, from hardware to network speed to the network file system used to the specific parameters of all those elements.

I'm no network/server expert by any stretch of the imagination, but you should post your details if you want someone more knowledgeable to help.

[list=1]
[*]Start with a detailed list of your HW from LTSP server specs to those of your fat clients.
[*]Describe network topology, protocols being used and as many details as possible including wiring and NIC type.
[*]Are you using NFS, NBD or something else?
[*]What are you running on the clients? If they are fat clients, can you do an independent *dmesg*?
[/list]
To start narrowing down your issues, make use of the various **top* utilities. You may have to install some of them:

[list]
[*]*htop* tells you cpu/RAM usage. Keep an instance running while you try launching minecraft and it should tell you a few things.
[*]*iotop* shows you disk throughput.
[*]*iftop* shows network throughput.
[*]This is an extremely useful page summarizing networking tools: [http://www.binarytides.com/linux-commands-monitor-network/](http://www.binarytides.com/linux-commands-monitor-network/)
[*]An old help thread, but still relevant, if&#8212;for nothing else&#8212;than as an example of the tweaking that must be done to maximize throughput and efficiencies: [https://ubuntuforums.org/showthread.php?t=2312766](https://ubuntuforums.org/showthread.php?t=2312766) You may wish to try this solution too.
[*]A more general and very in-depth How-To for optimizing NFS: [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html) Also this: [http://www.tldp.org/HOWTO/NFS-HOWTO/performance.html](http://www.tldp.org/HOWTO/NFS-HOWTO/performance.html)
[/list]
Post above info and hopefully, a guru will reply.

---

### Post by Tadaen_Sylvermane on 2018-01-05
> **DuckHook said:**
> Conceptually, there is no reason that LTSP clients would be inherently slow. In the real world, however, performance is dependent on a large number of factors, from hardware to network speed to the network file system used to the specific parameters of all those elements.

I'm no network/server expert by any stretch of the imagination, but you should post your details if you want someone more knowledgeable to help.

[LIST=1]
[*]Start with a detailed list of your HW from LTSP server specs to those of your fat clients.
[*]Describe network topology, protocols being used and as many details as possible including wiring and NIC type.
[*]Are you using NFS, NBD or something else?
[*]What are you running on the clients? If they are fat clients, can you do an independent *dmesg*?
[/LIST]
To start narrowing down your issues, make use of the various **top* utilities. You may have to install some of them:

[LIST]
[*]*htop* tells you cpu/RAM usage. Keep an instance running while you try launching minecraft and it should tell you a few things.
[*]*iotop* shows you disk throughput.
[*]*iftop* shows network throughput.
[*]This is an extremely useful page summarizing networking tools: [http://www.binarytides.com/linux-commands-monitor-network/](http://www.binarytides.com/linux-commands-monitor-network/)
[*]An old help thread, but still relevant, if—for nothing else—than as an example of the tweaking that must be done to maximize throughput and efficiencies: [https://ubuntuforums.org/showthread.php?t=2312766](https://ubuntuforums.org/showthread.php?t=2312766) You may wish to try this solution too.
[*]A more general and very in-depth How-To for optimizing NFS: [http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html) Also this: [http://www.tldp.org/HOWTO/NFS-HOWTO/performance.html](http://www.tldp.org/HOWTO/NFS-HOWTO/performance.html)
[/LIST]
Post above info and hopefully, a guru will reply.

Server is an AM1 Kabini quad 25w tdb. 8gigs of ddr3 1600 ram. 1tb spinning hard drive, 120gb ssd, 2tb usb 3.0 spinner. the ltsp chroot and image is on the ssd.
Network is full gigabit with a mix of cat 5e and cat 7 cabling. Single gigabit switch linking everything together with a single port going to the router which has a max of 10/100.
Server does dhcp, dns, ltsp, and a few other things. Load only exceeds 5-10% when wife and I play on the minecraft servers we run.
Using NBD as this is default for both Ubuntu & Debian. I have tried with both Debian and Ubuntu, Ubuntu ltsp server bare metal and a Debian ltsp running inside of an LXD container. Both exhibit the same issues. On the Ubuntu ltsp I tried switching to nfs following the guide in the wiki. Didn't work at all. So stuck with NBD.
I've been using my laptop as the fat client for testing. Normally I use wireless. To test ltsp I plug directly into the main switch. Under normal transfers from laptop to server over the wired network I average 80-90 megs a second give or take a few. The network is performing at gigabit speeds for sure.

Will run the *top commands and post back with more details.

---

