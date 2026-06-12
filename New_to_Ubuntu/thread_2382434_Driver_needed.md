---
title: "Driver needed?"
date: 2018-01-13
forum: New to Ubuntu
---

### Post by xipho2 on 2018-01-13
Hi,  The "Driver Manager" displayed: intel-microcode, version 3.20180108.0~ubuntu16.04.02 Processor microcode firmware for Intel. What is it good for and could it cause trouble? Generally, are drivers, offered via "Driver Manager" useful and trouble free, how can I check this? Used to Win, updates, etc. I check before installing, thus preventing a  broken OS.

---

### Post by TheFu on 2018-01-13
There have been stories in the headlines the last 2 weeks about the bugs in Intel CPUs.  This is an attempted fix for that at the CPU/firmware level.  There are also OS patches and library updates needed too.  

Some people have reported success, failures and broken systems from some of these patches.  I've seen that broadwell CPUs were reported to have a higher than normal failure with some patches from Intel.  There are also performance impacts (5-30%) were predicted after all the patches were installed.  DBMS was reported as the most impacted.

What should you do?  I cannot say.  I suppose it depends on your risk acceptance and computing habits.

I plan to delay patching for at least another week.

Some more readings:
[https://www.bleepingcomputer.com/news/security/intel-releases-linux-cpu-microcodes-to-fix-meltdown-and-spectre-bugs/](https://www.bleepingcomputer.com/news/security/intel-releases-linux-cpu-microcodes-to-fix-meltdown-and-spectre-bugs/)
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown)
[http://www.zdnet.com/article/linux-vs-meltdown-ubuntu-gets-second-update-after-first-one-fails-to-boot/](http://www.zdnet.com/article/linux-vs-meltdown-ubuntu-gets-second-update-after-first-one-fails-to-boot/)
and the Ubuntu Forums thread about these things: [https://ubuntuforums.org/showthread.php?t=2381801](https://ubuntuforums.org/showthread.php?t=2381801)

---

### Post by Yellow Pasque on 2018-01-13
> **xipho2 said:**
> Used to Win, updates, etc.Similar microcode updates come through Windows Update, though MS groups them with other updates or gives them generic names so user may not be aware. BIOS updates can also update the CPU microcode.

---

