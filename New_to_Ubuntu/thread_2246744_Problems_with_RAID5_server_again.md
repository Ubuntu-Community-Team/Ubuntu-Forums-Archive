---
title: "Problems with RAID5 server again"
date: 2014-10-03
forum: New to Ubuntu
---

### Post by pathos_society on 2014-10-03
Hi, everyone.  So, last year, [I posted this thread](http://ubuntuforums.org/showthread.php?t=2141880) detailing my troubles with my 4x2TB RAID5 Ubuntu server.  I got everything up and running at the time, but the age of the disks seemed to indicate they wouldn't be working for very long.  In fact, one person specifically named which disk (/dev/sde) would be the one to fail.

Well, everything stayed together for about a year and a half.

Today, I tried to start my server, and everything came up, but now the RAID is listed as "DEGRADED."

Three of the disks are showing "HEALTHY" under SMART status, one (and of course it's the aforementioned /dev/sde) is showing "Not Supported" under SMART status and "Unknown Scheme" (instead of "Master Boot Record") under Partitioning. "Edit components" under the RAID specifically names this disk as "FAULTY."

I'm running badblocks on that disk right now (which is taking forever, seeing as the disk is 2TB).  Anything else I can/should do to test the disk and make sure it's kaput?

---

### Post by tgalati4 on 2014-10-03
Burn a copy of Ultimate Boot CD and use the manufacturer's utility to run diagnostics on the drive.  You may get some information about which part of the drive failed.

If you are able to recover the RAID with a new disk, then you can try a low-level format on the bad drive to revive it.  If you do revive it, then put it in a USB enclosure and use it for camera/SD card backup or some other periodic use.

---

### Post by bab1 on 2014-10-03
> **tgalati4 said:**
> Burn a copy of Ultimate Boot CD and use the manufacturer's utility to run diagnostics on the drive.  You may get some information about which part of the drive failed.

If you are able to recover the RAID with a new disk, then you can try a low-level format on the bad drive to revive it.  If you do revive it, then put it in a USB enclosure and use it for camera/SD card backup or some other periodic use.

Note that you should never attempt to truly "low level format" any IDE or SATA HDD.  The term "low level format" is now used to mean ***full erase*** (the filling the drive with all zeros).  See [here]("http://knowledge.seagate.com/articles/en_US/FAQ/203931en") and [here]("http://wdc.custhelp.com/app/answers/detail/a_id/1211/p/227,294/session/L3RpbWUvMTQxMjMyMjM5Mi9zaWQvWWUybmxXM20=") for more information.

i personally have not done this type of "full erase".  If you can fill the drive with all zeros (data) then the drive is not bad.  Kind of a long winded test in my opinion.  I've never had any problems with  any of the drives I have re-purposed.  You should however, check that the drive is fully functional using S.M.A.R.T hard drive tools before putting it back in use.

---

### Post by tgalati4 on 2014-10-03
I have revived a few IDE drives with low-level formats.  I have not attempted any SATA drives.  I don't know exactly what happens during a low-level format.  I suspect that timing marks are put on the disk to help guide the heads.  With an older drive and worn arm mechanisms, the timing marks don't correspond with the head location so you get read and write errors.  Low-level formats can restore function by putting new timing marks that the worn arm can follow.  Now if there are other mechanical or electrical problems, a low-level format will either fail or the drive will work for a while and then fail again.

I only recommend a low-level format if standard methods fail:  deleting old partitions, creating new partions, making new filesystems on the new partitions, and installing software or copying data.  If any of those steps fail on an older, problematic drive, then a low-level format might revive the drive.

---

### Post by bab1 on 2014-10-03
> **tgalati4 said:**
> I have revived a few IDE drives with low-level formats.  I have not attempted any SATA drives.  I don't know exactly what happens during a low-level format.  I suspect that timing marks are put on the disk to help guide the heads.  With an older drive and worn arm mechanisms, the timing marks don't correspond with the head location so you get read and write errors.  Low-level formats can restore function by putting new timing marks that the worn arm can follow.  Now if there are other mechanical or electrical problems, a low-level format will either fail or the drive will work for a while and then fail again.

I only recommend a low-level format if standard methods fail:  deleting old partitions, creating new partions, making new filesystems on the new partitions, and installing software or copying data.  If any of those steps fail on an older, problematic drive, then a low-level format might revive the drive.

I wouldn't even attempt to do a true LLF on a modern ( < 10 years old ) HDD.  From SpinRite's web page:> 
[COLOR="#0000FF"]***No software of any sort can truly low-level format today's modern drives.**The ability to low-level format hard drives was lost back in the early 1990's when disc surfaces began incorporating factory written "embedded servo data". *[/COLOR]


The disk density on modern drives is such that the heads don't really drift that much and there is error correcting firmware on board in the Integrated Drive Electronics (IDE).  So in short, I say; a true LLF cannot be performed by a modern drive.  The servo data, cylinder and sectors are written onto the platters by a special machine called a servo-writer before they are assembled into drives.  You do not want to change that.

That being said.  It might be fun to take a truly junked drive and try a LLF on it.  But the user should know and understand what they are doing.  In any event (LLF or zeroing out a drive) you will loose all data.

---

