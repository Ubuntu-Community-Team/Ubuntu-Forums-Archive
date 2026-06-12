---
title: "Running windows and ubuntu 12.04 on two different harddrives"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by ph4t0mp00p3r on 2012-09-27
Hello all, first post here.

I have a laptop dual boot vista and ubuntu 12.04. I am in the process of building a desktop for school work and would like to nkow if it is possible to run ubuntu 12.04 and windows 7 on two different internal hard drives. By this I mean one hard drive dedicated to ubuntu 12.04 and one dedicated to windows seven and have the option to choose which to boot from upon start up, or would i have to change in the bios every time? My searching here and google have not turned up exactly what I am looking for. Thank you for any info you may be able to pass my way!

---

### Post by jingaling on 2012-09-27
Hi ph4t0mp00p3r (awesome name by the way!)

The quick answer to your question is yes, you can do it. Here's how:

So let's say you have HDD A that will run Win 7 and HDD B for bun2. First of all install Win 7 on A as you normally would, taking up the whole HDD apart from 150MB at the end (this will become apparent later).

Now, install bun2 on B, again taking up the whole HDD but create an EXT4 partition on your Windows drive using the 150MB you left over. Mark the label as /boot.

What this does is installs the two operating systems on separate drives. The boot loader (grub)is already aware of bun2 on HDD B but creating the /boot partition and installing grub on HDD A means that it then becomes aware of Windows also. Now when you boot up, you should get the option of loading either Windows or bun2 on seperate drives.

There may well be a more elegant solution to this but that's how I do it and it works for perfectly me. I wrote a blog post a while back about this subject, it may be useful for you:

[http://refugeeks.com/RefuGeeks/2012/06/how-to-correctly-partition-ubuntu/](http://refugeeks.com/RefuGeeks/2012/06/how-to-correctly-partition-ubuntu/)

Hope this helps,

Jing

---

### Post by snowpine on 2012-09-27
Yes, it is possible. The Ubuntu installer will ask you on which disk you wish to install. It will also auto-detect your Windows install so that the GRUB bootloader gives you the chose of operating systems each time you boot.

Detailed instructions here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2012-09-27
Recommend you keep the two drives entirely separate: one for Windows, the other for Ubuntu.

Install one OS on each drive, with only that drive connected.

Then, when done installing Ubuntu, reconnect the Windows drive, but continue to boot from the Ubuntu drive.

Boot into Ubuntu, open an terminal, and enter "sudo update-grub".  That will regenerate the default GRUB config file and add an entry for Windows 7.

When you reboot, you will get a menu offering you either Ubuntu or Windows 7.

---

### Post by ph4t0mp00p3r on 2012-09-27
Thank you all for the prompt replies. I am still about 2 weeks out from completing the desktop so I wanted to investigate and do some research before I got it done. I like the idea of having them on totally different drives. While I don't have a problem with dual booting, I will be doing a lot of programming and physics models on this pc. There will also be a lot of information assurance and network security homework done on it. I may actually just rely on a live usb drive with BT5. Not entirely sure yet, just exploring options at the moment. Again thank you all, this is why I chose to migrate my day to day computing to Ubuntu from windows, the community is awesome. I wish I had done this much sooner.:D

---

### Post by oldfred on 2012-09-27
All of the above is good info, but many new computers are now UEFI with gpt partitioning.

Most new UEFI systems also will boot in BIOS mode so above info still applies, but some have Windows installed in UEFI mode. If so you have to use the 64bit version of Ubuntu and also install it in UEFI mode. 

If Windows is in BIOS mode then all the above info applies and you install Ubuntu in BIOS/MBR mode also. 

I prefer to keep each drive totally separate, so when one hard drive fails you can boot the other drive. If any parts of install are needed from both drives any drive failure prevent booting. But I keep some data on both drives and backup some data between drives.

---

