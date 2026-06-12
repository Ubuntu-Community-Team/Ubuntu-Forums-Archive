---
title: "Ubuntu does not boot."
date: 2012-04-12
forum: New to Ubuntu
---

### Post by faitswulff on 2012-04-12
Just installed Ubuntu. Fiddled with rvm and installed ruby 1.9.3. Then I updated using the system package updater and restarted. I think it was when I hibernated that everything imploded.

As it stands, it gets to the boot screen, plays the startup sound, which loops erroneously before completely freezing.

I'm a complete linux noob. Any suggestions would be appreciated.

Thanks!

---

### Post by kc1di on 2012-04-12
sounds like it was updating when it hibernated not good. 

It would help others to know which version of ubuntu your using.

try this first. if you can get to the login screen click on the little ubuntu logo in the upper left of the password box click ubuntu 2d see if it lets you in to that. 
if it does let us know.

---

### Post by faitswulff on 2012-04-12
Crap. Login normally brings me straight to the desktop. I can get to command line as root through the recovery version?

Also, it's Ubuntu 11.10. x64, I think.

---

### Post by roelforg on 2012-04-12
> **faitswulff said:**
> Crap. Login normally brings me straight to the desktop. I can get to command line as root through the recovery version?

Also, it's Ubuntu 11.10. x64, I think.
Yes
and
unity-2d is a fallback incase normal unity failes

---

### Post by faitswulff on 2012-04-12
Okay, so from recovery command line, what do I do?

---

### Post by jjpcexpert on 2012-04-12
> **faitswulff said:**
> Just installed Ubuntu. Fiddled with rvm and installed ruby 1.9.3. Then I updated using the system package updater and restarted. I think it was when I hibernated that everything imploded.

As it stands, it gets to the boot screen, plays the startup sound, which loops erroneously before completely freezing.

I'm a complete linux noob. Any suggestions would be appreciated.

Thanks!

It would help if you posted everything you can from /var/log/* - censoring any personal details if at all possible. On pastebin or in attachments, of course.

---

### Post by faitswulff on 2012-04-12
How do I do that without a GUI? :confused:

---

### Post by kc1di on 2012-04-12
> **faitswulff said:**
> Okay, so from recovery command line, what do I do?

if you can get to the recovery teminal type the following one line at a time.

```
sudo apt-get autoclean

sudo apt-get update

sudo apt-get upgrade

```
if that fails
try this one

```
sudo dpkg --configure -a
```

---

### Post by faitswulff on 2012-04-13
^Couldn't get any of those to work. "Read only, no access to ../vars/" and dpkg gave me a similar response. But for some reason, everything works now, but I didn't do anything.

I ran fsck a few times from the recovery console and it would complain about something being in the future. Maybe I'm in the future now D:

It's a stretch since I don't even know what went wrong, but how do I prevent this from happening again? Definitely not using hibernate anymore.

---

### Post by mastablasta on 2012-04-13
do you have a large enough swap partitions?

---

### Post by faitswulff on 2012-04-13
The disk utility says that the swap file partition is 1.9GB. Big enough?

---

### Post by 0011235813 on 2012-04-13
> **faitswulff said:**
> The disk utility says that the swap file partition is 1.9GB. Big enough?

How much RAM do you have? Click on System Settings, go to System Info, and tell us. If the swap is less than the RAM, then indeed hibernate would not work. Also, have you encrypted your /home directory? That would mean the swap is also encrypted and thus hibernate would not work.

PS: I'm not surprised Ubuntu fixed itself, something similar happened to me once, where half my hardware stopped working and when I went into recovery and booted again, everything went fine. Sometimes I think Ubuntu has a mind of it's own!

---

### Post by faitswulff on 2012-04-15
Well, it's back again.

I tried looking into the errors in depth:

fsck would "terminate with error 3"

Kidc1's suggestions resulted in terminal telling me that the files didn't exist.

Aftergoogling the error "superblock last mount time occurs in the future" it seems to be a problem with the hardware/bios clock.

Sorry for lack of exact quotes, this is written from my phone.

---

### Post by faitswulff on 2012-04-15
Also, I have 1GB of RAM. So hibernate should theoretically be fine.

---

