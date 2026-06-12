---
title: "Laptop becomes unresponsive"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by alphajunior on 2012-09-01
Hi guys

I've recently made the switch to Ubuntu 12.04 LTS and was pretty happy until this problem started cropping up:

From time to time, the running application completely freezes, the keyboard becomes unresponsive and I'm unable to do anything unless I forcibly hard boot the laptop again. This has happened thrice so far, once while I was running Darktable and the other 2 while running Chrome.

On restarting, I got an error screen (attached) with a message right at the end: 82.196012 Code: Bad EIP value. When I restarted once again, I didn't get the previous screen, but instead got a number of error windows (also attached) with messages such as:

Invalid Problem Report
This problem report is damaged and cannot be processed.

IOError('CRC check failed 0xab26dab1L!=0x6a2f9eafL',).

I then restarted the 3rd time around and opened just Chrome to post this message and it froze again (I also noticed that compiz had stopped responding). Tried all methods (Ctrl + alt + reisub and its numerous variations and I could not get the keyboard to respond so had to reboot again).

Kinda shook up. Any experts able to help?

Thanks
AJ
p.s. Had to take pictures of my screen as my keyboard (thereby printscreen) wouldn't work.
p.p.s I have since uninstalled Darktable, just in case.

---

### Post by acimi66 on 2012-09-02
Sounds frustrating.
This is what I found on the error.


"This error message means that a Cyclic Redudancy Check failed during  some operation, most likely while gzip'ing or un-gzip'ing a file.  Possible causes of this error include an incomplete gzip operation, and  hardware failure. A brute-force way to recover from this error is to  remove the rdiff-backup-data directory. However, this will remove all of  your past increments. A better approach may be to delete the particular  file that is causing the problem. A command like: $ **find  rdiff-backup-data -type f -name \*.gz -print0 | xargs -0r gzip** --test  will find the failing file. For more information on this approach, see  this mailing list post:  http://lists.nongnu.org/archive/html/rdiff-backup-users/2007-11/msg00008.html."

Try it out.
Hope this helps

---

### Post by tienlbhoc on 2012-09-02
try change software source

---

