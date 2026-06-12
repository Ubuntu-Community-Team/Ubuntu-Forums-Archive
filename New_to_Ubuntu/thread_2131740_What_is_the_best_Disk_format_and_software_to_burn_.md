---
title: "What is the best Disk format and software to burn a Ubuntu disk?"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by fosbinder on 2013-04-02
I have CD-R 's that couldnt hold the os if they wanted to and DVD-R that dont seem to be detected by the burning softare suggested in the tutorial .. Im thinking my HP DVD Writer 300n 1.25 cant write to them but thought Ide ask around here before buying a new DVD Writer

---

### Post by grahammechanical on 2013-04-02
I say that you have a choice - DVD+RW and DVD-RW. You want Read/Write. That way you can re-use the disk. CD-R/CD+R and DVD-R/DVD+R are Read only. You cannot re-use them.

Strictly speaking, the R = Recordable, and the RW = ReWritable.

[http://en.wikipedia.org/wiki/DVD_recordable](http://en.wikipedia.org/wiki/DVD_recordable)

> [COLOR=#000000][FONT=sans-serif]The "plus" format uses a more reliable phase modulation technique [/FONT][/COLOR][SUP][[2]]("http://en.wikipedia.org/wiki/DVD_recordable#cite_note-2")[/SUP][COLOR=#000000][FONT=sans-serif] to provide 'sector' address information. Introduced after the "-" format.[/FONT][/COLOR]

also take note of the  maximum write speed as well as the size in GB or the time for Video.

Regards.

---

### Post by edeneen on 2013-04-02
12.04 will fit on a CD
12.10 requires a DVD

---

### Post by d0006 on 2013-04-02
Do you have the latest firmware?  I have seen a few posts by people that have problems until they update the firmware.

Unfortunately you can not do this in Ubuntu (at least I do not know a way. If there is a way I hope someone will post it).

You will have to do this on a windows machine or copy the firmware update program to some kind of DOS bootable media.  Back in the day I did this with floppy disks but there is probably a way to do this with a CD or USB stick today.

You can always try to write to the CD from the command line.  Do a search and you will find instructions.

ALWAYS burn a distro at the SLOWEST speed your device supports!  It is much more reliable! Also, check the MD5sum.

---

### Post by kurt18947 on 2013-04-02
The CD/DVD drives I've used - a several years old Phillips IDE and Samsung USB both 'just work' with Brasero or k3b.  I don't know that you could burn an Ubuntu CD/DVD from a live session though I've never tried it.  Do you have an installed O.S, Ubuntu or Windows.?  You can use Windows to create a live CD/USB.  If you don't have burning software, Imgburn for Windows is often mentioned.  Another option if your subject machine supports USB booting would be a live USB.  Live USBs have some benefits over CD's, better speed and you can enable persistence on a liveUSB, no persistence with a CD/DVD.  To create a bootable USB install, I use Unetbootin.  Unetbootin is available for linux & Windows.  There is also a utility in Ubuntu called "startup disk creator".  Again, I don't know if that will work from other than an existing Ubuntu installation.

---

### Post by coldraven on 2013-04-02
Like kurt18947 I just install from a USB stick or a SD card.
Unetbootin works every time, but remember to empty the stick first.

---

### Post by bashhimup on 2013-04-02
Either get an DVD+RW, or get a 8 or 16 gb usb memory stick.

---

### Post by nerdtron on 2013-04-02
> **coldraven said:**
> Like kurt18947 I just install from a USB stick or a SD card.
Unetbootin works every time, but remember to empty the stick first.

This one is my tried and tested method.

When it comes to burning disks, any disk will do just fine as long as the ISO fits.
But ALWAYS remember to burn using the SLOWEST speed your disk or burner support.

---

### Post by fosbinder on 2013-04-03
ok.. well I have a working XP Pro PC here and im trying to make a disk for my laptop that cannot boot from usb and is without a working OS atm hence the need for a disk and the question ..Resources I have: the downloaded ISO's for 12.10 and 12.04 , Deamon Tools Pro and a writer drive that can write toDVD+R, DVD+RW, CD-R, CD-RW format disks..(Note: Uknown issue is preventing Demon from closing the disk when writing to CD-R)
 and CD-R disks

---

### Post by nerdtron on 2013-04-04
> **fosbinder said:**
> ok.. well I have a working XP Pro PC here and im trying to make a disk for my laptop that cannot boot from usb and is without a working OS atm hence the need for a disk and the question ..Resources I have: the downloaded ISO's for 12.10 and 12.04 , Deamon Tools Pro and a writer drive that can write toDVD+R, DVD+RW, CD-R, CD-RW format disks..(Note: Uknown issue is preventing Demon from closing the disk when writing to CD-R)
 and CD-R disks

From my experience when this type of error happens on a CD-R, you can no longer use it again, ever. So try using DVD+RW or CD+RW and try other programs other than Daemon Tools. There are a lot of great free apps that can burn ISO to disk like this one [http://www.freeisoburner.com/](http://www.freeisoburner.com/)

Hope that helps.

---

### Post by Slim Odds on 2013-04-04
> **d0006 said:**
> <cut>

ALWAYS burn a distro at the SLOWEST speed your device supports!  It is much more reliable! Also, check the MD5sum.
Myth police here. STOP perpetuating this myth! This has not been true for at least 10 years!

[http://www.digitalfaq.com/guides/media/dvd-media-concepts.htm](http://www.digitalfaq.com/guides/media/dvd-media-concepts.htm)

You will most certainly get WORSE result burning at the SLOWEST speed! Fact!

Maybe not at MAXIMUM speed, but definitely NOT as SLOWEST speed.

Do you own search for "slowest burn speed myth" or something similar. A little research will show that slowest speed is actually bad!

---

### Post by mamamia88 on 2013-04-04
I always just use dd on flash drives.  Much faster IMO.  dd if=pathtoiso of=/dev/sd(your flash drive letter)

---

