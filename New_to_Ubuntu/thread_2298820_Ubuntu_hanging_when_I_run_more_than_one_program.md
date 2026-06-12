---
title: "Ubuntu hanging when I run more than one program"
date: 2015-10-14
forum: New to Ubuntu
---

### Post by astrame on 2015-10-14
Hi,

I have recently switched to Ubuntu 14.04 from Windows. I have dual boot on my laptop. When I run a c++ program along with Matlab, the computer stops responding. For any action, it freezes first and takes a few seconds to do a small thing like opening a file in Matlab.

Please help.

---

### Post by mastablasta on 2015-10-14
post system specs and: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by buzzingrobot on 2015-10-14
Also, say some more about the "c++ program".  What is it?  What's it doing?  Does the locking up only happen with Matlab?

---

### Post by grahammechanical on 2015-10-14
There is a utility installed by default that monitors which processes are using the CPU and memory. Have it open and see what is grabbing most CPU and RAM resources

```
top
```

The software centre has something called System Load Indicator (also known as indicator-multiload). It puts an indicator in the top panel that monitors CPU, memory, disk activity useage. That sort of thing. These two utilities might help you to indentify what is causing the bottle-next.

Regards.

---

