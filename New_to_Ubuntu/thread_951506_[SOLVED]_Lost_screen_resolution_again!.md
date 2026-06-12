---
title: "[SOLVED] Lost screen resolution again!"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-10-18
Hi,

I lost 1024x768 screen resolution after recent upgrade to 2.6.27-7-generic kernel. The terminal says "displayconfig-gtk command not found".  Also
here's the terminal output after I tried to reconfigure xserver-xorg:

hoe1@hoe1-laptop:~$ sudo dpkg-reconfigure -phigh xserver.xorg
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed

So, how do I install xserver.xorg?

Here's the result of "sudo gedit /etc/X11/xorg.conf" (My Toshiba Satellite Pro4600 laptop uses Trident Microblade video card):


"Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection"

Please help me.  Thanks a lot!

:confused:

---

### Post by iClouseau88 on 2008-10-19
Please help me.  Here are additional info:

System>Preferences>Hardware Info>Device Manager>Devices:

82815 815 Chipset AGP Bridge
Cyberblade/XP

Vendor: Trident Microsystems
Device: Cyberblade/XP (video card)
Status: Status
Bus Type: PCI
Device type: unknown
Device capacity:unknown

Systen>Administration>Hardware Drivers:
"No proprietary drivers installed on this system"

It appears that when I updated to kernel 2.6.27-7 generic, X.org was upgraded and as a result, the ATI driver for thee Cyberblade video card was removed and so was "displayconfig-gtk".

Could you show me how to re-install the correct ATI driver for the above Intel 82815 chipset and Cyberblade video card?

I am lost.  Thanks a lot for your help.

---

### Post by BDNiner on 2008-10-19
Does the display return to normal when you use an older kernel? To choose a different kernel select it from the grub menu when you boot the computer.

---

### Post by Sealbhach on 2008-10-19
Is it 

xserver-xorg

or

xserver.xorg

?

Because the command you gave was:
```

sudo dpkg-reconfigure -phigh xserver.xorg
```

I think it should be 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

[http://www.google.co.uk/search?hl=en&safe=off&q=%22-phigh+xserver.xorg%22&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&safe=off&q=%22-phigh+xserver.xorg%22&btnG=Search&meta=)

Hope this sorts it out for you.


.

---

### Post by BDNiner on 2008-10-19
good eye, i completely missed that.

---

### Post by iClouseau88 on 2008-10-19
Hi,

I must have had a typo.  Here's what's on the terminal after I typed the command correctly:

hoe1@hoe1-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for hoe1: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081019165309
hoe1@hoe1-laptop:~$ 

Nothing else haappened.  Where do I go from here?  I have not tried staarting with an older kernel.

---

### Post by iClouseau88 on 2008-10-19
Hi,

I restarted Intrepid with an older kernel, i.e.  2.6.27-4.  Still get 800x600 screen resolution!

---

### Post by RedRat on 2008-10-19
I commiserate with you because my system got borked in a similar manner earlier this week with an update of the kernel in 8.04. The only way around was to re-install my NVidia video driver, which is an envyng driver. You can try that and see if you get your resolution back.

---

### Post by iClouseau88 on 2008-10-20
How do I  re-install (ATI?) video driver for Trident Microblade/XP video card?

Can anyone please help?

---

### Post by iClouseau88 on 2008-10-20
bump

---

### Post by peejamm on 2008-10-20
so "sudo displayconfig-gtk" doesn't work?

---

### Post by iClouseau88 on 2008-10-23
Nope!  I also found that Systems>Preferences>Hardware Drivers show "No proprietary Drivers" even though the 2 driver files called "ati_drv.so"and "trident_drv.so" are indeed within my computer.  How do I get Intrepid to read and load these 2 files?

I have seen many users whose screen resolution was messed up by the upgrade to Intrepid but so far even as RC1 is introduced today not one word came from Ubuntu about solution to this problem!

---

### Post by iClouseau88 on 2008-10-24
bump

---

### Post by iClouseau88 on 2008-10-24
Anyone at all?

Please help! I am getting desperate!

---

### Post by iClouseau88 on 2008-10-24
bump

---

### Post by iClouseau88 on 2008-11-09
Following sdavmor's suggestions in Hardware & Laptop sub-forum, I was able to get my 1024x768 resolution back! Perhaps what work were the facts that:

1) Trident driver is included in Section "Device";

2) HorizSync 28-51 was added to Section "Monitor". Note that in some older xorg.conf file I used "28-31" so "31" could have been a mistake;

3) VertRefresh 43-60 was added as well;

4) I used gtf command to generate the "Modeline" entry;

5) DefaultDepth24 was added just above "SubSection "Display"" of Section "Screen"

Here's my currently up-to-date xorg.conf file:

Section "Device"
Identifier "Trident Microsystems CyberBladeXP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
Option "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Generic Monitor"
Device "Trident Microsystems CyberBladeXP"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768_60.00" "800x600"
EndSubSection
EndSection

Now, how do I back up this xorg.conf file so that X doesn't get messed up the next time Ubuntu release a newer distribution and a new kernel? Secondly, where is the button to mark this thread as "SOLVED"?

My faith in Ubuntu Intrepid and Ubuntu Forums users have been restored. It's been tough for the last 2 weeks that I had to endure a smaller (i.e. 800x600) screen.

Cheers!

---

