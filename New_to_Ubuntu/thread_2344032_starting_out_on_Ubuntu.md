---
title: "starting out on Ubuntu"
date: 2016-11-21
forum: New to Ubuntu
---

### Post by bluenotesound on 2016-11-21
Hey there,

Newbie here, interested in starting out on Ubuntu. I'm moderately experienced with computing and I have plenty of experience with both Windows and OSX, but I want to give Linux a try and I understand Ubuntu is a great place to begin. Within the next couple months or so I expect to be getting a new laptop and building a new desktop, which is why I think now is a great time for me to get started, plus I want to become more tech-savvy in general. 

I've done my homework with the basics already, so I've already found links to ubuntu manuals and such and I'm already familiar with PC hardware and building. I'm here because I'd like to know if Ubuntu is a good fit for my particular needs--the desktop I'm building will, ideally, double as a audio production PC and as a home server. I think I can figure out how to manage either of those in isolation but an elegant solution for doing them both on the same machine and the same OS is where I'm having trouble. 

Audio production is pretty self-explanatory and I'll probably just get Ardour (if audio was all I wanted to do I'd probably go for KXStudio distro, too). The main goals for the server aspect are streaming music from my collection and backing up files and data. Not too concerned with video streaming. I plan on running either Ubuntu or Lubuntu on a laptop with a fairly small SSD, and my girlfriend uses a Windows 10 laptop so I'd like her to be able to sync with it as well for backing up her schoolwork and the like. I've been reading a bit about setups like Plex, Amahi, and LAMP, but they're all unfamiliar territory for me so that's where I'm most in need of advice. 

Apologies if that was wordy, but hopefully it makes my goals clear, and thanks in advance for any and all advice.

---

### Post by mörgæs on 2016-11-22
Yes, it was a little wordy. A forum works better if you ask one question in order to get one answer. More advice here:
[https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

Nevertheless, welcome to the fora.

Your project sounds interesting. My first comment is getting some used hardware a few years old, often it is better supported than new stuff.

---

### Post by HermanAB on 2016-11-22
Linux and OSX are almost identical, both being a version of UNIX.   The main difference is that with Linux, you can do anything you want, with no training wheels to hamper you.

The easiest quite trivial way to provide a file store to a Windows machine, is to create an anonymous FTP server, since an anonymous FTP client is baked into the Windows file explorer.  Any other file share method is much more complicated to do.

See the bottom of this for the FTP explanation: [http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html](http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html)

---

### Post by Mark Phelps on 2016-11-22
@bluenotesound:

One caution I would like to add is that synching your files in Linux to a Win10 PC is extremely hard and risky.

To begin, Win10 automatically enables a form of hibernation known as FastStartup -- not to be confused with Fast Boot, which is something different.  With this in place in Win10, Linux will not be able to see or mount the Windows filesystem because Win10 keeps it mounted even when it is not running. You would have to disable FastStartup in order for Linux to see and then mount the Windows filesystem.

Second, writing to a Windows filesystem from Linux is risky and dangerous, as that can easily corrupt the filesystem, and if that happens, Windows will not boot anymore --making it really HARD to fix because there are no Linux tools that can repair damaged Windows filesystems.

The safest way to share files between Linux and Windows is to either  (1) have a data-only NTFS partition on the Windows PC, or (2) to use a USB stick to do file transfer.

Something to think about when you mix the two filesystems.

---

### Post by ian-weisser on 2016-11-22
> **bluenotesound said:**
> Within the next couple months or so I expect to be getting a new laptop and building a new desktop, which is why I think now is a great time for me to get started, plus I want to become more tech-savvy in general. 

Advice #1: Start with a Virtual Machine. Ubuntu is free and you can easily install/reinstall as many times as you wish. So grab an Ubuntu Server ISO today, build a guest VM on your current host setup, and start playing with server configurations and networking. By the time your hardware arrives, you will have a better idea of what you want to do.
 
Advice #2: Be prepared to take a few steps back. Your Win and OSX power-user skills are likely to lead you astray in a Linux environment. Simple tasks like installing and upgrading software are entirely different...for good reasons. You will learn many new skills. You may destroy a system or two (hello, VMs), since the power and flexibility of Linux is also the power to destroy.

Advice #3: After you play for a while with a VM, erase it and start over. The second time, start with good Linux security habits and good Linux maintenance habits from the beginning.

---

### Post by bluenotesound on 2016-11-22
Thanks to everyone for the tips! Apologies again for the wordiness.

The VM advice is well-taken and I definitely think I'll experiment with that a bit before I take a plunge. I'm also glad to get that info on the compatibility issues with windows to Linux, I wasn't aware (though I can't say I'm too surprised) that there are particular issues there. 

Since I have this old Dell laptop that still has a fairly large hard drive and my storage needs aren't extensive, I may even use the desktop just for audio and general purpose use and try Amahi or Ubuntu Server on the old laptop. Might as well repurpose it instead of just throwing it out, and I can always upgrade to something bigger later if needed.

---

