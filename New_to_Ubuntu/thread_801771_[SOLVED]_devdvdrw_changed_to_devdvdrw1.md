---
title: "[SOLVED] /dev/dvdrw changed to /dev/dvdrw1"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by civilmonkey on 2008-05-20
Hi there,

When I upgraded from Ubuntu 7.10 to 8.04 my DVD burner device name changed from /dev/dvdrw to /dev/dvdrw1.  

It's not really hampering me, I'm just curious why this might have happened and how to change it back (so that I don't have to specifically tell programs what my DVD burner is called).

Thanks

---

### Post by mc4man on 2008-05-21
Do you have 1 or 2 cd/dvd drives? 
If you have one there's a couple of fairly easy ways to fix. Run ```
sudo lshw -C disk
``` and post. If you have 2 (and want to switch links) also copy and post from /etc/udev/rules.d - the contents of 70-persistent-cd rules

edit: post the ..cd rules even if you only have 1 drive

---

### Post by civilmonkey on 2008-05-21
Only 1 DVDRW drive.  I removed the physical disks from the lshw posting to save space.  The cd rules file seems to show my dvd drive twice, once as ide, once as scsi.  My DVD drive is definitely connected with an ide cable.

lshw:
```

 *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-H10A
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JL02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open


```

70-persistent-cd rules:
```

# HL-DT-ST_DVDRAM_GSA-H10A (pci-0000:00:06.0-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVDRAM_GSA-H10A (pci-0000:00:06.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATE$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATE$

```

---

### Post by mc4man on 2008-05-21
This is what you can do. run in terminal ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
``` (copy and paste, if you see blank page exit without saving ,you didn't copy all the com., try again)
What you want to do is delete the first instance of your drive and then carefully edit the 2nd one as such. (just remove the 1 from each) (y_ou are leaving the scsi entry_)
```
# DVDRAM_GSA-H10A (pci-0000:00:06.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATE$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}$
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATE$
```

Save, then run gksudo nautilus and navigate in filesystem to /dev  Inside you'll see links (look like files with an arrow) Delete all of the following _you find_ (what you need will be rewritten when you reboot)
cdrom, cdrom1, dvd, dvd1, cdrw, cdrw1, dvdrw, dvdrw1, sr0, sr1 (sr0,sr1 are far down the page)
_Only delete links !_ Not scd0 
Reboot and ck. in /dev you should only see dvd,dvdrw,cdrom, ect.
all apps that default to a device at /dev/dvd will be able to access your drive now
This is very simple actually, but if unclear ask before doing.

what seems to happen when you upgrade is 70-persistent-cd rules is not cleared of the old drive setting, it simply adds a new somewhat redundant entry and assigns /dev links that are 1 up. When you try to playback most apps default to /dev/dvd and can't find the device which is now at /dev/dvd1
Note: the scsi method is how things are done now, whether the drive is sata or ide is irrelevant.

re edit if you have 2 dvdrw drive and simply want to switch links then simply make changes in ...cd rules and reboot, no need to edit in /dev, though ck. fstab to see if it's the way you want as far as mount point

---

### Post by civilmonkey on 2008-05-22
Worked like a charm.  Thanks very much.

Is there any user friendly documentation for stuff like this?  I tried to find something online but this forum is just so easy :)

---

### Post by jelofson on 2008-05-23
Very happy I found this post. Thanks mc4man!

---

### Post by IgnorantGuru on 2008-05-31
> **mc4man said:**
> This is what you can do. run in terminal ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Nice troubleshooting.  This isn't just a result of upgrading - I did a fresh install of Kubuntu Hardy/KDE3 and encountered this misconfiguration.  Both IDE and SCSI versions of the DVD drive were listed in 70-persistent-cd.rules.  Removing the IDE section, changing "dvd1", etc. to "dvd" in the SCSI entries, and deleting the links in /dev as advised by mc4man above corrected this problem.

This bug was first reported 3 months ago during alpha testing of Hardy, with no progress thus far.  Does someone not want Ubuntu users to play commercial DVDs?

---

### Post by mc4man on 2008-05-31
> Does someone not want Ubuntu users to play commercial DVDs?  While I'm sure the studios wish there were no open source players i don't think it's anything intentional. There's something not quite 'correct' concerning ...rules and considering it controls/overrides the links in /dev can cause issues. (also occurred in gutsy). what i do think is multimedia playback, usability and customizing of such is not considered 'important' and is reflected in hardy. 
As a side note I've seen another odd behavior of ...rules. If you do an install of hardy with a cdrw drive and a dvdrw and then at some point replace the cdrw drive with a dvdrw drive ...rules doesn't change to reflect this. The cdrw entry stays as is and while the new dvdrw drive will work as a device - /dev/scdx it gets no dvd, dvdrw links and so can't be accessed by apps using /dev/dvdx

Do you have an ide or sata drive?, I don't have one but I was thinking that that would also be a case where the device would be right (scd0) but it may be given dvd1, ect. links

---

### Post by IgnorantGuru on 2008-05-31
> **mc4man said:**
> While I'm sure the studios wish there were no open source players i don't think it's anything intentional.

I don't know - insufficient data.  I do know that studios and their related interests do more than wish, and a popular way to sabotage security and operability lately is to make a 'mistake'.  "Oops, this gaping security hole that has been open for two years (SSL anyone?) was an accident, I swear."  Can't be proven one way or the other (plausible deniability), but it's time for people to wise up a bit.  I think three months is a long time to fix a known problem which renders DVDs unplayable in the distribution.  Whoever is responsible should not be in charge of that area anymore.  And if it is true that "multimedia playback, usability and customizing of such is not considered 'important'", I would ask WHY, and at whose behest?  It is important to most users.

> Do you have an ide or sata drive?, I don't have one but I was thinking that that would also be a case where the device would be right (scd0) but it may be given dvd1, ect. links

I have an IDE dvd drive, a SATA hard drive, and another IDE hard drive.

I also don't understand why PATA drives are being labeled "/dev/sda" and why IDE DVD drives are being identified as scsi.  I think you alluded to a rationale for this but it seems it will create confusion.

Anyway thanks for the fix!  Workarounds are all we have when bug reports are ignored for 3 months.

---

