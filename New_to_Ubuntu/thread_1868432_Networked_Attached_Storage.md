---
title: "Networked Attached Storage"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by skywalker45 on 2011-10-24
Hey All! I know there are plenty of threads on here regarding NAS but I really can't sort through them all and some are a little over my head. To get to the point I am running Ubuntu 11.04 on my desktop and have a Western Digital My Book 1TB hard drive attached to my router via USB (NAS). The problem is I cannot see or in any other way connect to this device. I can connect to my Windows laptop, my girlfriends MAC and they can all connect to me and the 1TB hard drive. Am I missing something?? I'm sure I am of course and since I'm relatively new to Linux, or just really don't understand all the inner workings that well, I need some assistance here. Thanks in advance for all your help. I'm thinking I probably don't have some packages installed that I need but before you ask I do have samba installed and it runs well.

---

### Post by jnorthr on 2011-10-25
Never had any of these devices myself, so can only guess a few ideas. Since storage devices can be attached to a router, these are not seen by the ubuntu kernel as directly connected devices, the only ones the kernel typically works with. Devices attached to a router need to be made known to the kernel in a different way and the kernel may or maynot like to play nicely with the devices of some vendors - yours may be one, but dunno - so now we get into the area of using networking to talk to storage devices and for that we can use either cifs or smb - read this: [http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block)

so that's the background. 

Now look at this: [http://ubuntuforums.org/archive/index.php/t-801579.html](http://ubuntuforums.org/archive/index.php/t-801579.html)  which will baffle the heck out of you and give you an idea why some things in ubuntu are easy and some are way harder than you might image. This is gonna be hard to do - sorry. :confused:

---

### Post by skywalker45 on 2011-10-28
It's okay! I know it's going to be difficult but I also know it can be done. I can look up the IP for the NAS on my router and have no trouble getting there with http or ftp but those obviously aren't the methods I want or need to use. I think the issue here is using smb and cifs as you suggested as well as tinkering with some system files to tell the kernel where to look and keep my fingers crossed that they play well together. Thanks for the links though! They are very helpful! :)

---

### Post by Paqman on 2011-10-28
Your NAS is most likely sharing using the SMB/CIFS protocol, which is what Window networks use for shares. That's fine, as Ubuntu can connect to this using something called SAMBA. The SAMBA client is preinstalled on your machine, so you should just be able to navigate to it through the network link on the left of the file manager. 

That will give you access until you log out. If you want to have your shares permanently mounted on boot you'll have to [add entries to /etc/fstab]("http://ubuntuforums.org/showthread.php?t=288534").

Setting up access to network shares on Ubuntu is a little harder than it should be, but nothing too daunting.

---

