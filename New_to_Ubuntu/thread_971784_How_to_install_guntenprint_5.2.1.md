---
title: "How to install guntenprint 5.2.1?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by madsc89 on 2008-11-05
Ubuntu hardy

I've tried to install this package now: [http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

However, I find that I'm in a little over my head.

Ive got the Epson Stylus DX8450, which isn't supported until 5.2.0, and 5.0.2 is the newest in synaptic.

Therefore, I downloaded it from the site above, and followed the instructions in the Install file, and didn't get any errors along the way.
However, my printer still isn't in the driver list when adding a new driver.

Can someone please guide me through the best way of installing 5.2.1, as I am stuck.

Thank you.

---

### Post by brandoncolorado on 2008-11-05
> **madsc89 said:**
> Ubuntu hardy

I've tried to install this package now: [http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

However, I find that I'm in a little over my head.

Ive got the Epson Stylus DX8450, which isn't supported until 5.2.0, and 5.0.2 is the newest in synaptic.

Therefore, I downloaded it from the site above, and followed the instructions in the Install file, and didn't get any errors along the way.
However, my printer still isn't in the driver list when adding a new driver.

Can someone please guide me through the best way of installing 5.2.1, as I am stuck.

Thank you.

Have you looked through the repository?  I can't find it, but maybe it has a different name.  

Here are good instructions for compiling.
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Joeb454 on 2008-11-05
```
sudo apt-get install cups-driver-gutenprint
```

It may be "cupsys" if you're running 8.04

---

### Post by madsc89 on 2008-11-07
Either that command did it, or it was simply to restart the computer (in terminal, it said that 0 packages were changed).

It still doesn't work, though.
The state just remains: printing: Job-printing.

And the printer status says either: "Printing: Unable to connect to CIFS host, will retry in 60 seconds..." or: "ready", or: The PPD file is version 5.0.2, and that gutenprint is 5.2.1.(or something like that.)

Ant suggestions?

Thank you

---

