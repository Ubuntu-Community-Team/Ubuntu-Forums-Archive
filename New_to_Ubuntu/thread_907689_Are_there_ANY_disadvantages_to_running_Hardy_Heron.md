---
title: "Are there ANY disadvantages to running Hardy Heron on windows?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Rukaru on 2008-09-01
It sounds so easy. I will mostly be using windows for my laptop I use for college(yes I know ubuntu is better), but I'd like to have ubuntu as well. I dual-boot ubuntu and XP on my desktop. On this, I'd like to try that new feature that lets you run ubuntu on windows like you'd run a program. I just want to know, are there ANY disadvantages at all to doing this? Related to security, usability, or anything? I just don't want grub on this computer so this would be a nice alternative. Can you still have compiz and all that? Once in ubuntu, is it exactly the same as you run it during a dual boot just without grub?

---

### Post by porchrat on 2008-09-01
I've never tried wubi (ubuntu running within windows) myself, but I've seen quite a few people with graphics problems.  Affects compiz and general performance.  Then again some people seem to get on fine as well...I'd say give it a try what have you got to lose.

---

### Post by Sef on 2008-09-01
> Then again some people seem to get on fine as well...I'd say give it a try what have you got to lose

Are you prepared to reset up XP is necessary?  **Back up** your data first before you do.  I set up wubi on my desktop, and it works ok with it.  I would suggest downloading the Live CD and using it for a while to see if Ubuntu works on your system and what, if any, problems you encounter.

Also check out the wubi forum.

---

### Post by Rukaru on 2008-09-01
> **Sef said:**
> Are you prepared to reset up XP is necessary?  **Back up** your data first before you do.  I set up wubi on my desktop, and it works ok with it.  I would suggest downloading the Live CD and using it for a while to see if Ubuntu works on your system and what, if any, problems you encounter.

Also check out the wubi forum.


It's a vista actually.  Is the live CD actually a safer alternative?  What could using Wubi do to windows if it just acts like a program?

---

### Post by porchrat on 2008-09-01
well he said he dual boots it currently so it must work on his system...he just wants to know about wubi issues I suppose he needs someone like yourself Sef with experience in wubi

---

### Post by Rukaru on 2008-09-01
> **porchrat said:**
> well he said he dual boots it currently so it must work on his system...he just wants to know about wubi issues I suppose he needs someone like yourself Sef with experience in wubi

No I want to run Wubi on my laptop I use for school.  I'm dual booting on my desktop, so it's a completely different machine.

---

### Post by mrsteveman1 on 2008-09-01
Wubi doesn't make Ubuntu run inside windows, it just lets you install Ubuntu without changing the partitions on the drive, and it puts an entry in the Windows boot menu for Ubuntu.

You still have to reboot to run Ubuntu and after that it runs normally, but root is loopmounted from a file on the Windows partition.

Once it is running everything should be the same except perhaps some amount of slower disk access, and wiki says hibernation won't work.

---

### Post by molochi on 2008-09-01
It sounds like you might want to try a VM setup. A virtual machine will allow you a measure of security in that linux isn't going to be infected by a compromised or hostile site or an emailed virus. However, Windows may still be connected to the internet, so external attacks (like worms and port probes) on your box could hit windows' defenses and vulnerabilities first. Also if you later intentionally expose windows to a file acquired through the VM you are exposing it to any threat that file poses.

As far as hardware support is concerned, a virtual machine is going to emulate a very basic video card in software and video performance is poor. I wouldn't bother with most games or even You Tube. VM's are useful for examining files or sites that might have malicious intent. They are useful for testing software under different OSs. A guest virtual machine is stored as a large file, that can be copied run on any machine. Also, an Ubuntu VM gives you access to its large library of software without affecting a host system's installation.

Microsoft VPC is a freebie so it's worth trying. Wikipedia lists a large number of VM programs

---

### Post by Bölvaður on 2008-09-01
I recommend Virtualbox

---

### Post by egalvan on 2008-09-01
> **Rukaru said:**
> I just don't want grub on this computer so this would be a nice alternative.

If it's just grub you want to keep off, then place it on a USB thumb drive.
 (grab that 'obsolete' 16megger your classmate threw in the trash)

Set your lappy to boot first from the USB, then the first hard drive.
If the thumb drive is installed on boot, grub will load...
if not, then the first drive will be booted.

No need to touch Vista, except to make room for an ubuntu extended partition.
 It won't be seen by Vista.

ErnestG

:popcorn:

---

### Post by ctswhole on 2008-09-01
I ran Ubuntu from Wubi on Vista and didn't notice any disadvantages.  They say that the disk performance is slightly inferior when using Wubi over a standard install (or dual-boot), but with that said I still didn't notice any differences.  Ubuntu ran great through Wubi, and when using Wubi I was able to navigate through the Vista filesystem when I was running Ubuntu.

---

### Post by Trav1s on 2008-09-01
I would also second a slight decrease in performance.  I used Wubi, installed Hardy on a separate partition on the same drive as XPPro.  My wife complained about boot time after the Wubi install.  Removed it and picked up some speed... However, the install/uninstall was painless.

---

