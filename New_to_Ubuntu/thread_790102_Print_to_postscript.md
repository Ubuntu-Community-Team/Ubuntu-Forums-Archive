---
title: "Print to postscript"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by DexterLB on 2008-05-11
So, I know there is a "print to file" option in most software that prints to a postscript file.

I design PCBs with ExpressPCB, which is for windows only and I have installed it under wine. BUT expresspcb doesn't have a "print to file" option. Under windows I was creating a new printer, in my case HP laserjet 1150 and set the output as "FILE", and when I print trough this printer, it generates a postscript. Is there a way to do something similar under Ubuntu? Something like cups, but which prints into a .ps, not into a .pdf?

---

### Post by kwacka on 2008-05-11
You've almost certainly got 'ps2pdf' installed already as part of ghostscript.

Its been a while since I used it but I seem to recall its just a 'ps2pdf infile.ps outfile.pdf' command.

---

### Post by DexterLB on 2008-11-03
I mean, printing directly to PS not through PDF...

---

