---
title: "General Tips"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by mohaham on 2005-04-10
Hi Folks,

I came across some good tips for Debian users, check them out...

INSTALL

apm
* if ACPI doesn't work and/or your system is older, use apm

cpufreqd
*(manual and automatic adjusting of cpu speed)

gnome cpufreqd applet
* interface to above
go to /usr/bin as root and chmod +s cpufreq-selector (now you can change speeds by clicking on icon in gnome-panel)

laptop-mode-tools
* controls spindown of hard disks and cpu speed on/off battery

laptop-net
* auto configures networking when you plug in cable, disables when you unplug;

tpb (for thinkpads)
xosd
add nvram to /etc/modules (for thinkpads, maybe others)
* these add on-screen display and operation for laptop control buttons

if suspend doesn't work, add scripts in /etc/apm/suspend.d and resume.d to stop and restart alsa and pcmcia services which can interfere with suspend. It's easy... just copy an existing script and tweak it.

firestarter
* easy to use firewall - you can allow incoming connections by clicking on them or setting policies; I added it to the networking script to start/stop when networking did

ssh
* don't use ftp or telnet, use ssh for secure communications!


CONFIGURE:
change /etc/syslog.conf and reroute everything to /dev/tty8 instead of log files --> reduces disk activity and you can see stuff by pressing CTRL-ALT-F8

change /etc/hdparm.conf and add dma, 32bit, multisector and umask settings to your hard drive

change /etc/fstab and add noatime to all writeable media in the options section (ie. rw,user,noatime) These prevents your hard disk from writing access time on each file you read

change /etc/inittab and comment out all but the first two of the six console ttys... saves RAM

move /etc/exim4 DISABLED_exim4 and /etc/inetd DISABLED_inetd as these are probably useless services on a notebook

SECURITY

* prevent outside use of portmap
edit /etc/default/portmap to listen only to localhost
but keep it around for famd which automatically updates your file browser contents when they change

* not allow root login on consoles
mv /etc/securetty to DISABLED_securetty and touch and empty version; this forces you to login as a regular user and su to root

* not allow ssh root login
make sure you install and use ssh for communicating remotely to/from your notebook
edit /etc/ssh/sshd_config to remove rootlogin... again this means you must ssh in as a regular user and su to root

* remove linux info and warn off people
change /etc/issue to a prohibition on unauthorized use and email address for loss/theft. These file is displayed on consoles

* install nmap and run it to probe ports
you should have many other than cups, instant messenger, mail, portmap, etc.


*Original post --  [http://www.osnews.com/comment.php?news_id=9516](http://www.osnews.com/comment.php?news_id=9516)*

---

### Post by maqi on 2005-04-13
Nice :) 

Some very cool tips ... especially some simple ways to harden the system a little more. Thanks!

maqi

---

### Post by kuleali on 2005-04-13
Nice, :)

---

### Post by nickless on 2005-07-08
Nice tips, but can someone make them a bit more noob-friendly ? :D

> 
gnome cpufreqd applet
* interface to above
go to /usr/bin as root and chmod +s cpufreq-selector (now you can change speeds by clicking on icon in gnome-panel)

How's it called that thinggy? Synaptic didn't find anything like that :)
> 
change /etc/syslog.conf and reroute everything to /dev/tty8 instead of log files --> reduces disk activity and you can see stuff by pressing CTRL-ALT-F8

How can I do that? :D 
> 
change /etc/hdparm.conf and add dma, 32bit, multisector and umask settings to your hard drive

Well adding dma seems rather simple, but 32bit,multisector, umask (unmask?) ist seems more complicated, especially, because I don't dare to change anything there, without more information  :roll: 
> 
* prevent outside use of portmap
edit /etc/default/portmap to listen only to localhost
but keep it around for famd which automatically updates your file browser contents when they change

what? :? 
> 
* not allow root login on consoles
mv /etc/securetty to DISABLED_securetty and touch and empty version; this forces you to login as a regular user and su to root

Allright, I moved it, but what means "and touch and empty version" ?

If someone could just post some examplkes of what I have to type or how the file should look afterwards, It would be really great :)

---

### Post by mohaham on 2005-07-09
> 
 gnome cpufreqd applet
* interface to above
go to /usr/bin as root and chmod +s cpufreq-selector (now you can change speeds by clicking on icon in gnome-panel)


type this in a terminal
chmod +s cpufreq-selector 

then right click on the Gnome Panel -> add to Panel -> CPU Frequency Monitor....
now when u click on the CPU frequency Monitor, you will be able to change the CPU frequency Manually...

> 
change /etc/syslog.conf and reroute everything to /dev/tty8 instead of log files --> reduces disk activity and you can see stuff by pressing CTRL-ALT-F8

edit /etc/syslog.conf  like this

sudo gedit /etc/syslog.conf

at the end of file replace /dev/xconsole  with  /dev/tty8  or  /dev/tty1 

> 
 change /etc/hdparm.conf and add dma, 32bit, multisector and umask settings to your hard drive

here's my /etc/hdparm.conf file

/dev/hda {
        mult_sect_io = 16
        write_cache = off
        dma = on
        spindown_time = 56
        lookahead = on
}


> 
 * prevent outside use of portmap
edit /etc/default/portmap to listen only to localhost
but keep it around for famd which automatically updates your file browser contents when they change

ignore this..
when you install portmap, it by default listens only to localhost

> 
 * not allow root login on consoles
mv /etc/securetty to DISABLED_securetty and touch and empty version; this forces you to login as a regular user and su to root

ignore this..
root logins are disabled by default in Ubuntu

---

### Post by traherom on 2005-07-10
Nice, I didn't know the cpu scaling thing. :)

---

### Post by martigan on 2005-07-13
Excellent! 

For people using a Dell Inspirion 1150 / Intel Mobile 2.8 Ghz Laptop do:

sudo chmod +s cpufreq-selector

and add to your etc/modules : acpi-cpufreq

All others dont seem to enable scaling support somehow,


Kind regards 

Martigan

---

### Post by regeya on 2005-07-13
[QUOTE=kuleali]Nice, :)[/QUOTE]

Nice postcount incrementer

---

### Post by Tamir on 2005-07-13
[QUOTE=regeya]Nice postcount incrementer[/QUOTE]
 Thank you very much!, I will try the firewall thing.

---

### Post by nickless on 2005-07-14
thx mohaham :D

---

### Post by nickless on 2005-07-17
Still a proglem here :)
here is what I added:
```
/dev/hda1 {
	mult_sect_io = 16
	write_cache = off
	dma = on
	spindown_time = 56
	lookahead = on
}

/dev/hdb1 {
	mult_sect_io = 16
	write_cache = off
	dma = on
	spindown_time = 56
	lookahead = on
}

/dev/hdd {
       dma = on
}
```

I get errors when it tries to load these options. It's even telling me that there isn't a /dev/hdd device (should be my cdrom, if I believe fstab)

```

HDIO_SET_DMA failed: Invalid argument
HDIO_SET_MULTCOUNT failed: Invalid argument
[...]

```

---

