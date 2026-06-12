---
title: "HOWTO: Reducing boot time in Breezy using InitNG"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by temcat on 2005-10-22
[B]Attention: The latest info in InitNG can be found on [https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG).

This HOWTO is outdated. I stopped to maintain it, since I was running Windows exclusively for some time, and then decided I can live with classical init as it is.[/B]

Frustrated with the long boot time in Breezy and want to do something about it? Here comes the remedy! Meet InitNG - a new generation init program that is able to reduce your boot time by a third to a half. Below are step-by-step instructions how to do it on your system.

IMPORTANT: InitNG is pretty much work in progress, and not all things may work. Currently it does everything I personally want, but it may not be the case for you - your success depends on the combination of hardware and software you use. Suggestions, fixes, hacks and workarounds offered by people will be incorporated in this HOWTO.

1. Download InitNG version 0.3.3-2 from [http://alioth.debian.org/download.php/1230/initng_0.3.3-2_i386.deb](http://alioth.debian.org/download.php/1230/initng_0.3.3-2_i386.deb)

2. Install it:

```
sudo dpkg -i initng_0.3.3-2_i386.deb
```

3. Change the content of dbus.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/attachment.cgi?id=69](http://bugzilla.initng.thinktux.net/attachment.cgi?id=69)

4. Change the content of hald.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/attachment.cgi?id=70](http://bugzilla.initng.thinktux.net/attachment.cgi?id=70)

5. Set up gdm/kdm to load on default runlevel. To do that, run

```
sudo ng-update add daemon/gdm default
```

if using Gnome, or

```
sudo ng-update add daemon/kdm default
```

if using KDE.

6. Set up coldplug to run on system runlevel (we need this to have working sound - thanks Bitmastro!):

```
sudo ng-update add system/coldplug system
```

7. OPTIONAL: Set up various things that you may or may not need.

7.1. Start ADSL modem on boot (when using eciadsl driver)

7.1.1. Create a file called eciadsl.i with the following content:

```
service system/eciadsl {
    need = system/initial system/mountfs system/usb
        
start {
    /usr/local/bin/eciadsl-start
}

stop {
    /usr/local/bin/eciadsl-stop
}
}
```

7.1.2. Put this file in /etc/initng/system directory.

7.1.3. Set ADSL service to start on default runlevel:

```
sudo ng-update add system/eciadsl default
```

7.2. Start Jack audio daemon on boot (if you don't know what it is, you most likely don't need it).

7.2.1. Create a file called jackd.i with the following content:

```
service daemon/jackd {
	need = system/initial system/mountfs system/coldplug system/alsasound
	daemon = /usr/bin/jackd
	daemon_args = -R -d alsa -d hw:0
}
```

Note that parameters (daemon_args) listed here are only an example - you should set them according to your needs.

7.2.2. Put this file in /etc/initng/daemon directory.

7.2.3. Set Jack daemon to start on default runlevel:

```
sudo ng-update add daemon/jackd default
```

7.3. Start wireless connection on boot (thanks Manny C!).

[http://ubuntuforums.org/showpost.php?p=441841&postcount=55](http://ubuntuforums.org/showpost.php?p=441841&postcount=55)

This worked for a specific configuration mentioned in the post referenced above. Let me know if it works for you.

7.4. More scripts for setting up other useful things can be found here (thanks Samuel!):

[http://forum.initng.thinktux.net/viewforum.php?f=9&sid=1f418ad14fc6157bcf8855c0184409a7](http://forum.initng.thinktux.net/viewforum.php?f=9&sid=1f418ad14fc6157bcf8855c0184409a7)

8. Set up GRUB for booting with InitNG. To do that, edit /boot/grub/menu.lst. Find an entry that looks like

```
title Ubuntu, kernel 2.6.12-9-686
root (hd0,8)
kernel /boot/vmlinuz-2.6.12-9-686 root=/dev/sda9 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-686
savedefault
boot
```

Your actual entry may look slightly different, but it must be the option that you normally choose to boot into Ubuntu.

Insert an identical entry below. Remove the word 'splash' from the 'kernel' line in the newly created entry and append 'init=/sbin/initng' to that line (without quotes). Replace 'Ubuntu' word in the 'title' line with something like 'Ubuntu (InitNG)'.

9. Reboot and choose 'Ubuntu (InitNG)' in Grub boot menu.

After that, the system should correctly boot, and you should be able to login to Gnome/KDE. In my case the actual boot time reduced by 25 sec (from 65 sec to 40 sec). Your results may vary, depending of your configuration.

If something does not work, you can always boot into your normal configuration - just choose the boot option that you cloned in the Grub menu. Meanwhile, here's some fixes suggested by the kind people in this thread:

* If you have problems with ACPI, frequency scaling etc., try these quick links:

[http://ubuntuforums.org/showpost.php?p=434971&postcount=27](http://ubuntuforums.org/showpost.php?p=434971&postcount=27) (thanks Maecenas!)
[http://ubuntuforums.org/showpost.php?p=435518&postcount=30](http://ubuntuforums.org/showpost.php?p=435518&postcount=30) (thanks Rob2687!)

If you don't need ACPI, you can turn it off altogether:

```
sudo ng-update delete daemon/acpid default
```

* To make NVidia modules load (by mounting volatile kernel modules), do as prescribed here:

[http://ubuntuforums.org/showpost.php?p=435346&postcount=29](http://ubuntuforums.org/showpost.php?p=435346&postcount=29) (thanks Meralon!)

Have Fun.

---

### Post by DoeRayMe on 2005-10-22
I had my adsl modem start up everytime i start my computer before, now its stopped, how do i get that working again? thanks though, its really fast now

---

### Post by temcat on 2005-10-22
[QUOTE=DoeRayMe]I had my adsl modem start up everytime i start my computer before, now its stopped, how do i get that working again? thanks though, its really fast now[/QUOTE]

Someone has to  create .i file for running this service or adjust the existing /etc/initng/net/net.i file. Maybe I'll do it later for eciadsl.

---

### Post by blakken on 2005-10-22
thanx very much for the tip ,it's really nice although my internet interface had to be manually started with ifup eth1 command!any idea how to make this little script?
;)

---

### Post by DutchR_PW on 2005-10-22
This looks great, but I have two little questions:

- Does it still have the splash screen (USplash or whatever it's called)?
- Does it also work in Hoary?

---

### Post by DoeRayMe on 2005-10-22
[QUOTE=temcat]Someone has to  create .i file for running this service or adjust the existing /etc/initng/net/net.i file. Maybe I'll do it later for eciadsl.[/QUOTE]

Thanks i would appriciate that, as i use eciadsl

---

### Post by temcat on 2005-10-22
[QUOTE=DutchR_PW]
- Does it still have the splash screen (USplash or whatever it's called)?
[/QUOTE]

I disbled usplash by removing the word 'splash' from 'kernel' line, because it didn't worked (switched to console somewhere in the middle).

[QUOTE=DutchR_PW]
- Does it also work in Hoary?
[/QUOTE]

No idea - I have only Breezy :-)

---

### Post by DoeRayMe on 2005-10-22
Problem, I get this error when i reboot

failed to initialize HAL!

btw, found out its to do with my usb modem being plugged in, hope the eciadsl thing gets sorted soon, not rushing of course

---

### Post by temcat on 2005-10-22
[QUOTE=blakken]thanx very much for the tip ,it's really nice although my internet interface had to be manually started with ifup eth1 command!any idea how to make this little script?
;)[/QUOTE]

1) Look at the content of /etc/initng/net/net.i

2) Read the relevant socuments in /usr/share/initng

3) Edit net.i file

4) Run

```
sudo ng-update add net/net default
```

5) Post your net.i file here if you had success!

---

### Post by temcat on 2005-10-22
[QUOTE=DoeRayMe]Problem, I get this error when i reboot

failed to initialize HAL!
[/QUOTE]

Have you changed the dbus.i and hald.i files as prescribed? Check again, do it if you haven't and run

```
sudo ng-update add daemon/dbus default
sudo ng-update add daemon/hald default
```

just in case.

---

### Post by DoeRayMe on 2005-10-22
I get this when i try to do the hal one

> will@ubuntu:~$ sudo ng-update add daemon/hal default
Warning: "daemon/hal" isn't a script or a runlevel, it's being removed from listError: you didn't specify any script


thanks in advance

---

### Post by heimo on 2005-10-22
[quote=DoeRayMe]Problem, I get this error when i reboot

failed to initialize HAL!

btw, found out its to do with my usb modem being plugged in, hope the eciadsl thing gets sorted soon, not rushing of course[/quote]

Do as temcat says. I also got this error at first attempt as my copy-paste from forum to text editor broke hald.i lines.

---

### Post by heimo on 2005-10-22
[quote=DoeRayMe]I get this when i try to do the hal one



thanks in advance[/quote]

hald

---

### Post by BLTicklemonster on 2005-10-22
I've sat here with a dull look on my face fighting my inner deamons (daemons?) for a while now. I said I wouldn't do it. But I can't help myself. 

Please forgive me.



" I want a fast Ubuntu boot, too!!!"




There. I did it. Sorry.

:rolleyes: 

:cool:

---

### Post by DoeRayMe on 2005-10-22
When i reboot it goes back to the old way, shouldnt it set as default?

---

### Post by BLTicklemonster on 2005-10-22
[QUOTE=DoeRayMe]Problem, I get this error when i reboot

failed to initialize HAL!

btw, found out its to do with my usb modem being plugged in, hope the eciadsl thing gets sorted soon, not rushing of course[/QUOTE]


Are you kidding? Do you know how long it took Dave to get HAL not to initialize? 

anyway, I found that booting into recovery mode and typing startx does the same thing. I wonder if that's just a bug they'll fix or not. My mouse is usb, and it works fine in recovery mode.

---

### Post by DoeRayMe on 2005-10-22
Fixed, i commented out the boot process and just have the current one

It now works, just modem that needs sorting out

---

### Post by johannes on 2005-10-22
Really nice speed. But I couldn't get it working with jackd (audio) in realtime mode so I can't use it.

---

### Post by temcat on 2005-10-22
[QUOTE=DoeRayMe]Fixed, i commented out the boot process and just have the current one

It now works, just modem that needs sorting out[/QUOTE]

Please see the updated HOWTO - now eciadsl works, too.

---

### Post by temcat on 2005-10-22
[QUOTE=johannes]Really nice speed. But I couldn't get it working with jackd (audio) in realtime mode so I can't use it.[/QUOTE]

I'll look into it. Meanwhile, what is the command to start and stop jack daemon in realtime mode?

---

### Post by temcat on 2005-10-22
[QUOTE=johannes]Really nice speed. But I couldn't get it working with jackd (audio) in realtime mode so I can't use it.[/QUOTE]

OK, please see update HOWTO - now jack is started at boot time with realtime scheduling.

---

### Post by johannes on 2005-10-22
Wow, that was fast. :)  Now it's working great!

---

### Post by DoeRayMe on 2005-10-22
thanks alot for the eciadsl part, i really appriciate it

---

### Post by Samuel on 2005-10-22
i tried this and my system booted super fast... into console mode :( 

anyway this is the output when i install it with dpkg

```
Setting up initng (0.3.3-2) ...
Automatically generating system,runlevel,default.runlevel and up.runlevel
sed: can't read /etc/X11/default-display-manager: No such file or directory
Adding daemon/acpid to default.runlevel
Adding daemon/dbus to default.runlevel
Adding daemon/hald to default.runlevel
Adding daemon/vixie-cron to default.runlevel
Adding net/eth0 to default.runlevel
Adding system/alsasound to default.runlevel
Adding system/laptop-mode to default.runlevel
Adding daemon/syslogd to default.runlevel
Done generating files.

```

im using the nvidia-glx drivers from apt-get, what do i need to change to beable to use initNG?

---

### Post by DoeRayMe on 2005-10-22
one more quick question, it has eth0 enabled but when its shutting down, it says its not configured

How can i turn this off?

---

### Post by Rob2687 on 2005-10-22
no more frequency scaling on my laptop with this :(
(piii 1ghz)

Took off about 30 seconds from my boot time though

---

### Post by maecenas on 2005-10-22
Nice HowTo!

But I think Just turning ACPI off because it throws errors on startup isn't a good solution, especially for laptop users like me.

I had a litle Problem with frequency scaling too.
On my thinkpad the following seems to work:

1. delete cpufreqd from default.runlevel if it exists
```
# ng-update delete daemon/cpufreqd
```
2. add powernowd to default.runlevel
```
# ng-update add daemon/powernowd
```
3. replace the content of /etc/initng/system/speedstep.i with
```

service system/speedstep {
        need = system/initial system/modules system/mountroot
	use = system/static-modules system/coldplug
        #depends = system/initial system/modules
        start {
                modprobe cpufreq-ondemand &> /dev/null
		modprobe cpufreq_userspace       
		modprobe cpufreq_stats           
		modprobe cpufreq_powersave      
		modprobe cpufreq_conservative 
                modprobe speedstep_centrino
                cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor > /tmp/origgovanor
                echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
		exit 0
        }

        stop {
                echo `cat /tmp/origgovanor` > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
		exit 0
        }
}

```
The line
```

               modprobe speedstep_centrino

```
could vary from system to system.
If doesn't work you can try deleting the line.
Otherwise you have to find out which module controls speedstep on your system an insert it there.

4. replace the content of /etc/initng/daemon/powernowd.i with
```

service daemon/powernowd {
        need = system/initial system/mountfs system/speedstep
        #use = 
	daemon = /usr/sbin/powernowd
	daemon_args = "-q"
}

```
And that should do the trick.

I've got still some problems with ACPI though.
I get those errors on boot time:
```

FATAL: Error inserting asus_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/asus_acpi.ko): No such device

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```
But I don't know if these modules are really needed by my system anyway?
The ibm module gets loaded.
At least I encountered no misbehaviour so far.

---

### Post by joakim2 on 2005-10-22
Certainly shaved startup time... But it doesn't mount the volatile kernel modules dir so nvidia module is not available and GDM fails to start.

---

### Post by meralon on 2005-10-22
[QUOTE=joakim2]Certainly shaved startup time... But it doesn't mount the volatile kernel modules dir so nvidia module is not available and GDM fails to start.[/QUOTE]

I have replaced /etc/initng/system/initial.i with the following:

```
service system/initial {
    use = system/readahead
    critical
start {
    /etc/init.d/mountvirtfs start
    /etc/init.d/udev start
    /etc/init.d/udev-mtab start
    /sbin/lrm-manager --quick
    exit 0
}
}
```

The line /sbin/lrm-manager mounts the volatile-directory.

---

### Post by Rob2687 on 2005-10-22
[QUOTE=maecenas]
The line
```

               modprobe speedstep_centrino

```
could vary from system to system.
If doesn't work you can try deleting the line.
Otherwise you have to find out which module controls speedstep on your system an insert it there.
[/quote]

How could I find out which module to use? My laptop is a PentiumIII-M.

Edit: Figured it out.  It's acpi_cpufreq :)

---

### Post by Samuel on 2005-10-22
[QUOTE=meralon]I have replaced /etc/initng/system/initial.i with the following:

```
service system/initial {
    use = system/readahead
    critical
start {
    /etc/init.d/mountvirtfs start
    /etc/init.d/udev start
    /etc/init.d/udev-mtab start
    /sbin/lrm-manager --quick
    exit 0
}
}
```

The line /sbin/lrm-manager mounts the volatile-directory.[/QUOTE]

worked a treat, thankyou meralon :)
20 seconds to boot from power on to gui, very nice

---

### Post by souled on 2005-10-22
I followed this howto exactly, but something went horribly wrong. When I boot up, the GDM is loaded with like 16 bit color or something, and it looks all ugly. When I try to log in, I get an error message saying my "session lasted less than 10 seconds, if I didn't log out then there could be an installation problem or I may be out of diskspace. Try logging in with the failsafe session. View details ~/.xsession-errors."

I tried logging in with the failsafe session, but the same message comes up.

When I switch to terminal and cat .xsession-errors, I get some stuff
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp - (bunch more stuff)
Then it has a bunch of errors about IceTrans. 

_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.

And about 10 more lines of _IceTrans errors. 

Help please!

EDIT: I didn't see the end part about adding stuff to grub. Will try that now.

Ok I edited the boot stuff and it still happens. Maybe something else is wrong with my system?

---

### Post by Manny C on 2005-10-23
Great HOWTO! Worked perfectly for me! ACPI and Sound work perfectly. Not sure about the Net config. Will let you know! :)

Great work!

---

### Post by Manny C on 2005-10-23
[quote=temcat]1) Look at the content of /etc/initng/net/net.i

2) Read the relevant socuments in /usr/share/initng

3) Edit net.i file

4) Run

```
sudo ng-update add net/net default
``` 
5) Post your net.i file here if you had success![/quote] 
Step 2 is deficient. No directory under /usr/share/ called initng. Must look under /usr/share/doc/initng.

And wireless doesn't start up automatically. I need to issue the following command after startup to get it working:
```
 sudo ifup eth1 
```
and then it works. Will look at how to get this integrated in one of the .i files in a couple of weeks.

---

### Post by Snakey on 2005-10-23
After I've applied these changes, I always have to restart the following script to make my printer work:
```
sudo /etc/init.d/cupsys restart
```

---

### Post by Samuel on 2005-10-23
[http://forum.initng.thinktux.net/viewforum.php?f=9&sid=1f418ad14fc6157bcf8855c0184409a7](http://forum.initng.thinktux.net/viewforum.php?f=9&sid=1f418ad14fc6157bcf8855c0184409a7)

some good scripts here to get various things working

---

### Post by berserker on 2005-10-23
I've gotta ask.  How many times do you reboot your Linux box that you really need to shave 30-40 seconds off the boot time?

"Why does anyone climb a mountain?  Because it's there!"

"Incoming missile!  Is the linux computer still rebooting?  OMG!  I knew I should have followed that InitNG thread!"

:p

---

### Post by Snakey on 2005-10-23
[QUOTE=berserker]I've gotta ask.  How many times do you reboot your Linux box that you really need to shave 30-40 seconds off the boot time?

"Why does anyone climb a mountain?  Because it's there!"

"Incoming missile!  Is the linux computer still rebooting?  OMG!  I knew I should have followed that InitNG thread!"

:p[/QUOTE]
We always want a faster boot! :p LOL
Sometimes it's very handy, when I've turned my pc off to go to bed, but I've forgotten to print some documents, it's faster ;) I managed to get from grub to the login screen in ~15-18 seconds, after logon, it takes ~4-8 sec to load everything; the panel, nautilus, (gaim)...

---

### Post by GeneralZod on 2005-10-23
I haven't dared try this myself, but I thought I'd chime in and say "Thanks!" for writing up this HOWTO and for sticking around to support it.  Nice work! :)

Hopefully, in a few releases time, this will be used by default!

---

### Post by exparrot on 2005-10-23
I'm going to try and install this after upgrading to Breezy this afternoon, but first a question or two:

1) What is Jackd and is it necessary? I don't see it being used on my current Hoary install even though the binary for it is installed.

2) What is coldplug? How/why is it different to hotplug?

3) Can I leave ACPI enabled? Is it likely to work? I'm on a laptop.


Thanks!

---

### Post by Manny C on 2005-10-23
[quote=exparrot]I'm going to try and install this after upgrading to Breezy this afternoon, but first a question or two:

1) What is Jackd and is it necessary? I don't see it being used on my current Hoary install even though the binary for it is installed.

2) What is coldplug? How/why is it different to hotplug?

3) Can I leave ACPI enabled? Is it likely to work? I'm on a laptop.


Thanks![/quote]

1) Dunno. Didn't need to fiddle with this. Sound works for me.
2) Dunno
3) Left it enabled on my laptop. Suspend to RAM works just as well as it did before INITNG.

---

### Post by evs on 2005-10-23
[QUOTE=berserker]I've gotta ask.  How many times do you reboot your Linux box that you really need to shave 30-40 seconds off the boot time?

"Why does anyone climb a mountain?  Because it's there!"

"Incoming missile!  Is the linux computer still rebooting?  OMG!  I knew I should have followed that InitNG thread!"

:p[/QUOTE]

I usually boot up several times a day, considering it's a laptop.  On a server, or even a workstation, I wouldn't be too concerned, especially since InitNG still needs some work.  I can't wait to give this a try on my laptop though.

---

### Post by Manny C on 2005-10-24
[quote=evs]I usually boot up several times a day, considering it's a laptop. On a server, or even a workstation, I wouldn't be too concerned, especially since InitNG still needs some work. I can't wait to give this a try on my laptop though.[/quote]

Why do you need to boot up a laptop several times a day? Is ACPI not working for you?

---

### Post by prasys on 2005-10-24
xparrot

1. Dunno

2. coldplug is mainly used for to detect devices which are not hotplug (a good example of hotplug is USB thumbdrive , they get detected automaticly when you plug it and plug out. Mainly , you need coldplug to detect some devices in your lappie. Keep it on , don't try to disable it

3. Yeah of course you would. It depends , if your BIOS is blacklisted (thank god , there are few) then it should work

---

### Post by skyboy on 2005-10-24
Woo, works like a nice Formula 1 now, thanks.

---

### Post by evs on 2005-10-24
[QUOTE=Manny C]Why do you need to boot up a laptop several times a day? Is ACPI not working for you?[/QUOTE]

Pretty much.  I fixed my DSDT so that I can get my battery status, and hibernate was working out of the box.  Suspend to ram would suspend fine, but the screen stayed black after resuming, and when I tried to fix it, I broke hibernate as well.  I don't care too much about hibernate because it took almost as long to resume as a fresh boot.  But yes, if I could get suspend to work properly then I wouldn't be shutting my laptop down very much, although a faster boot would still be welcome.

---

### Post by sailor420 on 2005-10-24
If I install this and it borks itself, would I be able to boot normally using the other Grub option, the one we clone the InitNG one from?

I'd love to try this out, but I just got done with a somewhat hairy dist-upgrade and am a little hesitant to tank my system :)

---

### Post by sailor420 on 2005-10-24
[QUOTE=Manny C]And wireless doesn't start up automatically. I need to issue the following command after startup to get it working:
```
 sudo ifup eth1 
```
and then it works. Will look at how to get this integrated in one of the .i files in a couple of weeks.[/QUOTE]

Is this working now? Wireless is my primary internet connection, so having to issue this everytime on boot is somewhat annoying :(

---

### Post by joakim2 on 2005-10-24
[QUOTE=sailor420]Is this working now? Wireless is my primary internet connection, so having to issue this everytime on boot is somewhat annoying :([/QUOTE]

I'd tend to say that if you're not a fiddler/tester/adventurous, initng is not for you right now. It takes a little patience getting it the way you want it in its current state.

---

### Post by sailor420 on 2005-10-24
I don't mind tinkering; that's one of the things I like most about Linux. I just don't want to make my system unbootable since my Windows install isn't working at the moment :)

---

### Post by temcat on 2005-10-24
The HOWTO is updated! Nothing new basically, just made an overall rewrite and inserted direct links to some helpful posts in this thread.

---

### Post by mathjazz on 2005-10-24
Thanks man, it works great!

Now we only need something similar for GNOME startup ...

---

### Post by temcat on 2005-10-25
[QUOTE=mathjazz]Thanks man, it works great!

Now we only need something similar for GNOME startup ...[/QUOTE]

This is coming soon, too: [http://nat.org/2005/october/#Keep-It-Simple-Stupid](http://nat.org/2005/october/#Keep-It-Simple-Stupid)

---

### Post by BLTicklemonster on 2005-10-25
6 pages... how stable is this now? I'm on my like 6th install of breezy, more of hoary, and I've got what I want out of it finally, except for ripping and burning archival dvds... I don't want to set it to boot faster and loose anything.

---

### Post by Manny C on 2005-10-25
Ok. Got my wireless connection working. I have my IPs dynamically allocated. No fixed IPs. So I modified [this]("http://forum.initng.thinktux.net/viewtopic.php?t=44&sid=8d08d42ee04d4932cadadbfd2af48069"). Create a file /etc/initng/daemon/eth1.i with the following contents
```
 service net/eth1 {
    depends = system/initial system/checkroot system/modules
        start {
        echo "Starting net/eth1 now"
        ifup eth1
        }
        stop {
        echo "Stopping net/$NAME now"
        ifconfig $NAME down
        }
}

```
Then issue the following command to ensure this script is run on boot up.
```
 sudo ng-update add net/eth1 default 
```

This doesn't bring the connection up after suspending laptop. Will look into this later.

---

### Post by temcat on 2005-10-25
[QUOTE=BLTicklemonster]6 pages... how stable is this now? I'm on my like 6th install of breezy, more of hoary, and I've got what I want out of it finally, except for ripping and burning archival dvds... I don't want to set it to boot faster and loose anything.[/QUOTE]

I wouldn't suggest putting InitNG on "production" machines just yet. You'd better wait for it to enter stable status. Having everything working with no fuss is more important that cutting those 20-30 sec. However, even if you installed it and something went wrong, you can always boot the traditional way - just use your normally chosen option in Grub menu.

---

### Post by temcat on 2005-10-25
[QUOTE=Manny C]Ok. Got my wireless connection working. [/QUOTE]

Thanks man! I'm updating the HOWTO with this.

---

### Post by crypto178 on 2005-10-25
Thanks for the great HOW-TO.

There is just one thing not working for me, inetd doesn't start (I need it to get hotway to work, see [http://ubuntuforums.org/showthread.php?t=73763](http://ubuntuforums.org/showthread.php?t=73763)). 
I saw there was a script for xinetd on those forums : [http://forum.initng.thinktux.net/viewtopic.php?t=98](http://forum.initng.thinktux.net/viewtopic.php?t=98) but I didn't succeed in modifying it to work with inetd. Does anyone know how to make inetd start with initng ?

---

### Post by squibbon on 2005-10-26
hufff, to many steps. can't do i think. any alternatives?

---

### Post by heimo on 2005-10-26
[quote=squibbon]hufff, to many steps. can't do i think. any alternatives?[/quote][LIST=1]
[*]install InitNG[/LIST]Just one step. ;) ;) ;) If you run into trouble, you can try the original - I think temcats version is very nice, very detailed and pretty much works just because it's so detailed. Other alternative would be to wait until it gets included in the default install of Ubuntu (I believe making boot process faster was goal for Breezy, but didn't get included, not sure about Dapper, after all its main goal is stability).

EDIT: Of course, unless someone packs this into single script / makes a deb package.

---

### Post by mathjazz on 2005-10-26
VMWare stopped working for me. I receive an error message, telling me to make sure that kernel module "vmmon" is loaded.

Any hints?

---

### Post by Heliode on 2005-10-27
Thanks for your very well worded and easy-to-use howto, temcat. I've tried it in a virtual machine first, and it worked perfectly, turning a 53 second boottime into a 38 second one. This encouraged me to try it on my two physical machines (laptop and workstation)

They were both largely successful, but it seems a few modules fail to load. On my laptop, my wireless card isn't loaded at all. (the device isn't initialized, I don't see it in network management or with 'ifconfig -a') 

On my workstation, there seems to be a problem with Portmapper. I have a couple of NFS shares in my fstab which I automatically mount at boottime. With InitNG however, they don't. When I try to mount them manually, it takes a really, really long time (like 5 minutes per mount). This led me to conclude a problem with portmap. However, I've added 'portmap' to both 'default' and 'system' runlevels, but in both cases NFS mounts don't seem to mount at boot time. 
I also have the problem with VMWare's 'vmmon' kernel module not being loaded, but I believe this to be related to the network card driver on the laptop failing to load (since I had to compile that module manually).
[[Edit: If I do 'sudo /etc/init.d/portmap start' and then do 'mount -a', all my nfs shares are mounted in about three seconds, so the problem is indeed in portmapper not starting]]

Any light you would be able to shed on the situation would be hightly apperciated.

---

### Post by Heliode on 2005-10-27
Ok, I figured out the VMWare part, and made some progress on the other two...

**For VMWare:**

fist of all, you need to add vmware to the default runlevel with:
```
sudo ng-update add vmware default
```
However, there is a path hardcoded in the InitNG config file for VMWare that probably isn't valid, namely the path to the executable 'vmnet-bridge'. To figure out where you have it on your system, open a terminal and type "which vmnet-bridge". For me the path was "/usr/bin/vmnet-bridge".

Now open "/etc/initng/daemon/vmware.i" in your favorite editor. Look for the line that says
```
exec /opt/vmware/bin/vmnet-bridge /dev/vmnet0 eth0
```
and replace it with the correct path, which in my example is:
```
exec /usr/bin/vmnet-bridge /dev/vmnet0 eth0
```
Also note that if you want vmware to bridge over a device other than eth0, this is the place to change it. 

Now reboot, and it should work!

For the laptop wireless interface; it uses the 'rt2500' module, but manually modprobing that after InitNG-bootup doesn't activate the device either, still looking into that. 

As for Portmap, the problem seems to be in the '/etc/initng/daemon/portmap.i' file, which says the following:
```
service daemon/portmap {
        need = system/mountroot virtual/networking
        start {
                [[ -f  /etc/conf.d/portmap]] && . /etc/conf.d/portmap
                /sbin/portmap ${PORTMAP_OPTS}
                # If we don't sleep then applications needing on portmap
                # will not successfully connect
                sleep 5
        }
}

```
I won't claim to know exactly what this does, but it seems to check if /etc/conf.d/portmap is there, which it isn't. However, even after manually creating this file (and even hashing the check out) portmap stil isn't started. I'd like some help with this from somebody with more experience with this sort of thing than me.

I'll keep you posted ;-)

---

### Post by bradroger on 2005-10-28
Step 6 - I get this error:

brad@bradubuntu:~/Downloads$ sudo ng-update add system/colplug system
Warning: "system/colplug" isn't a script or a runlevel, it's being removed from list
Error: you didn't specify any script

Is there something blatantly obvious I skipped or missed or is this a bug?

---

### Post by bradroger on 2005-10-28
oh sorry...I tried it again and got
Success: added "system/coldplug" to runlevel "system"
I'll try to be a little less trigger happy!!

---

### Post by gluon on 2005-10-28
I really love the speed boost given by InitNG, but I'm having a problem with it. When I boot using InitNG, I cannot use Matlab fully.
In the start-up (starting in console-mode), I get following:

$ matlab
/opt/matlab/bin/util/oscheck.sh: line 134: /lib/libc.so.6: Lupa evätty
??? MATLAB was unable to open a pseudo-tty: No such file or directory [2,1]
The unix() and ! commands will not work in this MATLAB session.  Other
commands which depend upon unix() and ! will also fail.  Your system may
be running low on resources.  If the problem persists after a reboot,
check with your system administrator and confirm that your pty subsystem
is properly configured.

Does anyone have an idea how this could be resolved?

---

### Post by graabein on 2005-10-28
[QUOTE=heimo]Other alternative would be to wait until it gets included in the default install of Ubuntu (I believe making boot process faster was goal for Breezy, but didn't get included, not sure about Dapper, after all its main goal is stability).

EDIT: Of course, unless someone packs this into single script / makes a deb package.[/QUOTE]

Oh that would be great. A script is *perf*ect. Hope they put a high priority on snappy boot time in Dapper.

---

### Post by BLTicklemonster on 2005-10-28
[CENTER][IMG]http://www.restrainingbolt.com/otherprops/pics/misc/dapperdan.jpg[/IMG]

smootherest linux ever[/CENTER]

---

### Post by parpic2002 on 2005-10-28
This is my net.i file.



service net/eth0 {
	need = system/mountfs system/modules system/hostname system/ifupdown-debian
    	use = system/static-modules system/coldplug daemon/cardmgr
	start = /sbin/ifup
	start_args = -a
	stop  = /sbin/ifdown
	stop_args  = -a
}

service net/eth1 {
        depends = system/initial system/checkroot system/modules 
        start { 
        echo "Starting net/eth1 now"
        ifconfig eth1 192.168.1.74 netmask 255.255.248.0 broadcast 192.168.1.32
        } 
        stop {
        echo "Stopping net/$NAME now"
        ifconfig $NAME down
        }
}

service net/lo {
	# */
	need = system/mountfs system/modules system/hostname system/ifupdown-debian
	use = system/static-modules system/coldplug
	start = /sbin/ifup
	start_args = lo
	stop  = /sbin/ifdown
	stop_args = lo
}

service net/* {
	# */
	need = system/mountfs system/modules system/hostname system/ifupdown-debian
	use = system/static-modules system/coldplug daemon/cardmgr
	#provide = virtual/networking
	start = /sbin/ifup
	start_args = $NAME
	stop  = /sbin/ifdown
	stop_args  = $NAME
}


Just work ok

---

### Post by snowpalmer on 2005-10-28
I tried to install this on mine.  I'm on an amd64 machine so there wasn't a deb but I downloaded the latest source and created a deb by using checkinstall.  Everything installed just fine but I get this when it boots.

** "initng_common.c", load_to_active():
08:05:46 -- line:105 FAIL:       load_to_active(default): Can't get service!
SEGFAULTED!

Anyone have any dieas?  I'm not expert, so I'm pretty stumped.  Has anyone successfully used this on a 64 bit system?  A comment [here]("http://triggerit.tr.funpic.de/blog/?p=7") sounds like people are using it on amd64.

---

### Post by snowpalmer on 2005-10-28
Ok.  I got it working now.  This is what I did.

I downloaded

[https://alioth.debian.org/download.php/1226/initng_0.3.3.orig.tar.gz](https://alioth.debian.org/download.php/1226/initng_0.3.3.orig.tar.gz)
[https://alioth.debian.org/download.php/1224/initng_0.3.3-1.dsc](https://alioth.debian.org/download.php/1224/initng_0.3.3-1.dsc)
and
[https://alioth.debian.org/download.php/1223/initng_0.3.3-1.diff.gz](https://alioth.debian.org/download.php/1223/initng_0.3.3-1.diff.gz)

Executed

dpkg-source -x initng_0.3.3-1.dsc
cd initng-0.3.3/
dpkg-buildpackage -rfakeroot

That gave me a .deb file to install.  Once I uninstalled my previous one and installed this one things came up just fine (except for wireless.. I will have to look at that)

---

### Post by Joshua Hesketh on 2005-10-28
Excellent tutorial!, had nearly no troubles.

The only thing that I am stuck on is getting my fglrx drivers to work. I have an ATI radeon 9600xt and followed [this]("http://ubuntuforums.org/showthread.php?p=423589") tutorial to install the drivers which used the module-assistant.

I don't know much about loading modules but when I booted in with init.d the drivers worked 100%, but with initNG fglrxinfo displays correct information, glxgears work fine too, but apps like fgl_glxgears and ppracer display FGL errors and try and process the graphics with the CPU and lags.

Any help would be good. Thanks.

---

### Post by XQC on 2005-10-29
Works fine for me, too.

Only thing there's left is that GDM now starts in English and I would prefer German ;)
How can I change this?

---

### Post by parpic2002 on 2005-10-29
Only webcam on GYACHE won`t work with initng.

---

### Post by sailor420 on 2005-10-29
Installed it, and everything looked to be working except my wireless. I used the script that the one here was adapted off of, since I *do* use fixed IPs... But no go.

Would I have to specify the SSID/WEP through an iwconfig command in that eth1.i file to make it work?


EDIT: Just tried it, no go. I've got no idea here, folks.

---

### Post by sailor420 on 2005-10-29
OK, this might help yall... I don't know what to make of it, but some of yall might...

ifconfig eth1 when running under initd:

```

eth1      Link encap:Ethernet  HWaddr 00:02:8A:78:71:CF
          inet addr:192.168.7.63  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:fe78:71cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1587 errors:19936 dropped:0 overruns:0 frame:19936
          TX packets:1181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:388 txqueuelen:1000
          RX bytes:1282461 (1.2 MiB)  TX bytes:204028 (199.2 KiB)
          Interrupt:11 Base address:0x8000

```

When running under initNG:

```

eth1      Link encap:UNSPEC  HWaddr 00-02-8A-78-71-CF-00-84-00-00-00-00-00-00-00-00
          inet addr:192.168.7.63  Bcast:192.168.7.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:127 errors:1925 dropped:0 overruns:0 frame:1925
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:5575 (5.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000

```


Any ideas?


EDIT: Here's my eth1.i file:

```

service net/eth1 {
    depends = system/initial system/checkroot system/modules
        start {
        echo "Starting net/eth1 now"
        ifconfig eth1 192.168.7.63 netmask 255.255.255.0 broadcast 192.168.7.255
        }
        stop {
        echo "Stopping net/$NAME now"
        ifconfig $NAME down
        }
}

```

---

### Post by sailor420 on 2005-10-29
Hmmm, looks like it was spitting a bunch of errors when loading the eth1.i file, but I couldn't catch them because they flew by so fast... I assume all those messages are logged; anyone know where? I couldn't find them from a cursory glance through /var/log :confused:

---

### Post by berserker on 2005-10-29
I gave this a whirl with the latest deb package (0.3.4-1) and enjoyed a remarkably faster boot.

However, cupsd wouldn't load even after I tried the init script and the biggest problem was that I couldn't get a bash prompt after launching a konsole terminal within KDE (I couldn't type anything in even though my keyboard works).

Also, when trying to launch Kate with kdesu I received a "No SU found" error.

Things that make you go hmmmmm....

---

### Post by Rob2687 on 2005-10-29
Booting with this method makes my sound break sometimes. Sometimes there is no sound at all and sometimes everything that uses ALSA plays super fast. Like chipmunks talking kind of fast.

Sound card is an onboard ESS Allegro card in my laptop.

Btw is anybody else getting error messages when they have a terminal window open? I keep seeing this in my terminal windows:
```

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: "initng_common.c", load_to_active() #105 FAIL:

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: load_to_active(runlevelU): Can't get service!

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: "initng_handler.c", start_new_service_named() #322 FAIL:

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: Unable to load active for service runlevelU

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: "initng_common.c", load_to_active() #105 FAIL:

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: load_to_active(runlevelu): Can't get service!

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: "initng_handler.c", start_new_service_named() #322 FAIL:

Message from syslogd@localhost at Sat Oct 29 23:18:13 2005 ...
localhost InitNG: Unable to load active for service runlevelu

```

---

### Post by cwf on 2005-10-29
Thanks a lot for the great HOWTO.  I need help with setting up InitNG to do one more thing that my normal boot does.

I followed this HOWTO:  [http://www.ubuntuforums.org/showthread.php?t=42737&highlight=fancontrol]("http://www.ubuntuforums.org/showthread.php?t=42737&highlight=fancontrol")

in order quiet down my PC.

What I need to do now is adapt the init.d startup script given in that HOWTO to work with initNG.

I tried to write a script 'daemon/fancontrol' and add it to InitNG but it didn't work.  I'm sure one of you experts could write up an initNG script in seconds by looking at that init.d script.  

Any help is greatly appreciated. Thanks!

---

### Post by sailor420 on 2005-10-30
OK, well I looked some more at other init scripts, and it seemed all the other ones were using "needs" rather than "depends"... Changed that and it fixed some of the errors, but its still not working. Not working as in I can't even get the device up manually once booted. I've gotta be missing some module or other dependancy... Any way of figuring out what? I guess the first step would be finding the log of those error messages...

---

### Post by RubenGonc on 2005-10-30
How can I initialize my speedtouch connection given by this script:

> #!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $count -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    br2684ctl -b -c 0 -a VP.VC
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    sleep 10
    pppd call speedtch
    exit 0
  fi
  sleep 1
  let "count += 1"
done
echo "The Speedtouch firmware didn't load"

Thanks

---

### Post by sailor420 on 2005-11-01
Yikes... This thread kinda dropped off... Anyone?

---

### Post by sailor420 on 2005-11-06
*bump*

This thread died pretty suddenly...

---

### Post by Bitmastro on 2005-11-06
Ok... let's bring some instability :-)

There is a new version out.., you can grab it here
[http://alioth.debian.org/download.php/1245/initng_0.3.5-1_i386.deb]("http://alioth.debian.org/download.php/1245/initng_0.3.5-1_i386.deb")

but, watch out.. it gave me some trouble (i.e. the system won't boot at first)
so here's what I've done..
(this will remove all your previous initng scripts)
[LIST=1]
[*]boot with the old init
[*]in a console type: sudo apt-get remove --purge initng
[*]install the new version with: sudo dpkg -i initng_0.3.5-1_i386.deb
[/LIST]

now edit (with root privileges) /etd/initng/daemon/dbus.i
to have this
```

daemon daemon/dbus {
        need = system/initial system/mountfs system/bootmisc
	
        pid_file = /var/run/dbus/pid
        daemon {
              DAEMON=/usr/bin/dbus-daemon
              NAME=dbus
              DAEMONUSER=messagebus
              PIDDIR=/var/run/dbus
              PIDFILE=$PIDDIR/pid
              DESC="system message bus"

              if [ -e /etc/default/dbus ]; then
                . /etc/default/dbus
              fi

              if [ ! -d $PIDDIR ]; then
                mkdir -p $PIDDIR
                chown $DAEMONUSER $PIDDIR
                chgrp $DAEMONUSER $PIDDIR
              fi
              if [ -e $PIDFILE ]; then
                PIDDIR=/proc/$(cat $PIDFILE)
                if [ -d ${PIDDIR} -a  "$(readlink -f ${PIDDIR}/exe)" = "${DAEMON}" ]; then
                  echo "$DESC already started; not starting."
                else
                  echo "Removing stale PID file $PIDFILE."
                  rm -f $PIDFILE
                fi
              fi
              echo -n "Starting $DESC: "
              $DAEMON --system $PARAMS
              echo "$NAME."
              }
}

```

add hald to the default runlevel
at your discretion add readahead (it should load some files from the hd to the ram, to have a faster access... in my case it added ~3 sec to the startup process... but who knows :-) )
you try to cut down times installing mingetty ("sudo apt-get install mingetty") instead of getty (it should be a little faster), then remove getty from the default runlevel and replace it with mingetty
for the same reason install dash (a lighter bash) with "sudo apt-get install dash"
edit the file /etc/initng/daemon/instant-gdm.i and change the path from /usr/bin/gdm to /usr/sbin/gdm
```

#To get this working, remove consolefont from system.runlevel
#This is just a test (for now)
#make this a plugin, make it hold all services except from what we need (and what that needs) and sleep 2 seconds after starting gdm.  Should make it start FAST.
#we can use /proc/bus/pci (lspci) to find out which modules we need to load.
#fix gdm? :p, it's sloooow.
daemon daemon/instant-gdm {
    need = system/initial system/mountfs system/hostname
    #do we need  system/modules?
    nice = -4;
    daemon {
        echo "STARTING INSTANT-GDM"
    	modprobe mousedev 2>&1 >/dev/null
    	modprobe nvidia 2>&1 >/dev/null
    	modprobe fglrx 2>&1 >/dev/null
	if [ -e /sys/class/input/mice/dev ]; then
	    mkdir -p /dev/input
	    mknod /dev/input/mice c 13 63 &>/dev/null
	fi
        echo "STARTING INSTANT-GDM-DAEMON"
	exec /usr/sbin/gdm -nodaemon
    }
}

```
then cd to /lib/modules/*your kernel version*/kernel/drivers/acpi
and rename (again, you must have root privileges) the modules you don't use to *module_name*.not, in this way the acpi script won't load them and show the error "FATAL: Error inserting blah, blah" at boot time (this is only a cosmetic change)

here's my dafault runlevel
```

system
daemon/acpid
daemon/dbus
daemon/vixie-cron
net/eth0
system/alsasound
system/speedstep
system/laptop-mode
daemon/syslogd
daemon/klogd
system/readahead
daemon/mingetty
daemon/hald
daemon/instant-gdm

```

btw... if you need something particular.. you can try to load it from the old init.d...
make a file in /etc/initng/system/
and call it, for example myscript.i
```

service system/myscript {
#add all the things that you need, for example net/eth0 or system/modules or whatever
    need = system/initial system/mountfs


start {
#call you old script 
  /etc/init.d/oldscript start
}

stop {
  /etc/init.d/oldscript stop
}
}

```
and add it to your runlever

I hope i didn't forget anything... :rolleyes: 
bye :-)

---

### Post by telmo on 2005-11-06
[QUOTE=maecenas]
I've got still some problems with ACPI though.
I get those errors on boot time:
```

FATAL: Error inserting asus_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/asus_acpi.ko): No such device

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```
But I don't know if these modules are really needed by my system anyway?
The ibm module gets loaded.
At least I encountered no misbehaviour so far.[/QUOTE]

Neither have i, but i would like to remove those errors. I have an ibm and the module is loaded alright, but i just hate errors... And it would increase mu boot speed about a nano second... :D

Ideas anyone?

EDIT: GOT IT! Thax for this last post. I should of read all the posts. Dumb me!

---

### Post by Trigger|Debian on 2005-11-07
Hi guys!

The alioth packages are created by me. It's nice to see that you are quite happy, but I have to mention something: If you write new scripts please send them to the Initng mailinglist (initng@initng.thinktux.net) and Initng will ship these scripts with the next release.
If you find bugs, report them on [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net) and we will try to fix the bug upstream.
If you want to talk to us, come to #initng on freenode.
If you have a problem with the Debian package (not with Initng) you can drop me a mail if you want (but ask here first ;) ). You'll find my address on the alioth site. 
You can drop me a comment in my blog anyway, if you want...

Bye
Trigger

PS: I will release a package for 0.4.0 tonight.

---

### Post by trinaryouroboros on 2005-11-08
Installed Dapper Drake, tried InitNG 4.0 - Segfaulted.

InitNG does not work well with dragons...

On the brighter side of things, since Dapper I've had an increase in boot time. It takes roughly 12 seconds to boot! Then again I'm using AMD64.

---

### Post by Bitmastro on 2005-11-09
Well, I'm using drake, and I've got the 0.4.0-1 version from alioth... and everything is running fine (some trouble in shutdown, but nothing critical) but I'm on x86, so maybe that's the problem... (I had some trouble with segmentation fault too, at first)

---

### Post by cerberos on 2005-11-09
Ok I think I understand how to edit the config files for this, but I can't work out which extra dependency is needed to fix things.  My eth1 is not being brought up properly at the moment, requiring a:
sudo ifup eth1
after boot to get me on the net properly.  Can anyone suggest how I can work out what I need to add to the eth dependencies so that it will load correctly first time?

Relevant info:
eth0 is onboard network on nforce mobo
eth1 is add in intel card as the onboard tends to overheat during summer.

---

### Post by Bitmastro on 2005-11-09
try this
```
sudo ng-update add net/eth1
```
I hope it works.
bye!

---

### Post by cerberos on 2005-11-09
Ahh, thats how that * in the net.i file works, thats a pretty neat way to do things.

gonna reboot right now

---

### Post by opera118 on 2005-11-09
[QUOTE=berserker]I've gotta ask.  How many times do you reboot your Linux box that you really need to shave 30-40 seconds off the boot time?

"Why does anyone climb a mountain?  Because it's there!"

"Incoming missile!  Is the linux computer still rebooting?  OMG!  I knew I should have followed that InitNG thread!"

:p[/QUOTE]

I'm not alone to getting tired of these twisted ideas that just because Linux is somewhat stable (or rather Was stable), then boot time is not an issue.

There are those, like me, who actually turn off the computer while not using it (sleeping is one good reason), to save energy and money. Open your eyes. 24/7 usage was leet 10 years ago.

But the fact is that a new init system can fix systematic problems that we've had for years now, by that, initng is truly one giant step ahead. I'm quite susprised no one has replaced the old init long ago.

To me, this is easily a nominee for lpoty - linux project of the year ;) 

O

---

### Post by berserker on 2005-11-09
[QUOTE=opera118]Open your eyes.[/QUOTE]

Lighten up.  It was a joke.

[QUOTE=opera118]I'm quite susprised no one has replaced the old init long ago.[/QUOTE]

Good point.  I tried BeOS about five or six years ago.  AMAZING bootup time!

---

### Post by Benjamin_Lebsanft on 2005-11-10
Doesn't seem to work on amd64. I tried everything from compiling 0.3.3 0.3.5 and even 0.4.0. They all segfault. The deb magic posted some pages before doesn't work either. Is there something I do wrong or does initNG simply not work on my platform ?

Edit: Got it working, but reboot causes my BIOS to stop booting again without pushing the reset button.

---

### Post by sailor420 on 2005-11-10
Should all of the previous scripts and tweaks from the tutorial here still work?

---

### Post by UbuWu on 2005-11-10
You can see the difference by installing 
[http://people.ubuntu.com/~scott/packages/bootchart_0.8-0ubuntu1_all.deb](http://people.ubuntu.com/~scott/packages/bootchart_0.8-0ubuntu1_all.deb) it will create a png in /var/log/bootchart with all boot details.

---

### Post by Benjamin_Lebsanft on 2005-11-11
I get the following error on my desktop when shutting down:

shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl

---

### Post by Jingo on 2005-11-12
I have been using version 3.3 , but now installed version 4.0.

Now all my partitions gets mounted on boot. Normally my Windows partitions doesn't get mounted but show up in Nautilus. They don't show up in Nautilus but are already mounted... don't get it. I don't want them mounted!!!

Where should I look?

/Jingo

---

### Post by domino on 2005-11-17
Just wanted to say thanks to this script, I was able to use it as a "Safe Mode" GUI for Ubuntu. I fallowed a how-to that didn't quite turn out the way I had planned. I couldn't log in gnome either in root or user mode. Something with the runlevels. Anyway, I booted InitNG and was able to repare the problem. It's just too bad that I don't have enough time to get all my hardware and 3rd party apps to work with this how-to.

Thanks

---

### Post by bekamyn on 2005-11-17
Thank you. 

Panasonic Toughbook CF-45
266Mhz
160MB RAM


From Grub to Login
Without InitNG   1:10
with InitNG        0:48

There's a newer version out that seems to work much better. It's available through SVN

[quote=initng.thinktux.net]
Get the latest version
svn checkout [https://svn.initng.thinktux.net/initng](https://svn.initng.thinktux.net/initng)

NOTE:
Due to a bug in the 0.4.2 release tarball, it might be necessary to run
./autogen.sh before you run ./configure.
./configure is atomatically invoced by ./autogen.sh, but if you want to pass
additional oprions to configure [eg --with-splash], you need to run configure again.
To run autogen.sh, you need to have automake, autoconf, and libtool installed.
[/quote]

To get it working on my laptop I had to:
ng-update del daemon/acpid <-- Remove acpi
edit daemon/hald.i and comment out
# use = daemon/acpid

Code:

#nano /etc/initng/system/pcmcia.i append to the "need = " system/coldplug


Make Pcmcia and Cardmgr play nice.

ng-update add system/pcmcia system
ng-update add daemon/cardmgr default
ng-update add net/net default

---

### Post by foxy123 on 2005-11-17
tried to install from svn and got an error:

```
$ sudo dpkg -i initng_0.42-1_i386.deb
Selecting previously deselected package initng.
(Reading database ... 127505 files and directories currently installed.)
Unpacking initng (from initng_0.42-1_i386.deb) ...
dpkg: error processing initng_0.42-1_i386.deb (--install):
 trying to overwrite `/etc/hotplug/net.agent', which is also in package hotplug
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 initng_0.42-1_i386.deb

```

any idea what this net.agent is?

---

### Post by Manny C on 2005-11-18
[New version]("http://alioth.debian.org/project/shownotes.php?group_id=30760&release_id=628") of InitNG out. Trying it out now. Here are the changes that need to be made with your initial post temcat:
[LIST=1]
[*]Point 1: New link location [here]("http://alioth.debian.org/download.php/1251/initng_0.4.0-1_i386.deb").
[*]Point 2: Update with this:
```
sudo dpkg -i initng_0.4.0-1_i386.deb
```
[*]Point 3: Not needed anymore
[*]Point 4: Should stay.
[*]Point 5: Kdm already setup (step unneeded)
[*]Point 6: Coldplug already setup (step unneeded)
[*]Point 7: Only checked 7.3: Still needed.
[*]Point 8: Still required.
[*]Point 9: Still the same. 
[/LIST]
Can confirm that this worked.

---

### Post by cerberos on 2005-11-19
so does anyone know how to use initNG and not cause the loading of DRI to fail with the FGLRX drivers?

---

### Post by Trigger|Debian on 2005-11-19
[QUOTE=cerberos]so does anyone know how to use initNG and not cause the loading of DRI to fail with the FGLRX drivers?[/QUOTE]
Hehe, I'm interested in this issue, too. Are there more people with this problem?
On my Debian box everything is fine.

BTW: I'm working on the packages for 0.4.4 now :)

---

### Post by cerberos on 2005-11-19
I've been trying version 0.4.0-1 as described just above to try and see if that could be some chance fix the driver issue and I'm getting broken HAL message, and yes my hald.i looks like it should from the howto.

---

### Post by curtis on 2005-11-19
I get the same error message with HAL as well...
That is with the newest version 0.4.4
I did try the hald.i and dbus.i files you had on page 1.
Both failed with some sort of syntax error.
My guess is the new version is slightly different with the .i files.

---

### Post by Trigger|Debian on 2005-11-19
Ok guys, 0.4.4-2 is out - try this one. Maybe you should read my blog entry before installing: [http://triggerit.tr.funpic.de/blog/?p=28](http://triggerit.tr.funpic.de/blog/?p=28)
Dbus should now start Hal automatically (0.4.4-1 didn't do it) - please forgett the hald.i script and remove it from your runlevels.
You slightly need to modify dbus.i. Open it and replace "DAEMON=/usr/bin/dbus-daemon-1" with "DAEMON=/usr/bin/dbus-daemon".
If you have problems with the nVidia/fglrx/... module add the following at the end of system/initial.i: "/sbin/lrm-manager --quick"
Please tell me if my proposed fixes work - I'm on Debian Sid and not Ubuntu.

If you have any other problems: Tell me here.
If you have .i files which are not shipped by the package please mail them to mailinglistenATonline.de. I will add them upstream.

---

### Post by curtis on 2005-11-19
I did install the latest one though, 0.4.4-2
I'll see if I can get HAL to work.

---

### Post by Bitmastro on 2005-11-19
in gdm.i and instant-gdm.i the path should be /usr/sbin/gdm instead of /usr/bin/gdm. in laptop-mode.i I put /usr/sbin/laptop-mode start instead of laptop_mode. hald seems to be running.
bye

---

### Post by curtis on 2005-11-20
[QUOTE=Bitmastro]in gdm.i and instant-gdm.i the path should be /usr/sbin/gdm instead of /usr/bin/gdm. in laptop-mode.i I put /usr/sbin/laptop-mode start instead of laptop_mode. hald seems to be running.
bye[/QUOTE]
That is what I needed to do...
Still can't get hald to work though.

---

### Post by Trigger|Debian on 2005-11-20
[QUOTE=Bitmastro]in gdm.i and instant-gdm.i the path should be /usr/sbin/gdm instead of /usr/bin/gdm. in laptop-mode.i I put /usr/sbin/laptop-mode start instead of laptop_mode. [/QUOTE]
Gr, why can't Ubuntu use the Debian paths? I'll investigate if I can find a solution for this.
> 
hald seems to be running.

:)

[QUOTE=curtis]That is what I needed to do...
Still can't get hald to work though.[/QUOTE]
Are you sure you have the latest dbus.i installed?
It should contain these lines, which start hal:
```
if [ -d $EVENTDIR ]; then
  run-parts --arg=start $EVENTDIR
fi

```

---

### Post by curtis on 2005-11-20
I fixed it, 
Issue was in dbus.i

Needed to turn:
```
     
              DAEMON=/usr/bin/dbus-daemon-1
              NAME=dbus-1

```

Into:

```

              DAEMON=/usr/bin/dbus-daemon
              NAME=dbus

```

Works fine now.

---

### Post by Trigger|Debian on 2005-11-20
Hehe, [http://www.ubuntuforums.org/showpost.php?p=505443&postcount=108]("http://www.ubuntuforums.org/showpost.php?p=505443&postcount=108") mentions this ;) 
Good to see it working :)

I think you need to change the paths in 
```
if [ -e /etc/default/dbus-1 ]; then
  . /etc/default/dbus-1
fi

``` too if you want your settings to be sourced.

---

### Post by curtis on 2005-11-20
[QUOTE=Trigger|Debian]Hehe, [http://www.ubuntuforums.org/showpost.php?p=505443&postcount=108](http://www.ubuntuforums.org/showpost.php?p=505443&postcount=108) mentions this ;) 
Good to see it working :)[/QUOTE]
Yea...
I do remember seeing that post now that you have mentioned it again.

---

### Post by berserker on 2005-11-20
After tweaking the dbus and adding the cupsd and samba scripts to the default runlevel, initng is working great.

I think it's almost ready for prime time.

It decreased my boot time from 72 to 42 seconds.

Great work, guys!

---

### Post by Benjamin_Lebsanft on 2005-11-20
[QUOTE=berserker]I think it's almost ready for prime time.[/QUOTE]
I'll second that. Would make more people trying ubuntu the first time say "wow that's fast". As boot time is one of the biggest complaint my windows using friends have this would be great.

---

### Post by foxy123 on 2005-11-20
thanks a lot for the How-To and a new version of initng. I have finanlly set it up on my laptop. I am not sure that the gain is significant (from 55 sec to 48 sec), but at least it is something. Hopefully, the boot time will eventually decrease, though I doubt if we ever catch up with Window, which is not obviously the aim.

---

### Post by cerberos on 2005-11-21
0.4.4-2 is all good, pre-emtivly did all the mods suggested in the last few days, and everything worked nice (after adding gdm & my other network cards to the run level)
In fact everything is working better than it was under 3.3-2, as now the FGLRX drivers are working :)

---

### Post by tuke81 on 2005-11-22
great how to thanks. It really boost up my boot time :D .

I had little script that make my mice working smoothly. I get it here:
[http://ubuntuforums.org/showthread.php?t=4357]("http://ubuntuforums.org/showthread.php?t=4357")
:confused: :( :mad: :???: 
So when I get this finally boot, mine script was gone and mice was veryvery sticky. But I thinked that it cant be so hard to make that script work again. So I did my best and get it working by adding few lines to /etc/initng/system/bootmisc.i:

```
#!/bin/sh
echo "Tunning Logitech mouse..."
lmctl -8 --sms
```

at the end before lines wait and exit 0, and vóila it works as smoothly as before. :D :cool:

---

### Post by sailor420 on 2005-11-23
[QUOTE=berserker]I think it's almost ready for prime time.[/QUOTE]

I'm not sure about that, but it's definitely an incredible piece of software, and I've been very impressed with the speed of development. It's still probably a year or more away from being able to be included in distros, though...

---

### Post by Trigger|Debian on 2005-11-23
[QUOTE=Benjamin_Lebsanft]Doesn't seem to work on amd64. I tried everything from compiling 0.3.3 0.3.5 and even 0.4.0. They all segfault. The deb magic posted some pages before doesn't work either. Is there something I do wrong or does initNG simply not work on my platform ?

Edit: Got it working, but reboot causes my BIOS to stop booting again without pushing the reset button.[/QUOTE]
Now I got a package for AMD64 on Alioth - maybe you want to test it.
If it doesn't work and you want the problem to be solved open a bug on [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net)

---

### Post by sailor420 on 2005-11-25
Anyone had any luck getting the newest version, 0.4.4-2 running? It's hanging on me, just before starting GDM...

Edit: ngc -s revealed that system/laptop-mode had failed to start... I don't really know where to go from here though... Anyone have any ideas?

---

### Post by berserker on 2005-11-25
[QUOTE=sailor420]Anyone had any luck getting the newest version, 0.4.4-2 running? It's hanging on me, just before starting GDM...[/QUOTE]

Did you try the fix below?

[QUOTE=Bitmastro]in gdm.i and instant-gdm.i the path should be /usr/sbin/gdm instead of /usr/bin/gdm. in laptop-mode.i I put /usr/sbin/laptop-mode start instead of laptop_mode. hald seems to be running.
bye[/QUOTE]

---

### Post by sailor420 on 2005-11-25
[QUOTE=berserker]Did you try the fix below?[/QUOTE]

Just tried that, and it fixed the hang with laptop-mode... Now everything seems to be started, but its still hanging. Oddly enough, I can get to TTY2-6, but the first one just hangs there after everything is done--no prompt, no "Runlevel default up in X seconds", nothing. :(

---

### Post by JimmyJazz on 2005-11-25
honesty, WOW this is great very good work I'm loving my new boot time this marks a heavy blow to any thoughts I was having of ever going back to windows.

---

### Post by JimmyJazz on 2005-11-25
also is it me or are shutdown times much faster as well

---

### Post by Trigger|Debian on 2005-11-25
[QUOTE=sailor420]Just tried that, and it fixed the hang with laptop-mode... Now everything seems to be started, but its still hanging. Oddly enough, I can get to TTY2-6, but the first one just hangs there after everything is done--no prompt, no "Runlevel default up in X seconds", nothing. :([/QUOTE]
You will never get a login on tty1 per default - but if ou have no "Runlevel default up in X seconds" something is wrong.
Which service fails? Login on tty2 and have a look at "ngc -s".

[QUOTE=JimmyJazz]also is it me or are shutdown times much faster as well[/QUOTE]
For sure they are - Initng stops services parallel if possible. SysVinit doesn't.

---

### Post by jcmkk3 on 2005-11-26
[QUOTE=temcat]This is coming soon, too: [http://nat.org/2005/october/#Keep-It-Simple-Stupid](http://nat.org/2005/october/#Keep-It-Simple-Stupid)[/QUOTE]

I was wondering if you were meaning that you were working on implementing Nat's idea, or that it was just generally coming soon to gnome?  Of course it's easy enough to use that little script to log into gnome, the problem is logging out.  Anyone know how to get gnome to log out properly when starting with Nat's script?  It would be great to get this thing working right because it makes things just that much speedier.

---

### Post by sailor420 on 2005-11-26
[QUOTE=Trigger|Debian]You will never get a login on tty1 per default - but if ou have no "Runlevel default up in X seconds" something is wrong.
Which service fails? Login on tty2 and have a look at "ngc -s".[/QUOTE]

Yes, but tty1 should be launching GDM, correct? It just hangs there. And I forgot to add to the previous post, I did just what you suggested and checked ngc -s, and didn't see anything that had failed to start.

EDIT:

OK, I was stupid and forgot to add GDM to the startup, which is why it wasnt starting. I did that, and it worked fine. Still lots of errors (CPU frequency scaling, HAL, and wireless not working), but I'll play with those a bit later and see what I can get going.

---

### Post by Trigger|Debian on 2005-11-26
Don't forget to edit daemon/dbus.i as proposed above to get dbus/hal working.

---

### Post by foxy123 on 2005-11-26
what about splash? will it work in initng?

---

### Post by sailor420 on 2005-11-26
[QUOTE=Trigger|Debian]Don't forget to edit daemon/dbus.i as proposed above to get dbus/hal working.[/QUOTE]

Got it, that fixed the HAL error.

So, problems remaining:

1) CPU Scaling. I did the fix mentioned in the HOWTO, and it now works, but is throwing all sorts of errors at the start and adding about 8-10 seconds to the boot time as it times out. Any ideas? Has anyone gotten CPU scaling to work on 4.4?
2) Wireless. Eth1 is my primary connection (wireless), and is static. I setup the eth1.i file as it was on the Gentoo forums (linked to in the post about setting up eth1 for DHCP), but it won't work. It's configured on boot, and when I open the network config tool, everything is as it should be (SSID, WEP key, IP address, gateway, DNS, etc), but it's still not working. It's seeing the access point, but won't connect despite my tinkering. I also made sure that eth1 is set as the default gateway device, to no avail. Any ideas?

---

### Post by foxy123 on 2005-11-26
Scaling and wi-fi work fine for me.

---

### Post by sailor420 on 2005-11-26
[QUOTE=foxy123]Scaling and wi-fi work fine for me.[/QUOTE]

Is wifi your primary connection? Is it static IP or DHCP? What did you do to get scaling working?

---

### Post by foxy123 on 2005-11-26
[QUOTE=sailor420]Is wifi your primary connection? Is it static IP or DHCP? What did you do to get scaling working?[/QUOTE]
no, wi-fi is not my primary connection, though I use it quite often when I need to work downstairs) and it uses DHCP.

I just edited the script from the link in the how-to.
That's my wlan0.i
```
 service net/wlan0 {
    depends = system/initial system/checkroot system/modules
        start {
        echo "Starting net/wlan0 now"
        ifup wlan0
        }
        stop {
        echo "Stopping net/$NAME now"
        ifconfig $NAME down
        }
}

```

oh, for scaling I followed another lonk from HOW-TO, but add
```
modprobe acpi_cpufreq
```

instead 
```
modprobe speedstep_centrino
```

---

### Post by sailor420 on 2005-11-26
[QUOTE=foxy123]no, wi-fi is not my primary connection, though I use it quite often when I need to work downstairs) and it uses DHCP.[/QUOTE]

Hmm... That's exactly what I have, except for the wifi script being set to my connection and my using speedstep_centrino because that's what my machine uses... :( Back to tinkering...

---

### Post by sailor420 on 2005-11-26
An ifconfig eth1 while in an InitNG boot is returning this:

```

eth1      Link encap:UNSPEC  HWaddr 00-02-8A-78-71-CF-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.7.63  Bcast:192.168.7.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:153 errors:1975 dropped:0 overruns:0 frame:1975
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:9753 (9.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000

```

Link encap should be Ethernet and the HW Address clearly shouldn't have all those extra zeroes on the end... Any idea whats going on?

---

### Post by tariqf on 2005-11-27
Hi I've gone through this howto and everything works fine on my thinkpad r50e except I get the following error on boot;

localhost daemon/hald: /dev/mem: Permission denied

Any ideas what I can do?

---

### Post by rogeriovinhal on 2005-11-27
I managed to fix things and get everything to work fine, but at shutdown I get this error:
```
Nov 27 11:47:10 localhost InitNG: "initng_kill_handler.c", handle_killed_daemon() #157 FAIL:  daemon daemon/klogd, Returned with exit 1.
```

I also made splash work with InitNG, but the progress bar remains empty until the end.
As there is a percentage shown by InitNG, I think there may be a way to syncronize that with splash status bar. But how?

EDIT I am using 0.4.4-2

---

### Post by foxy123 on 2005-11-27
[QUOTE=rogeriovinhal]I also made splash work with InitNG, but the progress bar remains empty until the end.
As there is a percentage shown by InitNG, I think there may be a way to syncronize that with splash status bar.[/QUOTE]
hey, please keep us posted about your progress with splash, I am quite interested in this as well. BTW, how did you manage to make it work at all?

---

### Post by Trigger|Debian on 2005-11-27
Maybe you can get the splash working maybe not. Someone wrote a usplash plugin for Initng, but I don't know if it works.
Do the following: Get the sources of the package, edit debian/rules - configure must be run with --with-usplash, build the package with dpkg-buildpackage or whatever, add system/usplash to system.runlevel.

---

### Post by Tails on 2005-11-27
[QUOTE=Bitmastro]in laptop-mode.i I put /usr/sbin/laptop-mode start instead of laptop_mode. hald seems to be running.[/QUOTE]

what line I should put the "start" in??? cos, I dun see I fit that in to the script...

```

# description: Starts and stops "laptop-mode" - tweaks system behavior
#              to extend battery life.
#
# config:  /etc/laptop-mode/laptop-mode.conf

service system/laptop-mode {
        need = system/initial system/mountfs
start {
        /usr/bin/touch /var/run/laptop-mode-enabled

        # Run it with "force" so that syslog.conf and hdparm settings
        # are set correctly at system bootup.
        if [ -e /usr/sbin/laptop_mode ]; then
            /usr/sbin/laptop_mode auto force > /dev/null
        else
            /bin/echo "/usr/sbin/laptop_mode not found!"
            exit 1
        fi
        exit 0
}
stop {
        rm -f /var/run/laptop-mode-enabled
        if ! ( /usr/sbin/laptop_mode stop > /dev/null ) ; then
                exit 1
        fi

        exit 0
}

}

```

---

### Post by Trigger|Debian on 2005-11-27
Replace every laptop_mode with laptop-mode and you'll be fine.

---

### Post by rogeriovinhal on 2005-11-27
[QUOTE=foxy123]hey, please keep us posted about your progress with splash, I am quite interested in this as well. BTW, how did you manage to make it work at all?[/QUOTE]

Just eliminate all the "FATAL" warnings in bootup (you can see them in /var/logs/syslog) and put splash in grub. That should work without the progress bar.

It used to go back to verbose mode because of the errors, if there aren't any, it shouldn't.

---

### Post by benplaut on 2005-11-27
acpi is broken, and ath0 wifi won't configure at boot (only ethX :(  ), but for 13second boot, this is worth it!!!

---

### Post by souled on 2005-11-27
Ok I need a little help with some scripts. I want to run privoxy and tor. The script for privoxy is ```

service daemon/privoxy {
        need = system/initial system/localmount net/lo
        use = net/eth0
        daemon = /usr/sbin/privoxy
        daemon_args = "/etc/privoxy/config"
        pid_file = /var/run/privoxy.pid
}


```

And my script for tor is ```

service daemon/tor {
        need = system/mountfs net/lo virtual/networking daemon/privoxy
        daemon = /usr/sbin/tor
        daemon_args = --chuid tor
        pid_file = /var/run/tor/tor.pid
        HOME=/var/lib/tor
} 

```

When I start up, I can see some errors about privoxy and tor (but it goes by too fast). It says something about stuff not being found; I just know that they aren't being started. I added daemon/privoxy and daemon/tor to the default.runlevel which is what I'm supposed to do, right? Can anyone help me out?

---

### Post by alvinblank on 2005-11-27
If I wanted to remove InitNG, I just remove the deb packages and leave everything as it it? or do I need to change the files that were edited pior to InitNG?

---

### Post by ltmon on 2005-11-27
[QUOTE=alvinblank]If I wanted to remove InitNG, I just remove the deb packages and leave everything as it it? or do I need to change the files that were edited pior to InitNG?[/QUOTE]

If you want to stop using initng all you have to do is revert your /boot/grub/menu.lst entry to what it was previously.

If you really need to save the disk space (and initng doesn't take up much at all) just remove the package.

L.

---

### Post by benplaut on 2005-11-27
how do i get nvram to load at startup? messing up ThinkpadButtons

---

### Post by souled on 2005-11-28
Ok, I discovered the ngc command. When I try sudo ngc -u daemon/tor, I get this output ```
Message from syslogd@localhost at Sun Nov 27 21:41:26 2005 ...
localhost InitNG: "initng_i_parser.c", parse_opt() #749 FAIL: parse_opt(daemon/tor): line: "daemon = /usr/sbin/tor"!

Message from syslogd@localhost at Sun Nov 27 21:41:26 2005 ...
localhost InitNG: "initng_i_parser.c", parse_opt() #752 FAIL: sleeping 2 seconds......

Message from syslogd@localhost at Sun Nov 27 21:41:28 2005 ...
localhost InitNG: "initng_i_parser.c", parse_file() #256 FAIL: PARSE ERROR parse_file(daemon/tor): sleeping 2 seconds, then ABORT......
Got an response from initng, version: 0.4.4
Starting service:
        Failed to start service, daemon/tor (NOT_FOUND)
Command u, daemon/tor - Bad result!

```

The output is basically the same for privoxy. WHat do these errors mean?

---

### Post by foxy123 on 2005-11-28
[QUOTE=Trigger|Debian]Maybe you can get the splash working maybe not. Someone wrote a usplash plugin for Initng, but I don't know if it works.
Do the following: Get the sources of the package, edit debian/rules - configure must be run with --with-usplash, build the package with dpkg-buildpackage or whatever, add system/usplash to system.runlevel.[/QUOTE]
compiling and installing with checkinstall gives me the same error
```
dpkg: error processing initng_0.44-1_i386.deb (--install):
 trying to overwrite `/etc/hotplug/net.agent', which is also in package hotplug
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
```

I wonder what it means?

Anyway splash works fine (apart from progress bar) with 0.44 deb. I guess it is already compiled with usplash.

---

### Post by Trigger|Debian on 2005-11-28
[QUOTE=foxy123]I wonder what it means?

Anyway splash works fine (apart from progress bar) with 0.44 deb. I guess it is already compiled with usplash.[/QUOTE]
You should download the sources of the Debian packages and you won't have these problems. It is not compiled with --usplash. That's what you need to change.

---

### Post by foxy123 on 2005-11-28
[QUOTE=Trigger|Debian]You should download the sources of the Debian packages and you won't have these problems. It is not compiled with --usplash. That's what you need to change.[/QUOTE]
where can I find it? All I see are either source without deb-config or precompiled debs.

---

### Post by Trigger|Debian on 2005-11-28
On Alioth - *.dsc *.diff and *.orig.tar.gz are your friends.

---

### Post by foxy123 on 2005-11-28
[QUOTE=Trigger|Debian]On Alioth - *.dsc *.diff and *.orig.tar.gz are your friends.[/QUOTE]
i really do not know what to do with them. Are you planning to make next version with usplash enebled?

---

### Post by Trigger|Debian on 2005-11-28
Ok, so forgett it.
If it has no disatvantages I will build it with usplash enabled - but I think it should be no problem.

EDIT: 0.4.6 is out - I hope I'll buildthe package soon. Have very less time ATM.

---

### Post by Benjamin_Lebsanft on 2005-11-29
[QUOTE=Trigger|Debian]Now I got a package for AMD64 on Alioth - maybe you want to test it.
If it doesn't work and you want the problem to be solved open a bug on [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net)[/QUOTE]
working fine, thanks! Although I managed to compile it somehow on my old ubuntu version ^^

---

### Post by qaqa on 2005-11-30
I followed the directions for InitNG  - it shaves off more than 10 secs off my startup time!! 

I have a strange problem though :
Each time I start a console (konsole, gnome-terminal or even xterm) , I get an error message "Unable to launch child process". KDE su complains "the program su is not found" "Please check your PATH".
In KDM/GDM, if I select the "failsafe terminal" option, it immediately exits back to KDM/GDM..
So, I'm basically unable to get the command line!!

Has anyone else faced the same problems?

---

### Post by nim278 on 2005-11-30
Are you able to get a command line via CTRL+ALT+F1 ?

---

### Post by qaqa on 2005-11-30
[QUOTE=nim278]Are you able to get a command line via CTRL+ALT+F1 ?[/QUOTE]

Nope, no command line..infact, ctrl-alt-F1 doesnt do anything for me - not even an error message..

---

### Post by foxy123 on 2005-11-30
found a way to recompile it with usplash and progress bar works now... in a way..

---

### Post by Triton on 2005-12-02
NE1 have or could build me a script to launch apache2.  :D

---

### Post by curtis on 2005-12-03
[QUOTE=Triton]NE1 have or could build me a script to launch apache2.  :D[/QUOTE]
apache2 is built in...
ng-update add apache2 default

---

### Post by lucas on 2005-12-03
[QUOTE=curtis]apache2 is built in...
ng-update add apache2 default[/QUOTE]
Doesn't work for me though, i have to start it manually later, aswell mpdscribble (i  downloaded a script for it from the forums)

---

### Post by reet on 2005-12-03
Hi,
I have finally found the time to try this out, however I have run into a problem and cannot boot using InitNG. I have Ubuntu using 2 partitions: one partition for / and one partition for /home/. Both partitions are ReiserFS. Here is the error I get when booting:

```
Target filesystem does not have /sbin/initng
```
I don't understand this error because....YES IT DOES. I have checked and everything has been installed correctly according to this HowTo. My GRUB configuration for InitNG looks like this:

```
title		Ubuntu, kernel 2.6.12-10-k7 (InitNG)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro nolapic quiet init=sbin/initng
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot
```
Where hda4 is the partition mounted as /. What have I done wrong?

---

### Post by mw99 on 2005-12-03
Hi,

I'm trying to hack together a replacement for the postgres.i which ships with InitNG 0.4.7 as it won't start the server, and doesn't appear to use the best postgres scripts available (uses pg_ctl when pg_ctlcluster is available as a more sophisticated wrapper to it).

I figure I've done something dumb but just can't spot it, so any pointers much appreciated. I've tried it using both script and exec formats - the "su..." code in the script statements starts postgres fine from a root terminal:

```
service daemon/postgres {
    need = system/initial system/mountfs net/lo;
    script start = {
	su postgres -c "/usr/bin/pg_ctlcluster 8.0 main start 2>&1 > /dev/null"
    };
    script stop = {
	su postgres -c "/usr/bin/pg_ctlcluster 8.0 main stop 2>&1 > /dev/null"
    };
}
```

OR

```
service daemon/postgres {
    need = system/initial system/mountfs net/lo;
    suid = postgres;
    sgid = postgres;
    exec start = /usr/bin/pg_ctlcluster;
    exec_args start = 8.0 main start;
    exec stop = /usr/bin/pg_ctlcluster;
    exec_args stop = 8.0 main stop;
}
```

However, when I try to start deamon/postgres:

```
root@thinkpad:/etc/initng# ngc -u daemon/postgres
Next Generation init Control. version: 0.4.7
written by Jimmy Wennlund <jimmy.wennlund@gmail.com>

Got an response from initng, version: 0.4.7
Starting service:
        Failed to start service, daemon/postgres (FAIL_STARTING)
Command u, daemon/postgres - Bad result!

```
As I said, any pointers will be really appreciated!

---

### Post by reet on 2005-12-03
[QUOTE=reet]
```
Target filesystem does not have /sbin/initng
```
I don't understand this error because....YES IT DOES. I have checked and everything has been installed correctly according to this HowTo.[/QUOTE]
I've looked into this a little further. After I get the error, I am kicked to an "ash" command line. From here, I went into the /sbin directory, and sure enough there was no initng file. There were only a few contents and they are as follows:

udev
mdrun
modprobe
vgechange
udevstart
mdadm
rmmod
depmod
evms_activate

---

### Post by reet on 2005-12-03
Got it working. I missed the "/" before "sbin" in my grub configuration. Everything is working now.

---

### Post by Limulus on 2005-12-04
[QUOTE=temcat]Frustrated with the long boot time in Breezy and want to do something about it? Here comes the remedy! Meet InitNG - a new generation init program that is able to reduce your boot time by a third to a half. Below are step-by-step instructions how to do it on your system.

IMPORTANT: InitNG is pretty much work in progress, and not all things may work. Currently it does everything I personally want, but it may not be the case for you - your success depends on the combination of hardware and software you use. Suggestions, fixes, hacks and workarounds offered by people will be incorporated in this HOWTO.

[snip]

Have Fun.[/QUOTE]

Here's my experience using a Toshiba Satellite A25 laptop running Breezy.

First, following the instructions is important ^_-;  I browsed Alioth and downloaded the most recent version of InitNG... which didn't work (it stopped at 100%).

The version linked from the instruction post did work though. From when I press Enter in the GRUB menu until all the applets are loaded in Gnome, the boot time went from ~125 seconds down to ~95; nice!

I rebooted later and there was a glitch; Ubuntu was mounting my HD for the 30th time and so it did its little check... which ran, but the display was wacky; instead of nicely sitting at the bottom of the page, it took up the whole screen, displaying each percentage with the bar graph as a separate entry.  When it finished, insetead of completing the boot, it tried to *reboot*; there was some sort of mention about a hot reboot (?) but it didn't work.  I manually powered down and then back up again and it worked fine again.

So still a little rough around the edges, but wow, what speed! =D

**Edit:** I also tried 0.4.0-1 [as per the post]("http://ubuntuforums.org/showthread.php?t=80423&p=501661#103"), but it had the same problem as 0.4.4-2, even after modifying laptop-mode.i

---

### Post by Limulus on 2005-12-04
[QUOTE=Limulus]there was some sort of mention about a hot reboot (?) but it didn't work.[/QUOTE]
My memory of it was almost right; as per [http://initng.thinktux.net/index.php/Main_Page](http://initng.thinktux.net/index.php/Main_Page) it was a "really warm reboot" :)

**Edit:** Another glitch: I wanted to go into the printer settings (System -> Administration -> Printing) using initng 0.3.3-2 but I got the error: *The CUPS server could not be contacted.*  Rebooting without using initng worked fine.

---

### Post by Jingo on 2005-12-10
InitNG 0.4.7 is out...

Will there be an .deb package soon, or should I just compile this myself?

How do I create a .deb package if I compile this?

---

### Post by Trigger|Debian on 2005-12-10
Wait till tomorrow - maybe I'll find the time. Don't have mutch at the moment.
If not: compile it yourself. For 0.4.8 i'll definitely create a package as soon as it's out.

---

### Post by Trigger|Debian on 2005-12-11
The package for 0.4.7 is finally there. Read [http://triggerit.funpic.de/blog/?p=32](http://triggerit.funpic.de/blog/?p=32) for some notes about it.
Feedback is very welcome!

---

### Post by curtis on 2005-12-11
[QUOTE=Trigger|Debian]The package for 0.4.7 is finally there. Read [http://triggerit.funpic.de/blog/?p=32](http://triggerit.funpic.de/blog/?p=32) for some notes about it.
Feedback is very welcome![/QUOTE]
Will try now and post if it works.

---

### Post by curtis on 2005-12-11
Just tried it now.
Had some issues with acpid and hald starting, at least it booted up ;)

---

### Post by reet on 2005-12-11
I've just tried 0.4.7 with much success. In the version changes it reads:

   * Should be fully compatible to Ubuntu now - no more changes needed

Very nice. This is the first version where HAL has loaded without errors. The only change I actually had to make to the scripts was to add lrm-manager to "system/initial.i" to make sound work.

---

### Post by Trigger|Debian on 2005-12-11
[QUOTE=reet]The only change I actually had to make to the scripts was to add lrm-manager to "system/initial.i" to make sound work.[/QUOTE]
That's strange - lrm-manager should be started in system/modules.
Ah, I know - alsasound.i doesn't depend on modules.i. Will fix this with the next release.

---

### Post by Trigger|Debian on 2005-12-11
[QUOTE=curtis]Just tried it now.
Had some issues with acpid and hald starting, at least it booted up ;)[/QUOTE]
At least the acpid problem is fixed with the last bugfix release I made - there's missing a ';' ath the end of one of the first lines.
What's the problem with hal? Do you know how to fix it?

---

### Post by souled on 2005-12-11
With 0.47, I'm getting the "HAL failed to initialize" error when I log in to gnome. Do I have to modify a file to get this to stop?

---

### Post by curtis on 2005-12-11
I will look into fixing the issue with HAL, if I do find a way I'll post here.

Edit: the APCID bug must of caused HAL not to work... it works perfect with the newest package, good work :)

---

### Post by Trigger|Debian on 2005-12-11
Puh, can anyone compare /etc/initng/daemon/dbus.i and /etc/init.d/dbus and tell me what could be the difference which causes this error on some boxes?

---

### Post by souled on 2005-12-11
[QUOTE=curtis]I will look into fixing the issue with HAL, if I do find a way I'll post here.

Edit: the APCID bug must of caused HAL not to work... it works perfect with the newest package, good work :)[/QUOTE]

How do I go about fixing this bug?

---

### Post by Trigger|Debian on 2005-12-11
Use 0.4.7-2 and the acpid bug is fixed.

---

### Post by souled on 2005-12-11
Thanks it works now. How come when I try and run the command "sudo ngc -u privoxy," I get this output:
```
Got an response from initng, version: 0.4.7
Starting service:
        Failed to start service, daemon/privoxy (NOT_FOUND)
Command u, privoxy - Bad result!

```
I have it in the default.runlevel file...  I'm trying to use the default privoxy.i that the deb comes with. Does it matter if I don't have privoxy.pid file in /var/run even though the privoxy.i file points to that?

---

### Post by Limulus on 2005-12-11
I just tried 0.4.7-2, letting it overwrite the modifications in the .i files I had made for 0.3.3-2; it booted up beautifully without me needing to modify anything.  Very nice! (hopefully this can be included on the Dapper disks :-)

[QUOTE=Limulus]I wanted to go into the printer settings (System -> Administration -> Printing) using initng 0.3.3-2 but I got the error: *The CUPS server could not be contacted.*  Rebooting without using initng worked fine.[/QUOTE]
Just FYI, I still get this CUPS error after booting with InitNG.

---

### Post by souled on 2005-12-11
[QUOTE=Limulus]I just tried 0.4.7-2, letting it overwrite the modifications in the .i files I had made for 0.3.3-2; it booted up beautifully without me needing to modify anything.  Very nice! (hopefully this can be included on the Dapper disks :-)


Just FYI, I still get this CUPS error after booting with InitNG.[/QUOTE]

You have to start the CUPS daemon. add daemon/cupsd to your default.runlevel file. To start it without rebooting type "sudo ngc -u cupsd" in the terminal after you add daemon/cupsd to the runlevel file.

---

### Post by reet on 2005-12-11
...and just in case you are unfamiliar with adding/removing daemons with initng, type the following command to add cups daemon so that it will start with every boot:

sudo ng-update add daemon/cupsd

Wow, this entire howto could probably be changed to 3 steps:
1) install initng 0.4.7
2) edit grub menu
3) reboot

---

### Post by berserker on 2005-12-11
Everything works here except when I open a Konsole terminal inside KDE I have no prompt.  I can use the terminal at TTY2 (Ctrl-Alt-F2) with no problems.

Any ideas?

---

### Post by Limulus on 2005-12-11
reet, souled: confirmed that running the two commands:

> sudo ng-update add daemon/cupsd
sudo ngc -u cupsd
got it working in the current InitNG session and it worked after I rebooted without any further intervention.

Trigger|Debian: Will CUPS be added to future versions of InitNG by default? (I note for example that I no longer need to run "sudo ng-update add daemon/gdm default" as I had to using 0.3.3-2)

---

### Post by foxy123 on 2005-12-12
The new version does not work for me. Firstly I tried to install it over 0.44 and it did not start cpu frequency scaling and samba and gave a bunch of errors during booting. I tried to fix it but without any luck. Then I decided to emove initng completely and start over again. Now it des not boot and gave a lot of errors.

Where is a boot log file, so I could post some errors here?

---

### Post by Noahod on 2005-12-12
[QUOTE=qaqa]I followed the directions for InitNG  - it shaves off more than 10 secs off my startup time!! 

I have a strange problem though :
Each time I start a console (konsole, gnome-terminal or even xterm) , I get an error message "Unable to launch child process". KDE su complains "the program su is not found" "Please check your PATH".
In KDM/GDM, if I select the "failsafe terminal" option, it immediately exits back to KDM/GDM..
So, I'm basically unable to get the command line!!

Has anyone else faced the same problems?[/QUOTE]

Yes! I have exactly the same problem, only with a kernel I compiled myself. However, the same kernel works fine without initng. Does anyone know how to fix this?

---

### Post by foxy123 on 2005-12-12
[QUOTE=Noahod]Yes! I have exactly the same problem, only with a kernel I compiled myself. However, the same kernel works fine without initng. Does anyone know how to fix this?[/QUOTE]
ah, that was it! I was wondering why I could not start some apps with sudo...

---

### Post by berserker on 2005-12-12
InitNG 0.4.4.2 worked fine for me but the latest creates the "no prompt in Konsole" and "kdesu not found" errors that others are experiencing.

---

### Post by Trigger|Debian on 2005-12-12
Maybe it's a little bug in the package - please have a look at system/initial.i and start mountvirtfs a second time after udev (last package did this - accidentially removed this in 0.4.7) - just copy the line from above.
I can't verify this cause I'm not on my box... Will have a look tomorrow.

---

### Post by foxy123 on 2005-12-12
I have managed to make it work, though not everything:

I had to add gdm to a defaul runlevel.
The typo (laptop_mode vs laptop-mode) is still in laptop-mode.i

I did not manage to make ACPI work. I changed speetstep.i and powernowd.i according to the post in this topic but it does not work with 0.47. It is my biggest problem at the moment.

what about samba daemon and cups? Should I add them manually to the default runlevel?

---

### Post by berserker on 2005-12-12
[QUOTE=Trigger|Debian]Maybe it's a little bug in the package - please have a look at system/initial.i and start mountvirtfs a second time after udev (last package did this - accidentially removed this in 0.4.7) - just copy the line from above.
I can't verify this cause I'm not on my box... Will have a look tomorrow.[/QUOTE]

That did the trick!  Konsole and su now work normally.  

I do receive an error on startup when dbus tries to load but hotplugging works normally so it doesn't seem to affect anything.

---

### Post by berserker on 2005-12-12
[QUOTE=foxy123]what about samba daemon and cups? Should I add them manually to the default runlevel?[/QUOTE]

I had to add samba and cups manually.

```
sudo ng-update add samba
sudo ng-update add cupsd
```

---

### Post by Trigger|Debian on 2005-12-12
Services are only added automatically onthe first start - if you want to do it later execute "/sbin/gen_system_runlevel overwrite".
Does this add your missing files?

I will make a release in some minutes - please tell me which problems are not removed with it. I'll work on them!

---

### Post by idlewild on 2005-12-12
It's all working here, just had to apply the changes mentioned previously to get frequency scaling working. However, as mentioned in the release notes, the syntax of the .i files has changed. So here's the new config files:

/etc/initng/system/speedstep.i
```
  service system/speedstep {
        need = system/initial system/modules system/mountroot;
        use = system/static-modules system/coldplug;
        script start = {
                /sbin/modprobe cpufreq-ondemand &> /dev/null
                /sbin/modprobe cpufreq_userspace
                /sbin/modprobe cpufreq_stats
                /sbin/modprobe cpufreq_powersave
                /sbin/modprobe cpufreq_conservative
                /sbin/modprobe speedstep_centrino
                /bin/cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor > /tmp/origgovanor
                echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
                exit 0
        };

        script stop = {
                echo `/bin/cat /tmp/origgovanor` > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
                exit 0
        }
}

```

/etc/initng/daemon/powernowd.i
```
daemon daemon/powernowd {
        need = system/initial system/mountfs system/speedstep;
        # use =
        exec daemon = /usr/sbin/powernowd;
        exec_args daemon = "-q";
}

```

---

### Post by Trigger|Debian on 2005-12-12
Here you are: [https://alioth.debian.org/project/showfiles.php?group_id=30760&release_id=658](https://alioth.debian.org/project/showfiles.php?group_id=30760&release_id=658)
I really need your feedback :)

Especially if dbus and hald are working!

---

### Post by Trigger|Debian on 2005-12-12
Gr...

---

### Post by Trigger|Debian on 2005-12-12
> **idlewild]```
  service system/speedstep {
        need = system/initial system/modules system/mountroot said:**
> 

```


Will see to apply this...

> 
/etc/initng/daemon/powernowd.i
```
daemon daemon/powernowd {
        need = system/initial system/mountfs system/speedstep;
        # use =
        exec daemon = /usr/sbin/powernowd;
        exec_args daemon = "-q";
}

```
Should not be needed anymore with 0.4.7-3

---

### Post by foxy123 on 2005-12-12
it seems to work fine now. Thanks Trigger|Debian for a new version and idlewild for ACPI support.

I have recompiled it with usplash and have a nice progress bar now...

---

### Post by Trigger|Debian on 2005-12-12
Nice.
Now I can go to bed without any sorrows. :)

Will see if I can ship "native" usplash support with the next version.

---

### Post by idlewild on 2005-12-13
After installing 0.4.7-3, [networkmanager]("http://www.gnome.org/projects/NetworkManager/")  which uses dbus and hal stopped working. Sorry to be vague but I couldn't find any errors relating to the problem.

---

### Post by Trigger|Debian on 2005-12-13
[QUOTE=idlewild]After installing 0.4.7-3, [networkmanager]("http://www.gnome.org/projects/NetworkManager/")  which uses dbus and hal stopped working. Sorry to be vague but I couldn't find any errors relating to the problem.[/QUOTE]

Can you please have a look if dbus and hald are running? I really have no idea what could be the problem, if they are running.

@all: Same issue? Any solution?

---

### Post by Limulus on 2005-12-13
[QUOTE=Trigger|Debian]@all: Same issue? Any solution?[/QUOTE]
Is the Gnome NetworkManager even in Ubuntu? I installed the network-manager package, but I don't think that's the same thing (is it?)

---

### Post by Jingo on 2005-12-14
[QUOTE=Trigger|Debian]@all: Same issue? Any solution?[/QUOTE]

NetworkManager is kind of working here.

dbus is starting both hald and NetworkManager automaticly. (/etc/dbus-1/event.d)

I had a problem on shutdown, where some NetworkManager related (maybe dhcpb), coredumped.
This I solved by compiling the latest kernel (2.6.14.3-ck6)!? :confused: 

NetworkManager seems to work fine, at least for wired lan. But when I fire up wireless it quits, but guess that is not InitNG related.

---

### Post by Trigger|Debian on 2005-12-14
[QUOTE=Jingo]dbus is starting both hald and NetworkManager automaticly. (/etc/dbus-1/event.d)
[/QUOTE]
That's why I'm asking wether hald is running - with 0.4.7-3 I changed the scripts and hald is started by Initng now (hopefully ;) ). /etc/dbus-1/event.d is not used anymore.

---

### Post by muchio on 2005-12-14
Hi, just upgraded to the 0.4.7A initng version on AsusA2500L laptop and found that the old problem with ACPI still persists:
initng keeps tryin to load ibm and toshiba acpi drivers. How should I fix that? 

Cheers!

---

### Post by Benjamin_Lebsanft on 2005-12-15
edit: my bad ^^

---

### Post by foxiness on 2005-12-16
is sl-modem-daemon will work with this ? and how can i get it work if not ?

/etc/init.d/sl-modem-daemon


note: now am on step 8 and i will continue do it...

---

### Post by sailor420 on 2005-12-16
I'm a bit confused on the status of the new .i startup scripts... Have most of them been rewritten and included in this package, or is it going to take a lot of tweaking to get things up and running?

---

### Post by Trigger|Debian on 2005-12-16
[QUOTE=sailor420]I'm a bit confused on the status of the new .i startup scripts... Have most of them been rewritten and included in this package, or is it going to take a lot of tweaking to get things up and running?[/QUOTE]
All scripts released by Initng and shipped with the package are changed - you only have to change scripts you have written on your own. So normally you don't have to change a thing.

BTW: I just released the package for Initng 0.4.8.

---

### Post by souled on 2005-12-16
Installed 4.8... Thanks Trigger. However, I still can't get privoxy to work. I tried using the .i file that came default, and when I run it I get this error. 
```
Message from syslogd@localhost at Fri Dec 16 17:15:09 2005 ...
localhost InitNG: "initng_struct_data.c", d_set_string_var() #204 FAIL: Type can't be zero!

Message from syslogd@localhost at Fri Dec 16 17:15:09 2005 ...
localhost InitNG: "initng_static_states.c", handle_START_DEP_MET_service() #207 FAIL: Service privoxy, could not launch start, did not find any to launch!

Message from syslogd@localhost at Fri Dec 16 17:15:09 2005 ...
localhost InitNG: "initng_struct_data.c", d_set_another_string_var() #259 FAIL: Type can't be zero!

Message from syslogd@localhost at Fri Dec 16 17:15:09 2005 ...
localhost InitNG: "initng_struct_data.c", d_set_another_string_var() #259 FAIL: Type can't be zero!

Message from syslogd@localhost at Fri Dec 16 17:15:09 2005 ...
localhost InitNG: "initng_struct_data.c", d_set_string_var() #204 FAIL: Type can't be zero!
        Failed to start service, privoxy (FAIL_STARTING)
Command u, privoxy - Bad result!
```

Please help!

---

### Post by berserker on 2005-12-17
[QUOTE=Trigger|Debian]BTW: I just released the package for Initng 0.4.8.[/QUOTE]

I get error messages about some of the startup scripts; however, everything seems to work.

The problem is on shutdown when it freezes and complains about hald.  I have to hit the reset button to reboot.

---

### Post by Limulus on 2005-12-17
[QUOTE=Trigger|Debian]BTW: I just released the package for Initng 0.4.8.[/QUOTE]
Thanks for the heads-up; I just tried it and it works great :)

Say, I don't suppose you'd consider making an InitNG repository?
(e.g. like Boinc did [http://pkg-boinc.alioth.debian.org/](http://pkg-boinc.alioth.debian.org/))

---

### Post by foxy123 on 2005-12-17
[QUOTE=Trigger|Debian]BTW: I just released the package for Initng 0.4.8.[/QUOTE]
you did not enable splash, did you?

---

### Post by Trigger|Debian on 2005-12-17
@souled: Don't see the problem - consider to file a bug here: [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net)

@berserker: Did you download the package immediately after I released it tonight? For some minutes there was a broken package availlable for download. Didn't expect people to be so fast... ;) Try the one you can download now.

@Limulus: :)
A repository is on my todo list. Gimme some time.

@foxy123: Argh, sorry. I forgot about it.  Next time...

---

### Post by reet on 2005-12-17
I've just upgraded my computer to an Athlon64 system yesterday and have installed initng 0.4.8 on the new system. On a fresh Xubuntu install, initng automatically wanted to start powernowd which caused a segment fault. Removing powernowd from the startup fixed that easy enough. However I am having troubles rebooting. When I hit the reboot button, Ubuntu logs off to and I get the login screen. So I hit the reboot button on the login screen (GDM), and I get "Please wait, system now rebooting" or something along those lines, but nothing happens.

---

### Post by Trigger|Debian on 2005-12-18
It seems as if there are various bugs with Initng and AMD64.
It should be hopefully fixed with the next release. Please try the next version (don't know when it will be released) and tell me wether this works better or not.

---

### Post by foxy123 on 2005-12-18
[QUOTE=reet]I've just upgraded my computer to an Athlon64 system yesterday and have installed initng 0.4.8 on the new system. On a fresh Xubuntu install, initng automatically wanted to start powernowd which caused a segment fault. Removing powernowd from the startup fixed that easy enough. However I am having troubles rebooting. When I hit the reboot button, Ubuntu logs off to and I get the login screen. So I hit the reboot button on the login screen (GDM), and I get "Please wait, system now rebooting" or something along those lines, but nothing happens.[/QUOTE]
I tried it yesterday on my desktop and had a similar problem, though it is run on ordinary Athlon, not 64. I will try 0.47 which works perfiectly on my laptop to check if it is something to do with new version...

---

### Post by Matriz on 2005-12-20
How i can get initng to shutdown my USB devices in shutdown( in this case: my usb mouse) ? When i shutdown ,mouse stay on... something to do with ACPI maybe?... thanks for nice howto btw :razz:
edit: and Breezys default booter does shut it down.

---

### Post by Gael on 2005-12-21
It works great! Very fast! =D> 

Perhaps still remains a fix: to check in "instant-gdm" about different */usr/sbin*-*/usr/bin* folders like "dbus" does.

¿How can I get USB disks appearing in my desktop? ¿Is this due to using "coldplug" instead of "hotplug"?
FIXED: I lost a ";" in *dbus.i*. ](*,) 

Sorry my english.

---

### Post by Trigger|Debian on 2005-12-21
[QUOTE=Matriz]How i can get initng to shutdown my USB devices in shutdown( in this case: my usb mouse) ? When i shutdown ,mouse stay on... something to do with ACPI maybe?... thanks for nice howto btw :razz:
edit: and Breezys default booter does shut it down.[/QUOTE]
Could you (and all others) open bugs for issues like this in Initng's Bugzilla on [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net), please? This is the easiest way to have issues like this fixed upstream.
It is very hard for me to fix bugs I can't reproduce - if you add it in Bugzilla you will reach a much wider audience.

EDIT: Thanks for reporting the mouse issue (if it was you) :)

---

### Post by Matriz on 2005-12-23
Done. sry about it, dident know about initng bugzilla :rolleyes:

---

### Post by Trigger|Debian on 2005-12-23
Thx.
No problem - where should you knowit from. That's why I mentioned it ;)
Keep on finding and reporting Bugs!

---

### Post by curtis on 2005-12-23
Hi,
Last time I tried initng gets stuck on dbus with Dapper Drake.
I think this is due to the new releases of udev and possibily breakage of HAL and Dbus.
I'll attempt to fix it when I get back to my main computer (With Dapper Drake)

Edit: Now that I think about it, it probably is not an issue with Initng really... probably just broken packages.

---

### Post by kurokikaze on 2005-12-25
I'm running Ubuntu 5.10 on AMD64. I've downloaded initng_0.4.8-1_amd64.deb from the original site and correctly installed it. When I reboot I got a segmentation fault error on the Powernowd service. Has anyone solved or bypassed the amd64 version's bugs?

---

### Post by curtis on 2005-12-25
[QUOTE=curtis]Hi,
Last time I tried initng gets stuck on dbus with Dapper Drake.
I think this is due to the new releases of udev and possibily breakage of HAL and Dbus.
I'll attempt to fix it when I get back to my main computer (With Dapper Drake)

Edit: Now that I think about it, it probably is not an issue with Initng really... probably just broken packages.[/QUOTE]

Actually it boots up fine with the latest InitNG package, should of tried the latest first.
Only little warnings, but that is due to a half working HAL and DBUS in Dapper (Correct me if I am wrong of course)

---

### Post by Trigger|Debian on 2005-12-25
[QUOTE=kurokikaze]I'm running Ubuntu 5.10 on AMD64. I've downloaded initng_0.4.8-1_amd64.deb from the original site and correctly installed it. When I reboot I got a segmentation fault error on the Powernowd service. Has anyone solved or bypassed the amd64 version's bugs?[/QUOTE]
Initng is unusable an AMD 64 with versions prior to 0.5.0 - the package for 0.5.0 is lying in svn ([http://svn.debian.org/wsvn/pkg-initng)](http://svn.debian.org/wsvn/pkg-initng)), but I don't release it because of a littel bug with the environment files. If someone really want to have it: Build it out of this svn (I won't tell you how - you should know it if you want to try ;))

---

### Post by kurokikaze on 2005-12-27
[QUOTE=Trigger|Debian]Initng is unusable an AMD 64 with versions prior to 0.5.0 - the package for 0.5.0 is lying in svn ([http://svn.debian.org/wsvn/pkg-initng)](http://svn.debian.org/wsvn/pkg-initng)), but I don't release it because of a littel bug with the environment files. If someone really want to have it: Build it out of this svn (I won't tell you how - you should know it if you want to try ;))[/QUOTE]
Thanks, Trigger. Maybe I'll give it a try and let you know the results

---

### Post by reet on 2005-12-28
Due to the many probelms I've had with the AMD64 version of Ubuntu (well not Ubuntu's fault but the fault of other software that isn't 64-bit ready), I've moved back to 32-bit Ubuntu. By default, powernowd and nvidia-glx are started at boot. In the 64bit system, they caused a segment fault and I could not boot. On 32-bit they cause an error that whizzes by and I can't read it, but the computer does boot. Since I am not running a laptop, powernowd can be safely removed, and nvidia-glx doesn't seem to do anything, so I removed it as well from the startup routine.

Due to a post on a local mailing list, I have come to the realization that speed stepping is not working with the latest version of InitNG. There is an error at boot about a file scaling_governor that cannot be found when running the speedtep script. I have found that speed stepping works  when booting normaly without InitNG.

My processor is a Socket 939 Athlon64 3000+ (1.8GHz)
Motherboard is a Asrock 939Dual-SATA2

---

### Post by DigitalAxis on 2006-01-03
Wow.  So far all I've done is install InitNG-4.8_1, change my boot configuration, comment out GDM so I don't get two X sessions loading, and MAN...

With init, my computer takes 2:50 (GRUB to KDM) to boot.  With initNG my computer takes 1:02 to boot.  That's still too long, but there you go.  (I'm not connected to a LAN, that's where most of the boot time seems to be)

----

I am concerned about the system apparently trying to find the /sbin/nvidia-glx-config program first thing, and giving nasty errors when it can't.    I still get X with nVidia drivers, but should I change the order of something to get it to boot?  I assume the error has to do with the mountvirtfs not being done by the time it tries to find something on a virtual FS?  Hopefully SpeedStep will work with the next release too.

Actually, I have a lot of odd errors like the system failing to load a couple modules for things I know I don't have; will commenting out things like the hw_random and toshiba make anything go faster?

---

### Post by curtis on 2006-01-03
Newest release works perfect with Dapper.
Only thing I need to have a go at is removing the errors on NetworkManager and NetworkManagerDispatcher :D

---

### Post by DigitalAxis on 2006-01-04
Hmm...  Scratch those optimistic notes; my system froze when I tried to turn it off yesterday.  It printed out a lot of USB errors, and vc1 displayed a line about system/screen-console (or console-screen) having been started after 41000 seconds, which I calculate to be 11 hours plus...

Any thoughts? And where do you remove the modules it can't load?

---

### Post by Thug on 2006-01-05
i have tried to use initng. for the boot, no problems. but cups and iptables seems to be non-existant (for iptables i use a script that start automatically with B.U.M). wich kind of command i have to type in shell to make initng able to start this programs at start-up? thanks

Ps: sorry for my english :)

bye

---

### Post by otake-tux on 2006-01-05
initng is great. it definetly does reduce boot time.  

I found a sort of solution for the wireless problem.
I dont like to be connected at boot.  I like to activate my wireless card when I feel like it so I wrote a bash script.  Initng fails to modprobe ndiswrapper so each time you want to get online you have to modprobe ndiswrapper and the go to network-admin andactivate it.  So I wrote the following simple bash script:
type nano filename then

```
#!/bin/sh
sudo modprobe ndiswrapper
network-admin
exit
```
then chmod 555 filename
and whenever you want to activate your wireless card just right ./filename and activate it in network-admin.

I know this is not a fix but its better than having to modprobe each time you want to get online.  Does anyone have a better script?

---

### Post by Thug on 2006-01-05
[QUOTE=Thug]i have tried to use initng. for the boot, no problems. but cups and iptables seems to be non-existant (for iptables i use a script that start automatically with B.U.M). wich kind of command i have to type in shell to make initng able to start this programs at start-up? thanks

Ps: sorry for my english :)

bye[/QUOTE]
ok for cups. just the problem with the script for iptables (this file is in /etc/init.d)

---

### Post by BateauSurLEau on 2006-01-05
Hello

I'm having some problem with initNG 0.5 : I compiled the source on a Breezy amd64, everything went fine. I then followed the HOWTO, made the necessary changes in the files, etc...
The system boots fine (apart from some errors which I can't see, they're printing too fast) but I'm stuck with X : I'm in console-mode, in tty6 (don't know why, not that it matters... I think), and X won't start.
startx tells me no screen was detected. I'm using NVidia's 8178 driver on a GeForce4 MX 440, so I don't see why it doesn't work.

Thanks in advance, hope you got an idea to drag me out of this.

---

### Post by Trigger|Debian on 2006-01-08
[http://triggerit.tr.funpic.de/blog/?p=34](http://triggerit.tr.funpic.de/blog/?p=34)
Tell me which bugs persist - or better use bugzilla.
One word to the tutorial on page one: Most of the stuff isn't needed anymore. It should be updated!

---

### Post by foxy123 on 2006-01-08
[QUOTE=Trigger|Debian][http://triggerit.tr.funpic.de/blog/?p=34](http://triggerit.tr.funpic.de/blog/?p=34)
Tell me which bugs persist - or better use bugzilla.
One word to the tutorial on page one: Most of the stuff isn't needed anymore. It should be updated![/QUOTE]

thanks a lot. No splash I guess?

---

### Post by Trigger|Debian on 2006-01-08
You're right, sorry.
It was (is) on my todo list, but i was happy enough to have a running package. Didn't have the time to test different splash stuff.
Please report if the package works - I need some feedback.

---

### Post by BateauSurLEau on 2006-01-08
Nice release, my problem disappeared, I can now boot fine.
Thanks a lot.

---

### Post by berserker on 2006-01-08
[QUOTE=Trigger|Debian]
Please report if the package works - I need some feedback.[/QUOTE]

The latest one that works for me is 0.4.7-3.  The 0.5.1 gives me an fsck.ext2 error right after loading the kernel and stops there.

---

### Post by Dr Von Bon Bon on 2006-01-08
If I install this will it have any effect on how my computer runs, apart from the boot time of course?


Thanks.

---

### Post by Limulus on 2006-01-09
I upgraded from 0.4.8-1 to 0.5.1-1; the first time I booted with it, when Ubuntu started, there was an error message about HAL not starting... so I rebooted with it and then I noticed that my Battery Charge Monitor wasn't working.  Rebooting with the normal system, it worked fine *shrug*

I'll file a bug in a moment.

A curious note: when I uninstalled 0.5.1-1 and reinstalled 0.4.8-1, the latter didn't sart up like it had previously, even when I deleted /etc/initng first.

---

### Post by foxy123 on 2006-01-09
[QUOTE=Limulus]I upgraded from 0.4.8-1 to 0.5.1-1; the first time I booted with it, when Ubuntu started, there was an error message about HAL not starting... so I rebooted with it and then I noticed that my Battery Charge Monitor wasn't working.  Rebooting with the normal system, it worked fine *shrug*

I'll file a bug in a moment.

A curious note: when I uninstalled 0.5.1-1 and reinstalled 0.4.8-1, the latter didn't sart up like it had previously, even when I deleted /etc/initng first.[/QUOTE]

I've got the same problem with battery monitor.

---

### Post by foxy123 on 2006-01-09
I googled high and low, turned to IRC but still cannot find the solution to the batery monitor problem. I guess something does not load, but what and how to fix it?

---

### Post by Trigger|Debian on 2006-01-09
@foxy123: Wanted to talk to you in IRC, but the internet connection in university left me :(
Come around again and I'll be there hopefully.
Maybe it is a problem with acpid, but i'm not sure. Are the modules specified in /etc/default/acpid loaded? Try "modprobe battery". Is hal running and working?

@berserker: Maybe this is a problem with a too slow udev. I will investigate and hopefully find a solution. Can you try to delay initial.ii a bit with a "wait"a dn wee if it works then?

---

### Post by Heliode on 2006-01-09
[QUOTE=berserker]The latest one that works for me is 0.4.7-3.  The 0.5.1 gives me an fsck.ext2 error right after loading the kernel and stops there.[/QUOTE]

Same for me. Has anyone found a way around this yet?

---

### Post by Trigger|Debian on 2006-01-09
It seems to be the following bug: [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=393](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=393)

---

### Post by DigitalAxis on 2006-01-10
With InitNG 0.4.8-1, I only once (out of about 4 times) managed to shut down properly, every other time the system hung when it got to turning off the USB ports.  I'm not sure why.

With InitNG 0.5.1, everything's much slower, and the system hangs where it's trying to detect the ethernet cable (that's not plugged in).  I CAN use Ctrl-Alt-Del to get it to halfway shut down, but it won't even turn off properly.  I haven't looked at the log yet, but my system no longer boots with splash when set to boot normally.

---

### Post by Limulus on 2006-01-11
DigitalAxis: if you unistall InitNG does it boot normally then?

---

### Post by Trigger|Debian on 2006-01-11
@berserker Heliode and everyone else with problems like this
Can you please try the following:
Copy the files you find here [http://triggerit.tr.funpic.de/debian/initng/initfiles/system/](http://triggerit.tr.funpic.de/debian/initng/initfiles/system/) to /etc/initng/system and run &#8220;ng-update a system/udev system&#8221; to add udev.i to the runlevels. Reboot and hope the best ;)
I need to know of the problem persists. I never had problems and so I need your feedback. It seems as if we are too fast for udev.

@DigitalAxis: I need more information. Please open a bug in [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net)
Try to boot with "init=/sbin/initng --verbose" and see if you can see something usefull.

---

### Post by DigitalAxis on 2006-01-12
@Limulus
   No, it booted normally the second time.  I'm not sure what happened; I'll try to reproduce

@Trigger|Debian
   Will Do.

---

### Post by DigitalAxis on 2006-01-12
Ok, for some reason KDM is failing.

```
<...>
Jan 12 14:51:45 localhost daemon/kdm:
Jan 12 14:51:45 localhost daemon/kdm:
Jan 12 14:51:45 localhost daemon/kdm:  ** "initng_simple_launcher.c", simple_exec_fork()  line:191:
Jan 12 14:51:45 localhost daemon/kdm:  14:51:45 -- FAIL:^IEEEEEEEEEEEEEEEEEEERRRRRRRRRRRRRRRRRRRRRRRRRRROOOOOOOOOOOOOOOOOOOOOOOOOORRRRRRRRRRRRRRR!!!!!!!!!
Jan 12 14:51:45 localhost daemon/kdm:
Jan 12 14:51:45 localhost daemon/kdm:
Jan 12 14:51:45 localhost daemon/kdm:  ** "initng_simple_launcher.c", simple_exec
Jan 12 14:51:45 localhost InitNG: Service daemon/kdm has been stopped.
<...>
```
(Somehow X isn't being started?)

Anyway, the endless loop turned out to be daemon/sendmail as started by daemon/fetchmail, continually waiting for the internet (initng_netprobe.c) to come up but since my laptop's not online, no dice.

There's still an odd problem with "initng_common.c line 412. initng_common_mark_service: a state hook did not like this change."

I've appended a file with all of the various weirdness I found in /var/log/messages, though I'm not sure how much my selections will help anyone.

---

### Post by berserker on 2006-01-12
[QUOTE=DigitalAxis]Ok, for some reason KDM is failing.[/QUOTE]

Same here.  I have to manually start KDM.  The fsck.ext2 error is gone but it fails at KDM start.

---

### Post by Trigger|Debian on 2006-01-13
The path to kdm seems to be wrong (it should be /usr/bin/kdm). Did you cahnge this and it fails? If yes that's a real problem. If no only Initng's feedback is bad ;)

---

### Post by berserker on 2006-01-13
[QUOTE=Trigger|Debian]The path to kdm seems to be wrong (it should be /usr/bin/kdm). Did you cahnge this and it fails? If yes that's a real problem. If no only Initng's feedback is bad ;)[/QUOTE]

Works like a charm now.  Thanks!

---

### Post by foxy123 on 2006-01-13
I was trying to set up InitNG on my desktop yesterday. After several reboots it started sort of working, though the computer boots longer with InitNG then with default conf.

After few seconds the screen turns blank with only blinking underscore in the upper left corner. Then it prints something like (I am reproducing in from my menory):
```
computer's name
login
[4 ; 2R
```
and then I have gdm. However if I shut down the computer, it hangs, so I have to push reset button.

I wonder what would be the best way to debug it. If it is not easy, I will just leave it....

---

### Post by souled on 2006-01-13
[QUOTE=foxy123]I was trying to set up InitNG on my desktop yesterday. After several reboots it started sort of working, though the computer boots longer with InitNG then with default conf.

After few seconds the screen turns blank with only blinking underscore in the upper left corner. Then it prints something like (I am reproducing in from my menory):
```
computer's name
login
[4 ; 2R
```
and then I have gdm. However if I shut down the computer, it hangs, so I have to push reset button.

I wonder what would be the best way to debug it. If it is not easy, I will just leave it....[/QUOTE]

This happens to me when I try to boot. I haven't tried restarting yet...

---

### Post by Trigger|Debian on 2006-01-13
One more time my plea: **Please file bugs like the above (and any other) in bugzilla on [http://bugzilla-initng.thinktux.net](http://bugzilla-initng.thinktux.net) if you want to see them fixed!**
AFAIK I'm the only one from the Initng team reading this thread and I can neither reproduce nor fix ever bug :(
If you open a bug much more people will have a look at this.

---

### Post by foxy123 on 2006-01-13
[QUOTE=Trigger|Debian]One more time my plea: **Please file bugs like the above (and any other) in bugzilla on [http://bugzilla-initng.thinktux.net](http://bugzilla-initng.thinktux.net) if you want to see them fixed!**
AFAIK I'm the only one from the Initng team reading this thread and I can neither reproduce nor fix ever bug :(
If you open a bug much more people will have a look at this.[/QUOTE]
the problem is that it is very difficult describe this bug for the bugzilla. Do you think that the description in my above post is clear enough to file it as a bug?

---

### Post by Trigger|Debian on 2006-01-13
I think it is the only chance we have - otherwise this will be never fixed :(
Maybe someone else knows more informations and can add them.

---

### Post by sitedesign on 2006-01-13
I tried to use this howto but found that my atheros wifi card (ath0) would not work.

NOW FIXED!

So I then found that after using [this howto]("http://www.ubuntuforums.org/showthread.php?t=105437") to use the latest madwifi drivers for the atheros wifi card all is now working. (pay attention to post number 7 as there is a typo in the instructions at the top of the post)

I also had to modify /etc/network/interfaces
look for the following lines and put hash marks at the front as shown.
#mapping hotplug
#	script grep
#	map eth0


So if you have a wifi card listed as ath0 then this should help. Any problems then let me know, I may have missed some steps out.

---

### Post by Trigger|Debian on 2006-01-14
I'll make a release for 0.5.2 within the next time.
If someone knows scripts which need to be tweaked he should yell know and tell me what to change. Kdm is fixed.

EDIT: Ok, speedstep should work now...

---

### Post by Jingo on 2006-01-15
Will you compile it with splash support?

---

### Post by Trigger|Debian on 2006-01-15
Ok, 0.5.2 is out.
I want everybody to read this:[http://triggerit.tr.funpic.de/blog/?p=36](http://triggerit.tr.funpic.de/blog/?p=36) and please execute /etc/initng/count_me.sh.
I've built the package with usplash support - for I have no Ubuntu I don't know if it works. Tell it to me!

---

### Post by reet on 2006-01-15
Thanks for the update.

By simply upgrading my current package, speedstep still returns "FAIL_STARTING".

AMD Athlon64 3000+
Asrock 939DUAL-SATA2 motherboard
Linux 2.6.12-10-k7 kernel

---

### Post by Trigger|Debian on 2006-01-15
Uhm, can anyone point me to the problem with system/speedstep? I don't see why it fails. I thought it were not loaded modules, but now all modules should be loaded.

And if anyone tried to get usplash running: tell me. Maybe you need to add system/usplash to system.runlevel - I don't know.

---

### Post by eyebrowman92 on 2006-01-15
this works like a charm! i love it! i would like a splash screen though..

---

### Post by Limulus on 2006-01-16
[QUOTE=Trigger|Debian]Ok, 0.5.2 is out.
I want everybody to read this:[http://triggerit.tr.funpic.de/blog/?p=36](http://triggerit.tr.funpic.de/blog/?p=36) and please execute /etc/initng/count_me.sh.
I've built the package with usplash support - for I have no Ubuntu I don't know if it works. Tell it to me![/QUOTE]
0.5.2 doesn't work for me :(

When I boot with InitNG it gets a few seconds into the colorful display of text that scrolls by and then it all disappears and then the generic Terminal login appears but some of the characters at the end are replaced by "[4;4R"  Pressing enter a few times gets me to a normal login prompt and then I can login and then reboot out of that.

Reinstalling the package makes no difference.

The entry I use from /boot/grub/menu.lst
```

title		Ubuntu, kernel 2.6.12-10-686 (InitNG)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet init=/sbin/initng reboot=h
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

```

When I ran count_me.sh it said I was "user 768 counted" (that BTW was the second time I ran it; the first time I ran it, I used Nautilus and clicked on the file, but it disappeared so fast that I rant it a second time from Terminal to make sure it worked) in case you want to look at my specs.

Hope this works again for me soon.  As I recall, I had problems with some of the 0.4 series (because I use a laptop?)

---

### Post by foxy123 on 2006-01-16
[QUOTE=Limulus]0.5.2 doesn't work for me :(

When I boot with InitNG it gets a few seconds into the colorful display of text that scrolls by and then it all disappears and then the generic Terminal login appears but some of the characters at the end are replaced by "[4;4R"  Pressing enter a few times gets me to a normal login prompt and then I can login and then reboot out of that.

Reinstalling the package makes no difference.

The entry I use from /boot/grub/menu.lst
```

title		Ubuntu, kernel 2.6.12-10-686 (InitNG)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet init=/sbin/initng reboot=h
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

```

When I ran count_me.sh it said I was "user 768 counted" (that BTW was the second time I ran it; the first time I ran it, I used Nautilus and clicked on the file, but it disappeared so fast that I rant it a second time from Terminal to make sure it worked) in case you want to look at my specs.

Hope this works again for me soon.  As I recall, I had problems with some of the 0.4 series (because I use a laptop?)[/QUOTE]
I've got the same problem. As I understand InitNG changes a screen during the boot from tty1 to tty6 and as a result a number of services do not start (anacron on my desktop and keymaps on laptop). Although I do not know why.

I filed a bug a couple of days ago here: [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=407](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=407). I guess you may vote for it to show that more than one person is affected by this bug...

---

### Post by foxy123 on 2006-01-16
speedsteps still does not work for me. The scrip I have installed with 0.5.2 is:

```
service system/speedstep {
	need = system/bootmisc system/modules/cpufreq-ondemand system/modules/cpufreq_userspace system/modules/cpufreq_stats system/modules/cpufreq_powersave system/modules/cpufreq_conservative system/modules/speedstep_centrino;
	use = system/static-modules system/coldplug;
	script start = {
		/bin/cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor >/tmp/origgovanor
		echo ondemand >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	};
	script stop = {
		/bin/cat /tmp/origgovanor >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	};
}

```

The script which works for me is:
```
 service system/speedstep {
        need = system/initial system/modules system/mountroot;
        use = system/static-modules system/coldplug;
        script start = {
                /sbin/modprobe cpufreq-ondemand &> /dev/null
                /sbin/modprobe cpufreq_userspace
                /sbin/modprobe cpufreq_stats
                /sbin/modprobe cpufreq_powersave
                /sbin/modprobe cpufreq_conservative
                /sbin/modprobe acpi_cpufreq
                /bin/cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor > /tmp/origgovanor
                echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
                exit 0
        };

        script stop = {
                echo `/bin/cat /tmp/origgovanor` > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
                exit 0
        }
}
```

---

### Post by reet on 2006-01-16
Limulus, foxy123, it sounds like you don't have gdm or whatever display manager you use starting. Try:

sudo ng-update add daemon/gdm

---

### Post by foxy123 on 2006-01-16
[QUOTE=reet]Limulus, foxy123, it sounds like you don't have gdm or whatever display manager you use starting. Try:

sudo ng-update add daemon/gdm[/QUOTE]
no, I've got gdm started after showing the command prompt, though I had to add it manually. What I do not understand is why it chages the screen to tty6 and how it causes some services not to start properly?

---

### Post by Jingo on 2006-01-16
I have had severel problems getting this 0.5.2 running!
I first uninstalled my 0.4.8 version, which was great.

I have troubles with vixie-cron saying status "FAIL_STARTING". It complains over the pid_file at startup. Cron is started alright and the pid-file is right!? InitNg just don't think so.

Same goes for NetworkManager. I had to comment out the "pid_file" argument to let InitNG see it was loaded, and not break the dependancy chain.

Also on shutdown/reboot I get a coredump. How do I troubleshoot the coredump? I don't know which process gives the dump!?

---

### Post by Jingo on 2006-01-16
I have had severel problems getting this 0.5.2 running!
I first uninstalled my 0.4.8 version, which was great.

I have troubles with vixie-cron saying status "FAIL_STARTING". It complains over the pid_file at startup. Cron is started alright and the pid-file is right!? InitNg just don't think so.

Same goes for NetworkManager. I had to comment out the "pid_file" argument to let InitNG see it was loaded, and not break the dependancy chain.

Also on shutdown/reboot I get a coredump. How do I troubleshoot the coredump? I don't know which process gives the dump!?

---

### Post by Limulus on 2006-01-16
[QUOTE=reet]Limulus, foxy123, it sounds like you don't have gdm or whatever display manager you use starting. Try: sudo ng-update add daemon/gdm[/QUOTE]

While it added fine (Success: added "daemon/gdm" to runlevel "default"), I got the same result as foxy123 (namely, the same result as before; it didn't work).

---

### Post by reet on 2006-01-16
Limulus, Foxy123, am I to understand that gdm does not start and that you have to log in at the command prompt and start it manually? Or does it work, but you are looking at this peculiar "[4;4R" login screen for the entire boot process. If the latter is true, remove usplash and you should be able to observe the lovely boot process once again:

sudo ng-update delete system/usplash

---

### Post by Limulus on 2006-01-17
[QUOTE=reet]Limulus, Foxy123, am I to understand that gdm does not start and that you have to log in at the command prompt and start it manually? Or does it work, but you are looking at this peculiar "[4;4R" login screen for the entire boot process. If the latter is true, remove usplash and you should be able to observe the lovely boot process once again: sudo ng-update delete system/usplash[/QUOTE]
Hey cool, it worked! =D

BTW, I tested it and I need both for Ubuntu to start properly:

```
sudo ng-update add daemon/gdm
sudo ng-update delete system/usplash
```
(if I just delete usplash, it stops at 100%)

Speaking of usplash though, why is causing trouble when I don't have "splash" in the kernel line?

---

### Post by Limulus on 2006-01-17
[QUOTE=Trigger|Debian]Ok, 0.5.2 is out.
I want everybody to read this:[http://triggerit.tr.funpic.de/blog/?p=36](http://triggerit.tr.funpic.de/blog/?p=36) and please execute /etc/initng/count_me.sh.
I've built the package with usplash support - for I have no Ubuntu I don't know if it works. Tell it to me![/QUOTE]
OK, now that I have InitNG working, I can answer this question! :)

I put "splash" back in the kernel line and no, it doesn't seem to work properly ;)

Usplash starts fine and the progress bar moves a tiny bit, but there's no [scrolling text](http://root.chrizel.com/misc/usplash.png) as there should be and it quits back to InitNG's colorful text at 8 or 9%.  That was my experience anyway.

---

### Post by Jingo on 2006-01-17
I just uninstalled my 0.4.8 which worked great, and installed 0.5.2. Problems!

vixie-cron has a wierd behavior. Its status is "FAIL_STARTING" but is actually started. On startup is says something like "wrong pid_file. Pid of non-exsistent process", but when the system came up, crond is running and the pid_file has the right number!!???

I use NetworkManager. I had to comment out he pid_file argument in the .i file to have it start ?
If the .i file doesn't have a pid_file arg. How does initng shutdown NetworkManager ?
Anyone using NetworkManager?

And I have a coredump everytime I shutdown/reboot.
How do I investigate the coredump? I don't know which program causes this, but I suspect the dhcp started by NetworkManager.


Ups... just saw that my previous post did get through. I thought I last connection to the forum yesterday!

---

### Post by reet on 2006-01-17
[QUOTE=Limulus]BTW, I tested it and I need both for Ubuntu to start properly:

```
sudo ng-update add daemon/gdm
sudo ng-update delete system/usplash
```
(if I just delete usplash, it stops at 100%)[/QUOTE]
Of course, the boot process is complete but there is nothing to login with. At this point, if you hit alt+ctrl+f2 you would see a login screen and be able to work just fine.

---

### Post by Nevermore on 2006-01-17
my old desktop would really need a speedup in the boot process, so i tried that .deb package..
got the last release, followed the guide..
PANG:
seg fault..
says can't call the daemon service..
what to do?

---

### Post by jon_z on 2006-01-17
Radeon 9600XT, need fglrx drivers loaded, init-ng doesn't do it by default, any ideas?

*SOLVED*

Add  fglrx  to a blank line in /etc/modules
UPGRADE to the new version of initng!! then execute /etc/initng/count_me.sh

---

### Post by Trigger|Debian on 2006-01-17
[QUOTE=Nevermore]my old desktop would really need a speedup in the boot process, so i tried that .deb package..
got the last release, followed the guide..
PANG:
seg fault..
says can't call the daemon service..
what to do?[/QUOTE]
Don't follow the guide? It is horrible old and outdated! 99% of the changes are in the package. The syntax of scripts has changed and they won't work anymore. MAybe this is the reason for the segfault - the parser is a little bit bitchy concerning wrong scripts ;)
Can't anyone change it? I contacted the author - he told me he doesn't use Ubuntu anymore (at least ATM). Maybe everybody should write him a PM with the beg for an update. I'm willing to help...

---

### Post by Nevermore on 2006-01-18
i installed initng on another computer and it started no problem, and pretty fast (only the 4R 4] screen was there for a while) but i encountered those problems:
the net connection doesn't work, i have no net interface...
the shutdown doesn't work...it starts the shutdown and after a while hangs there, not turning off the computer, nor rebooting...
reboot doesn't work as well..
nice speed but i suppose the coldplug couldn't get the net interface...
im back to usual for now, hoping it will be working soon!
started in around 10 sec!!!

---

### Post by Limulus on 2006-01-18
[QUOTE=Trigger|Debian]Don't follow the guide? It is horrible old and outdated! 99% of the changes are in the package. The syntax of scripts has changed and they won't work anymore. MAybe this is the reason for the segfault - the parser is a little bit bitchy concerning wrong scripts ;)
Can't anyone change it? I contacted the author - he told me he doesn't use Ubuntu anymore (at least ATM). Maybe everybody should write him a PM with the beg for an update. I'm willing to help...[/QUOTE]

Only the author of the post can change the posts they've made...

Why don't you start a new thread?

Leave a note at the end of this one saying that its time to move on ;)

Plus if you start the new thread, you can edit the instructions in the top post as needed... And if there are no new posts to this thread, it will decrease in search ranking, etc. while the new one will increase. Also, maybe get the author of the first post in this thread to link to the new thread...

---

### Post by foxy123 on 2006-01-18
[QUOTE=Nevermore]i installed initng on another computer and it started no problem, and pretty fast (only the 4R 4] screen was there for a while) but i encountered those problems:
the net connection doesn't work, i have no net interface...
the shutdown doesn't work...it starts the shutdown and after a while hangs there, not turning off the computer, nor rebooting...
reboot doesn't work as well..
nice speed but i suppose the coldplug couldn't get the net interface...
im back to usual for now, hoping it will be working soon!
started in around 10 sec!!![/QUOTE]

for 4R 4 and shutdown problem do
```
sudo ng-update delete system/usplash
```

try to boot after that. It may solve your other problem. If not, let us know.

---

### Post by shade11 on 2006-01-20
Interesting guide. But can someone tell me how to startup GDM automatically?

---

### Post by Rob2687 on 2006-01-20
It should start automatically if you followed the guide properly. Initng is very buggy so yeah...

---

### Post by shade11 on 2006-01-20
Yes, well i followed instructions except for 7, because it sait it was optional. I am goint to try again today with 7. If i follow each one it will start GDM right?

---

### Post by Rob2687 on 2006-01-20
Yeah, make sure you only run one of the two commands in step 5.

Anywho...

Has anyone gotten wpasupplicant to start at boot?
I did the sudo ng-update add daemon/wpasupplicant default, but it gives an error which goes by way to fast to see what it is during boot time.

Something about needing daemon/wpasupplicant and daemon/wpacli

---

### Post by souled on 2006-01-20
You can view the boot log. In the terminal type "sudo ngc -L". You can find your error message in there.

---

### Post by shade11 on 2006-01-23
Well I did all of the 7 instructions. And there are still problems:
No sound, even after doing [this]("http://ubuntuforums.org/showthread.php?t=77078").
I want DHCP to succeed 100% of the Time.
I can't get ACPI to work even after following the instructions that were shown. I have a laptop so I really need it.

Please Help :(

---

### Post by Jingo on 2006-01-24
This 0.5.2 seems very buggy to me. I get very random errrors.
0.4.8 was rather stable, I am downgrading again.

Hope the next relases will be less buggy.
Will there be a 0.5.3 dep ? Or are we waiting for more bugfixes?

---

### Post by shade11 on 2006-01-24
ARRGH!

This ticks me off. HOW CAN I GET SOUND!

---

### Post by Trigger|Debian on 2006-01-25
[QUOTE=Jingo]Hope the next relases will be less buggy.
Will there be a 0.5.3 dep ? Or are we waiting for more bugfixes?[/QUOTE]
We will wait for a new release.
I'm very busy at the moment and not very mutch has changed between 0.5.2 and 0.5.3.
Please report your bugs in bugzilla ([http://bugzilla.initng.thinktux.net)](http://bugzilla.initng.thinktux.net)).
I neither have the bugs you report nor have I the time to fix them all.
You have the choice: if you report them they will be fixed, otherwise they won't be fixed. So easy is life.

Thx.

---

### Post by shade11 on 2006-01-25
Haha I am happy now. I got initNG to work thanks to my friend Benplaut. Sound, DHCP 100% successful, and ACPI works now. My boot time was reduced down to around 13 seconds. I had originally disabled some other processes with BUM and sysc-rc-conf.

---

### Post by benplaut on 2006-01-26
[QUOTE=shade11]Haha I am happy now. I got initNG to work thanks to my friend Benplaut. Sound, DHCP 100% successful, and ACPI works now. My boot time was reduced down to around 13 seconds. I had originally disabled some other processes with BUM and sysc-rc-conf.[/QUOTE]

no problem... if you need something, just 'call' ;)

---

### Post by Trigger|Debian on 2006-01-26
@shade11: Did you made changes in scripts (which were buggy) or did you make some changes on your system?
If you needed to change some scripts you should tell me :)

---

### Post by shade11 on 2006-01-26
Actually, Ben made a few changes to the intNG scripts and gave me this program he made that helps with DHCP.

---

### Post by Trigger|Debian on 2006-01-26
Oh, guys! 
You want me to deliver me a working package but you don't tell me what needs to be changed. You see the problem?

---

### Post by Jingo on 2006-01-27
[QUOTE=Trigger|Debian]
I neither have the bugs you report nor have I the time to fix them all.
[/QUOTE]

Are you or anyone using NetworkManager ?
I have filed a bugreport. Pid_file problem is known, but is very rare (random I'd say). I bet the problem with wrong pid number is causing my problems.

Sometimes InitNG doesn't shutdown properly, last print is "static-modules [stopped]", so I guess it hangs on bootmisc, but again is only 1/10 of the shutdowns!? What should I write in the bugreport. I don't have much data/facts to report!

/Jingo

---

### Post by shade11 on 2006-02-06
Well I got most of it working but:

-Can anyone help me with sound? I got it working but it doesn't want to work with most programs. I know it has to do with initNg because I can normally boot and it will have sound work all the time.

-Is is possbile to make DHCP succeed 100% of the time even if increasing boot time? Ben just gave me a tool incase it fails but I need it to work without a tool.

Thanks in advance.

---

### Post by wmvdg123 on 2006-02-08
Hi, I'm a noob, first time with Linux. So I downloaded initng_0.4.8-1_i386.deb to my desktop and then opened a terminal and entered,

sudo dpkg -i initng_0.4.8-1_i386.deb

But all I got was "error processing initng_0.4.8-1_i386.deb (--install):
cannot access archive: No such file or directory"

Any ideas about what I'm doing wrong? Thanks,
Wayne

---

### Post by foxy123 on 2006-02-08
[QUOTE=wmvdg123]Hi, I'm a noob, first time with Linux. So I downloaded initng_0.4.8-1_i386.deb to my desktop and then opened a terminal and entered,

sudo dpkg -i initng_0.4.8-1_i386.deb

But all I got was "error processing initng_0.4.8-1_i386.deb (--install):
cannot access archive: No such file or directory"

Any ideas about what I'm doing wrong? Thanks,
Wayne[/QUOTE]
why are installing 0.4.8? I guess the newest is 0.5.2? anyway, make sure that you typed the name of the dep without any typo and the file is actualy in the dir from where you try to install it. type ls to make sure...

---

### Post by wmvdg123 on 2006-02-08
Thanks Foxy123, you were right, I moved it to the "home" folder and then it installed fine :-)
Wayne

---

### Post by shade11 on 2006-02-09
I had to re-install Ubuntu because of the bugs. But it works alot better now. I even used a better journaling system format instead of ext3. Anyway, now that I re-installed I am getting more problems. Pretty much DHCP.

I have Gtk-wifi as my default and only Wireless connection manager. 50% of the time DHCP fails. So how can i get it to 100%?

---

### Post by foxy123 on 2006-02-09
[QUOTE=shade11]I had to re-install Ubuntu because of the bugs. But it works alot better now. I even used a better journaling system format instead of ext3. Anyway, now that I re-installed I am getting more problems. Pretty much DHCP.

I have Gtk-wifi as my default and only Wireless connection manager. 50% of the time DHCP fails. So how can i get it to 100%?[/QUOTE]
where do you use your wireless? maybe you can use static ip address instead of dhcp...

---

### Post by shade11 on 2006-02-09
I go to many networks. So I go to diffrent networks all the time.

---

### Post by haleakala on 2006-02-10
[QUOTE=shade11]Haha I am happy now. I got initNG to work thanks to my friend Benplaut. Sound, DHCP 100% successful, and ACPI works now. My boot time was reduced down to around 13 seconds. I had originally disabled some other processes with BUM and sysc-rc-conf.[/QUOTE]

I've got an Inspiron 6000 on which I've installed the version 0.33 of InitNG, and I'd like to install a new version to see what is new.

Shade11, it would be very nice from you if you could explain us how did you manage to install your version of  InitNG on an Inspiron 6000, I mean to be as precise as possible concerning the change you made to the normal version of InitNG, so that it works great...

Thank in advance!

Haleakala

---

### Post by Skippy le Grand Gourou on 2006-02-10
Hi ! Nice job : 
before > boot ~1'25s (+25s for session), shutdown ~23s
after > boot ~50s (+25s), shutdown ~10s \\:D/ 

However, I too have a cpu scaling problem, and neither modprobe speedstep-centrino (of course...), neither acpi_cpufreq solved it. My cpu is an AMD Sempron 3200+ (that's why I said "of course"), and the weird thing is the following : when I type
> sudo modprobe acpi
booting without InitNg, the answer is :
> FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.12-10-k7/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
So that seems ok. But when I type it booting on InitNg, it says :
> FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.12-10-k7/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

Anybody has an idea ?

Thanx.

---

### Post by macewan on 2006-02-11
Damn, that was so fast I thought something was going wrong. No joke


Thanks for introducing InitNG

---

### Post by Skippy le Grand Gourou on 2006-02-11
Erf, my printer (Canon PIXMA iP1500,with bjcups) also disappears with InitNg... :-?

---

### Post by macewan on 2006-02-11
[quote=Skippy le Grand Gourou]Erf, my printer (Canon PIXMA iP1500,with bjcups) also disappears with InitNg... :-?[/quote]

which driver were you using?

---

### Post by Skippy le Grand Gourou on 2006-02-11
[quote=maceman]which driver were you using?[/quote][These ones](http://linux.cergynux.net/canon/).

---

### Post by shade11 on 2006-02-11
[QUOTE=haleakala]I've got an Inspiron 6000 on which I've installed the version 0.33 of InitNG, and I'd like to install a new version to see what is new.

Shade11, it would be very nice from you if you could explain us how did you manage to install your version of  InitNG on an Inspiron 6000, I mean to be as precise as possible concerning the change you made to the normal version of InitNG, so that it works great...

Thank in advance!

Haleakala[/QUOTE]

I just followed the instructions. Thats all. Then I did [this]("http://www.ubuntuforums.org/showpost.php?p=429313&postcount=4"). I gave my laptop over to benplaut who gave me sound, then used this shell script he made called simplewifi. But simplewifi is just a program to execute incase DHCP fails. But I want it automated.

I still need help with DHCP.

---

### Post by DigitalAxis on 2006-02-11
Ok, 0.5.2-1 works on my laptop now, both for startup and shutdown.  I have sound and ethernet and usplash (except for a short blip I don't understand entirely)

With Init: startup 125 seconds
With InitNG: startup 77 seconds (shutdown 20)

It's still a bit long for my taste, but 48 seconds off is nothing to sneeze at either...  I suspect I'm loading stuff I don't need.

---

### Post by macewan on 2006-02-12
[quote=Skippy le Grand Gourou][These ones]("http://linux.cergynux.net/canon/").[/quote]

thanks

---

### Post by yanns on 2006-02-17
I'm testing initng with the 0.5.2-1 version found on [http://alioth.debian.org/projects/pkg-initng/]("http://alioth.debian.org/projects/pkg-initng/").

After package installation, I added the following lines in /boot/grub/menu.lst
```
title           Ubuntu InitNG, kernel 2.6.12-10-686
root            (hd0,6) kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda7 ro quiet init=/sbin/initng
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

I changed the "laptop_mode" by "laptop-mode" in the laptop-mode.i file.

Everything is working great.

I only got one problem: NetworkManager does not work any more, whereas it is working correctly with a "standard" boot.

I checked that NetworkManagerDispatcher.i and NetworkManager.i can be found in /etc/initng/daemon.

Any help welcome...

Edit: solution found
```
sudo ng-update add NetworkManager
sudo ng-update add NetworkManagerDispatcher
```

---

### Post by haleakala on 2006-02-18
Hi,

I must say it: yanns, I really appreciate your post! I tried what you did, and Ubuntu boots very well and faster with InitNG on my laptop.

Haleakala

[QUOTE=yanns]I'm testing initng with the 0.5.2-1 version found on [http://alioth.debian.org/projects/pkg-initng/]("http://alioth.debian.org/projects/pkg-initng/").

After package installation, I added the following lines in /boot/grub/menu.lst
```
title           Ubuntu InitNG, kernel 2.6.12-10-686
root            (hd0,6) kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda7 ro quiet init=/sbin/initng
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

I changed the "laptop_mode" by "laptop-mode" in the laptop-mode.i file.

Everything is working great.

I only got one problem: NetworkManager does not work any more, whereas it is working correctly with a "standard" boot.

I checked that NetworkManagerDispatcher.i and NetworkManager.i can be found in /etc/initng/daemon.

Any help welcome...

Edit: solution found
```
sudo ng-update add NetworkManager
sudo ng-update add NetworkManagerDispatcher
```[/QUOTE]

---

### Post by dodgeman79 on 2006-02-19
having trouble getting Initng to run at all.  here are the error messages I'm getting at bootup.

```
** "initng_depend.c", service_state()  line:113:
01:15:17 --WARN:   service "daemon/dbus" needs service "daemon", that could not be found
Not the one SEGFAULTED!
Initng segfaulted, will wait 20 seconds for you to start a gdb, before execve (sbin/initng-segfault);
```

that is typed word for word, also no matter how long I wait the computer will not do anything.  have to hard reset and boot up normal.

---

### Post by Trigger|Debian on 2006-02-19
Hey boys and girsl,

there will be a new Initng release in a few days and we are bugsquashing right now - if you want to see your bugs fixed add them on [http://bugzilla.initng.thinktux.net](http://bugzilla.initng.thinktux.net)
If you don't do it they won't be fixed. Life's easy, huh?

Thx
Trigger

---

### Post by Skippy le Grand Gourou on 2006-02-19
Are there so many bugs to report that the server is overflowed or is just your link dead ? :-k

I'll try later... :mrgreen:

---

### Post by Trigger|Debian on 2006-02-19
The link works perfectly for me :)
Please try again.

---

### Post by Jingo on 2006-02-22
0.5.4 out!!  ;-)

Can't wait for .deb! ;-) Hope some of my bugs where solved, although they are still "NEW" in bugzilla!

Keep up the great work.. This thing is just as importent for linux succes as Xgl...

---

### Post by Trigger|Debian on 2006-02-22
If you need it now you can get it from svn://svn.debian.org/pkg-initng/ ;)
I hope I will release the package tomorrow. Need to do some testing before.

---

### Post by sailor420 on 2006-02-23
Out of curiousity, any chance we could get this moved to the wiki? The install has changed a whole lot since the original post was last updated, but we can't update it because the OP has disappeared. With a wiki entry, it could be changed as new releases come out, regardless of whether or not the original author is still around. We could keep this thread here for discussion of problems, but I think it'd be much easier if the actual install instructions were in the wiki.

---

### Post by foxy123 on 2006-02-23
[QUOTE=sailor420]Out of curiousity, any chance we could get this moved to the wiki? The install has changed a whole lot since the original post was last updated, but we can't update it because the OP has disappeared. With a wiki entry, it could be changed as new releases come out, regardless of whether or not the original author is still around. We could keep this thread here for discussion of problems, but I think it'd be much easier if the actual install instructions were in the wiki.[/QUOTE]
i will ry to do it, though for Dapper as I have already switched to it.

---

### Post by Trigger|Debian on 2006-02-23
Yeah, a wiki entry sound very good.
And afterwards we close this thread and start a new one for problems.

BTW: [http://triggerit.tr.funpic.de/blog/?p=38](http://triggerit.tr.funpic.de/blog/?p=38)
The package is ready :)

---

### Post by benplaut on 2006-02-23
i'm trying to use this is dapper, running into a bit of trouble. When it's loading hal, i get a bunch of errors about "missing x or y relative value", and about relative values, too.

Anyone know why? using a fully updated system and the tweaks in the first post

---

### Post by Jingo on 2006-02-24
0.5.4 works for me. Until now at least.

Had to make small change to NetworkManager! Yes trigger, I have filed a bug-report.
Had to add "daemon/hald" to the "need" of NetworkManager.i else it would coredump on shutdown!

---

### Post by yanns on 2006-02-24
I tried 0.5.4, but nvidia module cannot be loaded.

I'll check when I have time.

---

### Post by Trigger|Debian on 2006-02-24
@benplaut: Forget the first post - it is completely outdated. Which version do you use? 0.5.4 can't work with the scripts rom the first post...
@ Jingo: Good. Will have a look at this.
@yanns: Is this only a problem of 0.5.4? Did it work before?

---

### Post by yanns on 2006-02-24
[QUOTE=Trigger|Debian]
@yanns: Is this only a problem of 0.5.4? Did it work before?[/QUOTE]
Yeah, it worked

---

### Post by Trigger|Debian on 2006-02-24
Hm, ok.
Once the problem was the not started lrm-manager. But if you look at the last lines of system/modules.i you see it is started. AFAIK nothing has been changed there since the last release.
Please try to find out what's the problem :-)

---

### Post by yanns on 2006-02-24
OK I found my problem: I installed the new version too quickly, and did not re-add gdm... :D

I thougt the problem come from nvidia cause I got this message:
"FATAL: could not open /lib/modules/2.6.12-10-686/volatile/nvidia.ko: No such file or directory"
whereas the file does exist.

---

### Post by Trigger|Debian on 2006-02-24
@yanns: Strange - normally it shouldn't be removed. But good, if it works now :-)

@all: If you have problems with NetworManager please add "need = daemon/hald" - seems as if the missing dependency on hald can cause problems.
See [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=476](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=476)

---

### Post by Jefim on 2006-02-24
Jesus! This works perfectly with my  system! The boot time was 65 seconds (I measured it), and now it is ONLY 30 sec! It's a miracle I say :) I'm really shocked. Thanks for the guide - finally ubuntu boots faster than windows (and in linux I have much more to boot!).

---

### Post by Limulus on 2006-02-25
[QUOTE=Trigger|Debian][http://triggerit.tr.funpic.de/blog/?p=38](http://triggerit.tr.funpic.de/blog/?p=38)
The package is ready :)[/QUOTE]

I just upgraded from 0.5.2 to 0.5.4; here are my notes:

I was running 0.5.2, downloaded 0.5.4 and installed it; when I went to reboot, my computer wouldn't shutdown or reboot (I had to manually power it down). [edit: Heh.  I didn't read the link closely enough: "we had an internel API change - this means the first reboot after updating a *running* Initng will be b0rked." I guess that explains it ;] I would thus recommend (for this release anyway) that if you're upgrading that you boot via a normal Ubuntu boot and upgrade from there.

I booted via a normal Ubuntu boot, uninstalled InitNG and then reinstalled it.  This deleted any changes I had made previously.  I then tried using it with splash and splash works now! :)  There was just one minor glitch where it switched back to the InitNG text for a second and then came back to the Ubuntu splash screen.  The [normal text](http://root.chrizel.com/misc/usplash.png) under the logo isn't working, but the progress bar works :)

At 100% it failed though; GDM did not start (the same problem as in 0.5.2).  I ran ```
sudo ng-update add daemon/gdm
``` and rebooted and then it started just fine :)  Printers didn't work in Ubuntu, but that's the same as in 0.5.2 too; just run ```
sudo ng-update add daemon/cupsd
``` and reboot.

There is one final problem that I don't have the answer to just yet; sound doesn't work ^_^;  I vaguely recall having this problem before with a previous version; I'll see if I can find the answer... or if someone posts it first I'd appreciate it :)

---

### Post by Limulus on 2006-02-25
[QUOTE=Limulus]There is one final problem that I don't have the answer to just yet; sound doesn't work ^_^;[/QUOTE]
I figured it out; I ran
```
sudo ng-update add daemon/esound
```
and rebooted and had sound :)

Edit: the above only works if the Multimedia Systems Selector is set to ESD before the computer reboots... how odd (I changed it ALSA and rebooted and there was no sound again...)

Edit2: I just booted and the audio didn't start; I wonder if its related to [bug 436](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=436)...

Edit 3: I filed this as [bug 489](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=489)

---

### Post by Limulus on 2006-02-25
On the advice of a more knowledgeable Linux user who asked "Can you start alsa manually after you have booted?" suggested I try:
```
/etc/init.d/alsa-utils start
```
the result was:
```
 * Setting up ALSA...
 * /etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'.
                                                                         [ ok ]
```
And no sound ;)

Edit: Same person infers that it "Sounds like it skipped the part where in modprobes your soundcard driver."

---

### Post by Jefim on 2006-02-26
I want Apache2 & MySQL servers to start, but initng can't (I don't know why). I added them to default (with ng-update), but there no change... How do I solve this?

---

### Post by Limulus on 2006-02-26
[QUOTE=Trigger|Debian]Yeah, a wiki entry sound very good.[/QUOTE]
Here you go: [https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG) :)
Edit away ;)

---

### Post by foxy123 on 2006-02-28
has anyone tried it on Dapper? I have a trouble with debian-ifupdown:
```
Feb 28 21:24:49 localhost system/ifupdown-debian: bash_helper[system/ifupdown-debian]: line 72: /etc/network/run/ifstate: No such file or directory
Feb 28 21:24:49 localhost system/ifupdown-debian: failed.
Feb 28 21:24:49 localhost system/ifupdown-debian: ifupdown-debian]: Error: Failure initializing /etc/network/run/ifstate
```

---

### Post by sailor420 on 2006-02-28
[QUOTE=Limulus]On the advice of a more knowledgeable Linux user who asked "Can you start alsa manually after you have booted?" suggested I try:
```
/etc/init.d/alsa-utils start
```
the result was:
```
 * Setting up ALSA...
 * /etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'.
                                                                         [ ok ]
```
And no sound ;)

Edit: Same person infers that it "Sounds like it skipped the part where in modprobes your soundcard driver."[/QUOTE]

Have you found out anymore about this or how to fix it?

Also, how do I make eth0 start on boot? I'm having to go in and manually start it after a reboot...

---

### Post by Trigger|Debian on 2006-03-01
[QUOTE=foxy123]has anyone tried it on Dapper? I have a trouble with debian-ifupdown:
```
Feb 28 21:24:49 localhost system/ifupdown-debian: bash_helper[system/ifupdown-debian]: line 72: /etc/network/run/ifstate: No such file or directory
Feb 28 21:24:49 localhost system/ifupdown-debian: failed.
Feb 28 21:24:49 localhost system/ifupdown-debian: ifupdown-debian]: Error: Failure initializing /etc/network/run/ifstate
```[/QUOTE]
It has been reported here: [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=487](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=487)
To be honest I don't really have an Idea what is happening here. Seems as if something has changed in Dapper.
Please do me a favour and attach /etc/init.d/ifupdown-clean and /etc/init.d/ifupdown to this bugreport.

---

### Post by foxy123 on 2006-03-01
[QUOTE=Trigger|Debian]It has been reported here: [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=487](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=487)
To be honest I don't really have an Idea what is happening here. Seems as if something has changed in Dapper.
Please do me a favour and attach /etc/init.d/ifupdown-clean and /etc/init.d/ifupdown to this bugreport.[/QUOTE]
I've no /etc/init.d/ifupdown-clean and /etc/init.d/ifupdown:
```
~$ locate ifupdown
/etc/udev/rules.d/85-ifupdown.rules
/etc/initng/system/ifupdown-debian.i
/var/lib/dpkg/info/ifupdown.config
/var/lib/dpkg/info/ifupdown.list
/var/lib/dpkg/info/ifupdown.templates
/var/lib/dpkg/info/ifupdown.postinst
/var/lib/dpkg/info/ifupdown.preinst
/var/lib/dpkg/info/ifupdown.postrm
/var/lib/dpkg/info/ifupdown.conffiles
/var/lib/dpkg/info/ifupdown.md5sums
/var/cache/apt/archives/ifupdown_0.6.7ubuntu7_i386.deb
/usr/share/doc/ifupdown
/usr/share/doc/ifupdown/changelog.gz
/usr/share/doc/ifupdown/examples
/usr/share/doc/ifupdown/examples/pcmcia-compat.sh
/usr/share/doc/ifupdown/examples/bridge
/usr/share/doc/ifupdown/examples/generate-interfaces.pl.gz
/usr/share/doc/ifupdown/examples/check-mac-address.sh
/usr/share/doc/ifupdown/examples/network-interfaces.gz
/usr/share/doc/ifupdown/examples/get-mac-address.sh
/usr/share/doc/ifupdown/examples/ping-places.sh
/usr/share/doc/ifupdown/TODO
/usr/share/doc/ifupdown/copyright
/usr/share/doc/ifupdown/contrib
/usr/share/doc/ifupdown/contrib/ifstate-check
/usr/share/doc/ifupdown/contrib/ensureifup
/usr/share/doc/ifupdown/contrib/ifstate
/usr/share/doc/ifupdown/changelog.Debian.gz
/usr/share/ifupdown
/usr/share/ifupdown/upgrade-from-0.5.x.pl
/usr/share/ifupdown/upgrade-from-hotplug.pl
/usr/share/NetworkManager/dispatcher.d/01ifupdown

~$ locate ifupdown-clean
~$
```

---

### Post by Trigger|Debian on 2006-03-01
Oha, very interesting. Looks like a major change.
Please gimme /usr/share/doc/ifupdown/, /usr/share/ifupdown and /etc/udev/rules.d/85-ifupdown.rules

---

### Post by NoWhereMan on 2006-03-01
[QUOTE=DigitalAxis]Ok, 0.5.2-1 works on my laptop now, both for startup and shutdown.  I have sound and ethernet and **usplash**[/QUOTE]
How? :mrgreen: I want it, too, using 0.5.4 :)

---

### Post by foxy123 on 2006-03-01
[QUOTE=Trigger|Debian]Oha, very interesting. Looks like a major change.
Please gimme /usr/share/doc/ifupdown/, /usr/share/ifupdown and /etc/udev/rules.d/85-ifupdown.rules[/QUOTE]
I have attached etc/udev/rules.d/85-ifupdown.rules to the bug report. /usr/share/doc/ifupdown/, /usr/share/ifupdown are directories, so make your pick...

---

### Post by sailor420 on 2006-03-01
Has anyone been able to get sound working?

---

### Post by NoWhereMan on 2006-03-01
[QUOTE=sailor420]Has anyone been able to get sound working?[/QUOTE]
it's the first i try it and for me it works out of the box... did you try to update?

---

### Post by sailor420 on 2006-03-01
Yeah, I'm running a clean install of 0.5.4, but like Limulus, I can't get anything running...

---

### Post by Trigger|Debian on 2006-03-01
[QUOTE=foxy123]I have attached etc/udev/rules.d/85-ifupdown.rules to the bug report. /usr/share/doc/ifupdown/, /usr/share/ifupdown are directories, so make your pick...[/QUOTE]
Thx.
Gimme both directories in a tar.gz or something like this :) 
BTW: Try to remove ifupdown-debian.i from the runlevel and see what happens.

@all with soundproblems: See if you can add something to the closed bug 489. Loaded modules e.g....

---

### Post by Limulus on 2006-03-01
[QUOTE=Trigger|Debian]@all with soundproblems: See if you can add something to the closed bug 489. Loaded modules e.g....[/QUOTE]
How would we go about doing that? (e.g. what command line should I run or what file should I look in?  I'm not a linux expert O:)

Comment #2 in bug 489 says "Please compare which modules concerning sond are loaded when you booted with Initng and which are loaded when you booted with sysvinit." so I take it I would have to run/view whatever twice: once using a normal Ubuntu login and another InitNG (0.5.4) login... Should I also run a third; one for InitNG 0.5.2 too?

---

### Post by Limulus on 2006-03-02
[QUOTE=Trigger|Debian]Gimme both directories in a tar.gz or something like this :) [/QUOTE]
FYI, you can grap a copy of them from the Dapper ifupdown DEB package on Ubuntu's website: [http://packages.ubuntu.com/dapper/base/ifupdown](http://packages.ubuntu.com/dapper/base/ifupdown)

---

### Post by Trigger|Debian on 2006-03-02
[QUOTE=Limulus]Comment #2 in bug 489 says "Please compare which modules concerning sond are loaded when you booted with Initng and which are loaded when you booted with sysvinit." so I take it I would have to run/view whatever twice: once using a normal Ubuntu login and another InitNG (0.5.4) login... Should I also run a third; one for InitNG 0.5.2 too?[/QUOTE]
Hm, yeah, if you want gimme all the three. "lsmod" is your friend.

Getting the Deba sounds good ;)
Will do this when i have some time.

---

### Post by foxy123 on 2006-03-02
[QUOTE=Trigger|Debian]Thx.
Gimme both directories in a tar.gz or something like this :) 
BTW: Try to remove ifupdown-debian.i from the runlevel and see what happens.

@all with soundproblems: See if you can add something to the closed bug 489. Loaded modules e.g....[/QUOTE]
here you are... attached to the bug report...

---

### Post by Limulus on 2006-03-03
[QUOTE=Trigger|Debian]Hm, yeah, if you want gimme all the three. "lsmod" is your friend.[/QUOTE]

<grin> Thanks; here you go.  BTW, when I reinstalled 0.5.4, sound worked the first time it booted, but didn't the second time, so here are the results of running lsmod from *four* boots:

```

Normal Ubuntu Login (splash line in GRUB)

$ lsmod
Module                  Size  Used by
binfmt_misc            11496  1
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
orinoco_cs              8872  1
orinoco                39820  1 orinoco_cs
hermes                  7264  2 orinoco_cs,orinoco
pcmcia                 26568  5 orinoco_cs
ipt_limit               2208  8
iptable_mangle          2720  0
ipt_LOG                 6976  8
ipt_MASQUERADE          3296  0
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0
ipt_REJECT              5376  1
ip_conntrack_irc       71696  0
ip_conntrack_ftp       72688  0
ipt_state               1792  6
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
usblp                  12640  0
video                  15748  0
toshiba_acpi           10716  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  12
af_packet              21768  2
rtc                    12344  0
pcspkr                  3396  0
yenta_socket           25292  3
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
i2c_ali15x3             7428  0
snd_ali5451            24740  0
snd_ac97_codec         83932  1 snd_ali5451
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  1 snd_pcm
pci_hotplug            27508  0
ali_agp                 6976  0
agpgart                34792  1 ali_agp
dm_mod                 57692  1
joydev                  9984  0
tsdev                   7776  0
snd_seq_dummy           3620  0
evdev                   9664  1
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
eeprom                  7312  0
lm90                   13476  0
i2c_sensor              3360  2 eeprom,lm90
i2c_ali1535             6948  0
i2c_core               21200  6 i2c_acpi_ec,i2c_ali15x3,eeprom,lm90,i2c_sensor,i2c_ali1535
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
ehci_hcd               34248  0
ohci_hcd               20644  0
usbcore               118044  5 usblp,usbhid,ehci_hcd,ohci_hcd
8139too                25504  0
8139cp                 19744  0
mii                     5696  2 8139too,8139cp
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  4
ide_generic             1376  0
alim15x3               12204  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   26896  969
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

```
```

InitNG 0.5.2 (no splash line in GRUB)

$ lsmod
Module                  Size  Used by
ipt_limit               2208  8
iptable_mangle          2720  0
ipt_LOG                 6976  8
ipt_MASQUERADE          3296  0
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0
ipt_REJECT              5376  1
ip_conntrack_irc       71696  0
ip_conntrack_ftp       72688  0
ipt_state               1792  6
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ipv6                  251232  6
af_packet              21768  2
yenta_socket           25292  3
rsrc_nonstatic         13376  1 yenta_socket
i2c_ali15x3             7428  0
snd_ali5451            24740  0
snd_ac97_codec         83932  1 snd_ali5451
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  1 snd_pcm
pci_hotplug            27508  0
ali_agp                 6976  0
rtc                    12344  0
agpgart                34792  1 ali_agp
pcspkr                  3396  0
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
video                  15748  0
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
toshiba_acpi           10716  0
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tc1100_wmi              6692  0
soundcore               9600  1 snd
joydev                  9984  0
evdev                   9664  1
tsdev                   7776  0
sony_acpi               5324  0
eeprom                  7312  0
lm90                   13476  0
pcc_acpi               11104  0
i2c_sensor              3360  2 eeprom,lm90
i2c_ali1535             6948  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  6 i2c_ali15x3,eeprom,lm90,i2c_sensor,i2c_ali1535,i2c_acpi_ec
psmouse                30116  0
mousedev               11616  1
button                  6480  0
battery                 9348  0
pcmcia                 26568  0
parport_pc             35236  0
lp                     12292  0
container               4384  0
ac                      4708  0
pcmcia_core            49348  3 yenta_socket,rsrc_nonstatic,pcmcia
parport                35912  2 parport_pc,lp
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
ehci_hcd               34248  0
ohci_hcd               20644  0
usbcore               118044  4 usbhid,ehci_hcd,ohci_hcd
8139too                25504  0
8139cp                 19744  0
mii                     5696  2 8139too,8139cp
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  4
ide_generic             1376  0
alim15x3               12204  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   26896  726
fbcon                  38496  0
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7992  0
cfbcopyarea             4608  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
softcursor              2272  1 vesafb
capability              4712  0
commoncap               6816  1 capability

```
```

InitNG 0.5.4 (no splash line in GRUB; sound working)

$ lsmod
Module                  Size  Used by
ipt_limit               2208  8
iptable_mangle          2720  0
ipt_LOG                 6976  8
ipt_MASQUERADE          3296  0
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0
ipt_REJECT              5376  1
ip_conntrack_irc       71696  0
ip_conntrack_ftp       72688  0
ipt_state               1792  6
ipv6                  251232  6
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
af_packet              21768  2
video                  15748  0
toshiba_acpi           10716  0
tc1100_wmi              6692  0
sony_acpi               5324  0
rtc                    12344  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
pcspkr                  3396  0
pcmcia                 26568  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
pcmcia_core            49348  1 pcmcia
snd_ali5451            24740  0
snd_ac97_codec         83932  1 snd_ali5451
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  1 snd_pcm
pci_hotplug            27508  0
ali_agp                 6976  0
agpgart                34792  1 ali_agp
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  2 snd_pcm,snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
eeprom                  7312  0
lm90                   13476  0
i2c_sensor              3360  2 eeprom,lm90
i2c_ali1535             6948  0
i2c_core               21200  5 i2c_acpi_ec,eeprom,lm90,i2c_sensor,i2c_ali1535
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  2 parport_pc,lp
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
ehci_hcd               34248  0
ohci_hcd               20644  0
usbcore               118044  4 usbhid,ehci_hcd,ohci_hcd
8139too                25504  0
8139cp                 19744  0
mii                     5696  2 8139too,8139cp
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  4
ide_generic             1376  0
alim15x3               12204  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   26896  726
fbcon                  38496  0
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7992  0
cfbcopyarea             4608  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
softcursor              2272  1 vesafb
capability              4712  0
commoncap               6816  1 capability

```
```

InitNG 0.5.4 (no splash line in GRUB; sound not working)

$ lsmod
Module                  Size  Used by
ipt_limit               2208  8
iptable_mangle          2720  0
ipt_LOG                 6976  8
ipt_MASQUERADE          3296  0
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0
ipt_REJECT              5376  1
ip_conntrack_irc       71696  0
ip_conntrack_ftp       72688  0
ipt_state               1792  6
ipv6                  251232  6
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
af_packet              21768  2
rtc                    12344  0
pcspkr                  3396  0
video                  15748  0
toshiba_acpi           10716  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
pcmcia                 26568  0
pcmcia_core            49348  1 pcmcia
pci_hotplug            27508  0
ali_agp                 6976  0
agpgart                34792  1 ali_agp
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24164  1 snd_seq
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  5 snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9600  1 snd
eeprom                  7312  0
lm90                   13476  1
i2c_sensor              3360  2 eeprom,lm90
i2c_ali1535             6948  0
i2c_core               21200  5 i2c_acpi_ec,eeprom,lm90,i2c_sensor,i2c_ali1535
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  2 parport_pc,lp
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
ehci_hcd               34248  0
ohci_hcd               20644  0
usbcore               118044  4 usbhid,ehci_hcd,ohci_hcd
8139too                25504  0
8139cp                 19744  0
mii                     5696  2 8139too,8139cp
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  4
ide_generic             1376  0
alim15x3               12204  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   26896  692
fbcon                  38496  0
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7992  0
cfbcopyarea             4608  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
softcursor              2272  1 vesafb
capability              4712  0
commoncap               6816  1 capability

```

**Edit:** Ah!  I think I see what's going on now; compared to the 0.5.4 with sound, the one without it is missing:

```

snd_ali5451            24740  0
snd_ac97_codec         83932  1 snd_ali5451
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10600  1 snd_pcm

```

**Edit 2:** I reopened [Bug 489](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=489)

---

### Post by Limulus on 2006-03-04
[QUOTE=sailor420]Has anyone been able to get sound working?[/QUOTE]
Based on what I found using lsmod, when you boot with 0.5.4 and there's no sound, run the following six commands:
```

sudo modprobe snd_pcm 
sudo modprobe snd_page_alloc 
sudo modprobe snd_pcm_oss 
sudo modprobe snd_mixer_oss 
sudo modprobe snd_ali5451 
sudo modprobe snd_ac97_codec 

```

The ali5451 one took a few seconds on my computer during which time the system was busy; even the clock froze... but when it finished doing what it did everything was back to normal.  After running those, I had sound on my system for that boot.  Try it and see if it works for you.

(Edit: if it does, save the above as something like "audio.sh" on your desktop; when you boot and there's no sound, double click the file and select "Run in Terminal".  This should be a good enough work-around until the underlying problem is resolved)

If not, post a copy of the output from running lsmod from a clean InitNG boot.

---

### Post by Trigger|Debian on 2006-03-04
Modprobing the modules does the job for sure, but this can't be the solution.
Try to run "sudo alsaconf" when you have started with Inintg and see if it works after a reboot.

---

### Post by Limulus on 2006-03-04
> **Trigger|Debian]Modprobing the modules does the job for sure, but this can't be the solution.[/QUOTE]
*nods* I know said:**
> 
Try to run "sudo alsaconf" when you have started with Inintg and see if it works after a reboot.
Hmm...

```

$ sudo alsaconf
sudo: alsaconf: command not found

```
I just did a search and from what I can piece together, Ubuntu doesn't have alsaconf; they removed it 'to make sure people use the Gnome interface' apparently... ^_^;

I'm guessing then that what does the configuration is the "Multimedia Systems Selector" (under System -> Preferences)

When I go to it and press test (making sure ALSA is selected), it says "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"

When I run the six sudo modprobe commands and repeat, it tests just fine.

*shrug*

Given that the sound works just fine without running anything else in 0.5.2 and that occasionally it runs on its own in 0.5.4, could it be that there's a timing problem somewhere in InitNG?

---

### Post by Limulus on 2006-03-04
[QUOTE=Limulus]
Normal Ubuntu Login (splash line in GRUB)
InitNG 0.5.4 (no splash line in GRUB; sound working)
[/QUOTE]
Just FYI, I compared these two and the former has everything the latter has, PLUS the following:

```

binfmt_misc            11496  1
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
orinoco_cs              8872  1
orinoco                39820  1 orinoco_cs
hermes                  7264  2 orinoco_cs,orinoco
usblp                  12640  0
yenta_socket           25292  3
rsrc_nonstatic         13376  1 yenta_socket
i2c_ali15x3             7428  0
dm_mod                 57692  1
md                     45584  0
vga16fb                12584  1
vgastate                9664  1 vga16fb

```

Edit: This leads me to suspect another bug; while adding daemon/cupsd gets the Printer Settings (System -> Administration -> Printing) working, I went to print a document from OpenOffice in an InitNG 0.5.4 boot and it wouldn't (the printer icon opened in the Notification area, showing the document, but nothing happened at the printer).  Booting normally and repeating the same steps resulted in a printed document ;)

I don't recall ever trying to print with a 0.5.2 install, so I don't know if this affects that version or not.

I just filed it as [bug 505](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=505)

Edit 2: I added *all* of those and printing still didn't work for me :/  I should add BTW that I use a USB printer.

---

### Post by kecci on 2006-03-06
Hi, i just installed InitNG 0.54 on my notebook (Dell Inspiron 630m + Ubuntu Dapper latest) following the instructions of the Ubuntu Wiki and all i get as soon as i  login into GDM is a terminal window which says repeatedly "bash: /dev/null: Permission denied". Please help me get this working!
p.s. i get these messages also if i log in via a tty console (e.g. hitting ctrl+alt+F2 and logging in), but i get a usable shell by hitting ctrl+c.

Bye

---

### Post by flummoxed on 2006-03-06
Uhh...

3. Change the content of dbus.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/...ment.cgi?id=69](http://bugzilla.initng.thinktux.net/...ment.cgi?id=69)

4. Change the content of hald.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/...ment.cgi?id=70](http://bugzilla.initng.thinktux.net/...ment.cgi?id=70)

These links are dead...

---

### Post by Limulus on 2006-03-08
[QUOTE=flummoxed]Uhh...
3. Change the content of dbus.i file in /etc/initng/daemon to this:
4. Change the content of hald.i file in /etc/initng/daemon to this:
These links are dead...[/QUOTE]
You're quoting from the very first post in this thread, which is for InitNG version 0.3.3-2, which is long outdated :)  See the Ubuntu Wiki Entry for details on how to install the latest version: [https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG)

---

### Post by Limulus on 2006-03-08
[QUOTE=kecci]Hi, i just installed InitNG 0.54 on my notebook (Dell Inspiron 630m + Ubuntu Dapper latest) following the instructions of the Ubuntu Wiki[/QUOTE]
"the most recent version for Ubuntu (Breezy) is 0.5.4"

Daper is a whole different animal; people have been reporting problems trying to use InitNG as it now exists with Dapper...

I will update the Wiki to make it more explicit that those instructions are for Breezy only.

---

### Post by Trigger|Debian on 2006-03-08
We finally have migrated the Website and the whole bug management to Trac.
Bugzilla is dead. If you know a bug please go to [http://initng.thinktux.net](http://initng.thinktux.net) and open a ticket.
We need more bugs ;)
If someone has a solution for the Dapper naetworking probs: Tell me :)

---

### Post by lleberg on 2006-03-08
My networking died after trying this (from the wiki) howto..

Any tips getting it up and running again?

---

### Post by Trigger|Debian on 2006-03-10
0.5.5 is out: [http://triggerit.tr.funpic.de/blog/?p=39](http://triggerit.tr.funpic.de/blog/?p=39)

---

### Post by NoWhereMan on 2006-03-11
w00t! :mrgreen:

---

### Post by glennric on 2006-03-11
0.5.5 is nice.  Sound works without doing anything.  
I just added daemon/gdm (for gnome), net/eth0 (to get internet), daemon/cupsd (for printing), and system/speedstep (for cpu frequency stuff), and now everything works just like with a normal boot except much faster boot up and shut down.

---

### Post by Trigger|Debian on 2006-03-11
Ok, Dapper users. I have had a looked at the weird new ifupdown package and I have something you can try (don't know if it works).
Open /etc/initng/net/net.i and search for "service net/lo"
Replace it with the following code:
```
service net/lo {
        need = system/initial system/mountfs;
        script start = {
                [ -d /var/run/network ] || mkdir /var/run/network
                ifup --allow auto lo
                exit 0
        };
        exec stop = /sbin/ifdown lo;
}
```
Search in the rest of the script for occurences of "system/ifupdown-debian" and delete these entries. If this script is in one of your runlevels: Remove it.

Now try to reboot. If it fails with more networking problems:
Remove all occurences of "net/whatever" (e.g. net/all) from the runlevels and try again).

Last step: Tell me what happened.

---

### Post by briancrutin on 2006-03-11
big help! thanks!:)

---

### Post by dashed on 2006-03-11
i installed 0.5.5

im wondering.. howd u enable internet connection?

---

### Post by foxy123 on 2006-03-11
> **Trigger|Debian]Ok, Dapper users. I have had a looked at the weird new ifupdown package and I have something you can try (don't know if it works).
Open /etc/initng/net/net.i and search for "service net/lo"
Replace it with the following code:
```
service net/lo {
        need = system/initial system/mountfs said:**
>  || mkdir /var/run/network
                ifup --allow auto lo
                exit 0
        };
        exec stop = /sbin/ifdown lo;
}
```
Search in the rest of the script for occurences of "system/ifupdown-debian" and delete these entries. If this script is in one of your runlevels: Remove it.

Now try to reboot. If it fails with more networking problems:
Remove all occurences of "net/whatever" (e.g. net/all) from the runlevels and try again).

Last step: Tell me what happened.
hey, it did help. The only daemon which failed was klogd. Also although I've got  daemon/samba/smbd  and daemon/samba/nmbd loaded, I cannot get samba connetion. Please note that I have modified speedstep script according to the instructions posted earlier.

---

### Post by xsupernerdx on 2006-03-11
I have InitNG installed and everything is working as it should except frequency scaling. I've got an Athlon XP-M in my laptop and it doesn't seem to like the instructions found in this thread. Can anyone help? I'm sure it's something minor that I'm not bright enough to figure out. Thanks.

---

### Post by dashed on 2006-03-11
im like a super noob in linux. 

im using ubuntu 5.10 and initng 0.5.5.

i didn't want to enable my ethernet connection from the network settings panel every time i log in. how do i automatically enable this with initng? O.o

---

### Post by sailor420 on 2006-03-11
[QUOTE=dashed]im like a super noob in linux. 

im using ubuntu 5.10 and initng 0.5.5.

i didn't want to enable my ethernet connection from the network settings panel every time i log in. how do i automatically enable this with initng? O.o[/QUOTE]

Should be as easy as "sudo ng-update add daemon/eth0".

---

### Post by dashed on 2006-03-11
[QUOTE=sailor420]Should be as easy as "sudo ng-update add daemon/eth0".[/QUOTE]

it didn't work.


this is what i got:

daemon
Warning: "daemon/eth0" isn't a script or a runlevel, it's being removed from list
Error: you didn't specify any script

---

### Post by glennric on 2006-03-11
I added speedstep and powernowd and the cpu frequency scaling works.  
"sudo ng-update add system/speedstep" and
"sudo ng-update add daemon/powernowd"

---

### Post by glennric on 2006-03-11
dashed:
It should be 
"sudo ng-update add net/eth0"

---

### Post by Trigger|Debian on 2006-03-11
@Foxy123: Good to hear. Did you need to remove net/all and things like this?
I wonder how I can ship a changed script - they wouldn't support Breezy and Debian...
We will see...

---

### Post by sailor420 on 2006-03-11
[QUOTE=glennric]dashed:
It should be 
"sudo ng-update add net/eth0"[/QUOTE]

Doh! Sorry, brain fart! ;)

---

### Post by foxy123 on 2006-03-12
[QUOTE=Trigger|Debian]@Foxy123: Good to hear. Did you need to remove net/all and things like this?
I wonder how I can ship a changed script - they wouldn't support Breezy and Debian...
We will see...[/QUOTE]
no I just made the changes to the script... I really surprised that they changed things in Dapper so that it's different from Debian. You should either stick to Debian and we put the necssary changes in wiki or you could ship a Dapper script as optional and we put in wiki that in Dapper one should replace net.i say with net.dapper...

---

### Post by dashed on 2006-03-12
[QUOTE=glennric]dashed:
It should be 
"sudo ng-update add net/eth0"[/QUOTE]

sorrry it diddn't work.

i still had to enable the connection fro mthe network settings.

---

### Post by RaptorRaider on 2006-03-12
Why are we not closing this thread and starting a new one with a decent startpost?

---

### Post by xsupernerdx on 2006-03-12
Frequency scaling is still not working for me. Do I need to have anything installed besides powernowd (and InitNG of course)?  Also, what do I put in the place of "modprobe speedstep_centrino" on the speedstep.i file?

---

### Post by dodgeman79 on 2006-03-13
These two steps have broken links
> 3. Change the content of dbus.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/...ment.cgi?id=69](http://bugzilla.initng.thinktux.net/...ment.cgi?id=69)

4. Change the content of hald.i file in /etc/initng/daemon to this:

[http://bugzilla.initng.thinktux.net/...ment.cgi?id=70](http://bugzilla.initng.thinktux.net/...ment.cgi?id=70)


---

### Post by foxy123 on 2006-03-13
[QUOTE=dodgeman79]These two steps have broken links[/QUOTE]
Please do not use this howto, as it is redundant. Use wiki link in the first post instead.

---

### Post by NoWhereMan on 2006-03-13
[QUOTE=RaptorRaider]Why are we not closing this thread and starting a new one with a decent startpost?[/QUOTE]

Why don't we just UPDATE the first post, as seen in other howtos here ? :mrgreen:

---

### Post by xsupernerdx on 2006-03-13
I followed the wiki and used the 0.5.5 debs. I tried to get frequency scaling to work with and without editing the speedstep.i and powernowd.i files...still no luck.

---

### Post by glennric on 2006-03-13
[QUOTE=xsupernerdx]I followed the wiki and used the 0.5.5 debs. I tried to get frequency scaling to work with and without editing the speedstep.i and powernowd.i files...still no luck.[/QUOTE]

Hmm, I don't know.  I just added speedstep and powernowd and it worked.

---

### Post by cerberos on 2006-03-14
Just upgraded from version 0.4.8-1 to 0.5.5-1 and am having troubles with getting the fglrx drivers working (fglrxinfo reports mesa crap), the previous comment of putting "fglrx" into /etc/modules isn't the current fix as its already in there.

Can anyone help me?

---

### Post by yanns on 2006-03-15
Just upgraded to 0.5.5-1 too.
And I got problem with nvidia module not being loaded.

A guy on IRC (Trigger|Debian ?) told me to enter
sudo lrm-manager --quick
before loading nvidia driver and that works.

I am trying to investigate on "/etc/initng/system/modules.i" to know why this command is not run on boot. Without any success so far.

If somebody has ideas...

---

### Post by Trigger|Debian on 2006-03-15
@yanns Yes, it was me :) 
Do you have system/modules/depmod in system.runlevel? If not this is the reason and I will add it automatically with the next package. Add it with "ng-update a system/modules/depmod system"

[B]I just created a new page with a howto, but it seems as if it need to be moderated first.
I will post the link when I have it. Please don't reply to this thread anymore - use the new one when availlable.[/B]

---

### Post by yanns on 2006-03-15
[QUOTE=Trigger|Debian]@yanns Yes, it was me :) 
Do you have system/modules/depmod in system.runlevel? If not this is the reason and I will add it automatically with the next package. Add it with "ng-update a system/modules/depmod system"

[B]I just created a new page with a howto, but it seems as if it need to be moderated first.
I will post the link when I have it. Please don't reply to this thread anymore - use the new one when availlable.[/B][/QUOTE]

Trigger, you're my hero!
It's working!

---

### Post by Trigger|Debian on 2006-03-19
Hm, my little howto doesn't show up.
Seems as if we need to stay here for the moment.

@yanns: :) 
@all: Please execute "ng-update a system/modules/depmod system"

---

### Post by Trigger|Debian on 2006-03-20
Ok, here we go. Please use this thread from now on: **[http://www.ubuntuforums.org/showthread.php?t=144831](http://www.ubuntuforums.org/showthread.php?t=144831)**

**PLEASE DON'T ANSEWR HERE ANYMORE!**

---

### Post by robtotheb on 2006-04-11
Can I safely remove InitNG using synaptic?

---

