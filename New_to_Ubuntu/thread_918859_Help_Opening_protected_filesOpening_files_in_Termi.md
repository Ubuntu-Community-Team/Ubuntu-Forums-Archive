---
title: "Help: Opening protected files/Opening files in Terminal?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-13
I just installed RkHunter and ran a scan using it. It gave me a few warnings, and told me to look in the rkhunter.log file located in /var/log/. Trying to open the file, it told me I did not have the proper permissions to view it, and so would not allow me access. I then attempted to manually get to it through Terminal with the intent to sudo it open, but I then realized I have no idea how to open files like that through the Terminal.

Any help would be appreciated.[-o<

---

### Post by Mornedhel on 2008-09-13
In the terminal :

gksu gedit /var/log/rkhunter.log

or

sudo [your favorite console editor here] /var/log/rkhunter.log

where [your favorite console editor here] is any one of emacs, vim, nano, etc.

---

### Post by Grimhound on 2008-09-13
@Mornedhel: Thanks.
Now, would you happen to know anything of what this means?
> [11:46:28] Performing filesystem checks
[11:46:28] Info: Starting test name 'filesystem'
[11:46:28] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:46:42]   Checking /dev for suspicious file types         [ Warning ]
[11:46:42] Warning: Suspicious file types found in /dev:
[11:46:42]          /dev/shm/pulse-shm-2933119177: data
[11:46:43]   Checking for hidden files and directories       [ Warning ]
[11:46:43] Warning: Hidden directory found: /etc/.java
[11:46:43] Warning: Hidden directory found: /dev/.static
[11:46:43] Warning: Hidden directory found: /dev/.udev
[11:46:43] Warning: Hidden directory found: /dev/.initramfs

---

### Post by hyper_ch on 2008-09-13
does are just warnings....

that's nothing unusual

---

### Post by Mornedhel on 2008-09-13
Some of it.

> [11:46:42] Warning: Suspicious file types found in /dev:
[11:46:42]          /dev/shm/pulse-shm-2933119177: data

He's complaining here that there's something in the shared memory (used for sharing memory between programs). That's pretty standard there. It's PulseAudio stuff, nothing to be worried about.

I have the same hidden directories in /etc and /dev as you do. I wouldn't be very worried though, rkhunter pretty much always finds false positives. Did you have a particular reason for running a rootkit detector ?

---

### Post by Grimhound on 2008-09-13
Thanks to you both! :D

---

### Post by HanDez on 2011-07-06
^^BUMP..I just had the exact same issue(down to the warnings and all) and this clarified everything..no worries. 
:guitar:

---

### Post by s.fox on 2011-07-06
Thread Necromancy.  Please start your own thread.  Thank you.

Thread Closed.

---

