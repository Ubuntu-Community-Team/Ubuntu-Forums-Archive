---
title: "How to try KDE4 on an external USB drive, without BIOS USB boot support"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by gregphil on 2008-09-12
I would like to play with the new KDE 4.1.1 release, but I don't want to screw up my existing ubuntu or kubuntu (on separate disks) installs.

I managed to download the kubuntu Live CD and burn the iso image.  I managed to install it to an external USB disk (and put grub on the external disks MBR).  I edited by internal grub menu.lst to add an option to boot from the USB image (or so I thought).

However if I try to use the new grub option to boot into KDE 4 I just get "Error 21: Selected disk does not exist".   

After playing around with grub some and reading many posts I conclude grub require BIOS support to read the USB disk during startup.  My ASUS P4PE motherboard (with the latest BIOS update) does not seem to offer any USB option in the boot order.  Thus I think this means the BIOS Int13 does not provide BIOS USB disk support.

Is there any way around this?  For example can I boot to ubuntu or kubuntu install on an internal disk first (so the linux USB drivers are loaded), and then "jump to" the KDE 4 install on the USB disk?  I read most of the articles at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) and did not find a solution.

Any suggestions, other than get a new computer?

---

### Post by wolfen69 on 2008-09-12
[This]("https://help.ubuntu.com/community/BootFromUSB") may help.

---

### Post by gregphil on 2008-09-12
That links looks like it is on the right track, but I can't quite follow what he is saying. I think I would want to use the option he discussed "Booting the kernal from an internal hard drive".  However by that point in his post the instructions are becomming very brief and I can't quite see what he is saying.

It looks like what he is saying is: 

1. Copy the external USB "initrd" and "vmlinuz" files to the internal hard drive (in his example to a new directory "/vols")

2. Edit GRUB's /boot/grub/menu.lst on the internal hard drive to add the option to boot from the files just copied.

But in his example changes to "menu.lst" I don't see reference to "/vols"

title  Ubuntu
root   (hd0,1)
kernel /vmlinuz-(your number) root=/dev/sdb1 ro quiet splash
initrd /initrd.img-(your version)

So.....if my new install of KDE 4 is on the USB drive /dev/sdd = (HD3,0) where should I copy the two USB kernal boot files to, and how do I link to them in the revised GRUB munu.lst on by bootable internal hard disk?

Sorry to need so much hand holding, but the solution is not obvious to me.

Thank You.

BTW GRUB already has two options (ubuntu and kubuntu) using the same kernal (the latest).  This new KDE 4 test would also be using that kernal, so maybe I don't enven need to copy the kernal, but instead on the new "kernel" line point at "root=/dev/sdd1"  ? ? ?

---

### Post by indytim on 2008-09-12
This might help:

[http://kubuntuforums.net/forums/index.php?topic=3081748.0]("http://kubuntuforums.net/forums/index.php?topic=3081748.0")

IndyTim

---

### Post by gregphil on 2008-09-12
That second suggestion was way to complex to figure out.  But I kept trying and seem to have found a solution !!

So to recap this is what I did:

1. downloaded kubuntu KDE 4 line CD image
2. burned iso image onto a CD
3. booted up kubuntu KDE 4 cd
4. selected "install" option
5. choose install destination to be an external USB disk
6. let installer do a "guided partiton" of entire USB disk
7. answered questions down to "Ready to Install" prompt
8. CAREFULL HERE ! clicked "advanced" button and
9. selected bootloader installation to be on USB disk (to leave my normal boot disk MBR alone)
10. let install copy files to USB disk (takes ~ 15 minutes)
11 reboot.
12 at existing GRUB menu (on internal harddisk) select the existing ubuntu install.
13.once logged into ubuntu, mount the USB drive
14. copy the USB drive /boot/grub/menu.lst selection entry lines
15. open the local internal hard disk /boo/grub/menu.lst
16. add (at the end) the lines copied from the USB grub menu.lst

Now for the tricky part...... (the GRUB menu won't work as is)

17. Edit the new final entry in GRUB's menu.lst on the internal hard disk to add rootdelay=15 to the end of the "kernel" line AND change the "root=" line to point at the internal hard disk instead of the external USB disk. For my system change (hd3,0) to (hd1,0) in the KDE4 section, note the kernel line "root=" info stays the same, it points at the USB disk UUID  

[HTML]<pre>

title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

title		Ubuntu  kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

title		Kubuntu kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		KDE4    kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=30252918-934c-435e-b092-5cdc4b969dfc ro quiet splash rootdelay=15
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

</pre>[/HTML]

I think this means I am using the copy of the kernel from the internal hard disk to boot, but the external USB disk for everything else.  Since the kernel version is the same on both disks this is fine with me.

18. save the /boot/grub/menu.lst on the internal hard disk

19. reboot and select the new menu item in the GRUB menu.

**********************************
Success ! it boots up into KDE 4 on the USB disk.  
20. Then use the adept updater to update the brand new KDE 4 install (about 80 Meg's worth) 
21. Then go to [www.kubuntu.org](www.kubuntu.org) and get the link to the new KDE 4.1.1 3rd party mirror:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
Open up adept updater and add the 3rd party location to the repositories list.
22. Finally let Adept update KDE to KDE 4.1.1 (about a 120 meg download). 
23. Reboot and select the new KDE 4.1.1 USB install.

This seems to be working fine (except for various KDE 4 issues)

Thanks for your help!

---

