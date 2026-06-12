---
title: "&quot;no init found&quot;"
date: 2022-05-31
forum: New to Ubuntu
---

### Post by robertjjenkins on 2022-05-31
Hello

I have Ubuntu running on an old machine that I use for CNC machining. I know absolutely nothing about Ubuntu, and only use this machine to run Linuxcnc. Today when I tried to boot, I got this message:

no init found. Try passing init= bootarg
BusyBox v1.13.3 (Ubuntu 1:1.13-3-1ubuntu11) built-in shell (ash)

I have no idea what any of this means. I think I could probably manage to reinstall some version of Ubuntu, but I don't want to lose my Linuxcnc configuration, nor all the CNC gcode files that are stored on my desktop. 
As I say, I know nothing at all about Linux so would really appreciate a word-of-one-syllable kind of help about what I can do

Robert

---

### Post by ActionParsnip on 2022-05-31
If you boot an older kernel, does it help?

---

### Post by robertjjenkins on 2022-05-31
Thanks, but you see I don't really know what this means (this is my level of ignorance). 
Because I have (in the past) run two different CNC machines from this PC, there is another Linux version on the PC, and when I boot up, I get a menu that gives me the choice of the two versions (plus some memory test options). The other version works fine (but the files I want are not accessible from there). I don't see any option to boot into an older kernel.

---

### Post by #&amp;thj^% on 2022-05-31
Some how the system, has become a bit corrupt, you can save the important portions of the current Ubuntu install, with a Live USB installer  "Trial" mode to another media/drive.
I would do that first, before any attempt to fix this.

Now here is a link I feel you should be able to follow: [https://www.lifeonnetwork.com/linux/solved-no-init-found-try-passing-initbootarg/](https://www.lifeonnetwork.com/linux/solved-no-init-found-try-passing-initbootarg/)

---

### Post by robertjjenkins on 2022-05-31
Thanks!

---

### Post by ActionParsnip on 2022-05-31
Hold left SHIFT at boot. Then use a different kernel to boot. May help

---

