---
title: "My new issue this day!! cant mount any hard drive or usb"
date: 2021-07-03
forum: New to Ubuntu
---

### Post by handrew on 2021-07-03
Hi all
The OS was totally fine last night!
This morning I can not access any volumes, that includes any USB stick, external hard drive or the M.2 drive I have internally.
Trying to mount or accessing any of these results in a message: "Not Authorized to perform Operation"..
I am at a loss as to WHY this would have occurred and how to fix it!
Easy steps to a fix would be appreciated.
All ok one day, bad the next, LORD!

thanks

---

### Post by oldfred on 2021-07-03
Did Windows turn UEFI secure boot back on. 
Or did it reset UEFI and  you have to go back and redo all the settings you changed. 
Like AHCI, turn off Secure boot, turn on allow USB boot or full USB settings, and usually some others, depending on brand.

---

### Post by handrew on 2021-07-04
Thanks for replying.! It is interesting, on one hard drive I have windows. The computer is a dual boot with linux set as the first choice. I'll investigate what you suggest. I note that  creating a new profile (user) resolves this issue and I can access all devices per usual, leading me to think the issue resides in an altered config file on the linux system. I am not bright enough to figure that out technically. If you know where to look, its about permissions I think, let me know..  Thanks again...

---

### Post by oldfred on 2021-07-04
Did you change permissions?
A new user should not then have permission & ownership to old folder/files as it would be different owner, if Linux format.

Look at this to see permissions & owner.
ls -l

If looking at NTFS partition owner will be root, but permissions should still let you see files.

---

