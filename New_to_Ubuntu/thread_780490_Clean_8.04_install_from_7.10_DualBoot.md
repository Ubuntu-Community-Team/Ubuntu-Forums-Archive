---
title: "Clean 8.04 install from 7.10 DualBoot?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by johanus on 2008-05-03
I'm dual booting WIN2K with 7.10.  Since I've been having recurring problems with screen resolution not staying stable, I downloaded 8.04  planning for a clean install.  When my last effort to fix my 7.10 problem seemed more promising than before,  I gave in to the system's prompting me to do an upgrade to 8.04.  I was blindsided by the questions about configuration of menu.lst and now see that my 8.04 upgrade is still booting the 7.10 kernel.  I would  now like to blow away 7.10 and do the clean install I should have done, but I'm worried about how to avoid messing up boot access to Windows. Could I just wipe the existing Ubuntu partitions and install from the 8.04 CD?  Many thanks for any guidance!

---

### Post by jon zendatta on 2008-05-03
hell0
yes i need help with this one also. i have dual of 10% winxp & remainder 'gutsy'>> i would like to try a clean 8.04 install without breaking my micro$haft partition(which only exists for schoolwork)!:KS

---

### Post by itix on 2008-05-03
Great, then I'll give whatever help I can to both of you. According to my experience, yes you can. I had xp and ubuntu dual booted before and I messed up ubuntu countless times, and the only means I had of fixing those was to resinstall since I was a linux noob. It worked for me all those countless times so it should work for you guys.

Just delete the ubuntu partitions with gparted from the live CD and install on the largest continious free space and the problem will be solved ;)

---

