---
title: "Vista doesn't boot anymore"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by KIAaze on 2008-06-14
Hi,

I wanted to install Ubuntu on my cousin's computer.

However, after testing the Ubuntu Live-CD, I can't reboot into Vista anymore, altough I haven't even installed Ubuntu yet. :(

What happens it that it keeps loading (Vista) for a very long time and then reboots.

I had a look at the boot sector (which I got using the dd command) with khexedit on my own PC and saw this in it:
> A disk read error occured. Bootmgr is missing. Bootmgr is compressed. Press ctrl+alt+del to restart.


When I tested the live-CD, I tried the "sleep" function to see if it works.
The PC apparently went to sleep, but I couldn't wake it up, so I wanted to reset it. Since there was no reset button and keeping the power button pressed didn't reset it (actually it did, but it seems I didn't press it hard enough), I just switched the power switch on the back off an on again.

My guess is that this is what corrupted the boot sectors, but I'm not sure.

I tried using the Vista DVD to repair it, but it didn't change anything.
Note: The Vista DVD I have is one provided by the manufacturer (Medion) and it's Vista Home premium, so maybe it doesn't offer all the repair options. For instance, I couldn't find a "recovery console".

Booting from the Ubuntu CD still works, so I was thinking about installing Ubuntu in dual-boot and then booting through GRUB.
Would that work? or would it just try to use the broken Vista boot sector?

Does anybody know how to fix the Vista boot sector or run fsck (or chkdsk) on the Vista partition?

I attached the MBR backups I made using the dd command, as well as ouputs of df, fdisk and lspci.
The PC actually already had two partitions: one called BOOT in NTFS and one called RECOVERY in FAT32.

---

### Post by rraj.be on 2008-06-14
Just your bootmgr is screwed up.

Use vista installation disc to clear it by repair.

---

### Post by KIAaze on 2008-06-14
I already tried the repair function from the Vista disc, but it didn't work.
Apparently there's a way to access a recovery console, but I didn't see how.

Right now, I'm backing up all the data using the Ubuntu Live-CD.
Then I'll try the Vista disc again.

---

### Post by rraj.be on 2008-06-14
Ok ..

Thats the better idea.Backup and try repair or reinstalation.

---

### Post by meierfra. on 2008-06-14
> Booting from the Ubuntu CD still works, so I was thinking about installing Ubuntu in dual-boot and then booting through GRUB.

No. Grub does not boot Vista on its own. It just tells the Vista boot loader to take over the booting.

> 
or would it just try to use the broken Vista boot sector?

Yes

---

### Post by meierfra. on 2008-06-14
Give this a try:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

---

### Post by KIAaze on 2008-06-14
Thanks very much for that link.
Now I at least have access to the different repair options.

I made a system restore, but it still doesn't boot. I suppose system restore doesn't repair the MBR.

Currently, I'm trying the "Step Three: Manually Repairing the Vista Bootloader", but I have a big problem:
There's no bootsect.exe on the CD. :(

I feel this is more a Vista problem than an Ubuntu problem, altough it started out with me wanting to install Ubuntu.

edit:
I did find this: [http://www.vistabootpro.org/index-changelog.php](http://www.vistabootpro.org/index-changelog.php)
which is said to have bootsect.exe, but how do you run an .exe if windows doesn't work?... :/

---

### Post by meierfra. on 2008-06-14
> There's no bootsect.exe on the CD.

Are you using you own cd or did you use the [cd from the EasyBcd site]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by KIAaze on 2008-06-14
I used the ones I downloaded from the site.
However, I made a discovery: to access all the recovery options from the "original" Vista DVD, I just have to deselect everything before clicking next in the window asking which partition to fix.
Then it starts the repair menu.
(I actually also used isomaster to add bootsect.exe to the iso I downloaded, but now that I know how to use the real DVD, I don't need it. ^^)

However, step 3 from [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD) didn't work, so I'm moving on to the "nuclear holocaust"...

---

### Post by KIAaze on 2008-06-14
...
Vista loading bar and then black screen... :/

---

### Post by meierfra. on 2008-06-14
Did you try running  "chkdsk"

---

### Post by KIAaze on 2008-06-15
Yes, I ran it with:
chkdsk c: /f /r

Apparently it found bad sectors and fixed them.
Then when I rebooted, I could boot into safe-mode.
I finished backing up data, but after rebooting again, it just loaded endlessly again (i.e. more than 10 minutes).

I did find out something strange however:
I used the Live-CD again and copied the MBRs from BOOT and RECOVER again and only the RECOVER MBR seems to have changed with all the things I tried in the recovery console (including the "nuclear holocaust method").

But the MBR of the RECOVER partition still contains a message about missing bootmgr when viewed with hexdump.

Another thing is that now, when I launch the partition editor, it puts an exclamation point next to the NTFS partition and doesn't show how much space is used on it. The info message suggested using ntfsclone --rescue.
Will I need an external hard disk with the same size to use this or does it create a compressed copy?
It's a 500 GB disk with about 100 GB used after all.

Worst case scenario would be broken HD, but before that I'll try a full system recovery. :(

P.S: Is there a way to remove the Vista splashscreen and see what Vista is doing?
Because maybe it is doing something when loading endlessly, I don't know. :/

---

### Post by KIAaze on 2008-06-15
Ok, I gave up and used the system recovery disk. The data was backup up so it's not that bad, except that a lot of things need to be reconfigured an reinstalled. :/

If I want to install Ubuntu, should I use 32-bit or 64-bit?
Both Live-CDs worked, but I heard some things don't work with 64-bit.

---

### Post by meierfra. on 2008-06-15
> I gave up and used the system recovery disk. 

Yes, it  looked like that was your only option left.

> If I want to install Ubuntu, should I use 32-bit or 64-bit?
Don't really know, but the opinion I have seen most:

 The 64-bit kernel causes some problems and  only gives a slight improvement in performance.  So if optimal performances  is important to you, go for the 64-bit kernel. Otherwise choose the 32 bit.

---

