---
title: "computer does not run dvd to boot from ..."
date: 2014-06-05
forum: New to Ubuntu
---

### Post by michael170 on 2014-06-05
Hello.

I am completely new to Linux.

Over the years I have completely migrated to open source programs so I figure now it as good as time as any to switch operating systems.

I have two ( both antique ) computers.

The "old" one is a Dell 2400 ( P4, 256 ram ) ... was going to throw it away ( it was free ) but I have kept it as an XP box "just in case".

The "newer" is a Dell Inspiron 530 (2009, Core 2 Due 2.4 GHz, 4 gig ram, on board intel graphics)... (bought is used when my computer blew up and I need one quick).  I am running Windows 7 on it now with no problem.

I actually downloaded and tried "Mint Cinnamon 17" on the newer one and it ran great off a DVD.  I tried "Mint Mate 17" on the old one ..... slow but it still came up.

Before installing either, it was suggested to me that I "try a few flavors" of Linux before committing to any one.

So I downloaded Ubuntu 14.04 and Lubuntu 14.04

On the newer computer, I can not get past a purple screen Ubuntu and a few dots on it ( at first it did not even get to this point ... only to a purple screen with a symbol at the bottom)

Ironically, in the old computer, I got to a screen that said install or try ... but it would not get any further.

On the old  computer, I tried Lubuntu ... got to the install, try, test screen but after hitting try, nothing happens.

What do I do now?  is there any way to get Ubuntu to load onto my computer?

Thanks .... Mike

---

### Post by hollowsyndicate on 2014-06-05
try hitting any key on boot when you see the little man in the circle icon on the purple screen, hit F8 (I think), and set nomodeset. see if that works

---

### Post by oldos2er on 2014-06-05
According to the [Lubuntu wiki]("https://wiki.ubuntu.com/Lubuntu") the desktop installer needs a minimum of 384MB RAM. You could try the [alternate iso]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") instead.

---

### Post by oldfred on 2014-06-05
My two core2Duo systems are from 2006 with 1.5GB of RAM on laptop and 4GB of RAM on Desktop. Desktop was updated in 2009 to new nVidia card and motherboard and in 2012 to add an SSD.
Both run the 64bit version of Ubuntu, but laptop runs Unity so slow that it is unusable. So I use and prefer the older menu and top & bottom bars that fallback/flashback gives.

       [http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)

      
 [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

Your older system may need the 32 bit version, but your newer system should use the 64 bit version.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by grahammechanical on 2014-06-05
The minimum RAM for Ubuntu is 512 MiB with 1024 MiB (1GB) preferable. The minimum for Xubuntu and Lubuntu is 512 MiB. With Ubuntu the graphic card is also important. I doubt if the graphic adapter in the Dell 2400 will have the punch to run Ubuntu Unity. The minimum is [COLOR=#333333][FONT=Ubuntu]3D Acceleration Capable Videocard with at least 256 MB memory. The machine only has 256 MB RAM. The video memory must be much, much less than that.

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.[/FONT][/COLOR]

---

### Post by michael170 on 2014-06-05
Hmmmm .....

So I gave up on the old computer for now and concentrated on the newer one.

OK, so I was able to get to the options .... F8 ..... and I choose nomodeset along with acpi=off

When I hit enter, it just sat there on the options screen ... never went further.

I will have to go deeper into this.

I am still surprised it had no problem at all with Mint Cinnamon 17 ... which I was under the impression took more resources than Ubuntu.

Anyway, I will keep trying.  I will even download the iso again so I make sure I have a good disk (someone told me there was a way of verifying it ...but I can't figure out how).

Thanks ..... Mike

---

### Post by oldfred on 2014-06-05
You can verify the ISO with its md5sum.

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

