---
title: "can't boot ubuntu on vista"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by billk on 2008-08-16
Im running vista on an xw9300 amd64 box and trying to run ubuntu inside vista (wubi?).
Initially had "trojan" messages when doing the install (from an iso image). Shutdown avg,firewall and internet connection and the install went OK except for an "error trying to execute wubibcd::" at the very end. Installation seemed to complete except I didn't get a choice for booting vista or ubuntu. Followed a thread advising using easybcd. That worked and now I get a choice of os's. If I boot(try) to Ubuntu I just get the grub prompt.
I've looked at the bootloader commands in the C:\NST\NeoGrub MBR file and it looks like they should get me to C:\ubuntu\install\boot\vmlinuz eventually.
I have installed/uninstalled multiple times with the same results,checked the iso for errors and have run ubuntu from the CD all successfully.
Any ideas? (getting a little frustrated ](*,)
I seem so close......but
bill

---

### Post by nicedude on 2008-08-16
I would suggest not using WUBI and instead first reading a guide on how to do so then setting up a dualboot machine. This is highly superior to what you are trying, and there could be a good chance some windows software if blocking you from successfully doing what you are trying if you get a trojan warning. Although there are no TROJANS in Ubuntu or VIRUSES so whatever said that was either a false positive or in reference to another file.

---

### Post by alzie on 2008-08-16
Hi Bill.  I'm not familiar with Vista and Wubi,  but I have used Wubi in the past and had no problems.

I have 2 links here for you.  The first is the Wubi forum, they are usually very quick and the help there is great.  The second link is the Wubi guide.  It helped me a lot when I was using Wubi.  Check them out  :)

WUBI forum  [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

Wubi Guide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by billk on 2008-08-18
Just got back to my problem,thanks for the ideas.
I realize partitions would be the best way to go but I wanted to see if virtualizing this within vista really worked. I guess it does, just not all the time.
I'll browse through the guides and see if i find something useful.
Thanks.

---

