---
title: "[SOLVED] HP C4485 drivers (if necessary at all)"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by al.adab on 2008-09-22
hello,

I've just bought an all-in-one HP printer (Photosmart C4485). As I connected to my laptop (OS: Ubuntu Hardy 8.04), the system detected it right away. On the "printer configuration - localhost" window, I was able to register it as "HP Photosmart C4400 series" and get the drivers. I couldn't find the model C4480 in the list, though, and at the entry ", I set it as "HP Photosmart C4380". 

Printing and copying are ok. Scanning-to-print is also ok in terms of quality, except that the printer "zooms out" the original text (the size of the text after scanning + printing is 25% of the original). 

Scannnig-to-PC doesn't work at all. The scanner appears to attempt to scan, stops, and a message appears on the printer's display: "Scan Error: try scan from computer or see documentation. 

I don't know how to "scan from computer". Also I couldn't find anything in the HP troubleshooting documentation on the issue (well, they all seem to refer to Windows and Mac...) as to why the scan acts weird. I tried to turn both the PC and printer off, alternatively, simultaneously, but nothing changed. I also tried to look out for the C4485 drivers, but couldn't find it. I don't really know if this is the issue anyway...

Is anyone familiar with this kind of trouble? Can they help? Thanks!

---

### Post by timcredible on 2008-09-22
you don't need to do anything with hp printers/scanners.  just plug it in, boot the pc, and ubuntu will find it and configure it.  if you added drivers for something, try to uninstall them, you don't need them, hplip is installed by default.  you also shouldn't be changing stuff in the printer configuration area (i'm assuming this was in cups?).  use xsane to scan, or i would recommend installing kooka via synaptic for scanning, it's easier to use than xsane.

---

### Post by al.adab on 2008-09-22
Thanks, in the meantime I figured out I should add
*sudo apt-get install hpoj*
and now I can scan Xsane. 

I'd like to be able to save my scans as PDF files, but don't seem to be able to do it from Xsane. Any idea?

---

### Post by fredbird67 on 2008-12-28
Al.adab, you are a genius!

I got a new HP PhotoSmart C4450 for my birthday, which is tomorrow.  For me, the printing worked right off the bat.  The scanning, though, was another story.  Your suggestion, however, about the "hpoj" program, was just what the doctor ordered, and I now have scanning functions in Hardy! :)

---

