---
title: "can I use unbuntu to disinfect windows?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by walterbyrd on 2008-08-09
My mom's XP box is infected again. It boots, then gets a countdown bar, and then reboots. I think this is caused by an infected nda.exe file. 

I am not local. I am having my mom download ubuntu on a different PC. I am hoping I can somehow use unbuntu to help disinfect the XP box.

---

### Post by bobbob1016 on 2008-08-09
It is POSSIBLE, but more possible you will cause much more harm than good.  There is no way to be absolutely 100% sure you have disinfected a computer once you get a virus, they hide in many ways.  The best bet is to somehow reinstall XP, or Ubuntu, but since she's remote setting her up on Ubuntu won't be a great idea.

---

### Post by pparks1 on 2008-08-09
Well, if your plan is to take and have your mom INSTALL ubuntu and thus get rid of Windows...I guess that would work.

if your plan is to have her run some sort of a tool from the ubuntu cd which will fix her Windows machine and then she will continue to have and use Windows going forward....you are going to be disappointed.

---

### Post by dje on 2008-08-09
the [system rescue cd]("http://www.sysresccd.org") (110mb download) has the clamav anti virus installed on it, plus many other useful tools. I always keep a copy with me

dje

---

### Post by bpowell2005 on 2008-08-09
Can you mom hit F8 during the boot-up to get the boot-options for Windows? Have her boot into safe mode, download and install a good (free) virus checker like Avast Home, update it and run it; hopefully it can detect and remove the virus.

I have to agree with the previous posters, running virus scans on a windows drive from Linux, not a big problem...removing a virus from a Windows partition from Linux...much riskier...best to let Windows take care of its own house if at all possible.

---

### Post by bpowell2005 on 2008-08-09
All of that being said...next time you're visiting, you may want to set her up with a dual-boot setup, Windows and Ubuntu...then she can slowly get used to Ubuntu...and if Windows ever gets corrupted, she'll have a fresh (reliable) OS to switch to, no problems!

---

### Post by bobbob1016 on 2008-08-09
Running a virus remover on a non-running Windows can be *VERY* dangerous.  It might remove files that are needed to boot Windows because they are infected.  A BartPE CD MIGHT do this better, since Windows anti-viruses know what is needed and what isn't, clamav on Ubuntu might not.  I still think it is safer just to somehow have her do a reinstall.  Send an XP CD her way, and have some college/high school kid reinstall Windows after saving her data.  There is NO WAY WHAT-SO-EVER to be sure you got everything removed without a reinstall from a safe source.  If it gives her a timer, not a Windows timer, but from the virus, her NTFS could not be safely unmounted, so walking her through mounting it, and installing a scanner might be hard.

---

### Post by lukjad on 2008-08-09
I am not sure, so please do your reseach on this, but you can install clamAV in Ubuntu and have it scan for viruses. The only thing is that I am not sure how this could be done. Perhaps someone else here knows how?

---

