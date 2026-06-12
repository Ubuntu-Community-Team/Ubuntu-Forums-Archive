---
title: "Need a Little Advice to Get Started"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by bigtex2 on 2014-08-17
I'm new to Ubuntu although I did use Unix many years ago.

I'm looking to re-purpose an old (circa 2003) desktop PC that unsurprisingly doesn't get much use these days into a media server. I have installed the desktop version of Ubuntu on to this machine to demonstrate that it has sufficient power to run successfully.

Now I'd like to move on to creating and installing the server. I currently have a 160 Mb hard drive in the machine that has Windows XP installed on it as well as Ubuntu 12.04 which I installed under WUBI. What I would like to do is to install Ubuntu server 12.04 LTS (the lastest LTS is 64 bit and won't work on my machine I think) in a dual boot configuration on the existing drive and install two new 2 Tb hard drives for data that would be configured using some type or RAID format. The motherboard that is in the old machine only has two SATA ports, one of which is in use, so I will need to buy and install a PCI to SATA card that will allow me to add the new drives.

My questions are:

Does the configuration that I have briefly outlined above make sense in terms of creating a server that will primarily be used for serving media (photographs, music) within the local network as well as hosting a simple home web server?

What is the best way to set about installing the server version of Ubuntu. I imagine that I need to have the two new drives installed and recognized by the BIOS before I start the install. How should I specify the partitioning of the drives when install the OS?

What is the most appropriate server configuration given the simplicity of the needs for the system. I was thinking RAID 1, i.e. mirrored drives but I understand that there is also a RAID 10 configuration that may be appropriate. 

All suggestions or advice regarding how best to proceed would be greatly apperciated.

Tex

---

### Post by nerdtron on 2014-08-17
First, I don't think dual boot will server a purpose. You won't be needing XP especially if you configured RAID 1 on the 2x2TB drives.
I think you should dump the 160 GB hard drive because an old hardware can be unreliable so you can just connect the 2 new drives on the motherboard, setup RAID1 and install Ubuntu. See here for practice [https://www.youtube.com/watch?v=z84oBqOxsD0](https://www.youtube.com/watch?v=z84oBqOxsD0)

Why RAID1? Because you only have two identical drives, RAID 10 requires at least 4 drives.

---

### Post by Ratscallion on 2014-08-17
If you're making a media server on the local network, I can't recommend [Plex]("http://plex.tv") more. It has support on pretty much every device (including Chromecast, Android, iOS and web) and is also available on external networks (if you set that up). It doesn't require any other server apps, either.
I haven't tinkered with Ubuntu Server, but I imagine a simple apache server would meet your needs. You could try it with stock Ubuntu and XAMPP, just to get everything running, then work with server. Depends how much you want to tinker and whether it's for you or a 'production server'.

---

### Post by ian-weisser on 2014-08-17
> **bigtex2 said:**
> the lastest LTS is 64 bit and won't work on my machine
32-bit LTS is indeed available at download.ubuntu.com.  Look under the Alternate section.

> **bigtex2 said:**
> Does the configuration that I have briefly outlined above make sense in terms of creating a server that will primarily be used for serving media (photographs, music) within the local network as well as hosting a simple home web server?

Nerdtron is right: You won't need XP. I wouldn't leave XP on an internet-connected machine.
I disagree with nerdtron about the 160GB drive. Use it for your system, and the RAID for your data. Booting from RAID works, but I think it's unnecessarily complex. 
You can try both ways, or change back and forth. They both work.

> **bigtex2 said:**
> What is the best way to set about installing the server version of Ubuntu. I imagine that I need to have the two new drives installed and recognized by the BIOS before I start the install. How should I specify the partitioning of the drives when install the OS?

Download the 32-bit server .iso.
Put it on a USB stick.
Disconnect your data drives.
Install server to your system drive.
Reconnect your data drives.
Boot to your new server.
Experiment.
You don't need to have the two new drives recognized by anything. That's an after-install job if you want them to be data-only.

Remember to document your changes so, in the event of a catastrophe, you can do them again.

> **bigtex2 said:**
> What is the most appropriate server configuration given the simplicity of the needs for the system. I was thinking RAID 1, i.e. mirrored drives but I understand that there is also a RAID 10 configuration that may be appropriate. 

For starting out, I recommend 1 system drive, 1 data drive, and 1 backup drive. RAID can come later, when you need redundancy (which you probably won't for a home server).

Don't get locked into I-must-do-it-right-the-first-time. You may renovate and change everything in a couple months. That's why you document what you are doing...so you have notes to refer to. There are LOTS of right ways to do it. Have fun with it. Try different ways.

Keep good backups. LOVE your backups! And every so often, restore from your backup so you know you really can in an emergency.

---

### Post by nerdtron on 2014-08-17
> I disagree with nerdtron about the 160GB drive. Use it for your system,  and the RAID for your data. Booting from RAID works, but I think it's  unnecessarily complex. 
You can try both ways, or change back and forth. They both work.

If you put the OS on the 160GB drive and use software RAID on the 2x2TB drives, it makes sense. But if the 160GB hard drive failed will you still be able to read the 2x2tb drives RAID afterwards? I haven't tried it before, if the answer is YES then it's good.

---

### Post by bigtex2 on 2014-08-17
Many thanks for these responses.

A couple of follow-up points:

I suspect that my motherboard is so old that it isn't possible to boot from a USB stick. I guess that I will have to burn a CD or DVD and use that as the initial install.

As I understand the post above, I should install the server OS onto the the 160 Gb drive and then connect the two data drives. Will the OS automatically detect the two new drives and ask how they should be partitioned/configured?

The intent of the RAID configuration was that I would essentially have a real time backup of what is written to the drives. Why would you recommend performing backups of the data drive rather than have the real time system that the RAID configuration supplies?

---

### Post by nerdtron on 2014-08-17
> I suspect that my motherboard is so old that it isn't possible to boot from a USB stick. I guess that I will have to burn a CD or DVD and use that as the initial install.
Yes you can. Just burn the iso as an image and start booting.

> As I understand the post above, I should install the server OS onto the the 160 Gb drive and then connect the two data drives. Will the OS automatically detect the two new drives and ask how they should be partitioned/configured?
See my post above first before installing on the 160GB drive. Yes, the two sata drives should be automatically detected and you'll choose how to configure, partition and format them on the installer partitioning screen as long as you know what you are doing (or experiment until you get it right, that is how we learn).

> The intent of the RAID configuration was that I would essentially have a real time backup of what is written to the drives. Why would you recommend performing backups of the data drive rather than have the real time system that the RAID configuration supplies?
This is software RAID so you may need manual intervention when one of your drives failed. Although failure of two drives simultaneously is unlikely to happen, it could happen. Plus, for example, you write data and it is corrupted, the other copy on the mirrored drive is also corrupted. **Or if for example you deleted all data on you RAID drive, if you don't have backup copy on a separate machine (or external drive) then your data is lost.** RAID is not backup, it is redundancy.

---

### Post by bigtex2 on 2014-08-17
Nerdtron

Your advice regarding RAID being for redundancy rather than backup is well taken. That being said is there a particular backup tool that you would recommend I use to backup the primary data drive? Also, I currently have a one disk Synology NAS on the network - could I use this as a backup destination for the OS on the 160 Gb drive?

---

### Post by nerdtron on 2014-08-17
Sure do! If it is a NAS, then you can mount it (think of map network drive in windows) in Ubuntu. Then do your backups.
As for backup, I prefer to do it the manual command line way using my own written script with cron scheduler. Although there are GUI programs for backups, I haven't use them.
You're dealing with a server here so better be ready for command line.
The easiest way is to manually copy the files from your data partition to the NAS share. That is a different problem and might need a new thread.

---

### Post by ian-weisser on 2014-08-17
> **nerdtron said:**
> If you put the OS on the 160GB drive and use software RAID on the 2x2TB drives, it makes sense. But if the 160GB hard drive failed will you still be able to read the 2x2tb drives RAID afterwards? I haven't tried it before, if the answer is YES then it's good.

YES. You can reinstall completely, tell the new install of mdadm about the RAID, and it will rebuild the RAID and read it like nothing changed or you simply rebooted.

> **bigtex2 said:**
> Will the OS automatically detect the two new drives and ask how they should be partitioned/configured?

No. Ubuntu is stable and tested and and easy to install. But it's like a Lego set. It provides all the bricks, but you must learn how to put them together.

The server install is command line only.
It doesn't come with a GUI (good servers don't need GUIs).
It doesn't have install wizards.
It will autodetect your hardware, but it won't prompt you for anything. It figures you will tell it what you want when you're good and ready.
It's a change from what you are used to.
...and it's a lot of fun.  Really.
...and it's free.

---

### Post by JKyleOKC on 2014-08-18
I'd like to add one point: when first learning the rather different Linux way of doing things, many folk (including myself) find it easier using a GUI desktop with several Terminal windows open, than being restricted to a single CLI display. Back in 1990 I was one of the loudest detractors of the GUI revolution and even led a panel discussion at Software Development 90 titled "GUI? Phooey!" -- but over the years I've learned that multi-tasking really is a good way to work.

The major difference most people notice between the desktop and server versions of Ubuntu and its various flavors is the presence or absence of the GUI; the real key points are that the server is, as noted above, like a box of Legos that you have to assemble into what you want, and it's optimized to deal with multiple network connections. The desktop versions include all the frills one would expect, such as an office suite and games, and network connections are pretty much automated.

Thus for initial learning, I'd choose desktop versions and let the server wait until it's needed. I'm actually running several server programs here, but my systems are all Xubuntu desktop versions. It's the same as Ubuntu itself under the skin, but far fewer bells and whistles. I've found no need for the true "server" optimizations. You might feel the same way after doing your initial setup!

---

### Post by ian-weisser on 2014-08-18
> **JKyleOKC said:**
> Thus for initial learning, I'd choose desktop versions and let the server wait until it's needed.

I think that's *very* good advice.
You're also right about using multiple terminal windows.
Well said.

---

### Post by newb85 on 2014-08-18
I agree with JKyleOKC.  A beginner might be fine with server edition, but if his hardware will support a desktop environment (even a lightweight one), it will probably be more comfortable for learning.

If you want the DE and the server packages, then you have the option of either installing a desktop flavor and adding the server packages, or installing Server Edition and then installing the DE.  Either one should get you to basically the same place.

---

