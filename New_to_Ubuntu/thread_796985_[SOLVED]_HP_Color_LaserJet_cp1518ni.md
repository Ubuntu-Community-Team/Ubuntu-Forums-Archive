---
title: "[SOLVED] HP Color LaserJet cp1518ni"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by fballem on 2008-05-16
Have not been able to install my new printer. The version of HPLIP 2.8.5 is required. I downloaded it from HP website and tried to install. When all was done, when I print, I get the following error on my printed output:

PCL XL error
Subsystem: KERNEL
Error: IllegalAttribute
Operator: BeginPage
Position: 2

This is discouraging (to say the least). Any suggestions would be much appreciated. I would use the ubuntu HPLIP, except that my printer is not listed on it.

Many thanks,

---

### Post by fballem on 2008-05-18
> **fballem said:**
> Have not been able to install my new printer. The version of HPLIP 2.8.5 is required. I downloaded it from HP website and tried to install. When all was done, when I print, I get the following error on my printed output:

PCL XL error
Subsystem: KERNEL
Error: IllegalAttribute
Operator: BeginPage
Position: 2

This is discouraging (to say the least). Any suggestions would be much appreciated. I would use the ubuntu HPLIP, except that my printer is not listed on it.

Many thanks,
Has anyone managed to get an HP Color LaserJet cp1518ni to operate on ubuntu 8.04? If so, please provide this poor newbie with detailed instructions - at the moment I am looking at a $400 paperweight!

Many thanks,

---

### Post by fballem on 2008-05-20
Turns out there is bug in 2.8.5, specific to the cp1510 and cp1518 printers. It has been reported and is being tracked here:

[https://answers.launchpad.net/hplip/+question/33380](https://answers.launchpad.net/hplip/+question/33380)

---

### Post by fballem on 2008-05-28
A workaround has been identified and described at:

[https://answers.launchpad.net/hplip/+question/33380](https://answers.launchpad.net/hplip/+question/33380)

---

### Post by fballem on 2008-07-06
HPLIP 2.8.6 has been released, and does work - no workaround required. The new link is: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Use the automatic install option.

---

