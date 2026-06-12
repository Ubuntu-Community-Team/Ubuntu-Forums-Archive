---
title: "Ubuntu 64 bit installation"
date: 2018-10-05
forum: New to Ubuntu
---

### Post by alex-bingham on 2018-10-05
Please excuse me if I say something stupid, but I currently have the 32 bit version of Ubuntu 18.04 loaded alongside Windows 10 on my laptop.  I have checked my hardware and I understand I should be able to run the 64 bit version.  How can I upgrade to the 64 bit version from my current set up?

Many thanks

Alex

---

### Post by jimmy-frydkaer on 2018-10-05
To upgrade to 64 bit you need a clean install with a 64 bit iso

---

### Post by Autodave on 2018-10-05
Get the 64 bit version and boot to it.  When you get to the screen that asks you what you want to do, just choose to replace 18.04 with 18.04.

---

### Post by alex-bingham on 2018-10-05
Does that mean the Windows 10 partition will remain in place?

---

### Post by oldfred on 2018-10-05
To be sure, always best to use Something Else.
If you do not have Windows fast start up off, or if Windows needs chkdsk or has other issues, it make not be seen in Ubuntu installer.

Also make good backups both Windows & Ubuntu, particularly /home. You may want /etc, if you made multiple changes to system. I backup grub, network and a few others I manually edit. Also if you installed lots of applications, best to export list, so you can easily reinstall those applications. Otherwise you have to manually add those.

If you have 32 bit, is system booting in BIOS mode, not UEFI mode? Systems with pre-installed Windows 10 are UEFI with gpt partitioning.

---

### Post by alex-bingham on 2018-10-06
Thanks for the great advice. The laptop originally came with Windows 7 so I guess is still BIOS. To be honest I rarely use Windows but not all manufacturers seem to provide Ubuntu compatible versions of their software e.g. Garmin. Therefore the Windows requirement.

---

### Post by Autodave on 2018-10-06
Garmin is the ONLY reason that I still have a Windows machine.  And every time I boot it up to update the Garmin, it takes Windows a couple hours to update.  Sigh.

---

