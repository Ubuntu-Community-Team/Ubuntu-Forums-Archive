---
title: "HOWTO: Ubuntu on Asus V6800V"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Brathahn on 2005-04-15
Got a replacement for my Sony VAIO Z1SP, an Asus V6800V. This is my experiance with migrating from the Sony to the Asus. First of all I made a complete backup of the Sony to an external Firewire HDD using my good 'ole backup script based on:

[http://www.linux.com/article.pl?sid=04/09/15/1931240](http://www.linux.com/article.pl?sid=04/09/15/1931240) 

Then I installed Ubuntu 5.04 on the Asus which went like a breeze (as expected...  :wink: )

First of all after the installation I wanted my /home content back, connected the Firewire HDD, created my usual mountpoint ,/media/backup, and mounted the backup disk with 'mount /dev/sda1 /media/backup' from the console. So far I didn't login using the GDM and therefore the /home directory was basically empty...

After mounting the backup disk I changed to /media/backup/home/ and ran a script that copied eveything back to /home. The script is based on something I once found in the Gentoo forums (I think):

[B] #!/bin/sh
SOURCE=$1
DESTINATION=$2

if [ "$SOURCE" = "" ]; then
	echo ""
	echo "Syntax: copy.sh  SOURCE  DESTINATION"
	echo""
else
	if [ "$DESTINATION" = "" ]; then
		echo ""
		echo "Syntax: copy.sh  SOURCE  DESTINATION"
		echo ""
	else
		echo ""
		echo "Copying $SOURCE to $DESTINATION"
		echo ""
		tar lcf - $SOURCE|(cd $DESTINATION; tar xpvf - )
		echo ""
	fi
fi
[/B]

So from within /media/backup/home I ran ./home/brathahn/bin/copy.sh . /home. Sometimes later the script was finished and I logged in to find my familiar Ubuntu desktop.  :) 

Impressively all the important stuff was working out of the box, keeping in mind that the Asus is a brand new Sonoma based notebook. Trackpad incl. scrolling & sound was working. 

Also out of the box some of the Asus buttons worked: Bluetooth button switches bluetooth on and off, LCD brightness via Fn+F5/Fn+F6 and after uncommenting the ACPI_SLEEP=true line in /etc/default/acpi-support suspend to RAM works via Fn+F1, which was a surprise, Surprise was also that the notebook woke up properly although I use a vga=0x31B kernel parameter to get a better resolution on the console. This didn't work on the VAIO, only if I changed the kernel parameter to vga=normal.

The I came across this one, Asus M6N-Kompendium: ACPI [http://de.wikibooks.org/wiki/Asus_M6N-Kompendium:_ACPI](http://de.wikibooks.org/wiki/Asus_M6N-Kompendium:_ACPI) and I tried to give it a go. Unfortunately for most of you the link is in German but I guess it should be possible to figure it out anyway. 

The result was a bunch of scripts in /etc/acpi/events and subsequently in /etc/acpi:

in /etc/acpi/events I now have this:

[B]# /etc/acpi/events/asus_lid
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/asus_s3.sh



# /etc/acpi/events/asus_s3
# This is called when the user presses the Pad-Lock Key and calls
# /etc/acpi/asus_s3.sh for further processing.

event=.*hotkey.*6b[[:space:]].*
action=/etc/acpi/asus_s3.sh



# /etc/acpi/events/asus_s4
# This is called when the user presses the Fn+F4 and calls
# /etc/acpi/asus_s4.sh for further processing.

event=.*hotkey.*6d[[:space:]].*
action=/etc/acpi/asus_s4.sh



# /etc/acpi/events/asus_screenlock
# This is called when the user presses the Power4 Gear Key and calls
# /etc/acpi/asus_screenlock.sh for further processing.

event=.*hotkey.*5c[[:space:]].*
action=/etc/acpi/asus_screenlock.sh



# /etc/acpi/events/asus_mute
# This is called when the user presses the Fn+F10 and calls
# /etc/acpi/asus_mute.sh for further processing.

event=.*hotkey.*32[[:space:]].*
action=/etc/acpi/asus_mute.sh



# /etc/acpi/events/asus_up
# This is called when the user presses the Fn+F12 and calls
# /etc/acpi/asus_up.sh for further processing.

event=.*hotkey.*30[[:space:]].*
action=/etc/acpi/asus_up.sh



# /etc/acpi/events/asus_down
# This is called when the user presses the Fn+F11 and calls
# /etc/acpi/asus_down.sh for further processing.

event=.*hotkey.*31[[:space:]].*
action=/etc/acpi/asus_down.sh



# /etc/acpi/events/asus_eth0
# This is called when the user presses the Internet Launch Key and calls
# /etc/acpi/asus_eth0.sh for further processing.

event=.*hotkey.*51[[:space:]].*
action=/etc/acpi/asus_eth0.sh



# /etc/acpi/events/asus_eth1
# This is called when the user presses the Wireless LAN Key and calls
# /etc/acpi/asus_eth1.sh for further processing.

event=.*hotkey.*5d[[:space:]].*
action=/etc/acpi/asus_eth1.sh[/B]

and in /etc/acpi I have this:


[B]#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXuser;

if [ x$ACPI_SLEEP != xtrue ]; then
  exit;
fi

# Generic preparation code
. /etc/acpi/asus_prepare.sh

if [ x$LOCK_SCREEN = xtrue ]; then
  . /usr/share/acpi-support/screenblank
fi

if [ x$DISABLE_DMA = xtrue ]; then
  hdparm -d 0 /dev/hda
fi

echo -n $ACPI_SLEEP_MODE >/sys/power/state

if [ x$DISABLE_DMA = xtrue ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/asus_resume.sh



#!/bin/sh
# /etc/acpi/asus_s4.sh
# Hibernate (suspend-to-disk)

/etc/init.d/hotplug stop
/usr/sbin/laptop_mode stop
echo 4 > /proc/acpi/sleep
/usr/sbin/laptop_mode auto
/etc/init.d/hotplug start


#!/bin/bash
#  Lock the screen

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXuser;

su $user -c "(xscreensaver-command -lock)"





#!/bin/bash

#prevent acpid from processing any following events
touch /var/lock/acpid

# Find the currently running network interfaces...
INTERFACES=`/sbin/ifconfig | awk '/^[^ ]+/ {print $1}'`

# And shut them down
for x in $INTERFACES; do
    ifdown $x;
    ifconfig $x down;
done

# This is not guaranteed to work - several drivers appear to use names that
# are not the same as their module name
for x in /sys/class/net/*; do
    if [ -e $x/driver ]
	then
	MODULES="$MODULES `readlink $x/driver | awk -F/ '{print $7}' | tr [:upper:] [:lower:]`"
    fi
done

# Now do something similar for USB
for x in /sys/class/usb_host/*; do
    if [ -e $x/driver ]
	then
	MODULES="$MODULES `readlink $x/driver | awk -F/ '{print $7}' | tr [:upper:] [:lower:]`"
    fi
done

# Now remove various modules that might misbehave while suspending
for x in $MODULES; do
    rmmod $x 2>/dev/null;
done

# Unload PCMCIA cards
cardctl eject

# And remember which console we're on
CONSOLE=`fgconsole`

# Change away from X, otherwise it'll blow up when we POST the video interface
chvt 12

# Shut down services known to misbehave
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x stop
done

# And then try to save some video state
if [ x$SAVE_VBE_STATE = "xtrue" ]; then
  VBESTATE=`tempfile`
  vbetool vbestate save >$VBESTATE;
fi

# Make sure the backlight goes off
if [ x$USE_DPMS = "xtrue" ]; then
  vbetool dpms off
fi



#!/bin/bash

# Post the video card
if [ x$POST_VIDEO = xtrue ]; then
  vbetool post
fi

# Attempt to restore some video card state
if [ x$SAVE_VBE_STATE = xtrue ]; then
  vbetool vbestate restore <$VBESTATE
fi

# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
done

# Get PCMCIA cards back
cardctl insert

#run ifrename so that the interfaces are the same as previously
ifrename

# Bring up the interfaces (this should probably be left up to some policy
# manager, but at the moment we just bring back whatever we ifdowned)
for x in $INTERFACES; do
    ifup $x;
done

# Actually, we don't for the moment - we end up waiting for things to time out
# because multiple ifups want to write to the state file and it's locked. We
# need a better way of doing this - for now just bring back up whatever is
# flagged as auto
# ifup -a &

# Reset the time
hwclock --hctosys

# And make sure that the screen is on
if [ x$USE_DPMS = xtrue ]; then
  vbetool dpms on
fi

# Some hardware needs another X/console switch in order to bring stuff back
chvt $CONSOLE;
if [ x$DOUBLE_CONSOLE_SWITCH = xtrue ]; then
  chvt 12;
  chvt $CONSOLE;
fi

# now, we should poke xscreensaver so you get a dialog
su $user -c "(xscreensaver-command -deactivate)"

# we need to restart our services after the network is back
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x start
done

# Some hardware gets unhappy about button events unless we do this
rmmod button
modprobe button

modprobe ipw2200
# /etc/init.d/ifplugd restart

#Let acpid process events again
(sleep 1 && rm /var/lock/acpid)&



#!/bin/bash
#  Mute/unmute the volume

if [ "$(amixer | head -n 5 | grep -o '\[on\]')" == "[on]" ]
  then
  logger "Mute"
  amixer set Master mute > /dev/null
else
  logger "Unmute"
  amixer set Master unmute > /dev/null
fi



#!/bin/bash
#  Increase the volume

amixer set Master 1+ > /dev/null



#!/bin/bash
#  Decrease the volume

amixer set Master 1- > /dev/null



#!/bin/bash
#  Enable/disable eth0 LAN device

if [ "`grep eth0 /etc/network/ifstate`" == "eth0=eth0" ]; then
  # LAN is on
  ifdown eth0 > /dev/null
else
  # LAN is off
  ifup eth0  > /dev/null
fi




#!/bin/bash
# Enable/disable eth1 WLAN device

if [ "`grep eth1 /etc/network/ifstate`" == "eth1=eth1" ]; then
  # WLED is ON -> WLAN is on
  ifdown eth1 > /dev/null
  echo 0 > /proc/acpi/asus/wled
else
  # WLED is FF -> WLAN is off
  ifup eth1  > /dev/null
  echo 1 > /proc/acpi/asus/wled
fi




[/B]


I opted for copying and modifying the original prepare and resume scripts just in case the original ones are getting modified by an acpi-support upgrade....



So now everything is working as I want it ecept two things. Firstly ifplugd is not working anymore properly which seems to come down to the sk98lin driver for the onboard NIC. Strangely enough altough there's no cable plugged ifplugd detects a link and brings the interface up. Playing around with different detection modes of ifplugd didn't change anything. This was basically what got me started with the Asus buttons, I wanted something else instead of bringing the interfaces up and down manually...

The second thing that doesn't see to work are the fglrx drivers for the Mobility X600. I was playing with all kinds of MonitorOption settings in the xorg.conf but the result was always a black screen despite all the threads I read about it. 

I also realized that the fglrx drivers don't really play well together with supend to RAM and decided for myself that I'll stick to the xorg drivers although they don't have dri support for the Mobility Radeon X600 (yet). I rather have the notebook working like a notebook with lid closing and everything instead of having dri which I usually only use for the screensaver anyway....

Finally here's the usual lspci -v output:

[B]0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Asustek Computer, Inc.: Unknown device 1882
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03) (prog-if 00 [Normal decode])        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0000000-fbefffff
        Prefetchable memory behind bridge: d0000000-deffffff
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at a480 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at a800 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at a880 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ac00 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at dffffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: fbf00000-fbffffff
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Asustek Computer, Inc.: Unknown device 1915
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 9800 [size=256]
        I/O ports at 9c00 [size=64]
        Memory at dffff800 (32-bit, non-prefetchable) [size=512]
        Memory at dffff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Asustek Computer, Inc.: Unknown device 1886
        Flags: medium devsel, IRQ 20
        I/O ports at a000 [size=256]
        I/O ports at a400 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: medium devsel
        I/O ports at 0400 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150 (prog-if 00 [VGA])
        Subsystem: Asustek Computer, Inc.: Unknown device 1881
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b000 [size=256]
        Memory at f0000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fbee0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
        Subsystem: Asustek Computer, Inc.: Unknown device 173c
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbffc000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Expansion ROM at fbfc0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, VGA palette snoop, medium devsel, latency 248, IRQ 17
        Memory at 40000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=ff, secondary=ff, subordinate=ff, sec-latency=248
        I/O window 0: fffffffc-ffffffff
        I/O window 1: fffffffc-ffffffff
        16-bit legacy interface ports at fffd

0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at fbffa800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <available only to root>

0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: bus master, medium devsel, latency 248, IRQ 5
        Memory at fbffb400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:03:01.3 System peripheral: Ricoh Co Ltd: Unknown device 0592 (rev 08)
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: medium devsel, IRQ 5
        Memory at fbffb800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:03:01.4 System peripheral: Ricoh Co Ltd: Unknown device 0852 (rev 03)
        Subsystem: Asustek Computer, Inc.: Unknown device 1967
        Flags: medium devsel, IRQ 5
        Memory at fbffbc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:03:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2701
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at fbff9000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

[/B]

And the device section for the Mobility Radeon X600:

[B]Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
        Option          "AGPMode"               "4"
        Option          "AGPFastWwrite"         "true"
        Option          "BusType"               "PCIE"
        Option          "EnableDepthMoves"      "true"
        Option          "EnablePageFlip"        "true"
        Option          "BackBuffer"            "true"
        Option          "DDCMode"               "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "backingstore"          "true"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
EndSection[/B]

I also played around a bit with the composite but until there are full Radeon Mobility X600 support in XORG with dri and averything I guess it's not really worth it....


As summary I have to say that the Asus V6800V is perfect for running Ubuntu on it! I guess the dri problem will be fixed sooner or later with newer xorg drivers and the ifplugd, well I don't really need it anymore

---

### Post by Brathahn on 2005-04-19
Update: After applying the latest BIOS Update for this baby suspend to RAM wasn't working anymore as before.... :( After a bit of fiddling around it turns out that the vga=0x31B kernel parameter was the problem. After removeing everything works again but I lost my nice 1280x1024 console..... :neutral:

---

### Post by Brathahn on 2005-04-19
Update 2: On the Asus Driver & Utility CD Ver. 1.0 I found the original BIOS that was installed on the V6V when I bought it. Since this is a completely Windows free system I made a bootable CD with the help of [http://www.nenie.org/misc/flashbootcd.html](http://www.nenie.org/misc/flashbootcd.html) Motherboard Flash Boot CD from Linux Mini HOWTO, and reflashed the BIOS with the original version and voila! everything is back to what it used to be!  :-) 

Original BIOS version (and now again) is V6V0401A -> everything works

Newest BIOS verion is V6V0702A -> messes up S3 suspend when using high resolution framebuffer console.

---

### Post by Tschaeck on 2005-04-23
hi,

i bought the same notebook.
most things are working really fine, but suspend to ram is not working for me. notebook goes to sleep, but won't wake up again. did this work for you out of the box, or did you configure anything to get it working?
i also got a problem with acip reading the lcd status. dmesg is full of "Asus ACPI: Error reading LCD status" messages and a "LCD Status: off" (or something like that) OSD message comes up sporadically, that looks like that one when changing the lcd brightnes.

as you sad the most buttons are not working out of the box. please could you upload or email your acpi scripts/events. i seem not to be able to reconstruct them from your text above. thanks.

---

### Post by flipy on 2005-04-26
[QUOTE=Tschaeck]hi,

i bought the same notebook.
most things are working really fine, but suspend to ram is not working for me. notebook goes to sleep, but won't wake up again. did this work for you out of the box, or did you configure anything to get it working?
i also got a problem with acip reading the lcd status. dmesg is full of "Asus ACPI: Error reading LCD status" messages and a "LCD Status: off" (or something like that) OSD message comes up sporadically, that looks like that one when changing the lcd brightnes.

as you sad the most buttons are not working out of the box. please could you upload or email your acpi scripts/events. i seem not to be able to reconstruct them from your text above. thanks.[/QUOTE]
 same here, with a M6B00NE, and can't translate the german page you posted...

---

### Post by Brathahn on 2005-05-04
Well, suspend to RAM was working out of the box BEFORE I updated the BIOS. It went to sleep but didn't wake up when I used the VGA=0x31A as kernel parameter. However it worked with vga=normal. After downgrading the BIOS again to the orifinal one which came with the V6V everything is working again. I think it definately has something to do with the BIOS.

---

### Post by Brathahn on 2005-05-05
@ Tschaeck & flipy: check you private messages....

---

### Post by boorce.com on 2005-05-06
Hi !

I'm an happy asus v6800v 17 rw owner !
Not yet an ubutun user, but debian... 
I'm happy... but...
I've a strange problem with the v6v (both 04xx and 07xx bios) :

I have "acpi event pooling..."  
Description more precise :
ACPI works great : cpufreq, buttons, etc.  But when loading battery kernel module, ALL the events EXCEPT power button and LID seems to be queued ! Pressing Fn+Fx, unplugging AC, sleep button, all thoses events looks like being in a 2 or 8 stage queue acting like a "first in first out". And this queue is fed by Invisible events generated by the battery ! (Only in debian ! Windows, works whitout a flaw !)

Seems like no one have this problem in UBUNTU. so I will test with live CD... 
Do you have similar problem ?

---

### Post by boorce.com on 2005-05-06
[QUOTE=boorce.com]Hi !

I'm an happy asus v6800v 17 rw owner !
Not yet an ubutun user, but debian... 
I'm happy... but...
I've a strange problem with the v6v (both 04xx and 07xx bios) :

I have "acpi event pooling..."  
Description more precise :
ACPI works great : cpufreq, buttons, etc.  But when loading battery kernel module, ALL the events EXCEPT power button and LID seems to be queued ! Pressing Fn+Fx, unplugging AC, sleep button, all thoses events looks like being in a 2 or 8 stage queue acting like a "first in first out". And this queue is fed by Invisible events generated by the battery ! (Only in debian ! Windows, works whitout a flaw !)

Seems like no one have this problem in UBUNTU. so I will test with live CD... 
Do you have similar problem ?[/QUOTE]

Ubuntu LiveCD works fine ! No "acpi event pooling" bug !!!

Seems like a Debian kernel configuration issue... will look at it...

Bonus attachement : for all users, an "asus_acpi.c" tuned for V6V with bluetooth led support ! enjoy !

---

### Post by Tschaeck on 2005-05-06
[QUOTE=boorce.com]Bonus attachement : for all users, an "asus_acpi.c" tuned for V6V with bluetooth led support ! enjoy ![/QUOTE]
the bluetooth led and button work great out of the box. i didn't need to patch anything.

---

### Post by boorce.com on 2005-05-07
In fact, it's adding a bled entry in /proc/acpi/asus

(I haven't in the original driver)

I have now : tled, bled, wled.

echo 1 > bled acts as pressing the "bluetooth" button (the led and the bluetooth function are linked, not like touchpad or wireless buttons/leds)

now module loading V6V is recognised as supported.

For my "event spooling" bug on Debian. I've tested a ubuntu kernel on the debian, and It worked ! So I've applied the 2.6.10-5 configuration file on a debian 2.6.11 source whit latest acpi patch. and now all is working just fine. 1400x1050 vesa console, OpenGL acceleration with latest ATI drivers, bluetooth, wireless in "802.11b" mode. DVD authoring, touchpad ON/OFF, IEEE1394, and so on.
Not tested :
Sleep modes... (Next step of tweaking !)
Ricoh card readers (No drivers.)
PC CARD (no time for :D )

---

### Post by Tschaeck on 2005-05-08
[QUOTE=boorce.com]In fact, it's adding a bled entry in /proc/acpi/asus

(I haven't in the original driver)

I have now : tled, bled, wled.[/QUOTE]
i suppose that tled is the touchpad led, right? would be really cool to have that in proc. so how do i use your asus_acpi.c? do i have to recompile the kernel?

ps: do you guys experience that "lcd status error" which i reported in my first post? it is getting on my nervs more and more. and reading important things from dmesg is really hard because it gets heavily flushed with "Asus ACPI: Error reading LCD status" messages.

---

### Post by boorce.com on 2005-05-09
I had the LCD error. But the asus_acpi.c fixed it. and whit echo 0 > /proc/acpi/asus/lcd I turn the LCD off (in fact, it seems only to turn the backlight off...)

and echo 1 > /proc/acpi/asus/tled turns the led on. (or off, if you send a 0 )

echo 1 > /proc/acpi/asus/bled turns bluetooth led on AND bluetooth on. (hardware linked ?)
And It needs a kernel rebuild. (It is the asus_acpi.c which was originaly shipped whith the 2.6.11 kernel and was modded.).

---

### Post by abmcr on 2005-05-14
[QUOTE=Tschaeck]hi,

i also got a problem with acip reading the lcd status. dmesg is full of "Asus ACPI: Error reading LCD status" messages and a "LCD Status: off" (or something like that) OSD message comes up sporadically, that looks like that one when changing the lcd brightnes.
[/QUOTE]


I also have the problem in the dmesg output: "Asus ACPI: Error reading LCD status". I don't understand how to resolve it. The problem is only under kde desktop environnement (i.e.: KUBUNTU live) non in Gnome desktop (?). Thank you

---

### Post by luigi.malago on 2005-06-04
hi, i have a V6800V too,
i read that you cannot configuring X600 using fglrx, and i have the same problems.

i'm trying to solve it with onother guy that have the same notebook too..
you can read what are the problems here:
[http://forums.gentoo.org/viewtopic-t-343410.html](http://forums.gentoo.org/viewtopic-t-343410.html)

Do you think it's a problems of the drivers?
Is a new version of the drivers supposed to solve this problem?

Hope we can all work together to solve this problem..

thanks a lot.
Luigi

---

### Post by Tschaeck on 2005-06-04
[QUOTE=luigi.malago]hi, i have a V6800V too,
i read that you cannot configuring X600 using fglrx, and i have the same problems.

i'm trying to solve it with onother guy that have the same notebook too..
you can read what are the problems here:
[http://forums.gentoo.org/viewtopic-t-343410.html](http://forums.gentoo.org/viewtopic-t-343410.html)

Do you think it's a problems of the drivers?
Is a new version of the drivers supposed to solve this problem?

Hope we can all work together to solve this problem..

thanks a lot.
Luigi[/QUOTE]

i am using the latest ati driver and it works. only thing that is really crappy: when waking up from suspend, the driver makes the system freeze.

to get the driver working i had to disable the composite extension and declare my monitor as "LVDS".

---

### Post by luigi.malago on 2005-06-04
Do you have a v6800v and you ati-drivers works correctly with ATI X600 PCIe?

1) Can you post your xorg.conf?
2) Do you use Device "fglrx"?
3) Did you update your bios? 

me and another guy cannot find any way to make it work.

thanks a lot 
Luigi

---

### Post by Tschaeck on 2005-06-04
[QUOTE=luigi.malago]Do you have a v6800v and you ati-drivers works correctly with ATI X600 PCIe?

1) Can you post your xorg.conf?
2) Do you use Device "fglrx"?
3) Did you update your bios? 

me and another guy cannot find any way to make it work.

thanks a lot 
Luigi[/QUOTE]

i have a v6835v and it works correct with the ubuntu-fglrx driver but much faster with the latest ati driver.

1)
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
 RgbPath  "/usr/X11R6/lib/X11/rgb"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc105"
 Option  "XkbLayout" "de"
 Option  "XkbOptions" "nodeadkeys"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option  "HorizScrollDelta" "0"
 Option  "SHMConfig"      "on"
EndSection

Section "Device"
 Identifier "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
 Driver  "ati"
 BusID  "PCI:1:0:0"
EndSection





# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "LVDS, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=3150
    Screen 0
EndSection






Section "Monitor"
 Identifier "Standardbildschirm"
 Option  "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "ATI Graphics Adapter"
 Monitor  "Standardbildschirm"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
 Mode 0666
EndSection

#Section "Extensions" 
# Option "Composite" "Enable"
#EndSection
``` 

2) which device "fglrx"? i am using the fglrx driver, which has to be installed first. it is in the "linux-restricted-modules" package.
3) no i didn't

---

### Post by luigi.malago on 2005-06-05
thanks a lot!
i'm gonna try right now,
I'll let you know soon!

Luigi

---

### Post by Guybrush on 2005-06-05
I have problems to construct the scripts in /etc/acpi because i miss the filenames from most of the scripts. Can you please post all the filenames?

---

### Post by Brathahn on 2005-06-15
All the file names are after a # at the beginning of each file in the original post.

---

### Post by neongtr on 2005-06-30
wooww I just start with linux

  can you tell me or direct me how to change the acpi and xorg files please?

 and anyone got the card reader to work??

 thanks a lot, I am half way to the new world 

 cheers

---

### Post by Guybrush on 2005-07-12
[QUOTE=Brathahn]All the file names are after a # at the beginning of each file in the original post.[/QUOTE]

The file names are given for all files in /etc/acpi/events. 
After this section (starting with the line "and in /etc/acpi I have this:") there are in most cases no filenames at the beginning of the files.

---

