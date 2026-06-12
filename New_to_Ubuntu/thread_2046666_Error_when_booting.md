---
title: "Error when booting"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Angelofdeth on 2012-08-23
I just install Ubuntu 12.04 and it wont boot, it says       error: out of disk
                                                                                                                                                                                                           grub rescue> 
I'm new to this and I have no idea what to do or what this even means.  There is enough space on the hard drive because i erased everything and installed Ubuntu :(

---

### Post by Lisiano on 2012-08-23
For now, since there is nothing important on the system. Try to reinstall Ubuntu.

---

### Post by Angelofdeth on 2012-08-23
ok, do I install with the updates?

---

### Post by Lisiano on 2012-08-23
Refrain from updating during install. You can easily update after the install, plus even if you do update during the install, you will still need to update after.

---

### Post by oldfred on 2012-08-23
Are you installing to a large / (root) partition or drive? We sometimes get that type of error where grub cannot find the files in a very large / partition. I often suggest a smaller / partition of 25GB and the rest as /home. But then you have to use Something else or manual install to split the space as the auto install options only install / & swap.

---

### Post by Angelofdeth on 2012-08-23
Well re-installing it worked :D it says error: out of disk error: no graphics but then it boots so...i guess its working?

---

### Post by oldfred on 2012-08-23
Something does not seem quite right, but I do not know if it does boot what the issue may be.

There are log files that record the boot process. It just may say out of disk, but I still would check log files.

You can use Log File Viewer. I first check dmesg, but theere are many log files in /var/log.

---

