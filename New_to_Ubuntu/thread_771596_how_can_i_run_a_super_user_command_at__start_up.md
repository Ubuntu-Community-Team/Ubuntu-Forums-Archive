---
title: "how can i run a super user command at  start up ?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by nutpants on 2008-04-27
how can i run a super user command at  start up ?

the main online game i play is true combat elite. a mod for enemy territory..

but for sound to work i have to run
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
as a script as super user (sudo) after each restart of my laptop..

its a bit of a pain..

can i do it automatically?

(other than making a link in my menu to manually start, i would like to forget i have to do this each time.)

thanks for the help.

nutz

---

### Post by Bodsda on 2008-04-27
if the script is working then just add it into your sessions -- go to System--> Preferences--> Sessions    and add it there, this will run the script when you log in, however if you need to use sudo the i would add these lines of code to your script

This will reset the gksudo timer
```
sudo -k
```

and change any 'sudo'/'su' to gksudo

hope this helps

---

### Post by nutpants on 2008-04-27
surely there must be a way to pass the password for the super user command with out having to type it in each and every time the computer is restarted.

nutz

---

### Post by Bodsda on 2008-04-27
not without logging in as root -- which part of your script needs sudo?

---

### Post by zalberico on 2008-04-27
gnu/linux is set up so you are not root or the super user upon log in.  This is actually a security feature, one which many people say windows should really take in as well.  By not running as administrator you only allow access to that part of the system when you need to type and administrative command.  If you are always root or the super user and your system is compromised, the cracker or the virus will have complete access and be able to destroy your entire system rather than just one (replaceable) user account.  Sorry I don't know how to have you set default admin (you could log in as username root NOT recommended).  I Just thought you might not know the reason behind it.


Edit: I didn't realize you just wanted it for the script, never mind all this :)

---

### Post by daimaru on 2008-04-27
not sure this will work but try it. put your commands into the /etc/init.d/rc file  
that should start it at boot as root.

---

### Post by nutpants on 2008-04-27
> **Bodsda said:**
> not without logging in as root -- which part of your script needs sudo?

i dont have a clue,
i just found this info on a web site and the ghuy that did it said he ran it as a scrip as SU before each game.

thanks for the tips ill try the /etc/init.d/rc file

thing

nutz
( is there no way to do a
sudo -thisisthepassword sh runmyscript.sh     )
i know i could a few years back last time i played with linux, maybe it was the mandrake Linux but im sure it was still gnome

---

### Post by daimaru on 2008-04-27
um sorry better way to run a script at startup would be this.
Write a script. put it in the /etc/init.d/ directory.
Your script is called myscript. 

To run it at boot issue this command at terminal:
first make the script executable:
```
sudo chmod +x myscript
``````
update-rc.d myscript defaults  
``` For more info
  ```
man update-rc.d
```EDIT: well you might have to add some sudo's to the commands if it gives you access denied stuff

EDIT: for your script this would be 
```
sudo gedit /etc/init.d/myscript
```
```

#!/bin/bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
exit 0

```

---

### Post by Bodsda on 2008-04-27
ok this might work it might not -- 

add this to your script

```
password=$"enter your password here"
sudo -s ; $password
```

i doubt this will work but its the only thing i can think of

---

### Post by Monicker on 2008-04-27
> **nutpants said:**
> how can i run a super user command at  start up ?

the main online game i play is true combat elite. a mod for enemy territory..

but for sound to work i have to run
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
as a script as super user (sudo) after each restart of my laptop..

its a bit of a pain..

can i do it automatically?

(other than making a link in my menu to manually start, i would like to forget i have to do this each time.)

thanks for the help.

nutz


You can put the commands in /etc/rc.local, which run at each boot, after the other system services.

---

### Post by podfish on 2008-04-27
I recommend staying out of /etc/init.d, really.  You can create a script called /usr/local/start which will run with all the privileges it needs.  just make sure it starts with ``#! /bin/bash'' as illustrated above, and make sure you give it the executable bit with ``sudo chmod +x /usr/local/start''.  Anything you want to run at boot, just put it in here, and it will run after all the init stuff happens.

Likewise, anything in /usr/local/stop will run on shutdown, before all the init stuff gets killed.

This is the same solution all over the web for WolfET, as well--it must use the same engine.  The reason, of course, for this workaround is that the older quake-based games don't support alsa, and don't communicate properly with alsa's oss (the old sound crap) emulation.  Hope this helps.

SK

---

### Post by daimaru on 2008-04-27
> **podfish said:**
> I recommend staying out of /etc/init.d, really.  You can create a script called /usr/local/start which will run with all the privileges it needs.  just make sure it starts with ``#! /bin/bash'' as illustrated above, and make sure you give it the executable bit with ``sudo chmod +x /usr/local/start''.  Anything you want to run at boot, just put it in here, and it will run after all the init stuff happens.

Likewise, anything in /usr/local/stop will run on shutdown, before all the init stuff gets killed.

This is the same solution all over the web for WolfET, as well--it must use the same engine.  The reason, of course, for this workaround is that the older quake-based games don't support alsa, and don't communicate properly with alsa's oss (the old sound crap) emulation.  Hope this helps.

SK
hey thanks didn't know  about that .. I guess I'll have to shift a few script to /user/local/start

---

### Post by nutpants on 2008-04-27
> **podfish said:**
> I recommend staying out of /etc/init.d, really.  You can create a script called /usr/local/start which will run with all the privileges it needs.
Likewise, anything in /usr/local/stop will run on shutdown, before all the init stuff gets killed.

SK

now is this a bash script called "whatever" in the /usr/local/start/ directory
or is it a bash script called start in the local/ directory..

maybe im just dumb right now but neither one works for me.

thanks for the info.
nutz

edit
found this command that works
echo (password) | sudo -S (command)
but i would really like to get the "Anything you want to run at boot, just put it in here, and it will run after all the init stuff happens." working

---

### Post by podfish on 2008-04-28
/usr/local/start is actually a script by itself, but you can call other scripts from within it.

However, I think a previous poster is correct that it's /etc/rc.local on debian-based distributions like ubuntu.

SK

---

### Post by nowshining on 2008-04-28
> **Monicker said:**
> You can put the commands in /etc/rc.local, which run at each boot, after the other system services.

That's what I do for my sysmods :) however to make it easier you can just make a script, put it in /etc/ into a custom folder and make sure only root can access/view/edit it for safety of course then input the path to the script in the /etc/rc.local file.

example:

My script contents:

```


#!/bin/bash

# "open up" the PCI bus by allowing fairly long bursts
# for all devices, increasing performance
setpci -v -d *:* latency_timer=b0

#00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

setpci -v -s 00:00.0 latency_timer=b0

#00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])

setpci -v -s 00:1d.0 latency_timer=b0

#00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])

setpci -v -s 00:1d.1 latency_timer=b0

#00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller 
#3 (rev 02) (prog-if 00 [UHCI])

setpci -v -s 00:1d.2 latency_timer=b0

#00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])

setpci -v -s 00:1d.3 latency_timer=b0

#00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])

setpci -v -s 00:1d.7 latency_timer=b0

#00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])

setpci -v -s 00:1e.0 latency_timer=b0

#00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

setpci -v -s 00:1f.0 latency_timer=b0

#00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])

setpci -v -s 00:1f.1 latency_timer=b0

#00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])

setpci -v -s 00:1f.2 latency_timer=b0

#00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

setpci -v -s 00:1f.3 latency_timer=b0

#00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

setpci -v -s 00:1f.5 latency_timer=b0

#01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])

setpci -v -s 01:00.0 latency_timer=b0

#prefer inode/dentry cache to other caches
sysctl -w vm.vfs_cache_pressure=50

#set swappiness to zero/50%
sysctl -w vm.swappiness=50

#remove/disable pc cpeaker beeps
modprobe -r pcspkr

#cap bound echo 0xb0FEb0b0 ?> /proc/sys/kernel/cap-bound can prevent xfree86 from starting - keeps baad things from getting installed
#sysctl -w kernel.cap-bound=-100

#max kernel threads
#sysctl -w kernel.threads-max=8000

#set overcommit to strict 2
sysctl -w vm.overcommit_memory=2
#set overcommit ratio percentage to none
#vm.overcommit_ratio=0 #command not found :/ - moved to sysctl.conf
#kernel shared mem max & more
#Max size of shared memory in bytes
#sysctl -w kernel.shmmax=529006592
#This file contains the system-wide limit on the total number of pages of System V shared
#sysctl -w kernel.shmall=529006592
# This file specifies the system-wide maximum number of System V shared memory segments that can be created
#sysctl -w kernel.shmmni=650
#This file defines a system-wide limit specifying the maximum number of bytes in a single message written on a System V message queue
#sysctl -w kernel.msgmax=512000
#This file defines the system-wide limit on the number of message queue identifiers
#sysctl -w kernel.msgmni=25000
#his file defines a system-wide parameter used to initialize the msg_qbytes setting for subsequently created message queues. The msg_qbytes setting specifies the maximum number of bytes that may be written to the message queue
#sysctl -w kernel.msgmnb=512000

#read wakeup threshold
#sysctl -w kernel.random.read_wakeup_threshold=2048

#write wakeup threshold
#sysctl -w kernel.random.write_wakeup_threshold=2048

#pid max IDs
#sysctl -w kernel.pid_max=5000

#limit message rate
#sysctl -w kernel.printk_ratelimit=0

#limite message rate burst
#sysctl -w kernel.printk_ratelimit_burst=0

#Adjust the min and max read-ahead for files
#vm.max-readahead=50 #command not found for these :/ moved to sysctl.conf
#vm.min-readahead=50

#re-configure apt-get dpkg, synaptic on reboot in advance
dpkg --configure -a

#rebuld gcj database
rebuild-gcj-db

#rebuild sercurity providers
rebuild-security-providers 

#fix bs and delete
fix_bs_and_del

#Update Font Cache info. in /usr/shaare/fonts/
sudo fc-cache -f -v

#ldconfig
ldconfig

#let us clean up fonts and re-cache em'
dpkg-reconfigure fontconfig

#Update Locate Database
updatedb

#lets fc font cache again without the folders/dir
#fc-cache

#update pre-links links
prelink -m -R -a -f -q



 
```

My rc.lcoal file. (the one iine path that is #ed out is where it used to be.)

AGain these Are just an example to get your started, note tho that the rc.local file will startup exactly right after your login. If your wondering why I moved it, it is because of the security issues I finally saw when putting it in my home folder and the amount of damage it could do.

```
 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#/home/nowshining/scripts/sysmods
/etc/scripts/sysmods
exit 0



```

---

