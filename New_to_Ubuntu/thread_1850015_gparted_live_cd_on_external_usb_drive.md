---
title: "gparted live cd on external usb drive"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by mrtalkingbadger on 2011-09-25
Hi Guys,
i'm trying to partition my external usb drive using gparted to install the live image of gparted on it so i can partition my internal harddrive.

i get an error report about damaged sectors on my external drive telling me to chkdsk and reboot twice.
running chkdsk under windows is no problem but apparently the drive isn't checked on reboot the way it should be - most likely because it is an external drive windows doesn't use before login.
is there any way to run the procedure on command?
or any idea what else to try?

i appreciate every idea on how to go on

so long

---

### Post by MG&amp;TL on 2011-09-25
you can call CHKDSK manually from cmd.

See here:

[http://en.wikipedia.org/wiki/CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK")

Under "examples", close to the bottom.

---

### Post by BeRoot ReBoot on 2011-09-25
Gparted is included on the Ubuntu live-CD, you don't need to use a separate USB drive for a dedicated gparted distro.

---

### Post by mrtalkingbadger on 2011-09-25
@MG&TL:
i already did...several times, which took me around 3 days now -.-

i used the /r and the /f parameter. after the third time or so i also used /i and /c to save at least some time.
chkdsk runs as it should but it seems somethings got to happen on reboot since gparted advises to reboot "TWICE!".
i also read somewhere that the filesystem-checking-procedure after reboot is necessary so the changes are applied correctly, though i can't remember where i stumbled across this.
those simply are not run and i have a feeling they would if it was my internal drive.


@BeRoot ReBoot:
that should save me some time, although i have some issue with my burner as well.
i'm actually posting about right now. brasero just tells me i don't have enough space for a 100mb image on a 4,7gb dvd. same with a 2gb image.
otherwise i would have already burned a gparted livecd...
since i don't have an ubuntu live-cd with me i'll have to solve one of those issues first

thanks for the fast reply though :smile:

formating the drive won't repair the sector damage either if i'm not mistaken?

---

