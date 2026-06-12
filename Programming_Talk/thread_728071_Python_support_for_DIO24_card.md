---
title: "Python support for DIO24 card"
date: 2008-03-18
forum: Programming Talk
---

### Post by robo100 on 2008-03-18
I am very new to python and have ran into a little issue that I have not been able to solve. I have a Digital I/O card (PCI card) that I want to control with Python. I am running Ubuntu and can see the card under the hardware information, so I know the card is there. I have not found a way to get python to use the card. I looked at the pyparallel module but that seems to only work for a printer port. I found a few other modules for I/O using python but have not got them to install correctly. The ones I have tried are:

1.)  [http://www.hare.demon.co.uk/ioport/ioport.html](http://www.hare.demon.co.uk/ioport/ioport.html)
2.)  [http://portio.iriti.cnr.it/](http://portio.iriti.cnr.it/)

The first one just has a C file and a python example. When I try to run the python example it complains that the module ioport is not defined. Not sure what I need to do to get it to work (sorry I am a newbie). The second one I tried does not install correctly. It has a lot of complaints regarding the C code. Has anybody tried controlling an IO port that isnt a printer port? For the PCI card I have the base addresses and register map of the card, I just need to be able to write data to those base addresses.

---

### Post by themusicwave on 2008-03-18
I know with some hardware the OS makes a file associated with it.  This is the case with serial ports.

I wonder if there is such a file for this card.  Just a thought, maybe it will help.

---

