---
title: "no network connection"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by joelr8623 on 2008-11-15
bought computer and it has ubuntu 8.04 hardy as op system but cant get a network connection and i have never seen a system like this before.need help thnks:confused:

---

### Post by pytheas22 on 2008-11-15
Did the computer come with Ubuntu pre-installed?  If so, who did you buy it from?  If it was a reputable company, they should have installed network drivers for you; perhaps the problem is simply that you're not sure how to connect in Ubuntu.  In that case, in the top-right portion of your screen, you should see an icon in the system tray (near the clock) that looks like two computer screens.  Left-click on the icon and you should see a list of wireless networks, as well as an option to connect to the wired network if available.  Does this get you online?

If not, please open up a terminal (Applications>Accessories menu), type the following commands (one per line) and post the output here:
```

lshw -C Network
lspci -nn
uname -m
```

You can copy the output from the terminal by highlighting it, right-clicking and selecting copy.  Then paste it into a text file (Applications>Accessories>Text Editor to open a blank file), save it to a USB drive, and transfer the text file to a computer with Internet access so that you can post the information here.

---

### Post by cochingeek on 2008-11-16
Do you mean networking to other computers or an internet connection?
If for internet connection , what sort of internet connection do you have? a dial up modem, or a DSL cable broadband ?

---

