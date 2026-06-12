---
title: "Freezes at Boot Up Screen"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by kepz on 2013-04-14
First of all, I love Ubuntu.  It's been years since I've tried it again and now have been running on 12.10 for the past month.

Just recently, my Ubuntu would always freeze during bootup (after the first Ubuntu encryption password I think just after BIOS).  When it freezes, I would simply power it off and power it back on again which eventually comes good.  Just this morning though, I haven't been able to bootup successfully.

Is there a Safe Mode that I can boot into to see if it can fix itself again?  I'm needing my machine to boot up work quite urgently because I'm using it as my work PC.

---

### Post by crf on 2013-04-14
Try [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), or if you have the install cd or usb key [https://help.ubuntu.com/community/LiveCdRecovery]("https://help.ubuntu.com/community/LiveCdRecovery").

There is also a safe mode from the grub menu. I think if you press <esc> at bootup it will offer a menu.

---

### Post by kepz on 2013-04-14
Thanks for the reply crf.  I tried the Grub menu and went to advance and tried the version/update prior to my current update and it seem to work.  So it's something in the last update that has ruin my Ubuntu.  How can I remove that update or how can I select the update that works without having to go to Grub?

---

### Post by kepz on 2013-04-15
Damn...now it's not working at all. Can't boot using any of the previous updates. Back to square one. Not sure if this error is related, but it's trying to mount a file that is not there. See my attached pic. Can anyone help please?

---

### Post by kepz on 2013-04-15
OK... here's a screenshot where it fails/stops when trying to fix it through recovery.  Is it telling me that it's trying to mount a directory that is not there and then it just sits and hangs?

I'm really needing my laptop up because I've got important stuff I need to do for work, if someone can help please.

[ATTACH=CONFIG]241418[/ATTACH]

---

### Post by afz12 on 2013-04-15
I had the same problem with Ubuntu 12.04 - the latest updates caused boot failure. I posted this problem in this forum about a week ago and had a reply showing how to remove the latest Ubuntu version. As you found, earlier releases were fine, but the latest update destroyed the OS. It would boot sometimes, if you are lucky. However, earlier Ubuntu 12.04 updates in the advanced mode booted fine.

I removed Ubuntu 12.04 and replaced it with Ubuntu 12.10. This seemed to solve the boot problem, mostly. However it also started showing boot failure from time to time.

I see that Ubuntu 13.04 Beta is now available, and full release is available on 25 April (from memory!). I now use Ubuntu 13.04 Beta and it seems stable so far. It seems to run Virtualbox OK and some of the earlier "header" missing nonsense with Ubuntu 12.10 seems to be fixed. I am loosing confidence with Ubuntu daily! If you need Linux OS security I suggest you use dual boot with a different distro. I have had excellent results with Linux Mint (Cinnamon and Mate both seem very stable and secure). I use Mint Cinnamon on one partition and Ubuntu 13.04 Beta on a second. This seems to be a pragmatic solution to Ubuntu's problems.

---

### Post by kepz on 2013-04-15
Thanks heaps +afz12.  I'm downloading my Ubuntu 13.04 now hoping it'll fix my problems and get my virtual machines working again.  But I've lost 1 and half days trying to fix my issue.

I hope I don't lose everything with 13.04 Beta 2.  Wish me luck!

Err... I should have started my back up's during the download. Fail :(
Here's goes another day of unproductive work.

---

### Post by afz12 on 2013-04-15
Hi kepz. Ubuntu 13.04 Beta still seems to run OK - no boot issues. Although running a "fresh install" is usally the best approach, this time I ran an "upgrade to Ubuntu 13.04" as an option and its seemed OK - all my files were kept but some software was neglected - perhaps not supported in Ubuntu 13.04. Still, I had no problem re-installing whatever appropriate version was needed (e.g. Oracle has a specific version for Virtualbox on Ubuntu 13.04 already!). So, so far so good - I hope 13.04 works for you.

---

