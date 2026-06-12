---
title: "ELDK 4.1 Install Hanging"
date: 2008-06-27
forum: Programming Talk
---

### Post by Schlegz on 2008-06-27
Hello,

  Has anyone any experience installing ELDK onto Ubuntu?  I've have a problem where the installation just hangs on installing the gawk-arm_trg part.  This is on an AMD laptop and I've been able to successfully install ELDK on another desktop with an identical Ubuntu installation.  Any help and suggestions about what to change or look for are much appreciated. Thanks.

-Scott

---

### Post by supirman on 2008-06-27
Though not directly related to your question -- I just started using LTIB and I like it quite a bit.  I've never used ELDK, just thought I'd mention another tool in case you hadn't heard of it. 

see [www.bitshrine.org](www.bitshrine.org) for LTIB.

---

### Post by Schlegz on 2008-06-27
Thanks for the recommendation.  In this case, though, I'm required to use ELDK for this particular project I'm working on.  And being new to Ubuntu/Linux, I'm having some difficulties ironing out problems I run into.

-Scott

---

### Post by mtxelectronics on 2008-08-05
> **Schlegz said:**
> Hello,

  Has anyone any experience installing ELDK onto Ubuntu?  I've have a problem where the installation just hangs on installing the gawk-arm_trg part.  This is on an AMD laptop and I've been able to successfully install ELDK on another desktop with an identical Ubuntu installation.  Any help and suggestions about what to change or look for are much appreciated. Thanks.

-Scott

I had the same problem the solution is explained at this link: [http://lists.denx.de/pipermail/eldk/2008-July/000273.html]("http://lists.denx.de/pipermail/eldk/2008-July/000273.html")

---

### Post by amigabill on 2010-02-04
I'm trying to install eldk 4.2 on Kubuntu 9.10, inside Virtualbox on an XP host. I downloaded the 1.9GB iso file from
[http://ftp.denx.de/pub/eldk/4.2/ppc-linux-x86/iso/ppc-2008-04-01.iso](http://ftp.denx.de/pub/eldk/4.2/ppc-linux-x86/iso/ppc-2008-04-01.iso)


running the install as described goes nowhere:

bill@vbox:/media/cdrom0$ sudo ./install -d /opt/eldk_ppc/


Do you really want to install into /opt/eldk_ppc directory[y/n]?: y

Installing cross RPMs

sh: /opt/eldk_ppc/bin/rpm: not found
bill@vbox:/media/cdrom0$ 
bill@vbox:/media/cdrom0$ lrt /opt/eldk_ppc/bin/rpm
-rwxrwxrwx 1 root root 2167996 2010-02-03 23:55 /opt/eldk_ppc/bin/rpm
bill@vbox:/media/cdrom0$


Anyone give me a clue?

---

