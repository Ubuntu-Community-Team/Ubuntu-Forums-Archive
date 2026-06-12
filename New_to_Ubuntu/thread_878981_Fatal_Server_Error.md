---
title: "Fatal Server Error"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by 4evrnite on 2008-08-03
I got into Ubuntu/Linux & other distro's, over a year ago. Wanted to give Linux a try. I did give it a try, for a bit and went back to Win$loth. I really did not have a computer to install on, which is why I went back. I recently got a newer laptop and decided to use Linux on my old laptop, the beast, such as it is.

Anyways, I saw that Hardy was in "LTS" 8.04.1 and knew it was a stable version. I downloaded the Alt version, yesterday, 02 Aug 2008 and did a "command line" install, for low memory systems with Icewm. The install went without any problems and was way faster install than Dapper. The laptop specs are in my sig. Here are the probs that I am having:



Problem 1) This is what I get when I try to "startx":

(EE) S3VIRGE(0): Internal error: invalid bpp (32) in S3VScreenInit

Fatal server error:
AddScreen/ScreenInit failed for driver 0

waiting for X server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Sever error.


Now if I am reading that right, it is trying to load Icewm in 32bit mode and my laptop does not go that high. The max it can go is 24bit with screen size's of 1024x768, 800x600 & 640x480. Since I am unable to load Icewm, I am stuck at the command line.

----------------------------------------------------------------

Problem 2) When I run "sudo dpkg-reconfigure xserver-xorg" I get this after I configure the keyboard:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .2008080371416
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernal/drivers/acpi/battery.ko): No such device

I have no idea what that means^^.

----------------------------------------------------------------

Problem 3) I am have some probs getting on the internet, for updates, upgrades, installing, etc. I keep getting the same errors that this person was getting in this old thread:

[http://ubuntuforums.org/showthread.php?t=871015](http://ubuntuforums.org/showthread.php?t=871015)

Now I can get the updates, upgrades, etc., if I enter "sudo dhclient eth0" on the command line. But, I have to do that every time I want to get something from or on the internet. Although it works, it is just a pain to have to do that every time.


Any help on these matters would be greatly appreciated.

BTW, please do not ask me to do some command and post the results. Since I am unable to load up Icewm and therefore not able to get on the internet from that machine. That would mean I would have to manually type all that info in, like I did on the problems above, from my XP computer and that would be a Royal Pain In The Bum to do, since my typing and spelling are not that good.

Thanks, 
4evrnite

---

### Post by mattismyname on 2008-08-03
1] Edit /etc/X11/xorg.conf and look for lines containing the word "Depth".  Make sure they're set to 24 and not 32.  Save the file and try to start X again.

2]  I don't think that's a serious error.  I've always gotten that battery error as well.

3]  Make sure networkmanager is installed (sudo apt-get install network-manager).  It should handle automatically bringing the interfaces up.

---

### Post by 4evrnite on 2008-08-03
> **mattismyname said:**
> 1] Edit /etc/X11/xorg.conf and look for lines containing the word "Depth".  Make sure they're set to 24 and not 32.  Save the file and try to start X again.

2]  I don't think that's a serious error.  I've always gotten that battery error as well.

3]  Make sure networkmanager is installed (sudo apt-get install network-manager).  It should handle automatically bringing the interfaces up.

1] I looked in xorg.conf and depth is not in there. Since I can not post from that machine, I will copy the xorg.conf from a different thread and edit/change it to match mine:

```

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc101"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```


That is what mine looks like. In another thread I found this:

SubSection "Display"
Depth 24
Mode "1024x768"
EndSubSection

It said to put that in the "Screen" section. I forgot to mention that I did put the "SubSection" in and restarted the laptop, did "startx" and got the same thing in "Problem 1)". It still tried to load Icewm in 32bit mode.


2] Are you sure?? I know when you run "sudo dpkg-reconfigure xserver-xorg", it recofigures your language, keyboard, and screen resolutions, etc.. When I try it, I am unable to get past reseting up the keyboard. Meaning I can not set up the screen res at all. I just keep getting the same error in "Problem 2)". Also on start up and right after grub boots, I get this:

Starting up ...
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to Enable ACPI


3} Thank you for that, Did not know that existed, but, alas it did not work. I still have to do what is in "Problem 3)". How do I configure "network-manager" or can I I configure it??

---

### Post by mattismyname on 2008-08-03
For the last one, you could try: sudo /etc/init.d/networking restart

That's just a guess.

---

### Post by mattismyname on 2008-08-03
Nevermind that...looks like there's a different script to run networkmanager:

sudo /etc/dbus-1/event.d/25NetworkManager start
and
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher start

---

