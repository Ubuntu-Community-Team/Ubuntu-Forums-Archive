---
title: "Dual Boot (Wubi) = both OS are slower?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by LinuxLBC on 2008-04-25
I used Wubi to install Ubuntu to try it out.  Does this mean Ubuntu's not
running at top power/speed?  

When I boot in Ubuntu, is Windows touched at all or is it as if I only have Ubuntu on my computer?  

I know I can add/remove Hardy from Windows.  Does this mean Windows is involved at all times, even when I boot Ubuntu from startup of my computer?  

It's not that it's slow.  I just want to see it's top performance.

---

### Post by Patsoe on 2008-04-25
Wubi uses a file inside your Windows partition to run Ubuntu from, instead of a real partition. Otherwise, it doesn't affect Windows while running Ubuntu. Also, no parts of Windows are running while running Ubuntu this way.

The only thing that is slower when using Ubuntu through Wubi is hard disk access: it has to read from a file in a Windows partition and that's suboptimal.

---

### Post by LinuxLBC on 2008-04-25
Cool. Thanks.

---

### Post by yorkeandvedder on 2008-04-25
> **Patsoe said:**
> Wubi uses a file inside your Windows partition to run Ubuntu from, instead of a real partition. Otherwise, it doesn't affect Windows while running Ubuntu. Also, no parts of Windows are running while running Ubuntu this way.

The only thing that is slower when using Ubuntu through Wubi is hard disk access: it has to read from a file in a Windows partition and that's suboptimal.

I've been reading through the forums trying to get an idea about this performance issue...  Are there any other drawbacks to installing Hardy via Wubi, other than no Hibernation mode and slower hard disk access (how slow/bad is it?)?

Thanks!

---

### Post by KLR650 on 2008-04-25
I have a Hardy Heron wubi installation for a few weeks now.  I feel it is maybe a little slower than XP is on the same machine.  I won't know until I do a full install!

I haven't noticed XP slower at all.

---

### Post by Raistlin355 on 2008-04-26
I have 2 wubi installs on 2 different machines, and it runs great!  I haven't really noticed any horrible slow downs as far as running the os is concerned and it is a great way for novices and new Linux users to setup a dual boot system.  The only drawback I can see atm is that the hard drive it is installed on doesn't auto mount at boot up, and when you mount it via terminal it doesn't put an icon on the desktop. This however doesn't bother me, but there are those who would like this. Of course a start up script could fix this..........

---

