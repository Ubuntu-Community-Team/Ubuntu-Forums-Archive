---
title: "HOWTO: Dual Boot Intrepid Ibex and Backtrack 3 (final)"
date: 2008-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Xnyper on 2008-12-25
Note: Backtrack is just a live distro bundled with a bunch of tools.  90% of the time, you can just install those tools on your Ubuntu partition and avoid the hassle of dual booting.  However, there are reasons (e.g. hardware support) for doing this.

Backtrack installs LILO as its bootloader, Ubuntu uses GRUB.  I prefer GRUB, so I installed Backtrack first and Ubuntu second, and that's what I'll be covering here.  

Take a look at my notes below and then follow steps one and two in the guide here: [URL="http://kin.calvin.free.fr/blog/?p=16"]
http://kin.calvin.free.fr/blog/?p=16[/URL]
[LIST]
[*]If you aren't comfortable with cfdisk or QTparted you can boot to the Ubuntu CD and use gparted to do your partitioning, just type this into a terminal:```
sudo gparted
``` 

[*]You'll want at least the following:

one reiserfs partition for Backtrack, 
one ext3 partition for Ubuntu
and some swap space


[*]Once you're booted to the Backtrack live CD, and have your partitions all set up, open qtparted (KDE menu -> system) and find the partition you set up to install Backtrack on.  Remember which one it is, you'll need it later (in my case it was /dev/sda1).


[*]To save the installer (from firefox) right click the link in the guide and select "save link as."  If you doubleclick the .kmdr file in Konqueror it will launch the installer.  It doesn't need to be anywhere special (I ran it from my USB thumb drive).
[/LIST]
Once The installation finishes, reboot.  LILO should boot you to the Backtrack login.  log in, type ```
startx
``` and make sure all is well with your backtrack install.

Put the Ubuntu CD in and reboot.  Install Intrepid Ibex as usual.  Be sure to opt against reformatting the whole drive.  You'll have to designate your ext3 partition as root, but the installation should be otherwise painless.

The Ubuntu installation takes a gander at your partitions and makes an educated guess about what other operating systems you might have installed.  It sees the backtrack installation and puts the following entry into your menu.lst:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		BackTrack (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz root=**current** ro vga = 769 
savedefault
boot
```

This is *almost* correct.  In my experience, selecting this option in grub causes a "kernel panic" and Backtrack fails to load.  In order to fix this, boot into Ubuntu, open a terminal, and type: ```
gksu gedit /boot/grub/menu.lst
``` (that's a lowercase L, not the numeral 1) Scroll down to the backtrack entry and change it like so:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		BackTrack 3
root		(hd0,0)
kernel		/boot/vmlinuz root=**/dev/sda1** ro vga = 769 
savedefault
boot
```
That thing I said we'd need later--it goes in the place of **/dev/sda1**.  If there are other details that don't match the above configuration, it is probably best to leave them be--at least for the first try.

Save the file and reboot.  When you select the Backtrack entry from the grub menu, it should boot nicely into backtrack.
[I]
Note: If you would rather Backtrack boot directly into X (rather than needing to log in and then type startx) you can edit /etc/inittab and set the default runlevel to 4 i.e. change this line:
```
# Default runlevel. (Do not set to 0 or 6)
id:3:initdefault:
```
to this:```
# Default runlevel. (Do not set to 0 or 6)
id:4:initdefault:
```[/I]



I will do my best to help people with questions, but to be honest: I'm not entirely sure why this worked in the first place (the change to menu.lst that is) so I am not sure how helpful I will be troubleshooting.

---

### Post by ren_mot on 2009-01-25
Thanks a lot for this post
it was exactly what I needed

---

