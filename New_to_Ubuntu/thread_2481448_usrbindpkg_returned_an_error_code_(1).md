---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2022-11-30
forum: New to Ubuntu
---

### Post by thinkawarego on 2022-11-30
Hi,
I recently moved to Ubuntu from windows
I am having problems with this package linux-image-5.15.0-53-generic
I tried removing it with various commands but it didn't work
I tried apt --fix-broken install but it didn't work
Here is a screenshot

---

### Post by ian-weisser on 2022-11-30
The title is misleading. There is no dependency problem.

Elaborate on what you did that might have caused the missing file lists. It's okay to admit you did something foolish -- we have all been there. I go back to that well frequently.

If you did nothing that could have caused the missing file lists, then your storage hardware is suspect. Run SMART tests and prepare to replace that hardware.

---

### Post by TheFu on 2022-11-30
For people that like to tinker with their systems, causing problems is common.  Linux is like Unix and expects the administrator to know what they are requesting. The OS can't tell if it is stupidity or pure genius, so it assumes we are smart.  Sometimes the OS is too generous?

I've certainly screwed myself a few times over the decades doing stupid stuff .... that didn't seem stupid at the time.  ;)  It is a way to learn too.  Break, then fix it.  Sometimes the break is bad and requires reinstallation.  Hopefully, there isn't any data loss and the fix is something trivial.  

I haven't looked at the image ... images of text don't make sense.  This isn't MS-Windows.  Copy/paste the text into the thread editor here, so it is 1KB, not 1MB+.  Also, we can't copy/paste the specific lines to help solve the issue when images are used.

Ok ... looked at the image:
The typical solution for stuff like this is 
a) sudo apt update
b) sudo apt autoremove
c) sudo apt autoclean
d) sudo apt upgrade
e) df    -Th     /boot
f) df    -Thi    /boot
Ensure there's sufficient storage available. Normally, there would be an out of storage error, so that isn't likely, but ... never know. There are 2 types of out of storage errors.  no more blocks and no more inodes. The commands above check both. On large file systems, enough inodes are pre-allocated to handle anything. On small file systems, running out happens too often.

BTW, when posting commands and output, 3 rules:
1) always show the exact command used.
2) show the "relevant" parts of any errors ... usually 5 lines above and below the error if the output is over about 20-30 lines.  We probably don't need to see long lists of things 99% of the time.
3) wrap the copy/pasted command+output into the editor here, then use forum 'code-tags' around it all, so the columns line up.  We are used to seeing it that way, since it is what our terminals provide too.

In short, make it easy to help you. Please.

---

### Post by thinkawarego on 2022-12-01
I fixed the problem by iterating between manually removing the files and using sudo apt --fix-broken install 
This website provided the solution [https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/](https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/) (Solution 4 was helpful)

---

