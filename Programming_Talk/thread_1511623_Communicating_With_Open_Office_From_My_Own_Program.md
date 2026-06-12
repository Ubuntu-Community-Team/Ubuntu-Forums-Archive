---
title: "Communicating With Open Office From My Own Program"
date: 2010-06-17
forum: Programming Talk
---

### Post by Kerubu on 2010-06-17
I've written a small program (utilising the library libusb) which handles button presses on a remote control transmitted to a USB IR dongle. I now want to use the output of my program i.e. the button presses, to control the slides in Open Office Impress (presentation).

The problem I have is that I don't know how to communicate between my own program and open office, or only vaguely e.g. pipes. One way I have thought about doing it is to have the output of my program simulate key presses on the keyboard e.g. the space-bar or right-cursor button, but how would I go about programming this ?

Many thanks for your advice

Kerubu

---

### Post by DanielWaterworth on 2010-06-17
You need to send x events, using xlib. I assume you're using C/C++ because of libusb, in that case this may help [http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html)

---

### Post by Kerubu on 2010-06-17
> **DanielWaterworth said:**
> You need to send x events, using xlib. I assume you're using C/C++ because of libusb, in that case this may help [http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html)

Cheers Daniel that is EXACTLY what I'm looking for !

I am indeed using C but haven't done a great deal of X programming apart from a bit with Qt creator, but nothing that works directly with xlib.

Thanks for that :p

---

