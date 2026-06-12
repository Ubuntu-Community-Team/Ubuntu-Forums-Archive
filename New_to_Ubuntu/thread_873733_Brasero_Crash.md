---
title: "Brasero Crash"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-07-29
I'm trying to  burn my music collection to DVD using Brasero, but Brasero keeps crashing.  It creates a checksum for the disk and when it starts to actually burn, Brasero crashes.  Any ideas what is causing this?  Or what other programs out there will burn data DVDs?

---

### Post by Sef on 2008-07-29
> Or what other programs out there will burn data DVDs?

I use GnomeBaker.  It is available from the respositories.

---

### Post by dca on 2008-07-29
Verify write speed, if it's still within range you should still drop it down a little from there.  Start small, 4x write speed or something...

---

### Post by subaruwrc01 on 2008-07-29
Gnome Baker isn't working either,  but at least I get output.

```
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p Ryan Spicer -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-ryan/gnomebaker-V1NLEU | builtin_dd of=/dev/sr1 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using APOCALYPTICA_AMPLIFIED_A000.JPG;1 for  Amplified/Apocalyptica-Amplified(ADecadeOfReinventingTheCello)(HQ)-Back.jpg (Apocalyptica-Amplified(ADecadeOfReinventingTheCello)(HQ)-Front.jpg)
/dev/sr1: "Current Write Speed" is 6.6x1352KBps.
:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error

```

---

### Post by Bobrm2 on 2008-11-16
Having exactly the same problem. Attempting to backup Thunderbird (.Mozilla/thunderbird). Invoking Brasero requesting a "data" burn: should it be an "image" burn? Set disk size to 700, data is 254 MB in size.

Disks show no content; however the files I wish to copy are in "TMP". i.e. a inserted blank disk invokes Brasero. Now the "Space" bar is red in Brasero is all red indicating (?). There should be plenty of space left on the "blank" disk.

Must be leaving a step out. Your help appreciated.

Bob

---

### Post by anc2020 on 2008-12-03
Same problem here.

I've got a relatively fresh install of 64bit Ubuntu 8.10 on a quad core.

Both Brasero and GnomeBaker appear to start up okay, but both crash if I click on "Audion cd".

---

### Post by Orfintain on 2008-12-17
Brasero crashes sometimes on open and sometimes it makes it too the point where I add pick out songs for an audio CD but I have not be able to start a project.

Edit - I installed gnomebaker and it is doing the same thing

Edit 2 - I fixed k3b by install the extra packages (which means I don't need either of the other two problematic ones)

sudo apt-get install libk3b2-extracodecs

---

### Post by raydar on 2009-01-06
Same problem here: Brasero creates checksum and then just exits without any message.  

I see other people here trying other apps, and some say it helps, others that they do the same.  I guess I'll try & find out.

---

### Post by theozzlives on 2009-01-06
> **subaruwrc01 said:**
> I'm trying to  burn my music collection to DVD using Brasero, but Brasero keeps crashing.  It creates a checksum for the disk and when it starts to actually burn, Brasero crashes.  Any ideas what is causing this?  Or what other programs out there will burn data DVDs?

I took off Brasero and installed Nero Linux. Not free but works great.

---

### Post by raydar on 2009-01-06
I installed K3b, and rather than diligently testing it before installing libk3b2-extracodecs I went ahead and installed that too.  Burn was successful.  I don't like not understanding why it worked, but I'm glad it worked!  (Thanks, Orfintain)

---

### Post by cozmicharlie on 2009-01-06
This is a bug in Brasero and I recall it has something to do with the temp file it is trying to access.  I believe their is a fix but I don't remember exactly where I found it (a forum search should come up with something).  I fixed my problem by installing k3b as others have suggested.  IMHO, k3b is better than Brasero anyways.

---

### Post by jocheem67 on 2009-01-06
I use k3b instead of brasero too, due to crashing/instability....

However there's also the built-in burn-engine in ubuntu. Often that just suits my needs. It's very straightforward.

I don't see the need to use nero, k3b has the same specs. and maybe more....

---

### Post by cozmicharlie on 2009-01-07
> **jocheem67 said:**
> 
i don't see the need to use nero, k3b has the same specs. And maybe more....

+1

---

