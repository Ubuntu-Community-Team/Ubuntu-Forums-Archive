---
title: "HOWTO: Install InitNG for Ubuntu Hoary"
date: 2005-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by verbalshadow on 2005-05-27
HOWTO: Install InitNG for Ubuntu Hoary
Updated 26 Jun 05

WHAT IS INITNG:

From the readme

> "Initng is a full replacement of the old and in many ways deprecated sysvinit
tool. It is designed with speed in mind, doing as much as possible
asynchronously. In other words: It will boot your unix-system much faster, and
give you more control and statistics over your system.

The basic premise is that startup commands can be launched as soon as their
dependencies are met. This limits the effect of bottlenecks like I/O operations;
while one program is performing I/O, another can be utilizing the processor.
Initng tracks the individual service dependencies in its configuration files.

It is designed to use a minimum of system resources and to boot your system
quickly and safely."

What does that mean? Its the difference of giving birth to babies for humans and dogs.
Humans normal can have one baby at a time. Dog are capable of having many pups at one time.
So, getting a big family is easier for the dogs. Same is true for the Init process as well. Sysvinit does things one at a time. InitNG does as many as possible (and in the correct order) at once . This means a faster boot time for you and me.

INTRO:

There is a debian package out for InitNG you can get it [http://triggerit.tr.funpic.de/debian/initng/](http://triggerit.tr.funpic.de/debian/initng/). It is well done and installs with minimal problems but, I don't recommend it for use with Hoary for two reasons. When you use dpkg to install it you have to use --force-depends as it requires libc6 >= 2.3.2.ds1-21 , Hoary has 2.3.2.ds1.20ubuntu13. I have seen No Problems with running or compiling it against Ubuntu's version. The second reason is that SVN version has many fixes that make running it on Ubuntu better. If you do end up using the deb skip down to the Grub section.

PRE-INSTALL:
So we are going to build it from the Subversion Repository. Before for we do that make sure you apt-get or use Synaptic to install build-essianltals, svn and auto-make. Also if you have already install from a deb now is the time to remove it completely. You may want to print this out cause we will be rebooting during this HOWTO.

COMPILING AND INSTALL:

First we will get the source code from svn.

```
$ svn checkout http://jw.dyndns.org/initng/svn/initng
```

Once that is complete, we are going to compile it.

```
$ make
```

If there right any errors stop here. **IF NOT SKIP THE NEXT COMMAND**. Wait about 10-15mins then in the initng directory update the svn with the command below to update the src code. Remember svn is a moving target and the devs are actively updating the code and scripts.

```
$ svn up
```

Repeat the make command
```
$ make
```

If all went well with make than we can install now.

```
$ sudo make install
```

We are not done yet. We still have to setup Grub so we can boot to it.

SETTING UP GRUB:

We are going to edit the /boot/grub/menu.lst

```
$ sudo gedit /boot/grub/menu.lst
```

Scroll down to the bottom of the page. You should see something similiar to this.
Don't Panic if they it not totally the same. You maybe using a different kernel archieture then me.
> 
title		Ubuntu, kernel 2.6.10-5-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

We are going to copy and paste the top one right under itself. Now we are going to make InitNG are init of choice by adding this init=/sbin/initng to the end of the kernel line. Secondly we are going to change the title so we know what we are booting too Ubuntu InitNG is good. Your new entry should look similiar to below.

> title		Ubuntu InitNG 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda1 ro quiet splash init=/sbin/initng
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

Double check it. Looks good. Save it.

*Be aware that installing new/updated kernels in Ubuntu will overwrite this file.*

REBOOT. Right after you reboot grub will prompt you to enter the the grub menu if you are on a single OS system hit ESC before the countdown finishs. If you have dual-booting system then the menu will normal pop up by default unless you have changed this behavior.

Select are newly made entry. "Ubuntu InitNG"

Your system should boot( quickly i might add) and give you a the gdm login.If you don't get a login prompt it means that something failed to load and other boot process are waiting on it. Switch to tty2 by using ctrl-alt-f2.

Login.

Next we are going to check and make sure everything loaded alright.
Switch to tty2 or open a terminal
```

$ sudo ngc -s 
```

This shows us the list of services/daemons with there current status. I'm on a laptop and the screen with out framebuffering is small so i output the the list to a text file.
```

$ sudo ngc -s > ngc.lst
```

This is also good for troubleshooting what services are not running.
 
MAKING IT UBUNTU:
Add things that make Ubuntu what you expect.

```
$ sudo ng-update add hald acpid cupsd default
$ sudo ngc -x 
```

This add HAL, cups and Acpi to InitNG default runlevel. That should get you logged in the gnome with no errors displayed. There maybe some functionality missing that I havn't tried yet. If so let me know here or the InitNG forums.

ADD AND REMOVING SCRIPTS:
Add services to boot
```
$ sudo ng-update add * 
```
Delete services from boot
```
$ sudo ng-update del * 
```
where * is the name of the script or daemon

ok replace net/eth0 daemon/agetty with what ever you want to remove
SMALL THINGS THAT MAY NEED FIXING:
If you use a static IP address, the net/eth0 script doesn't set up eth0 correctly. I have been told a partial solution.
You need to edit /etc/initng/net/net.i

[HTML]$ sudo gedit /etc/initng/net/net.i[/HTML]


make the changes seen below in the start and stop portions.

```
service net/* {
	# */
	depend = system/mountfs system/modules system/hostname
	use = system/static-modules system/coldplug
	start {
		ifup ${NAME}
	}
	stop {
		ifdown ${NAME}
	}
}
```


ok this didn't not allow allow the eth0 to be config on boot but after boot(and log into gdm) i was able to now configure it using the networking dialog is the system->admin menu

 I have seen the dev/mapper/control error with the recent svn version i'm not sure the cause of it yet.

If you have a Nvidia graphics card you may have to use the drivers from nvidia to get to GDM login. see the initng.txt in the src code folder.

HATE UGLY TEXT BOOT:
i do have a partially work splashy init script to hide the uglies it does not update the progress bar but it does show the bootscreen.
save this to /etc/initng/daemon/splashy.i

```
service daemon/splashy {
	need = system/initial
	daemon = /sbin/splashy
	pid_file = /var/run/splashy.pid

start {
	start-stop-daemon --start --quiet --pidfile /var/run/splashy.pid \
		--exec /sbin/splashy -- boot 2> /dev/null
}

stop {
	start-stop-daemon --start --quiet --exec /sbin/splashy -- shutdown 2> /dev/null
}
```
then add splashy to the service by
```
$ sudo ng-update add splashy default 
```

WHERE TO GET HELP IF THINGS GO WRONG WITH INITNG:

The best place is the InitNG forums in the support section at [http://forum.initng.thinktux.net/](http://forum.initng.thinktux.net/)

---

### Post by Ninnghizidha on 2005-06-20
I dared it ....  ;-) 
And .. I'm still alive! :razz: 

... but it didn't work as supposed. Let me split my answer  into a few seperate parts:

1) The HowTo:
Everything worked fine, I installed subversion and compiled the package successfull. But i didn't think it is that clear, what this command does and how to use it: ```
$svn up
``` And I guess you should do this just in case you get errors, not the other way round.

2) The installation:
I installed it, edited the bootloader and started it up. It was quite fast! Really fast... At least at fast as the devil running away from a singing christian!! But - other than your HowTo said - I got the gdm-login. So, the gdm was running. I was happy about it, and entered. There I got my  first error "couldn't initialize HAL".

So, i started up a tty and entered the "ng-update"-commands ... which worked to. I rebooted, but it hanged while rebooting ... so i started over by a warmly push at the reset-button.

I started again, and since my drives were mounted 30 times - i got a while to read the messages initNG wrote: I saw, that initNG complained about the dev/mapper/control - if it were installed and so on...

The next error was quite big .. 3 lines filled with a string like "EEEEEEEEEEEERRRRRRRRRORRRRRRRRR" ...  but i wasn't able to read it, cause it booted so dam fast ... hehe ... but i managed to enter the graphical enviroment again. And again I read "couldn't init HAL" next to a new dialog-box - "Can't connect to gaim.". So, the eth0-static-adress-bug hit me.

So i tried to restart the PC, which started to hang again at the shu down: The last sentence it printed was "[GDM]    ......  [stopped]".

3) The Fazit:
This was enough for today ... i started up the old - and awfully slow (zzZZZ) - init-bootsequence .. but at least it worked - like I'm used to.

But i will try initNG again ... soon ... 


Thanks a lot for your guide,
Ninnghizidha.

---

### Post by tristan on 2005-06-21
I had a bit of a play with InitNG 0.1.3 tonight, and after a while I just took it off my system.

It built and installed without a hitch and on booting with InitNG took me right through to gdm without any need for intervention on my part. However I noticed that...

1 - InitNG went ahead and installed all the various startup services which I had specifically removed from my normal init, and so actually ended up taking just as long to boot as init! I've no idea how to remove them without a lot of hand editing.

2 - InitNG's implementation of dbus/hald doesn't actually work on my box, with a result that gnome-volume-manager won't start and I get no automounting of disks.

3 - The boot process was **UGLY**, and full of error messages. I'm used to booting with a nice splashy screen which hides all the ugliness! Splashy is not compatible with InitNG.

I actually think that InitNG is an excellent idea and will eventually make a hell of a difference to linux boot times, it just feels a bit rough around the edges at the moment (fair enough, it's only a 0.1 release). Maybe I'll wait a few more months, as the developers are certainly working at a furious pace.

Thanks for the howto anyway verbalshadow for inspiring me to try it out.

---

### Post by verbalshadow on 2005-06-21
Ok i'll answer what questions i can. Sorry it took so long for me too get back to you on your issues

[QUOTE=Ninnghizidha]1) The HowTo:
Everything worked fine, I installed subversion and compiled the package successfull. But i didn't think it is that clear, what this command does and how to use it:
Code:

$svn up

And I guess you should do this just in case you get errors, not the other way round.
[/QUOTE]

You are correct but svn up again won't hurt anything. all it does is bring the src code up to date from the SubVersioN repository.

[QUOTE=Ninnghizidha]
2) The installation:
I installed it, edited the bootloader and started it up. It was quite fast! Really fast... At least at fast as the devil running away from a singing christian!! But - other than your HowTo said - I got the gdm-login. So, the gdm was running. I was happy about it, and entered. There I got my first error "couldn't initialize HAL".

So, i started up a tty and entered the "ng-update"-commands ... which worked to. I rebooted, but it hanged while rebooting ... so i started over by a warmly push at the reset-button.

I started again, and since my drives were mounted 30 times - i got a while to read the messages initNG wrote: I saw, that initNG complained about the dev/mapper/control - if it were installed and so on...
[/QUOTE]

Newer builds of InitNG add dbus gdm and entranced automatically. so all you have you add using ng-update is hald acpid cupsd.
```
$ sudo ng-update add hald acpid cupsd default
``` I have seen the dev/mapper/control error with the recent svn version i'm not sure the cause of it yet.
[QUOTE=Ninnghizidha]
The next error was quite big .. 3 lines filled with a string like "EEEEEEEEEEEERRRRRRRRRORRRRRRRRR" ... but i wasn't able to read it, cause it booted so dam fast ... hehe ... but i managed to enter the graphical enviroment again. And again I read "couldn't init HAL" next to a new dialog-box - "Can't connect to gaim.". So, the eth0-static-adress-bug hit me.
[/QUOTE]

until today i didn't have a solution to the static ip problem. even then its only a partial solution but it is better then nothing.

You need to edit /etc/initng/net/net.i
```
$ sudo gedit /etc/initng/net/net.i
```
make the changes seen below in the start and stop portions.
```
service net/* {
	# */
	depend = system/mountfs system/modules system/hostname
	use = system/static-modules system/coldplug
	start {
		ifup ${NAME}
	}
	stop {
		ifdown ${NAME}
	}
}

```
ok this didn't not allow allow the eth0 to be config on boot but after boot(and log into gdm) i was able to now configure it using the networking dialog is the system->admin menu
[QUOTE=Ninnghizidha]
So i tried to restart the PC, which started to hang again at the shu down: The last sentence it printed was "[GDM] ...... [stopped]".

3) The Fazit:
This was enough for today ... i started up the old - and awfully slow (zzZZZ) - init-bootsequence .. but at least it worked - like I'm used to.

But i will try initNG again ... soon ... [/QUOTE]
Reboot and shutdown has a a few issues still :( i think this has to do with how fast its trying to shutdown but i'm not sure. i'm glad the issues didn't completely scare you away. it is beta software so bug are to be excepted.
[QUOTE=tristan]I had a bit of a play with InitNG 0.1.3 tonight, and after a while I just took it off my system.

It built and installed without a hitch and on booting with InitNG took me right through to gdm without any need for intervention on my part. However I noticed that...

1 - InitNG went ahead and installed all the various startup services which I had specifically removed from my normal init, and so actually ended up taking just as long to boot as init! I've no idea how to remove them without a lot of hand editing.
[/QUOTE]
ok. InitNG does not use sysvinit files to boot at all. It can be a pain i know sorry.
but the good news it is very easy to remove init scripts. first we need to see what scripts are loaded then remove what we don't want
```
$ sudo ngc -s
$ sudo ng-update del net/eth0 daemon/agetty
```
ok replace net/eth0 daemon/agetty with what ever you want to remove
[QUOTE=tristan]
2 - InitNG's implementation of dbus/hald doesn't actually work on my box, with a result that gnome-volume-manager won't start and I get no automounting of disks.
[/QUOTE]
I have no idea what is wrong here all my thumbdrives still automount. maybe that not what you mean. either way please post the details to the InitNG forum so the devs and people smarter then me can try and figure it out.
[QUOTE=tristan]
3 - The boot process was **UGLY**, and full of error messages. I'm used to booting with a nice splashy screen which hides all the ugliness! Splashy is not compatible with InitNG.
[/QUOTE]
i do have a partially work splashy init script to hide the uglies it does not update the progress bar but it does show the bootscreen.
save this to /etc/initng/daemon/splashy.i
```
service daemon/splashy {
	need = system/initial
	daemon = /sbin/splashy
	pid_file = /var/run/splashy.pid

start {
	start-stop-daemon --start --quiet --pidfile /var/run/splashy.pid \
		--exec /sbin/splashy -- boot 2> /dev/null
}

stop {
	start-stop-daemon --start --quiet --exec /sbin/splashy -- shutdown 2> /dev/null
}

}

```

i'm actually waiting for Upower to be released (by the guy who started usplash and splashy) he promises to support InitNG :) [http://www.nanofreesoft.org/index.php/Upower](http://www.nanofreesoft.org/index.php/Upower)

[QUOTE=tristan]
I actually think that InitNG is an excellent idea and will eventually make a hell of a difference to linux boot times, it just feels a bit rough around the edges at the moment (fair enough, it's only a 0.1 release). Maybe I'll wait a few more months, as the developers are certainly working at a furious pace.

Thanks for the howto anyway verbalshadow for inspiring me to try it out.[/QUOTE]

Its a great system who can complain about a total boot time of 15 sec.
be sure to come back. every release has better ubuntu/debian support.

---

### Post by 8FootSativa on 2005-06-25
Would the procedure be the same installing InitNG on Kubuntu?

---

### Post by verbalshadow on 2005-06-26
i don't know much about kubuntu but for the most part yes the install should detect kdm and set it up in the scripts to be loaded. 

if it doesn't you will need to remove gdm and add kdm in addtion to adding the command above.
after initNG boot and you get to the login, switch to tty2(or anyone but tty1 or tty10 thats were your Xserver is runnning)  login and run the following commands
```

$ sudo ng-update del gdm default
$ sudo ng-update add kdm default

```

Problems or things that you find you need to add or change please post here.

---

### Post by kamstrup on 2005-06-26
I tried a fresh snapshot of initng last night, but didn't get anything but a kernel panic. Furthermore my network was disabled when I rebooted with normal init... Or to be specific, my girlfriend noted that the network didn't work after I'd been playing around last night... Urgh - the icy breath of death was so close :-)

It was easy to fix luckily enough. I just had to click "Activate" in the network dialog... Phew.

---

### Post by kamstrup on 2005-06-26
Report from the front...

Ok, after a bit of menu.lst editing I got it "working". It does indeed boot fast when it works. The problem is that it does not seem to be able to boot again after it self has shutdown or rebooted the computer.

What I mean: 
 - Boot using initng. Everything but HAL seems to work :-). 
 - Shutdown. 
 - Restart again using initng. Computer hangs during boot without any error messages. 
 - Hard Reboot using normal init. Everything (including HAL) works. 
 - Shutdown. 
 - Reboot with initng and it works again (no hal)...

PS: The "sudo ng-update add hald acpid cupsd default"-trick got my printer and acpid working, but seemingly not HAL.

BOTTOMLINE:
Not ready for everyday use, but I will check it out regularly. It has great promise. Sort of reminds me of beagle version <=0.0.5 =D

---

### Post by dabear on 2005-06-26
OK, so I tried installing it, no problems. But when I boot using inting, it hangs at 84 per cent on some kinda service (or whatever). So I'm back to the ordinary init-thingy

---

### Post by charlieg on 2005-07-16
Just to note that if you want support for this or to report bugs, there is a dedicated Ubuntu section in the InitNG forums:
[http://forum.initng.thinktux.net/viewforum.php?f=6](http://forum.initng.thinktux.net/viewforum.php?f=6)

---

### Post by charlieg on 2005-07-24
Has anybody had any luck with [the latest initng](http://triggerit.tr.funpic.de/debian/initng/)?  (Latest being 0.1.4 at time of writing.)

---

### Post by crashd on 2005-08-02
I have hoary and I can install initNG 0.1.6?  
How I can upgrade libc6?

THX!

---

### Post by crashd on 2005-08-03
Ok, it works good! 
how I add pppoeconf at boot?

---

### Post by charlieg on 2005-08-12
Has anybody tried [runit](http://smarden.org/runit/) which seems to be fairly similar to InitNG?

---

### Post by tktreload on 2005-08-14
I also installed InitNG, and it seems to work fine. One thing that bothers me though is that i have to dhclient eth1 after boot, is there some place that I can set initng to start and bring up eth1 in stead og eth0?

after some reading, and trying out I found out a way to get out of "trouble".
I edited the script net.i in /etc/initng/net/
originally it said:

```
service net/* {
        # */
        need = system/mountfs system/modules system/hostname system/ifupdown-debian
        use = system/static-modules system/coldplug
        provide = virtual/networking
        start = /sbin/ifup
        start_args = $NAME
        stop  = /sbin/ifdown
        stop_args  = $NAME
}
```

and after editing I came out with:

```
service net/* {
        # */
        need = system/mountfs system/modules system/hostname system/ifupdown-debian
        use = system/static-modules system/coldplug
        provide = virtual/networking
        start = /sbin/ifup
        start_args = eth1
        stop  = /sbin/ifdown
        stop_args  = eth1
}
```

I guess it's a fairly simple way to take care of the problem, but I cant say that I'm sure that this edit has no ill effects elsewhere in the system.
I have had no problems so I'm happy

---

### Post by 8FootSativa on 2005-08-15
[QUOTE=charlieg]Has anybody tried [runit](http://smarden.org/runit/) which seems to be fairly similar to InitNG?[/QUOTE]

You can apt-get it if you want to try it (runit and runit-run), but do so with caution. I was unable to get it to work, though I most likely did something wrong.

If someone has been able to get it to work, please post your steps.

Runit looks much cleaner the initNG. :-)

---

### Post by lukanium on 2006-07-10
me, too. After apt-get install dchdbd ...everything works fine :)

---

