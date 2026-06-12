---
title: "How to get iTunes 7.1 working on Ubuntu"
date: 2007-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by smp500 on 2007-05-29
Anymore, it seems like one of the biggest drawbacks of Ubuntu is iTunes. Yes, you can use rhythmbox, gtkpod, amarok, and more to manage your iPod, and DRM is bad, too, but that doesn't seem to matter to a lot ofthe people I know. They just want iTunes. The people over at the Wine project have been trying to get iTunes to work on linux for a while, but are stuck at iTunes 6.0 without iPod or store support. For those of you out there who just want iTunes, it is possible to have it work fully on Linux (iPod and store support!!), but be warned -- You do need a Windows licence :-(.

The trick is VMware. Ubuntu 7.04 (Feisty) comes with player, but you can also buy VMware if you want to. I tested all of this with Ubuntu 7.04, a 1.8GHz Athlon XP with 512MB ram, and Windows 2000. 

First, you will need around 5 gigs on your harddrive (I used 10, but it is up to you). Go to [EasyVMX]("http://www.easyvmx.com/") and build a virtual machine. I just went with the defaults, only adding a 'windows.iso' as the second CD (you'll see why later), changing the name to "iTunes", and turning USB Autoconnect ON. Unzip it somewhere, for now we will just call it /home/me/iTunes.

Next, install windows. Just put the CD in and run:> cd /home/me/iTunes
vmplayer iTunes.vmx and install like normal. After rebooting, you need VMware tools to make the installation remotely useful. You have to get 
VMware Workstation to get VMware tools (which is needed to access the internet and install iTunes). Once you do, copy a file called windows.iso from the tarball to the directory with the VMX file.> tar tzvf VMware-workstation-x.x.x-yyyyy.tar.gz|grep windows.iso
tar zxvf VMware-workstation-x.x.x-yyyyy.tar.gz vmware-distrib/isoimage/windows.iso (or whatever the directory is)
Click the 'CDROM 2' button on to mount it in VMware and it should install itself. Now you are ready to install iTunes.

Download iTunes from inside the VM and install it. I wanted to make it seem to blend in more, so I told windows to auto-hide the taskbar. **VERY IMPORTANT: I had to manually enable DMA for my cdrom IN WINDOWS to burn CDs from iTunes!!**

Now iTunes works!! Better yet, iPod support works, so you can transfer purchased music, or even do a firmware update (worked on a 2G nano anyway). Just remember to do a > sudo umount /dev/sda2 before connecting it to iTunes, otherwise the FAT32 filesystem could be corrupted. Also, it is a good idea to wait until the VMware session is fully restored (bar at bottom right) before connecting the iPod.

To make it easier, save the following as 'itunes' and put it in your $HOME/bin> #!/bin/bash
ITUNESDIR=/home/me/iTunes
cd $ITUNESDIR
if [ "`mount|grep /dev/sda2`" != "" ]; then
 sudo umount /dev/sda2
fi
vmplayer iTunes.vmx Just run 'itunes' from the command line to start it up.

Like I said, I haven't tested it with Windows XP or Vista, so you are on your own there. I have my VM set to use 176MB of ram, and it runs faster than it does on my XP dual boot (which I now have no need for). Good Luck!!

---

### Post by JAmerican on 2007-07-04
Look into getting [Banshee]("http://banshee-project.org/Main_Page")

JA

---

### Post by mooha on 2007-07-04
```

Look into getting Banshee

JA
```


Absolutely nice

---

### Post by Krosis on 2007-07-04
I personally use a program called Songbird.  It's a lot like iTunes.  Nice How To.  Sure to help some people.  Good job.

---

### Post by Vevmesteren on 2007-07-06
I vote for Songbird too. Though it is quite resource hungry I find. The old Firefox problem. Let it run for a while and it seriously eats into your memory...

V

---

