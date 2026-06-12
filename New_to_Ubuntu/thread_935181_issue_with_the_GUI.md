---
title: "issue with the GUI"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by burn-e86 on 2008-10-01
When I boot up I cant access the GUI or get anywhere beyond the shell. I noticed that it gives me a message that tells me that the it cant resume from image before logging on.

I've tried using apt-get to upgrade what I've got already and installing Xorg-driver-fglrx then running 
sudo aticonfig --initial --force -input:/etc/X11/xorg.conf

but it gives me a message that the date is incomplete in file /etc/X11/xorg.conf


I then tried deleting the Xorg.conf and its backups and recreating it using 
sudo dpkg-reconfigure xserver-xorg 
but while it takes all my keyboard stuff it doesnt seem to wanna bother with the screen.

now when i run aticonfig --initial it gives me a message telling me to "please copy configuration file template to /etc/X11"

anyway Does anyone have any ideas? I also tried to run the liveCD but that doesnt work, it also just drops me into the shell.
btw this install is to my laptop
system is an Asus A8Series 
3Gb RAM
ATI Radeon HD2400

I did have it installed on my laptop a few months ago and everything was fine, after about a month or so it crashed and decided that it could not resume from the image. 
I got really frustrated, and after a while deleted the partitions and ran MBRFix. since then I've tried running SUSE, Fedora and Debian, none of which give me a GUI. SUSE and debian dont really do much and Fedora crashes and gives me a few lines of colour, regardless of whether it is installed or running the installer (i managed to install using the text option.). The first time that I instaled it was using the normal LiveCD, but this time around I had to use the alternative CD. the weird thing is that I didnt make any hardware changes or anything like that.

does anyone have any ideas as to the problem?

---

### Post by Terl on 2008-10-01
Maybe this will help get you started:  [http://ubuntuforums.org/showthread.php?t=586635](http://ubuntuforums.org/showthread.php?t=586635)  I see it says it is outdated, but there may be some useful info there.  Is this a very new card?  I know ATI is not the best at providing Linux support sometimes.

---

### Post by nowshining on 2008-10-01
> **burn-e86 said:**
> When I boot up I cant access the GUI or get anywhere beyond the shell. I noticed that it gives me a message that tells me that the it cant resume from image before logging on.

I've tried using apt-get to upgrade what I've got already and installing Xorg-driver-fglrx then running 
sudo aticonfig --initial --force -input:/etc/X11/xorg.conf

but it gives me a message that the date is incomplete in file /etc/X11/xorg.conf


I then tried deleting the Xorg.conf and its backups and recreating it using 
sudo dpkg-reconfigure xserver-xorg 
but while it takes all my keyboard stuff it doesnt seem to wanna bother with the screen.

now when i run aticonfig --initial it gives me a message telling me to "please copy configuration file template to /etc/X11"

anyway Does anyone have any ideas? I also tried to run the liveCD but that doesnt work, it also just drops me into the shell.
btw this install is to my laptop
system is an Asus A8Series 
3Gb RAM
ATI Radeon HD2400

I did have it installed on my laptop a few months ago and everything was fine, after about a month or so it crashed and decided that it could not resume from the image. 
I got really frustrated, and after a while deleted the partitions and ran MBRFix. since then I've tried running SUSE, Fedora and Debian, none of which give me a GUI. SUSE and debian dont really do much and Fedora crashes and gives me a few lines of colour, regardless of whether it is installed or running the installer (i managed to install using the text option.). The first time that I instaled it was using the normal LiveCD, but this time around I had to use the alternative CD. the weird thing is that I didnt make any hardware changes or anything like that.

does anyone have any ideas as to the problem?

as for the can't resume from images message - this is fine, the image is for suspend/hibernation and what ur seeing is what it is doing behind the splash screen before it goes into the kdm login screen - if u want u can install gdm and use it instead of kdm... :)

---

### Post by burn-e86 on 2008-10-01
I was told to get a print out of the log. unfortunitly I dont know how I could do that, so she told me to copy the WW and EE remarks, does this help at all?
from the top
(WW)The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
Entry deleted from font path.
(WW) ****INVALID MEM ALLOCATION **** B:0x0000000 e:0xc0000000 correcting^G
(WW) RADEON (0):R600 Support is mostly incomplete and very experimental
(EE) RADIEON(0):No valid linear framebuffer address
(EE) Screen(s) found, but none have usable configuration

---

### Post by nowshining on 2008-10-02
u can find the logs in /var/log/ and just open them up with kate/gedit.. :)

---

