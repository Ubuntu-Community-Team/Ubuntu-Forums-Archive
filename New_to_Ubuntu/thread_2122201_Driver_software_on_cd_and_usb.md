---
title: "Driver software on cd and usb"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by scissorgob on 2013-03-04
Hi My son and i have just built a computer, and have got it working, we have even managed to install Ubuntu 12.10 this is the only operating system on the computer. We are now having difficulty installing any f the drivers for mother board, gra[hics card and dvd drive, just comes up with an error code. Any ideas how to commence this process, all help greatly received.

---

### Post by Mr. Shannon on 2013-03-04
Ubuntu should have installed all but the graphics card driver for you, and it should prompt you to install that.  If it did not prompt you to install the graphics card drivers then bring up the Additional Drivers program and install from there.  The drivers that come with the hardware are most likely for windows, not linux, that is most likely why you are getting errors.

---

### Post by sudodus on 2013-03-04
Welcome to the Ubuntu Forums and the marvelous linux world :-)

Most of the time you don't need to install drivers like in Windows. Drivers come with the linux kernel. In some cases, typically for graphics cards/chips and wifi cards/chips and for printers, you may need proprietary drivers. Often these are special linux drivers, not the Windows ones, and you can get help with that here at the Ubuntu Forums if necessary. To my knowledge it is only for some wifi chips, that it is recommended to use Windows drivers.

If you specify your computer, we can help with more detailed advice, so please post at least

- cpu
- ram
- graphics card/chip
- wifi card/chip

---

### Post by grahammechanical on 2013-03-04
I built my own computer five years ago. I put the Ubuntu CD (given away free by a computer magazine) into the DVD drive and told it to install Ubuntu and to use the entire hard disk and that was all I had  to do to get a working computer with an operating system that has improved with every release. The motherboard did come with CDs with drivers for a Microsoft operating system and with some utilities that can only run under Windows. But they are not needed with Linux - or usable. 

By the way, with 12.10 we open System Settings>Software Sources>Additional Drivers tab. It is there we can activate proprietary video and wireless drivers. You are using Nouveau the open source video driver. That may be sufficient but depending upon the Graphic card you may see some alternative proprietary drivers. Remember, the drivers may work better than Nouveau but because they are proprietary code the Ubuntu developers do not have access to the code. If any are buggy (and I have experienced buggy proprietary video drivers) then we have to wait for the owners of the code to fix the problem and they are not always in such a hurry to do so.  Regards.

Regards.

---

### Post by scissorgob on 2013-03-04
Thanks guys that makes sense, are we able to install additional software such as games?

---

### Post by Cheesemill on 2013-03-04
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by sudodus on 2013-03-04
> **scissorgob said:**
> Thanks guys that makes sense, are we able to install additional software such as games?

- There are linux games.

- Some Windows games run via the interface system ***Wine***, that you can install. But many don't run. Many people ***dual boot***, to get the best of both worlds, linux and Windows.

---

### Post by Mark Phelps on 2013-03-04
> **scissorgob said:**
> Thanks guys that makes sense, are we able to install additional software such as games?

if these are Window games, you can save yourself a lot of work and frustration by going to the WineHQ website, the application compatibility database -- and looking up the game and version you want to use.

Anything not found, or rated less than GOLD, is going to be a waste of your time to try to install and get working.

If that's what you find for the games you want to run, you will need to keep Windows around for running those games.

---

