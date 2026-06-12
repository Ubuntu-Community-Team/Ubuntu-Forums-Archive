---
title: "Completely broke Ubuntu"
date: 2020-09-07
forum: New to Ubuntu
---

### Post by djtransverze on 2020-09-07
Hey guys, I'm brand new to Ubuntu after uninstalling Windows 10 for obvious reasons. My laptop has never ran so fast! I'm honestly amazed at how fast I can get work done on the Linux/Ubuntu Operating System, but I broke it. Bad. So badly that the command line doesn't work, and the whole computer is virtually unusable. I could just reinstall, but I kinda want to challenge myself (or you) to fix it.

So here's the situation, about 2 seconds after logging into my computer, the system freezes. I can use the mouse, but nothing else works. Ctrl+Alt+F1 does nothing, no shortcuts do anything, the only way to restart is to hold the power button or manually eject the laptop battery. If I manage to hit Ctrl+Alt+F1 before the system freezes, I can manage to open the terminal, but commands don't work. I just tried a simple ps command to see what processes were killing the machine, but it stopped, did nothing, prevented me from typing (still blinking the typing indicator, as if it was attempting to do something), and the cleared the terminal. After clearing the terminal, typing is impossible, but the indicator is still blinking on and off.

Sooo..... how did I break it? I only used the software for about an hour, and I've never used it before so bear with me. I have no idea how this particular thing broke it, but you can try to recreate it on a VM if you want to see for yourself. I have a MIDI controller called a Pioneer DDJ-SB2 for DJing, and I wanted to see if I could get it working on Ubuntu. I installed Mixxx, a program built for MIDI DJ controllers like mine. I programmed a slider or two, and all was working well until I discovered a preset in the Mixxx software that would let me use the controller for everything. I moved another fader, a linear MIDI control that generated an error for every iteration of fader movement, which seemed to me like an infinite number of errors. It slowed the computer down, and so I just rebooted to try again.

After rebooting it's just been broken with no hope whatsoever. Any ideas? I'm open to reinstalling the OS, I just want to see if it's fixable first.

---

### Post by crip720 on 2020-09-07
Unless you have Mixxx set as a start up program, a reboot should fix computer.  Thinking installing Mixxx happen at same time something else broke.  Boot up Ubuntu installer USB and check hard drive and file system before trying to install again.  Hard drive can be check with 'disks' and file system with fsck.

---

### Post by grahammechanical on 2020-09-07
My guess is that something is using up system resources (CPU and memory). A likely subject would be Mixxx. Remove Mixxx and do it through recovery mode.

At the Grub menu select Advanced Options for Ubuntu and select a Linux kernel with a recovery mode. At the Recovery menu select Network to establish an internet connection. When back at the Recovery menu select Root shell prompt. This command will remove Mixxx

```
apt remove <program>
```

When finished type exit to get back to the Recovery menu and select Resume. The desktop will load with a low video mode video driver. A reboot will load the normal video driver.

Regards.

---

### Post by TheFu on 2020-09-07
By chance, did you use sudo with any GUI programs?
Also, exactly which version of Ubuntu is being used?  Numbers, please, not "the latest" because we've found that "latest" often is not.

---

### Post by djtransverze on 2020-09-08
Well, guys, I don't think Mixxx was the issue. I've managed to get it unintstalled, and we're good. After a while, the OS seemed to be working fine. I used the computer yesterday with no issues. All I did was some internet browsing, I edited some Google docs in the Mozilla browser, but nothing else. Today the computer is randomly broken again after booting back up. I have no idea what's wrong with it now. I'm on 20.04.1 LTS (minimal installation). Any ideas?

---

### Post by oldfred on 2020-09-08
What brand/model system? What video card/chip?
Have you updated UEFI/BIOS and if SSD its firmware?
UEFI or BIOS install?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

You should not force shutdown as that can cause file corruption and then you need fsck to repair system, before you start to resolve issue.

---

### Post by TheFu on 2020-09-08
> **djtransverze said:**
> Well, guys, I don't think Mixxx was the issue. I've managed to get it unintstalled, and we're good. After a while, the OS seemed to be working fine. I used the computer yesterday with no issues. All I did was some internet browsing, I edited some Google docs in the Mozilla browser, but nothing else. Today the computer is randomly broken again after booting back up. I have no idea what's wrong with it now. I'm on 20.04.1 LTS (minimal installation). Any ideas?

If you didn't screw around with system settings in a terminal, didn't use sudo to run programs, then my last guess is there is a hardware problem of some sort. Check the log files.  Google "ubuntu logs" to find an article at help.ubuntu.com which explains how, what, and where those are. Look for warnings and errors.  If you find your eyes glazing over, take a step back, do something else and come back later. Logs take some time to get used to reading. Once you are good at it, you'll see they provide about 80% of what you need to figure out the cause for issues.  Unfortunately, knowing the cause isn't always helpful for some hardware.

I can assure you that Linux is very stable when there aren't any hardware issues and settings haven't been screwed with:
```
$ uptime
 11:54:28 up 30 days, 12 min,
```

But as you learn more, it is possible to tune your system to your likes and dislikes. Highly customizable systems, unlike Steve-OS and OS-by-committee rivals.

The boot-info report URL would definitely be helpful.

---

