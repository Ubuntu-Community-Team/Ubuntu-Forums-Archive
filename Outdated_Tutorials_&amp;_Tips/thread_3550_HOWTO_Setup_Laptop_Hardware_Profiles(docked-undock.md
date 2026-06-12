---
title: "HOWTO: Setup Laptop Hardware Profiles(docked-undocked)/HOWTO: Modify init scripts"
date: 2004-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Magneto on 2004-11-07
I use Ubuntu on my Dell Latitude C640 laptop and since I might not have the same environment around me as I would with a stationary PC, I must configure my laptop to change certain system settings while mobile.
The instructions laid out here pertain to any laptop setup and the lesson on creating rc scripts can be applied by anyone regardless of the type of system.  
If you have an ati radeon 7500 M7 32mb video card you can use my XF86Config-4 files - just change the XF86Config-4.2 file to correctly reflect your monitor's abilities.
Configuring XFree86 is beyond the scope of this document.
And if you have multiple network devices you can use the eth0 script as well. Configuration of networking devices is also beyond the scope of this document.


The first step is analyzing the problem.
**What are my needs?**
[Color=Blue]1. I need both my wireless card card working and the onboard ethernet working while I am at my workstation.
2. By default I only want my wireless card working while mobile.
3. I need different XFree86/Xorg settings based on whether I'm at my workstation and connected to an external monitor or mobile using the Laptop's LCD.
[/color]

**Now that I know what I need, how do I go about finding a solution and applying it?**
Well, I know from my past experiences with Linux/Unix that when the system starts initialization it looks to /etc/inittab for the runlevel to start.  Basically runlevels are different levels the system can operate under which load or do not load certain programs. This is useful for a number of system administration tasks including our present situation.    
[Color=Blue]
In Debian, which Ubuntu is based on, you have 3 different actions that you must address. Here's the process:

1.)When you power on your computer, your bootloader can tell the system what runlevel to start off with or it can not specify anything and defer to the inittab default setting. The default bootloader in Ubuntu is GRUB which is the Grand Unified Bootloader.
2.)Next your init configuration file located at /etc/inittab, tells the system to go with the default runlevel, unless your bootloader has specified a particular runlevel
3.)Now /etc/init.d/rc begins to execute the scripts from the runlevel passed to it from their corresponding directory - for example in runlevel 2, rc looks in /etc/rc2.d/ for executable files.
[/color]

With that in mind, here's my solution -[b]
[Color=Red]1.) Modify Grub to add a Mobile option to my boot menu. Since I mostly use my laptop at my desk connected to my CRT and keyboard etc, I will have my Docked/Stationary configuration be the default.
2.)Create 2 scripts - one to modify my XFree86 settings and another to modify my eth0 interface configuration.
3.)Place my scripts somewhere /etc/init.d/rc can see them.
[/color][/b]


Now I can address my solution.

**1.) Modify Grub.**
The Grub configuration file is /boot/grub/menu.lst . When you startup your computer and it boots it launches Grub and if you press the Esc key when prompted a menu will appear. The listings in that menu come from the entries in /boot/grub/menu.lst. We now will modify this file. 

so open up a terminal.  By default in Ubuntu you are using gnome. If you right-click your desktop the first item you will see on the resulting menu is  Open Terminal.

type the following at the command line
```

sudo nano -w /boot/grub/menu.lst
```

page down to the bottom of this file and you will find the following :


```
 ## ## End Default Options ##
[Color=Green]
title		Ubuntu 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

```[/color]

The FIRST entry in this file that looks similar to this is your default boot setting```
 [Color=Orange]title		Ubuntu 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot [/color] 
``` 

Make the changes in red
 
```
 
 ## ## End Default Options ##

title		Ubuntu [Color=Red] Docked [/color]
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot


title		Ubuntu [Color=Red] Undocked [/color]
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash [Color=Red]3[/color]
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot


title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin


```

Note the RED 3 - this sets Grub to tell our system to start at runlevel 3 
The other changes in the " title  Ubuntu " area are just labels - you don't have to use the word docked or undocked - but using some type of label that you can easily interpret is the best way to set it up.


press Control+o to save your changes - and Control+x to exit nano

Here's what my /boot/grub/menu.lst file looks-  ***Note*** I have my own kernel compiled by me listed here in addition to another OS.  I normally would NOT leave all the commented out lines in there but Ubuntu has a grub-install command that I guess uses them so I left them alone

[B]
2.)Create our Scripts.


A.)xsetup [/B]

I have two XF86Config-4 scripts that I use. One is for using the CRT connected to my laptop and the other is for using the LCD.  The one for use with the CRT is labeled XF86Config-4.2 because it will be used with runlevel 2 which is our system default setup in /etc/inittab.  The file for the LCD display is named XF86Config-4.3 for use in runlevel 3 which is our mobile/undocked runlevel. These files are both located in the /etc/X11 directory.
Here's a link to my XF86Config-4.2 file. 
from a terminal do the following

```
 sudo nano -w /etc/init.d/xsetup 
```

xsetup you can copy this and paste it into your terminal by hitting Control+Shift+v
```
#!/bin/sh

case "$1" in
    start|restart|force-reload)
	echo -n "Configuring the X server: "
	echo cp /etc/X11/XF86Config-4.$RUNLEVEL /etc/X11/XF86Config-4
	cp /etc/X11/XF86Config-4.$RUNLEVEL /etc/X11/XF86Config-4
	echo "Done"
	;;
    lcd)
	echo -n "Configuring X for LCD: "
	cp /etc/X11/XF86Config-4.3 /etc/X11/XF86Config-4
	echo "Done"
	;;
    crt)
	echo -n "Configuring X for CRT: "
	cp /etc/X11/XF86Config-4.2 /etc/X11/XF86Config-4
	echo "Done"
	;;
    stop)
	echo To stop X, kill the gdm process manually
	ps -ef | grep gdm
	echo "Done"
	;;
    *)
	echo "Usage: /etc/init.d/xsetup {start|lcd|crt|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0

```
[Color=Red]
This is useless if you don't have different XF86Config-4 files.
[/color]

save the file like you did previously and exit nano

now type

```
sudo chmod +x /etc/init.d/xsetup 
```


```
sudo ln -s /etc/init.d/xsetup /etc/rc2.d/S20xsetup
```


```
sudo ln -s /etc/init.d/xsetup /etc/rc3.d/S20xsetup
```



**B.) eth0 script **

This script is run only in init 2 or runlevel 2 which is the default and its for another network that my laptop will connect to via the onboard ethernet. By setting it up this way when I am mobile aka runlevel 3 and not likely to be constrained by ethernet cables it wont be configured and I can always run this script at anytime to change things.


```
sudo nano -w /etc/init.d/eth0
```

copy and paste this modify it to your system's needs


```
#!/bin/sh

case "$1" in
   start|reload|force)
	echo -n "Setting up Onboard Ethernet: "
	echo eth0 192.168.2.17
	ifconfig eth0 192.168.2.17
	echo "Done"
	;;
    stop)
	echo -n "Stopping Onboard Ethernet: "
	ifconfig eth0 down
	echo "Done"
	;;
    gatew)
	echo -n "Setting Onboard Ethernet as Gateway Interface: "
	echo eth0 192.168.2.17
	ifconfig eth0 192.168.2.17
	echo route del default gw 192.168.5.73 eth1
	route del default gw 192.168.5.73 eth1
	echo route add default gw 192.168.2.77 eth0
	route add default gw 192.168.2.77 eth0
	echo "Done"
	;;
    primary)
	echo Setting Onboard Ethernet as Primary Interface
	echo -n "Shutting down wireless: "
	ifconfig eth1 down
	echo Bringing up eth0
	ifconfig eth0 192.168.2.17
	echo route add default gw 192.168.2.77 eth0
	route add default gw 192.168.2.77 eth0
	echo "Done"
	;;
    noprimary)
	echo -n "Switching back to Wireless: "
	ifconfig eth0 down
	ifconfig eth1 up
	ifconfig eth1 192.168.5.17
	echo route add default gw 192.168.5.73 eth1
	route add default gw 192.168.5.73 eth1
	echo "Done"
	;;
    *)
	echo "Usage: /etc/init.d/eth0 {start|reload|force|stop|gatew|primary|noprimary}"
	exit 1
	;;
esac

exit 0

```


now type

```
sudo chmod +x /etc/init.d/eth0 
```


```
sudo ln -s /etc/init.d/eth0 /etc/rc2.d/S20eth0
```

this is so I can run it from the commandline

```
sudo ln -s /etc/init.d/eth0 /usr/bin/eth0
```



[Color=Red]
That's it!!!!!!!!!!
[/color]
Now when you start your system by default it will be configured to use your external Monitor and onboard ethernet.

And when you select your 2nd boot option for Ubuntu Undocked your LCD settings will automatically be applied and your onboard ethernet will not be setup.


Those scripts have a few extra helpful items in them ;)

---

### Post by brschmid on 2004-11-07
hey, since i have a Dell Lat. D505, i have a question about yours (sorta off topic, sorry)

are the fonts a little blurry to you? on mine they are i have  a 15" XGA screen.

---

### Post by Magneto on 2004-11-07
[QUOTE=brschmid]hey, since i have a Dell Lat. D505, i have a question about yours (sorta off topic, sorry)

are the fonts a little blurry to you? on mine they are i have  a 15" XGA screen.[/QUOTE]
nope i have a hundred or so ttfs i use in addition to a good XF86Config - i have a 14.q tft at 1400x1050 24 bit which is the best resolution- if i set it otherwise its not as sharp

---

### Post by brschmid on 2004-11-07
[QUOTE=Magneto]nope i have a hundred or so ttfs i use in addition to a good XF86Config - i have a 14.q tft at 1400x1050 24 bit which is the best resolution- if i set it otherwise its not as sharp[/QUOTE]
 hmm, mine is 1024x768 no matter what :( stupid cheap dell, at least i get a new one next summer.

---

### Post by brschmid on 2004-11-09
hey, how about this one?

i want to be able to boot up my laptop and have it set up to auto-activate the correct wireless network profile, so i don't have to mess with the GUI when i get into linux.

is there a way to do this?

---

### Post by Magneto on 2004-11-09
[QUOTE=brschmid]hey, how about this one?

i want to be able to boot up my laptop and have it set up to auto-activate the correct wireless network profile, so i don't have to mess with the GUI when i get into linux.

is there a way to do this?[/QUOTE]

theres a couple of different ways to do this

create a runtime script similar to your cpufreqd setup, a script that would just invoke iwconfig with your wireless settings and you'd put that in a runlevel -/etc/rc$.d directory and change grub to add some menu options so when u boot up you automatically get into  your correct wireless network - but if u use more than a few wireless networks that might not be best
you could write a few scripts one for each setting and just click on a launcher on your desktop or some folder to change them or there's an app


or you can try quickswitch which does what my howto lays out some what
[http://muthanna.com/quickswitch](http://muthanna.com/quickswitch)

this is to load quickswitch as a notification applet in gnome or kde - then u can right click it and select the configuration u want
[http://edgesolutions.ca/muthanna.com/quickswitch/quickswitch-gnome.html](http://edgesolutions.ca/muthanna.com/quickswitch/quickswitch-gnome.html)

---

### Post by brschmid on 2004-11-09
[QUOTE=Magneto]theres a couple of different ways to do this

create a runtime script similar to your cpufreqd setup, a script that would just invoke iwconfig with your wireless settings and you'd put that in a runlevel -/etc/rc$.d directory and change grub to add some menu options so when u boot up you automatically get into  your correct wireless network - but if u use more than a few wireless networks that might not be best
you could write a few scripts one for each setting and just click on a launcher on your desktop or some folder to change them or there's an app


or you can try quickswitch which does what my howto lays out some what
[http://muthanna.com/quickswitch](http://muthanna.com/quickswitch)

this is to load quickswitch as a notification applet in gnome or kde - then u can right click it and select the configuration u want
[http://edgesolutions.ca/muthanna.com/quickswitch/quickswitch-gnome.html](http://edgesolutions.ca/muthanna.com/quickswitch/quickswitch-gnome.html)[/QUOTE]
 will try that since i use 4 different networks in a given week :)

---

### Post by Magneto on 2004-11-09
[QUOTE=brschmid]will try that since i use 4 different networks in a given week :)[/QUOTE]

with quickswitch you can also use it to run cpufreqd 
yeah 4 is more than youd want to do with runlevels and not really necessary
i looked for a .deb package for quickswitch a little bit but didnt see one

---

### Post by bporcaro on 2007-03-07
hi, i have insert into eth0 
export http_proxy="xxx.xxx.xxx.xxx:8080"
but when write on the shell
env | grep http_proxy
i not see http_proxy
Gaim it does not work

help me.

Sorry for my english, but i a m italian user

thank you

---

### Post by andrewsawyer on 2007-03-08
Hi All,

I have been trying to get this to work with 6.10 however I'm having problems.  I hope someone might be able to help me.

I can see that I needed to make some changes, using xorg.conf instead of XF86Config, so my /etc/init.d/xsetup file is as follows:

```
#!/bin/sh

case "$1" in
    start|restart|force-reload)
	echo -n "Configuring the X server: "
	echo cp /etc/X11/xorg.conf.$RUNLEVEL /etc/X11/xorg.conf
	cp /etc/X11/xorg.conf.$RUNLEVEL /etc/X11/xorg.conf
	echo "Done"
	;;
    lcd)
	echo -n "Configuring X for Single Monitor: "
	cp /etc/X11/xorg.conf.3 /etc/X11/xorg.conf
	echo "Done"
	;;
    crt)
	echo -n "Configuring X for Xinerama: "
	cp /etc/X11/xorg.conf.2 /etc/X11/xorg.conf
	echo "Done"
	;;
    stop)
	echo To stop X, kill the gdm process manually
	ps -ef | grep gdm
	echo "Done"
	;;
    *)
	echo "Usage: /etc/init.d/xsetup {start|lcd|crt|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0
```

unfortunately, which ever boot option I choose, I get Xinerama - it doesn't copy the xorg.conf file.

Does anyone have any suggestions on a fix for this?

Cheers,

Andy

---

### Post by har5ha on 2007-07-22
> **andrewsawyer said:**
> Hi All,

I have been trying to get this to work with 6.10 however I'm having problems.  I hope someone might be able to help me.

I can see that I needed to make some changes, using xorg.conf instead of XF86Config, so my /etc/init.d/xsetup file is as follows:

```
#!/bin/sh

case "$1" in
    start|restart|force-reload)
	echo -n "Configuring the X server: "
	echo cp /etc/X11/xorg.conf.$RUNLEVEL /etc/X11/xorg.conf
	cp /etc/X11/xorg.conf.$RUNLEVEL /etc/X11/xorg.conf
	echo "Done"
	;;
    lcd)
	echo -n "Configuring X for Single Monitor: "
	cp /etc/X11/xorg.conf.3 /etc/X11/xorg.conf
	echo "Done"
	;;
    crt)
	echo -n "Configuring X for Xinerama: "
	cp /etc/X11/xorg.conf.2 /etc/X11/xorg.conf
	echo "Done"
	;;
    stop)
	echo To stop X, kill the gdm process manually
	ps -ef | grep gdm
	echo "Done"
	;;
    *)
	echo "Usage: /etc/init.d/xsetup {start|lcd|crt|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0
```

unfortunately, which ever boot option I choose, I get Xinerama - it doesn't copy the xorg.conf file.

Does anyone have any suggestions on a fix for this?

Cheers,

Andy

Andy, I made some modifications metioned below .... And it works  on **Ubuntu Fiesty** !! 

Try the following, and remember to **backup all the files you are editing**..  

I modfied my **/etc/event.d/rc-default** file [the modified part is in **bold**] 

> 
# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
            telinit S
[B]        elif grep -qE -w -- "[0-9]" /proc/cmdline; then
            RL="$(grep -Eo -w -- "[0-9]" /proc/cmdline)"
            if [ -n "$RL" ]; then
                telinit $RL
            else
                telinit 2
            fi[/B]
        elif [ -r /etc/inittab ]; then
            RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
            if [ -n "$RL" ]; then
                telinit $RL
            else
                telinit 2
            fi
        else
            telinit 2
        fi
end script


The following is my **/boot/grub/menu.lst** file to pass the the runlevel **3** parameter.

> title           Ubuntu - Laptop Mode [2.6.20-16-generic]
root            (hd0,5)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=4a2ed98c-a04c-47eb-b978-4b3e4ae1ea59 ro quiet splash **3**
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by andrewsawyer on 2007-07-23
Thank you!

I'll give it a try!

Andy

---

