---
title: "WIndows 10 repair loop after dual booting Ubuntu 22.04"
date: 2022-05-28
forum: New to Ubuntu
---

### Post by melvinmelvin on 2022-05-28
Hi
I recently installed Ubuntu 22.04 alongside Windows 10 and am currently unable to boot into Windows. Immediately after installing Ubuntu, I swapped over to check on Windows. I had no issue loading in at first, but noticed some Windows apps would not open and others would just close. I restarted and that is where I was met with the repair loop that failed each time. I created a Windows repair USB and attempted to repair the startup, but failed. I also ran some quick, non-destructive commands like *bootrec /scanos* which could not find my Windows install.

While in Ubuntu I installed Boot-repair and ran the summary option
[https://pastebin.com/HiXvaPMC](https://pastebin.com/HiXvaPMC)

As suggested in the app, I am looking for help before attempting any repairs with Boot-repair. Any assistance would be greatly appreciated.

---

### Post by oldfred on 2022-05-28
You have an UEFI system with UEFI installs.
And have UEFI secure boot on.
But it looks like you must have booted Windows repair flash drive in BIOS mode (with Secure boot off) as now you have a Windows boot loader in MBR, which with UEFI should be blank.

Run Windows repairs again when repair flash drive booted in UEFI mode.
You may want to turn off UEFI Secure Boot.
Note Windows updates may have turned secure boot back on and also may have reverted other UEFI settings and turned Windows fast start up back on which needs to be off for dual booting.

---

### Post by melvinmelvin on 2022-05-28
> **oldfred said:**
> You have an UEFI system with UEFI installs.
And have UEFI secure boot on.
But it looks like you must have booted Windows repair flash drive in BIOS mode (with Secure boot off) as now you have a Windows boot loader in MBR, which with UEFI should be blank.

Run Windows repairs again when repair flash drive booted in UEFI mode.
You may want to turn off UEFI Secure Boot.
Note Windows updates may have turned secure boot back on and also may have reverted other UEFI settings and turned Windows fast start up back on which needs to be off for dual booting.

Thanks for the reply

I experimented with Pop_OS and ElementaryOS some time ago on the same machine, which may have something to do the MBR entry. Looks like I didn't do good job cleaning up after.


Dipped back in:

Disabled Secure Boot
Fast Start was disabled at some point in the past

With Windows repair, should I be using the Start Up repair or Recovery option? If the former, that failed again. Is there a way to access the SrtTrail.txt log from within Ubuntu? I imagine I'll have access with the command prompt and notepad in Windows

---

### Post by oldfred on 2022-05-28
Windows turns fast startup back on with updates. If still off you can mount NTFS partitions that are not hibernated.
Even if hibernated, you can mount but only as read only. You then have to manually mount it as all the auto mount try for read/write.

No need to erase MBR, and often using dd to erase it is more dangerous than just leaving it. But never try to boot in BIOS mode as then that grub will just fail.

---

### Post by melvinmelvin on 2022-06-01
> **oldfred said:**
> Windows turns fast startup back on with updates. If still off you can mount NTFS partitions that are not hibernated.
Even if hibernated, you can mount but only as read only. You then have to manually mount it as all the auto mount try for read/write.

No need to erase MBR, and often using dd to erase it is more dangerous than just leaving it. But never try to boot in BIOS mode as then that grub will just fail.

I was finally able to get back to this mess I made. The fast start/boot remained off from the last time I toggled it.

I never knew how easy it was to access Windows files from Ubuntu. It has made this ordeal less annoying and I'm now considering wiping the entire thing and starting anew. 

As for the srttrail log file... it doesn't seem to point to anything?
[https://pastebin.com/jehfSVfG](https://pastebin.com/jehfSVfG)

Thanks again

---

