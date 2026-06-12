---
title: "A Plethora of Problems"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by amazingtaters on 2008-07-04
Hokay, so my friends HP Pavilion dv2000 is having some major issues. 

1. Firefox will run, but no window will open. Banshee does the same thing. System monitor shows them as running but in sleeping mode
2. Terminal will open a blank window but not allow any interaction.
3. On occasion programmes will simply close without warning. Pidgin is the worst for this, though Firefox does it as well.

---

### Post by silkstone on 2008-07-04
Hmmm... since nobody else has made any suggestions, have you tried booting from the live CD? At least that would show if there were any hardware problems.

---

### Post by batbuntu on 2008-07-04
Did you install some software recently? I had the same problem with Firefox after installing Celestia.

To make a long story short, I had to uninstall Celestia, and then use "apt-get autoremove" to delete some libraries that "apt-get check" reported were installed but unused. After that (I may have had to reboot) Firefox worked again.

If I'm not mistaken you can boot in safe mode and you will get a command prompt at which you can use the apt-get commands.

---

