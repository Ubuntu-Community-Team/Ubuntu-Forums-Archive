---
title: "Ubuntu 12.04 crash after cleaning computer ..."
date: 2013-02-11
forum: New to Ubuntu
---

### Post by somethis on 2013-02-11
Cleaned my computer carefully with aerosol and now it **crashes right after loging in**.

How can I **rule out if it's a hardware damage?**  If it isn't I could at least try reinstalling. Any suggestions on how to proceed?

Here is the **link to the logfile of Boot-Repair** - which I tried without success:

[http://paste.ubuntu.com/1630291/](http://paste.ubuntu.com/1630291/)


**Details**
Ubuntu will boot fine up to the login screen. Then - after I enter the password and hit login - it will hang. I am not able to enter anything at the resulting screen (see attachment)

Running memtest86 from the boot-up program resulted in 0 errors found.  Neither, did a check on the harddrives yield an error message.

---

### Post by mansonfan78 on 2013-02-11
It's possible you loosened a connection somewhere, I'd start by checking to make sure everything is securely attached.

---

### Post by stoogiebuncho on 2013-02-11
Have you tried booting a live CD or USB to see if that will load?

---

### Post by offgridguy on 2013-02-11
> **stoogiebuncho said:**
> Have you tried booting a live CD or USB to see if that will load?
+1, unfortunately unable to read screenshot.

---

### Post by somethis on 2013-02-12
Yes, Stoogie, that is from where I launched memtest86 - resulting in 0 errors found - as well as a check on the harddrives.  The live CD will boot without a problem.

> **stoogiebuncho said:**
> Have you tried booting a live CD or USB to see if that will load?

---

### Post by stoogiebuncho on 2013-02-12
Well, if it was me I'd try a reinstall next.  If you can save your home folder (including the hidden files), or if you have your home folder in a seperate partition, a reinstall doesn't take too much work.

Having said that, the fact that this happened right after you cleaned the computer does suggest a hardware problem... but reinstalling doesn't take that long and seeing as all your checks passed, it might be the logical next step.

---

### Post by matt_symes on 2013-02-12
Hi  

Can you boot into an older kernel ?

Kind regards

---

### Post by tgalati4 on 2013-02-12
Open up the machine and use compressed air--75 psi and really clean it out.  The cans just move the dirt around.

---

### Post by somethis on 2013-02-14
Matt, that worked!  I've gotten back into my system with full functionalty. :D

Had to go back to a kernel as low as 2.6.x, though.  I won't reinstall for now but if I notice unusual behavior I will.  Now, is a good time to run a backup on /home.

(an explanation on how to boot into an older kernel is here:
[http://askubuntu.com/questions/97731/ubuntu-keeps-crashing](http://askubuntu.com/questions/97731/ubuntu-keeps-crashing) )

Thank you!


> **matt_symes said:**
> Hi  
Can you boot into an older kernel ?
Kind regards

---

