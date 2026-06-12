---
title: "Can't get software to install"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by morrisasaurus on 2012-04-26
I recently installed ubuntu on my system, and upon attempting to download software (ie. gimp and skype), i receive this message:


CD/DVD 'Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.


I put in the installation disc and it still didn't work.

Everything else seems to be working fine, except for the software center.
Any ideas on how to fix this?

---

### Post by plucky on 2012-04-27
> **morrisasaurus said:**
> I recently installed ubuntu on my system, and upon attempting to download software (ie. gimp and skype), i receive this message:


CD/DVD 'Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.


I put in the installation disc and it still didn't work.

Everything else seems to be working fine, except for the software center.
Any ideas on how to fix this?

Open "Software Sources" and un-tick the CDrom as a source,as you don't need it.Then either reload or run from a terminal ```
sudo apt-get update
```


Good Luck

---

### Post by morrisasaurus on 2012-04-27
Awesome it worked :D. Thanks

---

### Post by plucky on 2012-04-27
> **morrisasaurus said:**
> Awesome it worked :D. Thanks

Please mark the Thread as **[Solved]** using [color=red]Thread Tools[/color] at the top of the page.

Good Luck

---

