---
title: "Display configuration problems"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by tbrownarcher on 2008-09-01
If I'm posting in the wrong place excuse me and redirect me please.
I started a thread on my display card nvidia and intel too which are not recognized and or i cannot properly configure them. I thought I was posting here and so I am trying now to do so.  The previous thread was on Launchpad. 
Nothing I have tried works and so I'm bringing my problems here.

I have a 
Dell dimension 3000
2.8 mhz processor 
320 gig windows xp hard drive
100 gig ubuntu hard drive

I have a westinghouse  L2046NV Monitor

the mother board is an intel with both ethernet network card and video card integrated into the mother board.

I have also a ethernet card and an nvidia 5500 video card in slots

I cannot get my display resolution over 640 X 480

I can hardly use the computer because nothing fits the screen which i think is a 20 " screeen it might be 19 " not sure but I don't think it matters either.  I don't know

I actually have been told by the computer that I am using the Nvidia drivers but nothing works and I can't figger out how to configure it or the intel integrated card.

Thanks
Nate

---

### Post by doas777 on 2008-09-01
> **tbrownarcher said:**
> If I'm posting in the wrong place excuse me and redirect me please.
I started a thread on my display card nvidia and intel too which are not recognized and or i cannot properly configure them. I thought I was posting here and so I am trying now to do so.  The previous thread was on Launchpad. 
Nothing I have tried works and so I'm bringing my problems here.

I have a 
Dell dimension 3000
2.8 mhz processor 
320 gig windows xp hard drive
100 gig ubuntu hard drive

I have a westinghouse  L2046NV Monitor

the mother board is an intel with both ethernet network card and video card integrated into the mother board.

I have also a ethernet card and an nvidia 5500 video card in slots

I cannot get my display resolution over 640 X 480

I can hardly use the computer because nothing fits the screen which i think is a 20 " screeen it might be 19 " not sure but I don't think it matters either.  I don't know

I actually have been told by the computer that I am using the Nvidia drivers but nothing works and I can't figger out how to configure it or the intel integrated card.

Thanks
Nate

if you are using the restricted drivers, then just open a terminal and run:
```
sudo nvidia-settings
```

you can set your resolution there, after setting them, be sure to save ans click teh button "Write to xorg.conf".

hope that helps,
frank

---

### Post by tbrownarcher on 2008-09-01
Doas:
Ok will try that but I did try it before.  It did not work.  Will try it again this is a new install so here goes... I will post the text i get if i can copy it

Thank,
Nate

---

### Post by tbrownarcher on 2008-09-01
here is the post from the terminal

nate@nate-linux:~$ sudo nvidia-settings
[sudo] password for nate: 
sudo: nvidia-settings: command not found
nate@nate-linux:~$ sudo nvidia-settings
sudo: nvidia-settings: command not found
nate@nate-linux:~$ 

When I did this before there was a command that i invoked before sudo nvidia-settings
do you know what that would be ???

Thanks,
nate

---

### Post by tbrownarcher on 2008-09-01
Here is an additional thing i did in terminal

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install displayconfig-gtk

then I ran
sudo nvidia-settings 

and got this and i'm sorry its so long

nate@nate-linux:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
nate@nate-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30 ssl-cert
The following packages will be upgraded:
  anacron app-install-data-commercial deskbar-applet eog evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-exchange evolution-plugins firefox firefox-3.0
  firefox-3.0-gnome-support firefox-gnome-support gcalctool gdm gnome-about
  gnome-cards-data gnome-desktop-data gnome-games gnome-games-data gnome-panel
  gnome-panel-data gnome-system-monitor gtk2-engines gtk2-engines-murrine
  gtk2-engines-ubuntulooks gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hal
  initramfs-tools iproute language-pack-en language-pack-gnome-en
  libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libgdata-google1.2-1
  libgdata1.2-1 libglib2.0-0 libglibmm-2.4-1c2a libgnome-desktop-2
  libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1
  libisc32 libisccc30 libldap-2.4-2 liblwres30 libnspr4-0d libnss3-1d
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpcre3
  libpoppler-glib2 libpoppler2 libpurple0 libsmbios1 libwnck-common libwnck22
  libxslt1.1 linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic
  linux-restricted-modules-common nautilus-sendto pciutils pidgin pidgin-data
  poppler-utils procps python-gobject python2.5 python2.5-minimal tzdata ufw
  update-manager update-manager-core update-notifier update-notifier-common
  xserver-xorg-video-intel xsltproc xulrunner-1.9 xulrunner-1.9-gnome-support
  yelp
100 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 117MB of archives.
After this operation, 1917kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
nate@nate-linux:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
nate@nate-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30 ssl-cert
The following packages will be upgraded:
  anacron app-install-data-commercial deskbar-applet eog evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins
  firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support gcalctool gdm gnome-about
  gnome-cards-data gnome-desktop-data gnome-games gnome-games-data gnome-panel gnome-panel-data
  gnome-system-monitor gtk2-engines gtk2-engines-murrine gtk2-engines-ubuntulooks gtkhtml3.14
  gvfs gvfs-backends gvfs-fuse hal initramfs-tools iproute language-pack-en
  language-pack-gnome-en libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libglibmm-2.4-1c2a
  libgnome-desktop-2 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 libisc32 libisccc30
  libldap-2.4-2 liblwres30 libnspr4-0d libnss3-1d libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpcre3 libpoppler-glib2 libpoppler2 libpurple0 libsmbios1 libwnck-common
  libwnck22 libxslt1.1 linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic
  linux-restricted-modules-common nautilus-sendto pciutils pidgin pidgin-data poppler-utils
  procps python-gobject python2.5 python2.5-minimal tzdata ufw update-manager
  update-manager-core update-notifier update-notifier-common xserver-xorg-video-intel xsltproc
  xulrunner-1.9 xulrunner-1.9-gnome-support yelp
100 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 117MB of archives.
After this operation, 1917kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
nate@nate-linux:~$ sudo nvidia-settings
sudo: nvidia-settings: command not found
nate@nate-linux:~$

---

### Post by doas777 on 2008-09-01
what do you get if you run:
```
sudo apt-get install nvidia-glx-new
```
?

---

### Post by bob74 on 2008-09-01
lt/backspace to force a reboot and bingo I found that I now had the choice of four resolutions. 
Hope this helps.

---

### Post by tbrownarcher on 2008-09-01
Doas:
was afraid you would be mad at the length of the last post... glad your're still here.

here is my result of doing what you asked 

nate@nate-linux:~$ sudo apt-get install nvidia-glx-new
[sudo] password for nate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-new is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nate@nate-linux:~$ 

looks to me like I have everything I need just don't know how to configure it...

Thank,
Nate

---

### Post by Ryadt on 2008-09-01
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bob74 on 2008-09-01
Sorry only part of my reply appeared .
Go to terminal and type "sudo shutdown now" (without the quotes).
Go to XFIX and hit enter. When that finishes go to normal reboot and hit enter.. I found that everything froze at that so I did a Control/Alt/Backspace to reboot and bingo I had the choice of four resolutions.
Hope you are successful.
bob74

---

### Post by tbrownarcher on 2008-09-01
Doas:
did that and here is the result after getting a whole bunch of questions about my keyboard and none about my display.

sigh

nate@nate-linux:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080901015203
nate@nate-linux:~$ 





thanks,
Nate

---

### Post by tbrownarcher on 2008-09-01
Bob:
Well nothing froze it returned me back to the x repair screen
at the reboot line and i came back with no problem.  I just do not have any change in my resolution. ??????????????? grrrrr ??????????

Thanks,
Nate

---

### Post by Ryadt on 2008-09-01
Did you enable your graphic card? In Hardware Drivers.

---

### Post by tbrownarcher on 2008-09-01
seems it does not always post my posts so i answered but can't find the post so you probably cant either.

I did you you said about xfix 2 times .. i still have only 800 X 600 resolution.  My monitor is capable of 1400 x something in windows i use 1280 X 1024 or something close to that ... 

all the windows are off screen and the mouse has a terrible problem so I need somethign at least like 1024 X 768 .  I see nothing like that anywhere.

What you did last is automatic is there a manual type config ?

Thanks,
Nate

---

### Post by Ryadt on 2008-09-01
Try ```
gksudo displayconfig-gtk
```
Configure from there.

---

### Post by nisaky on 2008-09-01
I had similar problem (maybe same) and it all was good after i reinstalled Ubuntu. 

Did maybe once when you booted Ubuntu showed something about your resolution settings, and you pressed configure? When i did that my resolution stayed in 800X600 mode. Just try to reinstall Ubuntu, it worked to me.

---

### Post by tbrownarcher on 2008-09-01
well, i tried that and finally got a list of video cards.  
when i invoke the nvidia all i get is 680 X 480

When I do not then it uses the intel video card. at 800 X 600.  That's usable but not good so I will not be using ubuntu long if i can't get this fixed ... 

The manual mode configuration was not easy either but i did get it to give me my care nvidia gforce fx generic (it's a 5500) capable of much more but i can't get it to work. 

Could it be that I actually need to disable the intel integrated card.  I can find no place to do that either.

Thanks,
Nate

---

### Post by tbrownarcher on 2008-09-01
Nisaky:
I have already reinstalled and got exactly the same ... 
thanks,
Nate

---

### Post by Ryadt on 2008-09-01
Try ```
sudo apt-get install nvidia-settings
```
Then do ```
gksudo nvidia-settings
```
Try to configure with it.

---

### Post by tbrownarcher on 2008-09-01
seems to me this may be the entire problem.  
after doing what you said in your last post it said that i wasn't using nvidia card even though other places report that i am and told me to do the next ..... 'gksudo nvidia-settings' then 'nvidia-xconfig' and i got the next lines...

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.


I don't know but for some reason it could not write so that could be the problem???

thanks,
Nate

---

### Post by Ryadt on 2008-09-01
Post the output of ```
lshw -C Display
```

---

### Post by tbrownarcher on 2008-09-01
this is what i got as you typed it first and secondly as with the sudo:

thanks,
nate

---

### Post by Ryadt on 2008-09-01
> **tbrownarcher said:**
> this is what i got as you typed it first and secondly as with the sudo:

thanks,
nate
Sorry, but what did you get?

---

### Post by tbrownarcher on 2008-09-01
oops i thought i pasted it but i guess not .. this is getting confusing .. sigh


nate@nate-linux:~$ lshw -C Display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: Display controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5 module=nvidia
nate@nate-linux:~$ sudo lshw -C Display
[sudo] password for nate: 
  *-display UNCLAIMED     
       description: Display controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5 module=nvidia
nate@nate-linux:~$ 


thanks,
Nate

---

### Post by Ryadt on 2008-09-01
Is your graphic card enabled? In System > Administration > Hardware Drivers.

---

### Post by tbrownarcher on 2008-09-01
yes the graphics card is enabled in hardware drivers.

thanks,
nate

---

### Post by Ryadt on 2008-09-01
Try to update```
sudo apt-get update && sudo apt-get upgrade
```
then```
sudo apt-get install linux-restricted-modules
```Then retry to configure.

---

### Post by bob74 on 2008-09-01
I'v spent hours and hours on this video resolution problem in the latest release and in this case at least have stumbled across a method.
I should explain that out of curiosity I installed the KDE and XFCE desktops and now have a choice of three desktop enviroments.
I logged into KDE and looked at the system settings and when I got to Display and Graphics found that my monitor was recognised(not in the case of gnome) and could configure the graphics. As a result I had 25 choices of resolution so I selected 1024x768 which is what I wanted and bingo I was away. I logged out and logged back into gnome and guess what when I checked screen resolution found that I had the same range of choices.
If you want to try this route go to terminal and type
"sudo aptitude install kbuntu-desktop"  (without the quotes). When it's installed you get a screen giving you the choice of desktop, select KDE and proceed as above. You can always make gnome your default setting.  I intend leaving the additional desktops but you can uninstall using the "sudo aptitude uninstall kbuntu-desktop"  if necessary.
Good luck and confirm that I am correct and perhaps some bright spark will explain how different desktops using the same kernel can interact in this way.

---

### Post by tbrownarcher on 2008-09-01
Wow ! thanks! i will try it .. I like kde anyhow and i was going to that problem next so thanks.  I haven't tried it yet but will let you know ...

thanks,
Nate

---

### Post by tbrownarcher on 2008-09-01
wow thanks i was going to install kde anyhow ... i will let you know .. 

well, i did it and got no window after installation i then rebooted and still no window so i have no options unless i find them ?
thanks,
nate

---

### Post by tbrownarcher on 2008-09-01
I have not gotten kde installed though i thought i was on the way.  I can't do this anymore as it is my bed time ... i'm very tired and so i will resume tomorrow or the next day ... thanks

thanks very much
Nate

---

### Post by SpongeBob SquarePants on 2008-09-01
Not sure whether this will help anyone but with Heron I always have problems with my resolution. I have a nVidia card, and after installing the proprietary driver (be it via Envy or other), I always get a maximum resolution of 640 x 480.....even using the nVidia Control Panel. The problem for me was the wrong choice of monitor.

Type in....

gksudo displayconfig-gtk

...and choose your monitor, along with the correct resolution. If it's not in the list choose "generic" and the correct screen resolution. 

Ctrl + Alt + Backspace. That's what works for me anyway.

---

### Post by Aquaman420 on 2008-09-01
I did have a similar if not the same problem described in this thread.  I actually still have it on my desktop.  To shed some light on this problem apparently what is happening is the graphics cards are not getting/able to get the EDID sent from the monitor which is what tells the graphics cards the resolutions and refresh rates of the monitors, this is essentially how plug-n-play works as I understand it.  The fix is not easy but there are threads on it.  You essentially have to tell your xorg.conf not to send the edid to the graphics card and manually edit them in the xorg.conf.  I would do a thread search for edid and nvidia.  Hope this helps someone.  You could look in your /var/log/xorg.0.log or similarly named and see if that's what it says.

---

### Post by tbrownarcher on 2008-09-02
aquaman:
I don't know how to do any of that.  first of all I would love to look into /var/log/xorg.0.log.  It says it does not exist.... that's my first question.. I probably use to know how but not now i have forgotten . 

I went through some of that documentation and my head is spinning .. sorry..

thanks,
Nate

---

### Post by tbrownarcher on 2008-09-02
spongebob:

I have ran gksudo displayconfig-gtk many times and i cannot do much with it.  stubbornly ubuntu does not recognize my monitor and or my vid card.  it knows the vid cards are intel and nvidia but it does not know a thing about my monitor.. I don't blame it cause I don't either .. it's a westinghouse lcd. 20 inch i think. probably too new for ubuntu to have addressed I don't know.  I can get 800 X 600 with the intell for resolution and that's sorta workable but not preferable for sure.
The monitor will do 1400 x something and i'm sitting here struggling with 800 sigh..

thanks,
Nate

---

### Post by tbrownarcher on 2008-09-02
Bob74

this is what is get when i typed in the install procedure you sent to me .

I also got no window when you said i should so maybe i should go manual i don't know how to do it though 

I guess the reason is that it could not find anything to do /// .. so What do I do ?



nate@nate-linux:~$ sudo aptitude install kbuntu-desktop
[sudo] password for nate: 
Reading package lists... 10Reading package lists... Done
Building dependency tree...Building dependency tree...Building dependency tree...Building dependency tree...Building dependency tree       
Reading state information..Reading state information..Reading state information... Done
Reading extended state infoReading extended state infoReading extended state information       
Initializing package statesInitializing package states... Done
Building tag database... 0%Building tag database... Done
Couldn't find any package whose name or description matched "kbuntu-desktop"
Couldn't find any package whose name or description matched "kbuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... 10Reading package lists... Done
Building dependency tree...Building dependency tree...Building dependency tree...Building dependency tree...Building dependency tree       
Reading state information..Reading state information..Reading state information... Done
Reading extended state infoReading extended state infoReading extended state information       
Initializing package statesInitializing package states... Done
Building tag database... 0%Building tag database... Done
nate@nate-linux:~$ 

thanks very very much,

nate (tbrownarcher)

---

### Post by tbrownarcher on 2008-09-02
Bob74:
I have kde up and running partially.  Seems it has boot trouble but i can get it running so it's ok for now... however I still cannot get the resolution right and in one place i get that i'm running the nvidia card but in another it tells me i'm not so I don't know what to do from here .... 
thatnks,
Nate

---

### Post by SpongeBob SquarePants on 2008-09-04
> **tbrownarcher said:**
> spongebob:

I have ran gksudo displayconfig-gtk many times and i cannot do much with it.  stubbornly ubuntu does not recognize my monitor and or my vid card.  it knows the vid cards are intel and nvidia but it does not know a thing about my monitor.. I don't blame it cause I don't either .. it's a westinghouse lcd. 20 inch i think. probably too new for ubuntu to have addressed I don't know.  I can get 800 X 600 with the intell for resolution and that's sorta workable but not preferable for sure.
The monitor will do 1400 x something and i'm sitting here struggling with 800 sigh..

thanks,
Nate

No, Ubuntu doesn't recognize my monitor either. The "detect" button is a waste of time. Can you not pick the "Generic" option and then choose "LCD 1400x1050" or "LCD 1400x900"...and then set the resolution underneath if necessary? That's what I did and it works fine.

---

### Post by Screaming Monkey on 2008-09-05
tbrownarcher: can you post your /etc/X11/xorg.conf ?  I had a tough time getting some things right with my nvidia card (geforce T4 2100) and had to do a bit of tweaking to get things right.  It ain't easy is it?

---

### Post by Aquaman420 on 2008-09-11
I didn't fix my problem but I did circumvent it by using my vga cable instead of my dvi cable.

---

### Post by hdz on 2009-06-11
Hey, I see you're going through a lot of trouble here.  I have the same system as you (Dell Dimension 3000).  I have Nvidia, but a not-as-powerful card, but still came around the same probs as you initially before hardy and with hardy.  8.10 supposedly has this fixed where you cannot compile your own (i think) and 9.10 i dont know about.  But in either case unless i missed or scanned over the other replies you're missing a few things...  in the xorg.conf you need to edit the xorg.conf in /etc/X11 and put the line BusID    "PCI:1:0:0".  Well that's the line from mine in your driver section.  Make sure you replace nv or vesa driver with nvidia.  You should have edited /etc/modules and added the line glx.  Go into your bios as well and disable the onboard intel graphics card, you would much rather have the nvidia card you have (blazingly faster).  Make sure in system, administration, hardware drivers that your card is checked.  after you download the nvidia driver for your card (96.43.09 is the highest that worked for me, i have gotten every previous .05 .03 .01 to work, i'm working on the new .11 now but with the new 2.6 kernel, im having probs so i stay with .09.  this may not be for your card.  but the higher version driver would be if the 96's aren't.  go to [www.nvidia.com](www.nvidia.com) and search for your driver or go to terminal > type 'nano nvidia.html' and paste this into it:

<div><script 
src='http://www.nvidia.com/content/includes/js/AC_OETags.js' 
language='javascript'></script><script>AC_FL_RunContent('flashVars', 
'widgetVersion=vertical&widgetLanguage=en-us','src', 
'http://www.nvidia.com/content/DriverDownload/widget/v2/driver_widget','width', 
'320','height', '620','align', 'middle','id', 'driver_widget','quality', 
'high','bgcolor', '#869ca7','name', 'driver_widget','wmode', 
'transparent','allowScriptAccess','sameDomain','type', 
'application/x-shockwave-flash','pluginspage', 
'http://www.adobe.com/go/getflashplayer');</script></div>

alt+f+x hit y to save or use gedit or whathaveyou.  open that with a graphical browsers and it'll search for your card and show what driver you need.  you'll get an .run file downloaded and ya must exit X completely to install nvidia driver.  i reboot and when x selection screen comes up i hit ctrl+alt+f2 to get tty2 console screen er getty.  the black screen heh.  i login then type 

sudo /etc/init.d/gdm stop to get x to stop, i never got nvidia working in kubuntu, if you have both installed it will still work for gnome.  after that
sudo sh ./NVIDIA NVIDIA-Linux-x86-96.43.09-pkg1.run --extract-only

this is just to make the NVIDIA dir with the files so you can see what it's using, which has nvidia-settings and copies it and other stuff you were asking in posts.  after this do

sudo sh ./NVIDIA-Linux-x86-xx.xx.xx-pkg1.run 

xx where your correct driver for your card is, if you do not know do 

sudo lshw -C Display or sudo lspci -vv and copy the PCI:X:X:X down you'll need it.  if you have agp card it's still gonna say PCI:blah.blah

the package runs and hopefully you can hit agree, yes yes install and it'll finish compiling kernel and driver and copy to correct directories and removing conflicting x config's.

now you are back to console prompt and you want to edit your xorg.conf in /etc/X11 because for me anyway, the nvidia-settings, whether in gui or by command-line, never puts in the pci bus device under the display driver settings.  Here is my /etc/X11/xorg.conf:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
    Load           "extmod"
    Load           "dbe"
    Load           "type1"
    Load           "freetype"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync 30-81
    VertRefresh 60
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Busid          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "False"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

--

now if glx is not added where i have it and the others, do so, if dri is in there i'm not sure with your card but with mine you must remove it.  if i would of had nvidia-glx package installed, it would of overwritten my xorg.conf and not of had the PCI:1:0:0 in the driver section.  You MUST put that in manually when manually configuring nvidia driver for x.  then of course make sure /etc/modules has glx in there.  This took me a long time to figure out, but search for nvidia ubuntu on google it'll take you right to the NVIDIA HOWTO that you need, otherwise read the post below.  i edit the xorg.conf beforehand in my $HOME and just sudo cp myoxorg.conf /etc/X11/xorg.conf then to start x again after i installed my drivers and configured everything correctly;

sudo /etc/init.d/gdm start

it will automatically take you to ctrl+alt+f7 where x normally starts and you will notice the difference.  make sure the driver is loaded when you log into gnome inhardware drivers and then right click desktop, preferences and go to the last tab where it says visual effects, it will have none selected, try normal which gives you soooooo much better features, such as winkey+e (EXPO) like vista view but better or alt+tab changes a bit, and you'll notice you're not in 800x600 or 640x480, whenever you get that black screen with the grey box where it flicks a few times and says configure... cancel or continue it's prob not reading the PCI:thing in xorg.conf or some other config is wrong.  

so remove nvidia-settings with sudo, and nvidia-glx
download your nvidia driver
ctrl+alt+backspace to log out of x or just reboot
ctrl+alt+f2 or f3 f4 etc
login in console
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-blah-pkg1.run
sudo nano /etc/X11/xorg.conf and put in the Busid  PCI:whateer under driver
sudo echo "glx" >> /etc/modules or just so you have the glx and nvctrl extension loaded with driver
sudo /etc/init.d/gdm stop (or restart) to start x and that it son.  read the nvidia howto and get kernel for nvidia source and make sure libc6 up to date etc.  hope this scrambeled explanation helps

check the README.txt and nvidia settings in  /usr/share/doc/NVIDIA_GLX-1.0/ it will help you immensely.

---

