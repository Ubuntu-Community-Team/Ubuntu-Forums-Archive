---
title: "External drive - WD My Passport - index error prevent mount?"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by Michele42 on 2012-11-05
Hello! Ubuntu Newbie here. 

Yesterday I mounted my WD My Passport hard drive with no problem. Then I reinstalled Ubuntu from scratch today (spending too long trying to get rid of lastfm - long story)
and now the drive won't mount. 

I get this:

 Error mounting /dev/sdb1 at /media/michele/My Passport: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/michele/My Passport"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $AttrDef, unexpected length (-1 != 2560).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

So I changed laptop and used Win7 - where the drive works fine - and tried to run chkdsk from the cmd prompt. It got stuck at stage 2 of 5 10% and told me:

correcting error in index $130 for file 1565
correcting error in index $130 for file 1565
Sorting out index $130 in file 1565 

and then went back to giving me the C: \users\ computer name > command line. And that's it. 

Is there any way I can fix this without having to reformat the drive, as I don't have enough space to save the files on my Win7 laptop? 

Win7 tells me the disc is 'healthy'. Yeah, right. 

Many thanks for taking the time to reply.

Edited to ask: I haven't tried a force mount yet because I'm not sure what line of command to use.

---

### Post by arpanaut on 2012-11-05
Are you sure that you ran the "chkdsk /f" on the external drive and not just the "C" system drive?

---

### Post by Michele42 on 2012-11-05
> **arpanaut said:**
> Are you sure that you ran the "chkdsk /f" on the external drive and not just the "C" system drive?

Yes. I did chkdsk f:/r

---

### Post by Michele42 on 2012-11-06
*bump* 

No solutions then?

---

### Post by Bashing-om on 2012-11-06
I am unclear of your present goal. Re-install windows? Ubuntu stand-alone ? Dual boot?
Do you presently have a stable operating system ?
In any event what does GParted (from liveCD) report ?
[INDENT]willing to help ==> BDQ

[/INDENT]

---

