---
title: "Suspend-to-RAM how-to (on ThinkPads)"
date: 2006-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Botond on 2006-01-05
Hi,
here's how to make suspend-to-RAM (sleep) work on an IBM ThinkPad R50e. I think the same will work on other laptops with an integrated i855G graphic card.
The whole thing probably works in earlier releases but I have a fully updated Dapper right now.

1. Edit the /etc/default/acpi-support file:
    uncomment these lines
        ACPI_SLEEP=true
        SAVE_VIDEO_PCI_STATE=true
    and leave these commented out
        # POST_VIDEO=true
        # SAVE_VBE_STATE=true

2. Fix [this bug]("https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/6454") in /etc/acpi/resume.sh as I've discribed there (remove the superflous "/vga" tag).

3. Don't append "splash" to the kernel options in /boot/grub/menu.lst
    (Suspent-to-RAM works right now on my system but this last step might not be necessary. I didn't have time to check it out yet.)

    Good luck!

---

### Post by Botond on 2006-01-05
OK, forget the last step. The graphical "splash" may remain and suspend will still work.

---

### Post by Botond on 2006-01-07
It turned out that there is a step 4 for the i810 Xorg driver:

4. Edit /etc/X11/xorg.conf
[INDENT]Section "Device"[INDENT]Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
Driver		"i810"
BusID		"PCI:0:2:0"
**Option		"VBERestore" "on"**[/INDENT]
EndSection

The highlighted line must be added.
[/INDENT]

---

### Post by kjempe on 2006-01-12
Hej Botond.

I really appreciate your instructions to activate STR on a ThinkPad R50e. unfortunately, this doesn`t quite apply to my ThinkPad, though it actually is an R50e.

I uncommented ACPI_SLEEP=true and uncommented # POST_VIDEO=true
and # SAVE_VBE_STATE=true. I didn`t find the line SAVE_VIDEO_PCI_STATE=true in my acpi-support so i just added it right below ACPI_SLEEP=true.

The bug you described in step two was not to be found in my resume.sh, which would have been fine, if it`d include at least something reminding of that command line. Maybe you could post your resume.sh, or something?

Step four was easy to apply, though. My computer now suspends to RAM but doesn`t get the display up again. Restarting via ctrl+alt+backspace doesn`t work either. Any recommendations? :???:

---

### Post by Botond on 2006-01-12
Hej,
apperently your acpi-support package isn't the same as mine. My system is a fully updated Dapper Drake right now, but as I saw Breezy uses the same version namely **0.50**. If for some reason the update is not an option for you then feel free to ask again because there's a not so elegant way of solving this problem and that other way was also working for me (people with other distros - like Fedora - usually go the other way).

Here's my resume.sh:
```
#!/bin/bash

# Post the video card
if [ x$POST_VIDEO = xtrue ]; then
  vbetool post
fi

# Attempt to restore some video card state
if [ x$SAVE_VBE_STATE = xtrue ]; then
  if [ $VBEMODE != "3" ]; then
    vbetool vbemode set $VBEMODE;
  fi
  vbetool vbestate restore <$VBESTATE
fi

# Restore video PCI state
if [ x$SAVE_VIDEO_PCI_STATE = xtrue ]; then
  for x in /sys/bus/pci/devices/*; do
    if [ -f /var/run/vga-pci-`basename $x` ]; then
	cat /var/run/vga-pci-`basename $x` >$x/config;
    fi
  done
fi

# Now source everything in /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
  . $SCRIPT
done

# And turn the framebuffer back on
for x in /sys/class/graphics/*; do
    if [ -f $x/state ]; then
        echo -n 0 >$x/state;
    fi
done


# Increase the firmware loading timeout while we're doing this
# Otherwise, swap thrash tends to lead to failure to start
if [ -f /sys/class/firmware/timeout ]; then
    timeout=`cat /sys/class/firmware/timeout`
    echo 100 >/sys/class/firmware/timeout
fi

# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
#run ifrename so that the interfaces are the same as previously
    ifrename
done

# And reset the firmware timeout
if [ -f /sys/class/firmware/timeout ]; then
    echo $timeout >/sys/class/firmware/timeout
fi

# Get PCMCIA cards back
cardctl insert

# Restart IR if necessary
if [ -f /var/run/irdadev ] && [ x$RESTART_IRDA = xtrue ]; then
    rm /var/run/irdadev;
    /etc/init.d/irda-setup start;
    /etc/init.d/irda-utils start;
fi;

# Bring up the interfaces (this should probably be left up to some policy
# manager, but at the moment we just bring back whatever we ifdowned)
#for x in $INTERFACES; do
#    ifup $x;
#done

# Actually, we don't for the moment - we end up waiting for things to time out
# because multiple ifups want to write to the state file and it's locked. We
# need a better way of doing this - for now just bring back up whatever is
# flagged as auto

ifup -a &

# Reset the time
hwclock --hctosys

# And make sure that the screen is on
if [ x$USE_DPMS = xtrue ]; then
  vbetool dpms on
fi

# Make sure that the drive power state is set correctly again
rmmod ac
modprobe ac
rmmod battery
modprobe battery
/etc/acpi/power.sh

# Some hardware needs another X/console switch in order to bring stuff back
chvt $CONSOLE;
if [ x$DOUBLE_CONSOLE_SWITCH = xtrue ]; then
  chvt 12;
  chvt $CONSOLE;
fi

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
  /etc/init.d/alsa-utils start
fi

# now, we should poke xscreensaver so you get a dialog
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
	su $user -c "(xscreensaver-command -deactivate)"
    fi
done

# we need to restart our services after the network is back
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x start
done

# Some hardware gets unhappy about button events unless we do this
rmmod button
modprobe button

# Kick the fans
rmmod fan
rmmod thermal
modprobe fan
modprobe thermal

if [ "`grep ibm_acpi /proc/modules`" ]; then
    # No, I don't know why
    rmmod ibm-acpi
    modprobe ibm-acpi
fi

# NNGH FAN HATE
for x in /proc/acpi/fan/*; do
    if [ "`grep on $x/state`" ]; then
	echo -n 3 > $x/state;
	echo -n 0 > $x/state;
    fi
done

#Let acpid process events again
(sleep 5 && rm /var/lock/acpisleep)&

```

And the output of "dpkg -l | grep acpi":
```
ii  acpi                                   0.09-1
ii  acpi-support                           0.50
ii  acpid                                  1.0.4-1ubuntu8

```

---

### Post by kjempe on 2006-01-12
Hmm....

Our restore.sh-files actually look quite different and I just don`t want to mess with that file and accidentally shoot my system. I do have Breezy installed and I did a lot of updates recently, as of all that were offered through my taskbar. 

dpkg -l | grep acpi gives following output:
```
ii  acpi                                0.09-1
ii  acpi-support                        0.46ubuntu1
ii  acpid                               1.0.4-1ubuntu8
```
I guess that I would only need to update the acpi-support, but official repositories and backports only offer the version I already have installed. Is there a possibility to just update that package or would that possibly ruin my installation? Otherwise, what`s that rude way you`ve been talking about?

---

### Post by kjempe on 2006-01-12
Allright, i got it working. Probably that was the not-so-elegant way...

I uncommented ACPI_SLEEP=true and left the rest of the acpi-support untouched. I then backuped my sleeps.sh and made a new one with the following:

```
#!/bin/bash

/bin/sync

/sbin/rmmod uhci-hcd
/sbin/rmmod ehci-hcd

/usr/bin/chvt 1

cat /proc/bus/pci/00/02.0 > /var/cache/video.config

echo -n mem > /sys/power/state

cat /var/cache/video.config > /proc/bus/pci/00/02.0

rm -rf /var/cache/video.config

/usr/bin/chvt 7

/sbin/modprobe uhci-hcd
/sbin/modprobe ehci-hcd
```

I then only had to modify the rights on that file to make suspend-to-ram work fine. :)

---

### Post by Botond on 2006-01-12
[QUOTE=kjempe]Allright, i got it working. Probably that was the not-so-elegant way...
[/QUOTE]

Exactly! How did you know that "chvt 1" was needed?

---

### Post by kjempe on 2006-01-12
I found an entry on a German site ([http://www.tuxmobil.de]("http://www.tuxmobil.org"))dealing with that matter and I copied and I pasted. :rolleyes:  
Do you maybe know how I get Gnome to ask for my password to log in as soon as the computer wakes up again?

---

### Post by Botond on 2006-01-13
Here's my sleep.sh:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If PowerManager is running, let it handle policy
if [ "`pidof PowerManager`" ] && [ x$1 != xforce ] && [ x$1 != xsleep ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then	    
	    export DISPLAY=":$displaynum"
	    . /usr/share/acpi-support/screenblank
	fi
    done
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 0 /dev/hda
fi

echo -n $ACPI_SLEEP_MODE >/sys/power/state

if [ x$RESET_DRIVE = xtrue ] && [ -b /dev/hda ]; then
    hdparm -w /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -d 1 /dev/hda
fi

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh

```

And here's my /usr/share/acpi-support/screenblank:
```
su $user -c "(xscreensaver-command -throttle)"
if [ x$LOCK_SCREEN = xtrue ]; then
	su $user -c "(xscreensaver-command -lock)"
fi

xset dpms force off
if [ x$RADEON_LIGHT = xtrue ]; then
    [ -x /usr/sbin/radeontool ] && radeontool light off
fi

```

I think the commands for figuring out the DISPLAY number are superflous, it's probably safe to call *su $user -c "(xscreensaver-command -lock)"* with "export DISPLAY=:0.0".

---

### Post by grinias on 2006-01-20
It works for AcerTravelmate 4101 too !!! Thank you guys !!!
I was trying to find a solution NOT to use vbetool on STR with my ATI X600 64MB PCI-Express video card since my BIOS's  info is awful.
And the solution is to use the info of  "/proc/bus/pci" as you suggest!!!

My device section of xorg.conf is

```

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
        Driver      "fglrx"
        Option      "ForceMonitors" "lvds,tv"
        BusID       "PCI:1:0:0"
EndSection

```
with the latest fglrx driver of ATI (not the Ubuntu package)
while i m using Kubuntu Breezy (acpi-support version is 0.46ubuntu1). 

I set these values in /etc/default/acpi-support

```


ACPI_SLEEP=true
POST_VIDEO=false
SAVE_VBE_STATE=false
USE_DPMS=false
LOCK_SCREEN=false #kde uses its own screensaver policy

```

and the only difference in [/etc/acpi/sleep.sh]("http://www.csd.uoc.gr/~grinias/Ubuntu/sleep.sh")  is that I use [prepare_S3.sh]("http://www.csd.uoc.gr/~grinias/Ubuntu/prepare_S3.sh")
and [resume_S3.sh]("http://www.csd.uoc.gr/~grinias/Ubuntu/resume_S3.sh")
(after I put them in /etc/acpi)
instead of prepare.sh and resume.sh of acpi-support package.

Thanx anyway, once again...

---

### Post by poofyhairguy on 2006-01-23
time to put this in place.

---

### Post by Deiu on 2006-02-13
[QUOTE=kjempe]Allright, i got it working. Probably that was the not-so-elegant way...

I uncommented ACPI_SLEEP=true and left the rest of the acpi-support untouched. I then backuped my sleeps.sh and made a new one with the following:

```
#!/bin/bash

/bin/sync

/sbin/rmmod uhci-hcd
/sbin/rmmod ehci-hcd

/usr/bin/chvt 1

cat /proc/bus/pci/00/02.0 > /var/cache/video.config

echo -n mem > /sys/power/state

cat /var/cache/video.config > /proc/bus/pci/00/02.0

rm -rf /var/cache/video.config

/usr/bin/chvt 7

/sbin/modprobe uhci-hcd
/sbin/modprobe ehci-hcd
```
[/QUOTE]

I tried your script and found it to be "almost" working. Suspend woks fine, but when I resume, it brings back X and then logs out and shuts down. Removing the chvt lines seems to make it work. Now I have a working suspend/resume. ;)

---

### Post by kjempe on 2006-09-30
Good evening.

I just thought it might be interesting to offer a copy-paste-solution for our suspend-to-ram problem with a Thinkpad R50e and Dapper.

/etc/default/acpi-support:
```

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
# SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```
/etc/acpi/sleep.sh:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs
. /usr/share/acpi-support/policy-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    if pidof xscreensaver > /dev/null; then 
	for x in /tmp/.X11-unix/*; do
	    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	    getXuser;
	    if [ x"$XAUTHORITY" != x"" ]; then	    
		export DISPLAY=":$displaynum"
		. /usr/share/acpi-support/screenblank
	    fi
	done
    fi
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 0 /dev/hda
fi

#echo -n $ACPI_SLEEP_MODE > /sys/power/state

  # change to console 1
  FGCONSOLE=`fgconsole`
  chvt 6

  # safe video state
  cat /proc/bus/pci/00/02.0 > /tmp/video_state

  # sync filesystem
  sync

  # sync hardware clock with system time
  hwclock --systohc

  # go to sleep
  echo -n 3 > /proc/acpi/sleep

  # waking up
  # restore system clock
  hwclock --hctosys

  # restore video state
  cat /tmp/video_state > /proc/bus/pci/00/02.0

  # change back to X
  chvt $FGCONSOLE

  # clean up behind us
  rm /tmp/video_state

if [ x$RESET_DRIVE = xtrue ] && [ -b /dev/hda ]; then
    hdparm -w /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -d 1 /dev/hda
fi

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh

```
/etc/acpi/resume.sh
```
#!/bin/bash

# Source from /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
  . $SCRIPT
done
```

Regards, Paul.

---

### Post by bimmermtb on 2006-10-24
I am having some difficulties with my suspend to ram after I shutdown my computer and restart it.  After I do any kind of reboot my acpi seems to forget a state or to run a function when I close the lid.  After I close my lid my computer still keeps running, but when I open the lid after about 2 min I find that my computer still in the process of suspending and everything is locked up and I have to do a cold boot.  I have an effect trick to get the suspend function running again, and that is to either one of the files acpi-support and sleep.sh and make a small change. For example uncommenting the SAVE_VBE_STATE = true and save the change.  Then going back and undoing the change that I made.  This seems to be enough to reboot the suspend to ram function and it starts working after that.  I tried everything on this forum, but the problem still continues.  Please I need help.

I have an R60 with the Integrated Intel Graphics Media Accelerator 950 graphics card.

---

### Post by phenest on 2007-07-18
This works for a Philips X56 (Twinhead H12Y).

Thanks.

---

### Post by phenest on 2007-07-18
Ok. Just to add that, although hibernate works, there is no sound after resuming.

---

### Post by Sunflower1970 on 2007-07-19
> **phenest said:**
> Ok. Just to add that, although hibernate works, there is no sound after resuming.

I found an answer to the problem here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

Towards the bottom of the page there's an answer which worked for me and sound:

In your  /etc/default/acpi-support change the HIBERNATE_MODE to HIBERNATE_MODE=platform

---

### Post by lhommemagique on 2007-07-20
I have a Fujitsu tablet running fistey fawn  and I just needed to follow step one to get my suspend to work
thanks.

---

