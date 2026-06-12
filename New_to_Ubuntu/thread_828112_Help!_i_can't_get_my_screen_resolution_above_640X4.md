---
title: "Help! i can't get my screen resolution above 640X480"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by CalvinMorrison on 2008-06-13
Hi I can't get my screen resolution above 640X480...

Yes i already tried to follow instructions that other people gave to us noobs on  other threads.


any help would be nice!


Thanks a tone

Calvin Morrison

[email]Crazycal00@gmail.com[/email]

---

### Post by noobuntu_ger on 2008-06-13
> **CalvinMorrison said:**
> Hi I can't get my screen resolution above 640X480...


Right after the installation of ubuntu ? My guess would be that u have to install a graphic card driver. 

Do u know what card you have ?

---

### Post by wolfen69 on 2008-06-13
what other instructions have you tried?

---

### Post by CalvinMorrison on 2008-06-13
I just searched it on the forums.

heres what i followed

.[http://ubuntuforums.org/showthread.php?t=806554&highlight=Screen+Resolution](http://ubuntuforums.org/showthread.php?t=806554&highlight=Screen+Resolution)

it worked on my freinds i just installed for him

but not on this one!

how do i know what driver i have?

---

### Post by wolfen69 on 2008-06-13
try this
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` reboot.

---

### Post by CalvinMorrison on 2008-06-13
okay i got this:

> 
calvin@Desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for calvin: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080613124004
calvin@Desktop:~$ 
calvin@Desktop:~$ 




---

### Post by CalvinMorrison on 2008-06-13
GREAT IT WORKS

thanks a bunch guys...

now it's at a good ol' 800X600.

---

### Post by alienexplorers on 2008-06-14
If you want to try for a higher resolution if your system can handle it make a modeline using gtf:
> terminator@terminator-desktop:~$ gtf 1024 768 70

  # 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync
You can add this to your monitor section of xorg.conf..

---

### Post by monkman on 2008-06-14
in my case it doesn' work. when i edit my xorg.conf like shown further down, ubuntu doesn't give me the option to turn to 12800x800.

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"mga"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1152	864
		Modes	"1280x800_60.00" "1152x864" "640x480@60"
	EndSubSection
EndSection
```

it's this video card

```
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 85)
```

i would like to access my desktop from my notebook without turning on the desktop monitor via ultravnc.maybee this is my problem?


solved this by raising the Virtual from 1152 864 to 1280 800 and turning on the monitor during login...

---

