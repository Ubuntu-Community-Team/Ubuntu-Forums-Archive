---
title: "Black Screen after Booting up into log-in screen 14.04LTS"
date: 2014-12-03
forum: New to Ubuntu
---

### Post by rangermartinez on 2014-12-03
Dual-Boot Ubuntu 14.04LTS alongside W8.1

About 4 days ago while last on Ubuntu14.04LTS I'm reading a .pdf format book (Think Python) that has been there for a few months now with no problems. One of the regular update notices pops up, I proceed to update. No restart required.

I close everything out and shutdown the pc. Later on I boot up w8.1 and everything works just fine. Shutdown properly.

Today I decide to boot up Ubuntu14.04LTS. Everything seems normal. I'm able to get into GRUB. I proceed to load up Ubuntu (actually load up into the log-in screen). Instead of taking me to log-in screen, the screen goes black. No mouse. No code. Nothing. I've tried changing quiet splash in the GRUB to ```
nomodeset_
``` (in reference to [My computer boots to a black screen, what options do I have to fix it?]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it")) but this doesn't seem to work as my logins end up being incorrect. I've also tried booting in recovery mode yet the code below is what is given back for every option I choose.

Now normally while booting up Ubuntu I would get the message of something like **"dev/mapper/cryptswap1 is not ready yet or not present"** and maybe a second later it would boot up fine, now it just crashes or goes into the black screen after giving me this same message.
What is wrong? What options do I have?

```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
fsck.fat 3.0.2 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
    Automatically removing dirty bit.
/dev/sda6: clean, 336768/14311424 files, 3208237/57216000 blocks
Performing changes.
/dev/sda2: 172 files, 29250/97280 clusters
mountall: fsck /boot/efi [715] terminated with status 1

```

---

### Post by Bucky Ball on 2014-12-03
Welcome. Can you boot Win? If so, boot to Windows, get to a stable desktop then shutdown. This seems to be the issue:

```
0x25: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt. 
```

Appears the drive has not been unmounted properly. If you boot back in and do a shutdown this will close the drive correctly. Hopefully. 

To the Ubuntu side, you could also try ... 

Sounds like you can get to a CLI (via recovery?). If you can enter code, try this:

```
sudo shutdown -h now
```

Restart the computer.

PS: See how to use [code] tags for code at last link in my signature. ;)

---

### Post by rangermartinez on 2014-12-03
I updated the post, had to write down the feedback on paper since this is my only machine. I tried your code and restarted it with no results. Also thanks for the instruction in your signature.

---

### Post by Bucky Ball on 2014-12-03
Can you boot into Windows and do a complete system shutdown?

---

### Post by rangermartinez on 2014-12-03
Did a bit of research and did the complete system shutdown through the CLI (terminal) on w8.1 as the normal shutdown is considered a "hybrid-shutdown". The shutdown was a success, yet Ubuntu still is not working - gives the same error messages.

If you have anything else I will try and if all else fails, I will reinstall if I must. 

I'd like to back up certain data, yet I don't know how since I can't get in.

---

### Post by sandyd on 2014-12-03
> **rangermartinez said:**
> Did a bit of research and did the complete system shutdown through the CLI (terminal) on w8.1 as the normal shutdown is considered a "hybrid-shutdown". The shutdown was a success, yet Ubuntu still is not working - gives the same error messages.

If you have anything else I will try and if all else fails, I will reinstall if I must. 

I'd like to back up certain data, yet I don't know how since I can't get in.

If you boot from a LiveCD/DVD/USB, you should be able to access your files from the file manager.

If you have not disabled fast startup in Windows 8.1, do _not_ change files in the Windows partition as it will cause potential corruption/other odd things happening in your Windows installation.

---

### Post by Mark Phelps on 2014-12-03
Windows 8 introduced a new default "shutdown" which is actually a new form of hibernation -- in which all partitions Win8 was accessing when it was running remain mounted -- even though Win8 is not actually running.  Doesn't matter HOW you shut it down, the hibernation remains in effect.

As mentioned, you have to disable FastStartup -- and then shutdown Win8.  Or course, this will then significantly lengthen the startup time for Win 8 because it isn't hibernating anymore.

---

### Post by rangermartinez on 2014-12-03
> **sandyd said:**
> If you boot from a LiveCD/DVD/USB, you should be able to access your files from the file manager.

Completely forgot I could do that, thanks for the reminder.

---

