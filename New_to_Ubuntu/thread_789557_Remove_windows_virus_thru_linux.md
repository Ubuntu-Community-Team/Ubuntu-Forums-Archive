---
title: "Remove windows virus thru linux"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by thedrizz on 2008-05-10
So i got a bit of a virus problem in my windows. Its to the point where when i move anything it gets all flashy, and it wont let me install antivirus there. I was going to try and scan the windows partition thru ubuntu. Any reccomendations on how?

---

### Post by TooRight on 2008-05-10
I'm not sure about that, but when you have bad trojan problems that won't let ya install or run antivirus software (like AVG), that's when I used to use Avast! It's free and will work and run even when others can't. Try it and see... and don't forget to do your scanning in safe mode

---

### Post by tamoneya on 2008-05-10
im using clamAV which will detect windows viruses.  What I would do is mount my windows partition in linux and then scan it with clamAV. It should take care of any virus you have there.  avast should work as well for this as the above poster mentioned.

---

### Post by mister_pink on 2008-05-10
While those suggestions may work, I hate to say it but with that many problems you probably just want to reinstall. I'd certainly never want to do any internet banking or anything on there ever again, you never know whats got left behind.

---

### Post by thedrizz on 2008-05-10
> **tamoneya said:**
> im using clamAV which will detect windows viruses.  What I would do is mount my windows partition in linux and then scan it with clamAV. It should take care of any virus you have there.  avast should work as well for this as the above poster mentioned.

I was under the impression clam only detects viruses, not remove them

---

### Post by CREEPING DEATH on 2008-05-10
install Ubuntu, then AVG for Linux, then mount and scan the windoze drive.

CD

---

### Post by jsuydam5 on 2010-03-13
its seems like you could install [malwarebyte's anti-malware]("http://www.malwarebytes.org/") with [wine]("http://www.winehq.org/") and then scan your windows drive, malwarebyte's has saved me from many viruses :)
whoa... this thread is pretty old. well i guess if you still haven't fixed it then i hope this helps ;)

---

### Post by presence1960 on 2010-03-13
IMHO the only surefire way to remove malware from your machine is to format your affected partitions and reinstall.

If you don't want to do that I suggest scanning with a bootable CD from avira. You can update the definitions then scan. it will give you the locations of all detected malware. Download it [here]("http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html") and then create the bootable disk.

You can then remove all files listed.

---

### Post by spectralblue on 2010-03-13
> **thedrizz said:**
> So i got a bit of a virus problem in my windows. Its to the point where when i move anything it gets all flashy, and it wont let me install antivirus there. I was going to try and scan the windows partition thru ubuntu. Any reccomendations on how?

My experience with both commercial and free AV varies. But really, I would prefer just to backup the necessary files, do a scan on these backups (being aware that all AV's are prone to false positives), then reformat the drive and reinstall windows. That is the best, easiest, and fastest ways to clean a system.

Viruses sometimes mess with the registry and a lot of other things in windows. Most AV's are able to fix most of these changes by default, but some do get left out, and after a while, your system gets so slow and unresponsive because of these changes.

---

### Post by sdpiowa on 2010-03-13
Having cleaned many virus off of computers, here's my $0.02.

I typically run a rescue disk first (like Kaspersky).  Rescue disks are Linux distributions built specifically for virus removal.

[http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/](http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/)
[http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)
[http://acs.pandasoftware.com/soporte/safedisk32/safedisk32.zip](http://acs.pandasoftware.com/soporte/safedisk32/safedisk32.zip)

---

### Post by 3rdalbum on 2010-03-13
Maybe I'm just old-fashioned, but I always follow the procedure online about "How to remove xyz virus" by deleting registry keys and eventually the program executable. If necessary, using the Ubuntu live CD to delete the executable.

But if it was my own machine, I would reinstall Windows straight away - because sometimes you can forget that a computer has had a virus, and then you use your credit card online, and BAM identity theft.

---

### Post by redbook4574 on 2010-03-14
> **sdpiowa said:**
> Having cleaned many virus off of computers, here's my $0.02.

I typically run a rescue disk first (like Kaspersky).  Rescue disks are Linux distributions built specifically for virus removal.

[http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/](http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/)
[http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)
[http://acs.pandasoftware.com/soporte/safedisk32/safedisk32.zip](http://acs.pandasoftware.com/soporte/safedisk32/safedisk32.zip)

Several anti-virus/malware progs are available from unetbootin. These can be put on to a self booting usb stick.

---

### Post by LequidMetal on 2010-03-14
Portable ClamAV might help .
It does not require installation .

---

### Post by Tikkyca on 2010-03-14
AVG should do the trick.

---

### Post by Elfy on 2010-03-14
Closed - Op has not been back since 2008.

---

