---
title: "boot &quot;Error: couldnt read file&quot;"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by buddy meier on 2012-03-21
i got into the software updater which i used to update all my software, and it said it needed to reboot after it was done downloading, pretty standard, so i let it and bam no rebooting, just comes up with boot screen asking what i want to boot, i choose ubuntu, with linux 2.6.38-13-generic, like usual, short wait then text pops up for a brief time saying "error: couldn't read file"
 
i can acess the basic command terminal but idk how to use it very extensively

---

### Post by ajgreeny on 2012-03-21
Try booting to an earlier kernel from the grub menu, eg the 2.6.38-12, if there is such a kernel.  If that boots OK, then I suspect you either have a corrupted kernel installed or there is some hardware incompatibility problem.  If the earlier kernel boots OK, purge the updated 2.6.38-13, and also remove it from your /var/cache/apt/archives folder then try updating again, maybe using a different server for the upgraded kernel this time.

---

### Post by buddy meier on 2012-03-22
im too much of a noob to go any further, i have no idea how to work any of this, imma just redownload thanks though

---

