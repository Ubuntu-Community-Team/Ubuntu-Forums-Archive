---
title: "[SOLVED] Cannot clean printer heads"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by hayden92 on 2008-07-19
Ubuntu 8.04 - Recently installed, tried re-installing, did not help

Hello,
I have a Canon IP3000 printer. The printer is recognised by Ubuntu and will print fine. Although the printing works, the quality of the print is very low and smudgy. The heads need to be cleaned. I found the control panel for the printer and can clearly see the button that says "clean print heads".

The button is grayed out and cannot be pressed. I think this may be a bug or missing application.

Please help me work this out because I need to print for work, and soon.

Thank you in advance.

---

### Post by jacktar on 2008-07-19
The head cleaning utilities for ink-jets usually only works with windows. I had to connect my Lexmark to a windows PC to clean the heads.

---

### Post by kestrel1 on 2008-07-19
Can't you clean the heads from the printer controls? You should be able to.
Or you could always manually clean the heads:
[http://www.normediasolutions.com/guides/cannon_printhead_cleaning/](http://www.normediasolutions.com/guides/cannon_printhead_cleaning/)

---

### Post by angelsguitar on 2008-07-19
I would recommend that you get the Turbo print drivers for your printer.  I have two Canon printers too (IP1600 and IP1800) and the only way I could gain the full functionality in Linux was to use that driver.  The only drawback is that the driver is not free (although you can test it and use it for free with some functions disabled).  But if you are willing to pay the price (I did, and was worth it), you'll have all the functionality that you had in Windows.  Here's the link to the site:

[http://www.zedonet.com/en_p_turboprint.phtml]("http://www.zedonet.com/en_p_turboprint.phtml")

In the future, if you need to purchase a printer for Linux, I would recommend that you get HP printers, as they are the best supported printers in Linux.

Hope this helps.

---

### Post by philinux on 2008-07-19
There is a package in synaptic worth trying. I use it for my epson r200.

**mtink**

Status monitor tool for Epson inkjet printers
This is a printer status monitor which enables to get the remaining ink
quantity, to print test patterns, to reset printer and to clean nozzle.

[B]Even if this monitor is targeted to Epson printer, some HP and Canon model are
supported.[/B]

It needs to be run as **gksudo mtink**

The menu item ends up in Accessories.

Worth a shot as it's free.

---

### Post by Wartin on 2009-01-26
> **hayden92 said:**
> 
Please help me work this out because I need to print for work, and soon.
Thank you in advance.


Hello, I found the way to clean the heads of my Canon ip1600 here:
[http://dayat-chasan.blogspot.com/2007/12/this-is-howto-for-installing-canon.html]("http://dayat-chasan.blogspot.com/2007/12/this-is-howto-for-installing-canon.html")

If your printer´s name (as listed in the printer manager) is ip1600, you have to execute:

cngpij -P ip1600

If it doesn´t work, it might be that you´re not part of lp group. Try adding your user to that group, or execute the program as root, with:
gksu cngpij -P ip1600

---

