---
title: "HOWTO: Installing Xfce 4.2"
date: 2005-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by peekj on 2005-01-26
I've written up a short guide on installing Xfce 4.2 on Ubuntu Warty Warthog. 

You can find it at [http://www.tuxme.com/node/358](http://www.tuxme.com/node/358)

---

### Post by barbarian on 2005-01-27
Very nice, thanx
 :-)

---

### Post by Buffalo Soldier on 2005-01-27
Excellent guide.

---

### Post by rapala61 on 2005-01-27
Very nice guide, but now i have no sound in Xfce 4.2, i have on Gnome tho...
Using the intel8x0 alsa driver cuz i have a nforce 2  chipset.. Abit NF7-S..
any hel appreciated..

---

### Post by DoubleDangerClub on 2005-01-28
I <3 you. :)  lol.  Man, I was looking for this exact article for the last 2 weeks.  Damn you rock!  great job.

DDC

---

### Post by matt on 2005-01-28
Very nice...worked perfectly as advertised. Thanks for the howto. Haven't decided if I'll keep it, since I like Gnome...but it does run nicely on my setup, which isn't exactly brand-new..

---

### Post by darkoptix on 2005-01-28
Great guide... XFCE runs a lot smoother than Gnome... Thanks!

---

### Post by JamesV on 2005-01-30
Dumb question, and I've never found this written anywhere I've looked: is the existing Gnome desktop removed first before installing Xfce, or is Xfce installed "on top of" the Gnome desktop?

---

### Post by rapala61 on 2005-01-31
Xfce is other window manager so  u will be given the oportunity to choose wich u want to use for ur session.... means=  no it wont uninstall gnome, u will be able to use gnome whenever u want just choose different session while in gdm.

---

### Post by arnoct on 2005-02-01
I got an error while installing:

configure: error: C++ preprocessor "/lib/cpp" fails sanity check

Any ideas?

[edit] Nevermind. g++ wasn't installed ^_^ </idiot>

---

### Post by rapala61 on 2005-02-01
[QUOTE=arnoct]I got an error while installing:

configure: error: C++ preprocessor "/lib/cpp" fails sanity check

Any ideas?

[edit] Nevermind. g++ wasn't installed ^_^ </idiot>[/QUOTE]

thats y one of the first things i do when reinstall warty is  # sudo apt-get install bin86 build-essential libncurses-dev  :)

---

### Post by knappen on 2005-02-02
Perfect, I was just looking for info on Xfce.

What would be the benefit of using Xfce over Gnome?

---

### Post by lycos on 2005-02-02
i tried to install xfce too. 
i installed all the files listed -dev files etc.
and after then i started the installing.
but i have little problem here.
root@ubuntu2:~ # ls
dbootstrap_settings                   Terminal-0.2.2-installer.bin
Desktop                               xfce4-4.2.0-installer.bin
gtk2-xfce-engine-4.2.0-installer.bin  xfce-goodies-4.2.0-installer.bin
install-report.template
root@ubuntu2:~ # chmod +x *.bin
root@ubuntu2:~ # xhost +localhost
localhost being added to access control list
root@ubuntu2:~ # sudo ./xfce4-4.2.0-installer.bin
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... pkg-config
Checking for GLib (GModule) >= 2.2.0... detected 2.4.7 in /usr
Checking for Gtk+ >= 2.2.0... detected 2.4.10 in /usr
Compiling installer-gui... failed, see /root/.xfce4.installer-log for details
Cleaning up... OK.
root@ubuntu2:~ #
also you can see the log file here: [the log file](http://www.geocities.com/saimaktay/thefile.txt) 
any help please... :cry:

---

### Post by Bdfy on 2005-02-02
to lycos: 
>>gcc: command not found :
apt-get install gcc 
BUT 
use apt-get install !!!!!! ( don't use .bin - it is bad for you package based system !!!!!
 )
[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

---

### Post by lycos on 2005-02-02
i managed to install xfce finally :)
after updating gcc and couple of something.
it is a great desktop manager really  :shock: 

but how can we take image of the screen here?

---

### Post by dusu on 2005-02-02
Hi, I've got 2 questions about xfce 4.2.

i) I'm currently using xfce 4.0. I would just like to know if xfce 4.2 and xfce 4.0 can live  together on one computer or if installing xfce 4.2 means getting read of xfce 4.0 ?

ii) Is there any way of apt-getting xfce 4.2 ?

---

### Post by Mr_Radarkontakt on 2005-02-02
I know this isn't the right way to do it, but I just added these lines into my sources.list:

#Debian Unstable

deb [ftp://ftp.de.debian.org/debian-non-US/](ftp://ftp.de.debian.org/debian-non-US/) unstable non-US/main
deb [ftp://ftp.de.debian.org/debian/](ftp://ftp.de.debian.org/debian/) unstable main contrib non-free
deb-src [ftp://ftp.de.debian.org/debian-non-US/](ftp://ftp.de.debian.org/debian-non-US/) unstable non-US/main non-US/contrib
deb-src [ftp://ftp.de.debian.org/debian/](ftp://ftp.de.debian.org/debian/) unstable main contrib non-free

And then installed Xfce4.2 
I haven't noticed any problems yet.

If you do like I did, remeber to comment the lines afterwards so you don't dist-upgrade the whole system to Debian Unstable.



//Mr Radarkontakt

---

### Post by vaskark on 2005-02-02
Installation worked great! I chose to install it locally. So how do I start it now? There's no gdm session entry for xfce-4.2 listed.

---

### Post by vaskark on 2005-02-02
I found out how to set it up for a local session here (Setting up GDM):
 
 [http://www.xfce.org/index.php?page=documentation&lang=en]("http://www.xfce.org/index.php?page=documentation&lang=en")
 
 I changed */usr* to */home/username/* in the path references, and copied the desktop file to */usr/share/xsessions*.

---

### Post by Jad on 2005-02-04
nice one! Thank you

---

### Post by dejitarob on 2005-02-04
Works great. I'm loving xfce - light, fast but still usefully feature-rich and easy.

---

### Post by KoolDrew on 2005-02-05
This isn't working for me.  Here is my log.

```
##
## Started installation of xfce4 at 08:35h
##
## Visit http://forum.os-cillation.com/ if you
## have problems using this installer.
##

# Environment variables
PATH is set to "/sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin:/bin:/usr/bin:/usr/local/ssl/bin:/usr/local/bin:/opt/openssl/bin:/usr/local/openssl/bin:/usr/pkg/bin:/usr/ucb:/usr/X11R6/bin:/usr/X11R6/bin:/usr/openwin/bin:/usr/local/bin:/opt/local/bin:/usr/pkg/bin:/opt/gnome2/bin:/opt/gnome/bin:/opt/xfce4/bin:/opt/xfce/bin:/root/local/bin:/root/xfce/bin:/root/xfce4/bin"
PKG_CONFIG_PATH is set to ":/usr/lib/pkgconfig:/usr/lib/pkgconfig"

## Checking for usable C compiler
gcc --version
/tmp/xfce4-4.2.0-installer/bootstrap.sh: line 1: gcc: command not found
## Checking for usable C++ compiler
g++ --version
/tmp/xfce4-4.2.0-installer/bootstrap.sh: line 1: g++: command not found
## Checking for GNU make
gmake --version
make --version
GNU Make 3.80
Copyright (C) 2002  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

## Checking for package config tool
pkg-config --version
0.15.0

## Checking for GLib (GModule) >= 2.2.0
pkg-config --atleast-version=2.2.0 glib-2.0 gmodule-2.0
Prefix=/usr
Cflags=-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
Libs=-Wl,--export-dynamic -lgmodule-2.0 -ldl -lglib-2.0  

## Checking for Gtk+ >= 2.2.0
pkg-config --atleast-version=2.2.0 gtk+-2.0
Prefix=/usr
Cflags=-DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
Libs=-Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  

## Compiling installer-gui (warnings enabled)
gcc -I. -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wl,--export-dynamic -lgmodule-2.0 -ldl -lglib-2.0   -O0 -o installer-gui main.c i2t/i2t-wizard.c i2t/i2t-page.c i2t/i2t-package.c   -Wall -Werror
/tmp/xfce4-4.2.0-installer/bootstrap.sh: line 172: gcc: command not found
## Compiling installer-gui (warnings disabled)
gcc -I. -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wl,--export-dynamic -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wl,--export-dynamic -lgmodule-2.0 -ldl -lglib-2.0   -O0 -o installer-gui main.c i2t/i2t-wizard.c i2t/i2t-page.c i2t/i2t-package.c   
/tmp/xfce4-4.2.0-installer/bootstrap.sh: line 172: gcc: command not found

```

---

### Post by lilpac on 2005-02-05
dit you start it under root?

---

### Post by Anubis on 2005-02-05
Perhaps you should add the directory containing `alsa.pc'
to the PKG_CONFIG_PATH environment variable
No package 'alsa' found

configure: error: Library requirements (alsa >= 0.9.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
!! Failed to configure xfce4-mixer, see the errors above
!! for details on the problem.

Where can I find `alsa.pc'?

---

### Post by KoolDrew on 2005-02-05
[QUOTE=lilpac]dit you start it under root?[/QUOTE]

Yes.

---

### Post by lilpac on 2005-02-05
[QUOTE=KoolDrew]Yes.[/QUOTE]

I Coulnd install Xfce propperly also the first time,
try installing kde first:

sudo apt-get install kde

afterwards try 2 install Xfce again :)
im not sure that this is gonna work though.

---

### Post by KoolDrew on 2005-02-05
Since I was having problems installing it this way I found a much better, faster and easier way.

[list]
[*]Open **/etc/apt/sources.list** as root and remove the **#** at the begining of the two URLs. 
[*]Run **sudo apt-get update**
[*]Run **sudo apt-get install xfce4**
[/list]

I got it up and running this way in no time.  Once it is installed you need to log out and choose sessions to change from the default.

---

### Post by Jad on 2005-02-06
what about keyboard indicator? any idea how to set it up?

---

### Post by Praetorian on 2005-02-07
This is my problem:
I have a old pc with a Pentium MMX 200 mhz and 96 mb.
how do I install XFCE. 
I been triening to install a base system like i is descripet here:

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Then I want to install XFCE but a only get errors.

Wat do I do wrong???

 :oops: sorry for my bad English :oops:

---

### Post by lilpac on 2005-02-07
OFFTOPIC

i don't know what chu do wrong :) but can i ask you something? :)
are you from games.telenet.be ? :p:p

greetz lilpac

---

### Post by rosslaird on 2005-02-09
> 
i) I'm currently using xfce 4.0. I would just like to know if xfce 4.2 and xfce 4.0 can live together on one computer or if installing xfce 4.2 means getting read of xfce 4.0 ?

ii) Is there any way of apt-getting xfce

i) Yes, you can have both -- if you installed 4.0 by way of Debian and 4.2 by way of the graphic installers from os-works. (Im sure you could make it work in other ways as well). Just put the 4.2 graphic-installer packages somewhere other than the 4.0 install.

ii) Yup. Enable the os-works repositories or the Debian Sid sources (careful with that last one to comment it out after). Look [here](http://www.os-works.com/view/debian/) for the os-works sources.

Ross

---

### Post by sputnik on 2005-02-17
Tried osworks sources and got the following  ](*,) 
> 
The following packages have unmet dependencies:
  xfld-desktop: Depends: xfce4 (>= 4.2.0.xfld-4) but it is not going to be installed
                Depends: xnetcardconfig but it is not going to be installed
                Depends: xterminal but it is not going to be installed
                Depends: rox-filer but it is not going to be installed

any ideas - should I be looking at sid? :eek:

---

### Post by tanari on 2005-02-23
The best way to install xfce is using xfce installer.

How to uninstall xfce ?

---

### Post by rosslaird on 2005-02-23
The installers are great. They are indeed the best way to install xfce. Get them from os-works, and make sure you get the Terminal installer as well.

As for uninstalling: the installer comes with an uninstaller, though I can't remember exactly where it lives. Either fire up the installer again and see if there's an "uninstall" option, or look in the bin directory where you installed xfce from the installer.

---

### Post by tanari on 2005-02-23
I have found it :)
```

cd /usr/local/bin
sudo ./xfce-goodies.uninstall
sudo ./xfce4.uninstall

cd /usr/bin
sudo ./gtk2-xfce-engine.uninstall

```

---

### Post by dejitarob on 2005-02-23
[QUOTE=sputnik]Tried osworks sources and got the following  ](*,) 


any ideas - should I be looking at sid? :eek:[/QUOTE]Have you tried the guide with the os-cillation gui installers originally posted at the top of this thread?

---

### Post by Karlos on 2005-02-26
OK....I have installed according to the blurb at the beginning of this thread

One problem tho...

when I log into a xfce session I have no desktop menu

I right click and nowt seems to happen ](*,)  
Any ideas..?

---

### Post by rosslaird on 2005-02-26
Make sure that you haven't started nautilus. Nautilus will take over the desktop (unless you tell it not to in gconf) and will kill the xfce desktop menu.
There's a guide somewhere on the xfce forums about this. (forum.xfce.org).

---

