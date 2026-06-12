---
title: "HowTo: set up AIGLX and compiz for Kubuntu"
date: 2006-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by eruditescholar on 2006-07-15
Hi, I've been using XGL under Gentoo on my desktop and I just installed kubuntu on my laptop and found no guides on using aiglx and compiz in KDE.


1. Install AIGLX and compiz (various guides are availabe)
2. Setting up AIGLX in KDM
   Change ServerCmd in /etc/kde3/kdm/kdmrc to:
   > ServerCmd=/usr/bin/Xorg-air :0
   Use 1 instead of 0 for ATI
3. Setting up compiz in KDE
   Add to /etc/environment
   > KDEWM=compiz-start

I'm running on intel graphics and AIGLX has been running fast and stable.

---

### Post by SeanHodges on 2006-08-07
Hello eruditescholar,

Thanks for the info, would it be possible to have a complete HOWTO put together for KDE? This information appears to be useful, but I'm not sure what guides you are referring to (search produces lots of Compiz/Gnome results, but I have failed to find any Compiz/KDE ones), and where these steps need to be done.

Alternatively, if you could suggest a good guide to use for step 1 (which one did you use?) I could maybe have a go at producing a complete KDE HOWTO myself.

The reason I ask this is that there appears to be no complete HOWTO for installing XGL or AIGLX with Compiz on KDE... I have not tried this exercise myself but I have been asked for a solution by a number of people. Scattered guides with bits of information is a start - but not a real help for novice users, or users experiencing difficulty with this approach.

If a complete HOWTO was not your intention here, please let me know anyway so I know where this issue needs to be approached.

Regards,

Sean

---

### Post by exhuma.twn on 2006-08-10
This is a duplicate of [http://www.ubuntuforums.org/showthread.php?p=1361796](http://www.ubuntuforums.org/showthread.php?p=1361796)

---

