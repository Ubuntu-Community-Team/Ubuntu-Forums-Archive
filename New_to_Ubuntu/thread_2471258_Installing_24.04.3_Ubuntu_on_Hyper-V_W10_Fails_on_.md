---
title: "Installing 24.04.3 Ubuntu on Hyper-V W10: Fails on first boot"
date: 2022-01-24
forum: New to Ubuntu
---

### Post by billvv on 2022-01-24
Installing 24.04.3 Ubuntu on Hyper-V W10, and pressing restart after   entering MOK key, the (console?) stops with messages like.. 'SQUASHFS   error: unable to read block xxxxxxxxx..  and later on... "Kernel panic - not synching' and 'systemd Tainted'
I've followed the steps at this   site for the installation steps:

[URL="https://dellwindowsreinstallationguide.com/ubuntu-20-04-lts-hyper-v/"]https://dellwindowsreinstallationguide.com/ubuntu-20-04-lts-hyper-v/
[/URL]
I've tried ^C, 'ENTER', etc. to leave the screen, but nothing works.

Looking for next steps.

Thanks!

---

### Post by MAFoElffen on 2022-01-24
You are overthinking this...

Capturing some screen shots to post for you... Will post back very soon.

EDIT:
Here goes. 
Run down summary: Create a Generation 2 Vm Guest. That tutorial is fairly complete on that. Remember that before booting it intially to install hte OS, to go to the VM's Machine Settings > Security; Ensure that SecureBoot" is enabled, enable TPM. Change certificates style to "Microsoft Certificates" (Windows style is it's default).

Boot Guest and install. When it gets to the Screen that wants you to enter a password for SecureBoot, Make one up. That is not really a SecureBoot thing, but a requirement for 'mokutil' to be able to enroll the MOK key later... Continue to install...

On the reboot, yes you have to enroll the MOK key at that screen. When it gets to "View Key 0" or "Continue"... I usually select View first to insure a valid key was generated. Then hit enter at that screen... Then continue. At the next screen, yes... Then enter the mokutil Password that you made up in the installation phase... Enter. Select Reboot.

That sums up the configuration of the guest machine and installing beyond what it normal.

Here is what my guest looks like from the UbuntuForums 'system-info' script:
[https://paste.ubuntu.com/p/MqKXpXgvQF/](https://paste.ubuntu.com/p/MqKXpXgvQF/)

On your error... If the error is that there is:
> 
'SQUASHFS   error: unable to read block xxxxxxxxx..  and later on... "Kernel panic - not synching' and 'systemd Tainted'

Then that is not a SecureBoot problem. That was a disk write problem during the installation. Ensure that the MD5Sum is good on the ISO you downloaded, then reinstall again.

On the version you have listed in your thread title... I think you had a typo. That would be 20.04.3 right? 22.04 doesn't get released until April of this year...

---

### Post by billvv on 2022-01-25
Thanks; I followed all of those steps several times; always with the error. I'll have to figure out how to check if the MDSSum is good. I don't have any problems with the disk writes for other software , unless it somehow writes to the SSD with too big of a file (64gb left on that one). 

On another note; it asks for a location for the Virtual Machine and for the Virtual Disk; I haven't been able to find out how big the Virtual Machine is to see if it will fit in the SSD; hoping that will speed things up. I select one of my 2tb drives for the Virtual disk. 

Yes, the title was a typo...

---

### Post by ActionParsnip on 2022-01-25
> **billvv said:**
> Thanks; I followed all of those steps several times; always with the error. I'll have to figure out how to check if the MDSSum is good. I don't have any problems with the disk writes for other software , unless it somehow writes to the SSD with too big of a file (64gb left on that one). 

On another note; it asks for a location for the Virtual Machine and for the Virtual Disk; I haven't been able to find out how big the Virtual Machine is to see if it will fit in the SSD; hoping that will speed things up. I select one of my 2tb drives for the Virtual disk. 

Yes, the title was a typo...
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

---

### Post by billvv on 2022-01-25
> **ActionParsnip said:**
> [https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

I have to have have linux installed before I can run linux commands. Ubuntu on Hyper-V on a W10 PC was my goal.

---

