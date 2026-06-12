---
title: "SiS Graphice Card not detected"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by m.xmen on 2008-11-30
hey brothers,i'm new in the linux world i just installed the ubuntu 8.04 ,i have Plug'n'play Screen ,and SiS 662_M662MX_M662 ,the problem is i have a realy bad resolution for my screen it's too big my last choice of resolution it's 800x600,and ther is no driver to my graphice card i tried to find it but i didn't find a thing,ubuntu detect my graphice card as SiS Real 256E,and my card is not this type,so please i need some help...

---

### Post by overdrank on 2008-11-30
> **m.xmen said:**
> hey brothers,i'm new in the linux world i just installed the ubuntu 8.04 ,i have Plug'n'play Screen ,and SiS 662_M662MX_M662 ,the problem is i have a realy bad resolution for my screen it's too big my last choice of resolution it's 800x600,and ther is no driver to my graphice card i tried to find it but i didn't find a thing,ubuntu detect my graphice card as SiS Real 256E,and my card is not this type,so please i need some help...

Hi and welcome, You can try the command ```
gksu displayconfig-gtk
``` and adjust your resolution there. If it fails then you can boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics issues.

---

