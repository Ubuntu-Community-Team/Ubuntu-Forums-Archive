---
title: "Ubuntu 12.04 HP2540 Printer Driver"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by Lawrenceharris on 2014-03-22
If you download printer drivers from HP's website and you get" can't open files" following their instruction. Try this at the terminal:

$ wget -c wget [http://prdownloads.sourceforge.net/hplip/hplip-3.13.9.run](http://prdownloads.sourceforge.net/hplip/hplip-3.13.9.run)

 $ sudo chmod +x hplip-3.13.9.run

 $ ./hplip-3.13.9.run


If it detects an earler version of hplip uninstall and replace with newer version when prompted. I spent several days of fustration before I stumbled onto this fix.

---

