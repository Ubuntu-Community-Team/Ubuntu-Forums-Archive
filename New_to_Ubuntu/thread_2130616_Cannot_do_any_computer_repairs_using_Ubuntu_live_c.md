---
title: "Cannot do any computer repairs using Ubuntu live cd"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by amvi on 2013-03-30
My son's Sony Vaio (Windows Vista) keeps relooping after windows updates..Computer was lost for over a year, so ton of updates..It stops at 28683/98320 C\Registry\Machine\Components\Derived Data..Also have a unexpected I/O error status 0xc00000e9 every now & then. Ive booted w/Ubuntu Live cd, but cannot fix anything with the terminal command prompts..Also cannot run scans from microsoft while booted in Ubuntu..I cannot boot into safe mode or any of the other options (just starts over, relooping again) I can get into BIOS, but still windows will not load.(relooping again).I can every now & then get into F10,(without Ubuntu) it will not accept any commands I type in. (NOEXECUTE=OPTIN) is whats there. I really need to do a chkdsk but cannot find anywhere that will allow me to type this in and it work. I do not have the Sony recovery cds. I have a windows vista start\up for my Gateway, but it doesnt work for this Sony Vaio VGN-AR605E laptop. 4 days now working on this. I would appreciate all help. Thank You very much.

---

### Post by ManamiVixen on 2013-03-30
First off, you need to realize Linux is not Windows. Anything and everything you know about Windows commands on the prompt, dump them in the trash. They will not work on Linux. If you want to fix Windows from the Linux Terminal, learn the Linux Command Line. Also, Ubuntu dosen't have tools to repair the Windows Registry and even then, there really aren't any tools that work well with NTFS partitions like what Windows Vista has. So you can't scan it or anything. You can't even resize NTFS partitions. Linux can really only Read Them and sometimes write.

If you want to repair Windows with a good, free, Rescue CD, Use this:
[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)
Be aware it is linux and will require learning the Linux Command Prompt. But it does have tools to handle Windows issues pretty well.

---

### Post by amvi on 2013-03-30
I do understand Linux is not windows. When I typed in sudo fdsk, it did tell me that this isnt Linux either..So, typed in ntfsfix /dev/sdc1 and it was some what reconized..and ntfsfix /dev/hda2..Yes, I would love to have the correct command prompts to just boot into my pc for repair. Is there a list of commands I can print to have on hand? Also, I am not a expert my no means at this, (aka, resizing partitions???) (honestly, I know nothing about commands, I just type in what forums say works) Thats what I need, tell me what to type in, or list of commands to print from another computer. I can follow directions very well. Thank you for your response and I will try that link.

---

### Post by carl4926 on 2013-03-30
> **amvi said:**
> My son's Sony Vaio (Windows Vista) keeps relooping after windows updates..Computer was lost for over a year, so ton of updates..It stops at 28683/98320 C\Registry\Machine\Components\Derived Data..Also have a unexpected I/O error status 0xc00000e9 every now & then. Ive booted w/Ubuntu Live cd, but cannot fix anything with the terminal command prompts..Also cannot run scans from microsoft while booted in Ubuntu..I cannot boot into safe mode or any of the other options (just starts over, relooping again) I can get into BIOS, but still windows will not load.(relooping again).I can every now & then get into F10,(without Ubuntu) it will not accept any commands I type in. (NOEXECUTE=OPTIN) is whats there. I really need to do a chkdsk but cannot find anywhere that will allow me to type this in and it work. I do not have the Sony recovery cds. I have a windows vista start\up for my Gateway, but it doesnt work for this Sony Vaio VGN-AR605E laptop. 4 days now working on this. I would appreciate all help. Thank You very much.


Dude, you sound totally confused.
Added to that it sounds rather like windows tried to install a service pack or some such but can't because of Grub. Vista is on the scrap heap anyway.

---

### Post by amvi on 2013-03-30
> **carl4926 said:**
> Dude, you sound totally confused.
Added to that it sounds rather like windows tried to install a service pack or some such but can't because of Grub. Vista is on the scrap heap anyway.

lol, am not a Dude but am confused. Yes, when my son was getting updates, it just stopped loading at what I mentioned earlier. Still no fix or how to in sight. I also dont have "places" on ubuntu live cd to look around to try a fix (as I seen in forums).

---

### Post by carl4926 on 2013-03-30
> **amvi said:**
> lol, am not a Dude but am confused. Yes, when my son was getting updates, it just stopped loading at what I mentioned earlier. Still no fix or how to in sight. I also dont have "places" on ubuntu live cd to look around to try a fix (as I seen in forums).

Sorry Hun :D

If you have a Vista DVD you can restore the MBR and boot record for windows. Then install the updates (Service Pack if that's what it is) Then restore grub from the Live cd of Ubuntu.
It's a pain, but actually a doddle if you have all the right things and knowledge. The most painful part I can assure you is the long wait whilst windows does it crazy updates and reboots.

---

### Post by The Cog on 2013-03-30
From the ntfsfix manual page:
> ntfsfix  is  a  utility  that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.
But unfortunately I think that's the best that Linux can do for you. Microsoft keep the workings of ntfs secret to prevent interoperability with any other operating system. It has taken a lot of work just to get reading and writing ntfs working in Linux, and I doubt that Linux will ever have good repair tools for ntfs. I'm impressed that you found ntfsfix by the way.

A Linux live CD might be able to read the files and copy your valuable data off to a USB drive, but that depends on being able to mount the problem disk in the first place, which may not be possible given the problems you are having anyway.

I think your best bet for repairing the disk is with windows tools. Perhaps remove the disk from the laptop and connect it to a working windows system.

---

### Post by MoebusNet on 2013-03-30
This is the only thing I can think of that might be of help:

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

---

