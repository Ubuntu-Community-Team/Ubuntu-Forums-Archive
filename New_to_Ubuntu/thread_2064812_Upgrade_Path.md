---
title: "Upgrade Path"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by MPhil on 2012-09-30
About to install Lubuntu on a vintage HP Pavillion a420n desktop. Presently has an AMD Athlon 3000+ processor and 512mb Memory on a board capable of 2GB. If I upgrade the memory to the max and upgrade the processor would the specs qualify the machine for Ubuntu?
 
If the machine could qualify for Ubuntu would a complete reinstall be required or just an upgrade? Guidance sought

---

### Post by 2F4U on 2012-09-30
According to these system requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

your machine should already be qualified, only the RAM is the bare minimum. So, if you upgrade to 2 GB of RAM, Ubuntu should run well.
Concerning the upgrade to Ubuntu, you can just add the package ubuntu-desktop on top of your existing installation.

---

### Post by mips on 2012-09-30
> **MPhil said:**
> About to install Lubuntu on a vintage HP Pavillion a420n desktop. Presently has an AMD Athlon 3000+ processor and 512mb Memory on a board capable of 2GB. If I upgrade the memory to the max and upgrade the processor would the specs qualify the machine for Ubuntu?
 
If the machine could qualify for Ubuntu would a complete reinstall be required or just an upgrade? Guidance sought

No point in upgrading that cpu as you are very close to the top of the range in that particular series.

Upgrade the ram to the max it can take. The HP site seems to indicate 1GB max [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00054872&cc=us&lc=en&dlc=en&product=388431#N765](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00054872&cc=us&lc=en&dlc=en&product=388431#N765) but they have been wrong before so try 2GB. new ram would be pretty expensive so try and find used ram at a recycler, classifieds etc.

I don't think you would be able to do a clean install of ubuntu on that machine as ubuntu does not come with a non-PAE kernel (cpu dependent) so you would have to install ubuntu-desktop on top of lubuntu as suggested earlier.

---

