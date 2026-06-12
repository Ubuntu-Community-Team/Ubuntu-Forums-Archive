---
title: "Why cant I edit this file?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by listerdl on 2011-10-29
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules

I am trying to edit this but a blank page appears. I am using root terminal...?

I cant even located the /lib/

Any idea where it is? Thanks!!

---

### Post by nothingspecial on 2011-10-29
If it opens a blank file then the file does not exist.

---

### Post by Vaphell on 2011-10-29
check where the file is exactly
```
locate 95-devkit-disks.rules
```

and sudo is for command line tools, gui stuff should use gksu

---

### Post by MG&amp;TL on 2011-10-29
Any filename preceded by a slash indicates that it starts at the *root* of the filesystem. Try :

```
cd /
ls
```

to see what this means. /lib should be there. By default, the terminal starts in /home/yourname.

---

### Post by jagajugue on 2011-10-29
Try,

$ ls /lib/udev/rules.d/95-*
or
$ ls /lib/udev/rules.d/

just to verify if the file is there.

---

### Post by elliotn on 2011-10-29
if it opens blank then edit that blank and save it, u must ensure its in a correct location or else u won't see the changes of what u trying to achieve

---

### Post by listerdl on 2011-10-30
OK thanks everyone am nearly there!!

I have found a hack to my problem which is this:

>>>>>>>>>>>>><<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

TEMPORARY WORK AROUND FOR THIS PROBLEM IN KARMIC: 

1. sudo gedit /lib/udev/rules.d/95-devkit-disks.rules

2. locate the following lines (about 1/3 the way into the file; search for "smart")

# ATA disks driven by libata
KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

3. comment out the second line by adding a # in front, so you should have

# ATA disks driven by libata
#KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="devkit-disks-probe-ata-smart $tempnode"

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>><<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

Now I am running Lucid so the tip from [launchpad]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852") is to edit this file called udisks and do the same:

```
gedit sudo /lib/udev/rules.d/udisks.rules
```

When I do that a blank file that is named udisks.rules opens but with no text and nothing to edit....

The file is 100% there since I did:

```
# ls /lib/udev/rules.d/
40-fuse-utils.rules                70-acl.rules
40-gnupg.rules                     70-hid2hci.rules
40-gpsd.rules                      75-cd-aliases-generator.rules
40-ia64.rules                      75-net-description.rules
40-infiniband.rules                75-persistent-net-generator.rules
40-isdn.rules                      75-tty-description.rules
40-libgphoto2-2.rules              78-graphics-card.rules
40-pilot-links.rules               78-sound-card.rules
40-ppc.rules                       79-fstab_import.rules
40-xserver-xorg-video-intel.rules  80-alsa.rules
40-zaptel.rules                    80-drivers.rules
45-fuse.rules                      [COLOR="Red"]80-udisks.rules[/COLOR]
50-firmware.rules                  85-console-setup.rules
50-udev-default.rules              85-dmraid.rules
55-dm.rules                        85-hdparm.rules
60-cdrom_id.rules                  85-regulatory.rules
60-floppy.rules                    85-usbmuxd.rules
60-persistent-alsa.rules           90-pulseaudio.rules
60-persistent-input.rules          95-keyboard-force-release.rules
60-persistent-serial.rules         95-keymap.rules
60-persistent-storage-dm.rules     95-udev-late.rules
60-persistent-storage.rules        95-upower-battery-recall-dell.rules
60-persistent-storage-tape.rules   95-upower-battery-recall-fujitsu.rules
60-persistent-v4l.rules            95-upower-battery-recall-gateway.rules
61-mobile-action.rules             95-upower-battery-recall-ibm.rules
61-option-modem-modeswitch.rules   95-upower-battery-recall-lenovo.rules
61-persistent-storage-edd.rules    95-upower-battery-recall-toshiba.rules
64-device-mapper.rules             95-upower-csr.rules
64-xorg-xkb.rules                  95-upower-hid.rules
66-xorg-synaptics.rules            95-upower-wup.rules
69-xorg-vmmouse.rules              97-bluetooth.rules
69-xserver-xorg-input-wacom.rules  README

```

- and clearly udisks.rules is there but there is nothing in the file?

Am I missing something really basic here??

Thanks....

---

### Post by listerdl on 2011-10-30
i figured it out - i was missing the 80 so it has to be: gedit /lib/udev/rules.d/80-udisks.rules

did it but error continues. Nightmare continues...

---

### Post by flanagan on 2011-10-30
So, now that you have called the file by the correct name, when you issue the command ```
gksu gedit /lib/udev/rules.d/80-udisks.rules
``` what exactly happens? In other words, when you say "error continues" and "nightmare continues" what is the exact error you are getting?

---

