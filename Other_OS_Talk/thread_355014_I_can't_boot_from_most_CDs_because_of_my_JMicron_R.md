---
title: "I can't boot from most CDs because of my JMicron RAID controller.. help!"
date: 2007-02-06
forum: Other OS Talk
---

### Post by presbp on 2007-02-06
There is apparently a known issue that the JMicron RAID controller does not work correctly unless the drivers are installed.  This JMicron controller controls my CD/DVD drives so I cannot boot a CD/DVD from them that don't have the drivers for the JMIcron installed.  

I think the Ubuntu LiveCD had them because I could run that but I have tried running Puppy Linux and LinuxFromScratch and no avail.  Is there a way to fix this that won't require alot of time and caffeine?  I would rather not have to purchase an external DVD/CD drive just to boot CDs/DVDs.  Also I have heard that USB external CD/DVD drives also have issues with booting and stuff.

---

### Post by RAV TUX on 2007-02-06
> **presbp said:**
> There is apparently a known issue that the JMicron RAID controller does not work correctly unless the drivers are installed.  This JMicron controller controls my CD/DVD drives so I cannot boot a CD/DVD from them that don't have the drivers for the JMIcron installed.  

I think the Ubuntu LiveCD had them because I could run that but I have tried running Puppy Linux and LinuxFromScratch and no avail.  Is there a way to fix this that won't require alot of time and caffeine?  I would rather not have to purchase an external DVD/CD drive just to boot CDs/DVDs.  Also I have heard that USB external CD/DVD drives also have issues with booting and stuff.
try going into your BIOS and turning RAID off...

---

### Post by presbp on 2007-02-07
I went into my BIOS and I don't think that turning RAID off is an option.  I can choose for the JMicron controller to run in IDE, RAID, or ACHI(I think) mode

---

### Post by RAV TUX on 2007-02-07
> **presbp said:**
> I went into my BIOS and I don't think that turning RAID off is an option.  I can choose for the JMicron controller to run in IDE, RAID, or ACHI(I think) modeIt should be an option

---

### Post by mips on 2007-02-07
> **RAV TUX said:**
> It should be an option

There are known issues with Jmicron though. Apparently you have to compile your own 2.6.19 kernel to sort the problems out.

---

### Post by RAV TUX on 2007-02-17
> **presbp said:**
> There is apparently a known issue that the JMicron RAID controller does not work correctly unless the drivers are installed.  This JMicron controller controls my CD/DVD drives so I cannot boot a CD/DVD from them that don't have the drivers for the JMIcron installed.  

I think the Ubuntu LiveCD had them because I could run that but I have tried running Puppy Linux and LinuxFromScratch and no avail.  Is there a way to fix this that won't require alot of time and caffeine?  I would rather not have to purchase an external DVD/CD drive just to boot CDs/DVDs.  Also I have heard that USB external CD/DVD drives also have issues with booting and stuff.reference this thread and see if it helps:

[http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)

---

