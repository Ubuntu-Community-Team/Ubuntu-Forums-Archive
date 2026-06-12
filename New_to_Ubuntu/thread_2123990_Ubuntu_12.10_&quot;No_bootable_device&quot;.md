---
title: "Ubuntu 12.10 &quot;No bootable device&quot;"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by olddognewtrix on 2013-03-09
I might have done something similar. 
I have an old Dell Inspiron laptop that runs on Vista and XP
1. Went online and burned a copy of Ubuntu 12.10 to disk
2. Put in the disk and ran it. 
3. When done, I had two operating systems to choose from at boot, Windows and Ubuntu. 
4. I tested Ubuntu and it worked. Admittedly I did not test Vista to make sure still working. 
5. Used terminal to tell Ubuntu OS manager to ditch Vista and XP. 
6. Restarted computer, got message that there is no bootable device. 
7. Got into BIOS settings, set up boot sequence to start with Cd drive
8. Tried to boot from Ubuntu cd again and this time failed
9. Took out an old Windows 7 disk that was originally for our Dell tower, tried that, and the Inspiron booted up!

What should I try next?  I have no interest in returning windows to that particular machine - want it to be the Linux machine but I will if that is what it takes to get Ubuntu running again. Receovering data is not an issue here - all data backed up externally.  Really just want Ubuntu running as nicely as possible, Windows or no Windows. 

Thanks!!!

---

### Post by grahammechanical on 2013-03-09
@olddognewtrix

It gets very complicated when two or more people are asking for individual help in the same thread. You did this:

> [COLOR=#000000]5. Used terminal to tell Ubuntu OS manager to ditch Vista and XP.[/COLOR]

Why did you not just use the Ubuntu CD to re-install telling the installer to Use the Entire disk (erasing contents)? You need to boot from Ubuntu CD. Fix that issue and you can re-install. For all we know you may have removed Ubuntu. You say this

> [COLOR=#000000]3. When done, I had two operating systems to choose from at boot, Windows and Ubuntu.[/COLOR] but then you say this:

> [COLOR=#000000]5. Used terminal to tell Ubuntu OS manager to ditch Vista and XP.[/COLOR] So, how many operating systems were on that disk? Two or three? And what Ubuntu OS manager are you talking about? You might be able to use this remix to fix your boot issues.

[https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix)

Look again in the BIOS settings. You are missing something.  Regards.

---

### Post by oldos2er on 2013-03-09
Posts moved to their own thread.

---

### Post by fiodev on 2013-03-09
I like using the live cd called "Super Grub Disk" boot into the kernel and reinstall grub from a terminal
or just reinstall over the ubuntu partition

---

### Post by oldfred on 2013-03-09
Some BIOS will not boot without a boot flag on a primary partition. Windows has to have a boot flag to boot, grub does not use the boot flag.
So if BIOS does not see boot flag it may report no bootable system, even if grub can boot. Check that you have a boot flag on any primary partition.

---

