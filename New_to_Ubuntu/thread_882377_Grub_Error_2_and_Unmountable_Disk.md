---
title: "Grub Error 2 and Unmountable Disk"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Matt Nichols on 2008-08-06
I'm running Ubuntu Feisty Fawn on a Dell XPS M1530, and out of the blue I get a "error 2" in Grub. Of course this means a referenced disk doesn't exist (right?), but it does. Ubuntu is installed on sda5, but Grub won't recognize it. I'm on a boot CD right now, and when I try to mount sda5, it says > mount: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error. This has happened to me twice before, and failing to find a way out of it, I just reinstalled Ubuntu. But I'd like to not have to do that yet again. Do you know how I can fix whatever has gone wrong and get my beautiful Linux back up and running? Also, what could cause this, and how can I avoid it in the future? Thanks a million.

---

### Post by phidia on 2008-08-06
You may want to get [system rescue cd]("http://www.sysresccd.org/Main_Page") & super grub disk.
You probably want to check the filesystem on that drive and you can do that with the livecd or the system rescue cd. 

For more info on checking the filesystem see the guide [here]("https://help.ubuntu.com/community/SystemAdministration/Fsck").

---

### Post by Matt Nichols on 2008-08-07
I ran fsck.ext3 (with -y), but it said that the filesystem still had errors:
> /dev/sda5: ********** WARNING: Filesystem still has errors **********
/dev/sda5: 92850/1974272 files (0.4% non-contiguous), 363387/7871850 blocks

I tried running it again (this time with -p), but I got this:
> /dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

I believe that's what I did the first time, so I think this isn't going to work. I'll try to get on someone else's computer to download and burn the System Rescue CD, but I'm loosing faith. Should I just give up and reinstall after all?

Thanks for all the help.

---

### Post by Tatty on 2008-08-07
Id advise getting a live CD and backing up all your personal data before going any further.

---

### Post by Matt Nichols on 2008-08-07
I'd love to, but I can't mount my disk to access my data. This seems to be the root of the problem. Is there a way to extract my data without having to mount the damaged filesystem? I didn't think so, but maybe...

---

### Post by phidia on 2008-08-07
> **Matt Nichols said:**
> I'd love to, but I can't mount my disk to access my data. This seems to be the root of the problem. Is there a way to extract my data without having to mount the damaged filesystem? I didn't think so, but maybe...

It may be possible actually. Take a look at the [Ubuntu wiki on Data Recovery]("https://help.ubuntu.com/community/DataRecovery").

---

