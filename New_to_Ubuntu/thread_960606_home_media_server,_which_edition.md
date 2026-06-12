---
title: "home media server, which edition"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by bartvh on 2008-10-27
I'm going to create a home media server and want to run Ubuntu on it. I need some help choosing which edition to get.

On the one hand, I want to use it as a media center (probably with MythTV) and for simple desktop tasks (browsing, checking mail, etc.). For this I would choose the Desktop Edition.

On the other hand, the server will be running a bittorrent client for downloading, and samba and apache to serve media files to computers in the network and online. It will run MySQL to support various applications. For these tasks the Server Edition would be better.

I know both editions can probably be customised to completely become the other. However, which one would accomodate my needs the most, out-of-the-box?

Thanks

---

### Post by Thelasko on 2008-10-27
The server doesn't have a [GUI]("http://en.wikipedia.org/wiki/GUI").  If you are new to Linux, I would recommend the Desktop version.

P.S. Have you looked in to [Mythbuntu?]("http://en.wikipedia.org/wiki/Mythbuntu")

---

### Post by bartvh on 2008-10-27
Well, I'm not an expert, but I have some experience with Linux. I'm currently running a Debian home server (without media center) and I host my websites on a Debian VPS. Even so, I'm fairly new, and I've never used a Linux Desktop for 'serious' stuff. I currently have an old laptop with Ubuntu Desktop connected to my TV to play stuff from the Debian server. I'd like to combine them in 1 machine :P

Anyway, Desktop sounds like the way to go then. The server part won't have to handle hundreds of connections at a time or anything like that, so it'll manage.

---

### Post by bartvh on 2008-10-27
Hmm, Mythbunty sounds alright. At least I'll be finished in a few clicks :) Are there any downsides to it?

By the way, I'm also going to install two hard drives (for /home) and put them in a software RAID 1. Any experience, tips or opinions about that?
Edit: Now that I think of it, would it be possible to use those disks for root (/). That would protect the entire system of disk failure. However, I cannot imagine how I would set it up, seeing as the PC needs to boot from '/' before the software RAID driver is loaded, right?

---

### Post by nhasian on 2008-10-27
for your home media server you might also want to take a look at [http://www.boxee.tv/](http://www.boxee.tv/)

---

### Post by ABCC on 2008-10-27
As you know both would be quite suitable. However, if you want to include desktop and multimedia use in your setup you'll be better going with the desktop. It's preconfigured with those tasks in mind, you'll have a useful system straight away. It should have slightly broader (multimedia) hardware support, very handy if you ever want to plugin some odd usb peripheral or pci card. 

As for samba, mysql and apache, the packages between the versions are the same. Both of those will take a bit of manual tweaking anyway. You're configuration is probably a bigger factor in how well these run than the server/desktop trade off. As for serving torrents, both versions are equally suited to this, you won't really see much difference there. Your best bet is probably to go with the desktop version. If you want lower resource use and a bit more stability you can turn off the X server and gdm so you can 'startx' to log into the desktop the old fashioned way.

However, tinkering is fun. I'd definitely choose the server just so I could spend longer tweaking. 

ABCC

---

### Post by dfreer on 2008-10-27
It really doesn't matter, if you are planning on having a GUI anyways, install with a Desktop CD. Installing with the server CD isn't going to make much difference, it just would be easier to add services as you need them vs. disabling services that you don't need and adding ones you do IMO. Just a matter of convience.

As for bittorrent, I'd recommend checking out using torrentflux or torrentflux-b4rt on the server.

EDIT: Just noticed you plan on using RAID. I think you need either the Server CD or Alternate Install CD if you want to install to a RAID. I'm currently using RAID on my server, make sure that /boot is on a Mirrored RAID 1, I would place that at the beginning of each drive, all the same size. That way BIOS can boot from any drive as they all have the same information. Then the rest of your OS can be on RAID 0,1,5 or whatever you want.

---

### Post by ABCC on 2008-10-27
> However, I cannot imagine how I would set it up, seeing as the PC needs to boot from '/' before the software RAID driver is loaded, right?

The easy fix is to put all but your boot partition in the RAID set.

ABCC

---

### Post by Thelasko on 2008-10-27
> **bartvh said:**
> By the way, I'm also going to install two hard drives (for /home) and put them in a software RAID 1. Any experience, tips or opinions about that?

I don't have any experience with RAID, but you would have to install software RAID.  I found a [how to page]("https://help.ubuntu.com/community/Installation/SoftwareRAID") on Software RAID.

---

### Post by bartvh on 2008-10-27
> As for bittorrent, I'd recommend checking out using torrentflux or torrentflux-b4rt on the server.
I've been using torrentflux-b4rt with great satisfaction for a while now :)

> The easy fix is to put all but your boot partition in the RAID set.

Here my Linux (or generic low-level OS) knowledge fails me. How exactly would I do this? What is needed to boot? How could I put both /etc, /var, /home and what-have-you on the RAID partition, without putting / in it's entirety on it?

Btw, really quick answers here. Nice :)

---

### Post by ABCC on 2008-10-27
Nope, Linux works the other way round from windows! In Linux / is the system root in which all folders are mounted. This allows you to define 'exceptions' which are not on the same disk and/or partition as where / is mounted. Rather than mounting drive letters (which themselves are like /) you mount subfolders. If you mount / on the software RAID but /boot on a non raid partition (or usb stick, all it does is store the kernel image and bootloader).

Now that I've looked into the 'how easy is it' bit it seems it is a bit easier even than expected. The installer should be able to guide you through a proper installation provided you partition manually. Plenty of guides available on the topic btw, such as []("http://http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") and even for RAID 10: [http://http://www.howtoforge.com/install-ubuntu-with-software-raid-10]("http://http://www.howtoforge.com/install-ubuntu-with-software-raid-10")

ABCC

---

### Post by Thelasko on 2008-10-27
> **ABCC said:**
> Plenty of guides available on the topic btw, such as []("http://http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") and even for RAID 10: [http://http://www.howtoforge.com/install-ubuntu-with-software-raid-10]("http://http://www.howtoforge.com/install-ubuntu-with-software-raid-10")

ABCC

Your link is broken.  [Here is a working one.]("http://www.howtoforge.com/install-ubuntu-with-software-raid-10")

---

### Post by bartvh on 2008-10-27
So I've read the guide from Thelasko's post ([this one](https://help.ubuntu.com/community/Installation/SoftwareRAID)). It seems like it'll work, but about these matters you can convince me of many things with little effort. Any educated opinions on the steps in that guide?

edit: Woops, didn't notice page 2. i'll read the other guide just posted
edit2: oh wait, no, raid10 is not what i want. i only have two disks :p

---

### Post by dfreer on 2008-10-27
Didn't read the guide, but this is how I set up my RAID server (general):

I have three 300 GB Identical Hard Drives that I will be using for the OS and data storage. 

/boot will need to be RAID 1, and I decide it only needs 1 GB of space. So that means I need to create three 1 GB partitions on each hard drive. Once the OS is installed, it doesn't matter which drive is booted as they all contain the same data.

I decide that I want to run RAID 5 on the / partition for reliability, and it will have 30 GB's of Hard Drive space. Since it's RAID 5, this means I need to create three 15 GB partitions, one on each drive.

Finally, this leaves me with approx 284 GB's on each drive. I decide to create one huge partition of 284 GB's, one on each drive, and run RAID 0 on it for ultra quick performance, mounting it as /dataraid0.

---

