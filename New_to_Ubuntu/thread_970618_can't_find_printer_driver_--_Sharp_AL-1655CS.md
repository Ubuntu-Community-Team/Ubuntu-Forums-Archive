---
title: "can't find printer driver -- Sharp AL-1655CS"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by theorist on 2008-11-04
I've heard great things about Ubuntu and am excited to finally be trying it out.  Two difficulties my make this a briefer stay than I hoped.  I can't get my screen resolution above 800x600 and I can't get my printer/scanner to work on Ubuntu.

The printer/scanner is a Sharp AL-1655CS.  It's a two year old, high volume, low marginal cost, USB 2.0 and ethernet, laser printer.  I can't find Ubuntu drivers for it.  I've used this printer over USB and the network using windows and macs.  I found others posting elsewhere seeking help getting this to work on Ubuntu, but they received no replies.  I can't find any ppd files on sharp's windows driver CD.  I can't find any linux drivers for this printer.  Ubuntu recognizes the printer over USB by name, but can't print a test page or find drivers.  I'd be happy to try other drivers if I knew where to start.  I'd really like to be able to used the double sided printing.

Thank you for any help enabling me to be a regular Ubuntu user.  I've been very happy with Xubuntu on my daughter's old un-networked desktop and would like to use Ubuntu as my primary OS if I can get the printer to work and get a decent display resolution.

Thank you

---

### Post by Peter09 on 2008-11-04
Hi,
first screen resolution.

Try booting in recovery mode. (Hit ESC at the grub prompt and then select the second option) Once the recovery menu comes up select the option to reconfigure your xserver.

Se how that goes, come back and tell us.

If it does not work post the output of the terminal command
```
lshw -C display
```

---

### Post by wizard10000 on 2008-11-04
Information on your printer driver is here -

[http://openprinting.org/show_printer.cgi?recnum=Sharp-AL-1655CS](http://openprinting.org/show_printer.cgi?recnum=Sharp-AL-1655CS)

good luck -

---

### Post by fbugnon on 2009-02-16
I'm also having the same problem with the copier/printer Sharp AL-1655CS. I've tried the suggestion on the mentioned page of openprinting.org but couldn't solve the problem (I guess the page it's been updated now and the suggestion were crossed/marked as wrong).

Finding a driver for this AL-1655CS would also be, for me, the last barrier into a whole switch...  (actually for a small business with +/- 10 computers) so, if anyone has an idea on how to get this printer to work, please post a message in this forum!

Cheers for all and good luck.

---

### Post by fbugnon on 2009-06-29
It looks like someone manage to do it:

> [http://ubuntuforums.org/showthread.php?t=855486](http://ubuntuforums.org/showthread.php?t=855486)

---

