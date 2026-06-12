---
title: "need driver for a usb720 modem from verizen"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by tech66147 on 2008-06-28
Hi, I'm new to this wonderful OS, will take a little to get use to.  I installed the Gutsy version, but when i try to use internet my Verizon USB720 modem they say (verizon, we don't have a driver for linux) and i say no way.  Where i live that's the only option for internet.  If there's no help out there i will have to uninstall and stick with windows which i really dislike.  please help!    the modem is a Novatel Wireless Expedite Ev-Do Modem

---

### Post by pytheas22 on 2008-06-28
This is one of the cards that gets you Internet access by connecting to a cellular network, right?  I don't know much about them, but I'd be surprised if there's no way to make them work on Linux.  Verizon probably just doesn't bother telling you how.

Plug in the modem and please post the output of:
```

lsusb
lspci
lshw
```

that should help figure out what to do.

Also, how do you connect this thing to your computer (USB, PCMCIA...)?

---

### Post by swimm3r137@gmail.com on 2008-06-28
> **tech66147 said:**
> Hi, I'm new to this wonderful OS, will take a little to get use to.  I installed the Gutsy version, but when i try to use internet my Verizon USB720 modem they say (verizon, we don't have a driver for linux) and i say no way.  Where i live that's the only option for internet.  If there's no help out there i will have to uninstall and stick with windows which i really dislike.  please help!    the modem is a Novatel Wireless Expedite Ev-Do Modem

conveniently enough, I work for verizon, and actually sell these aircards to people all day long, so I think I can help you.  For one, yes, they are not compatible with anything but windows.  But, if you are familiar with wine, install it, because it will act as a windows installer on linux and install the software on the cd that comes with your aircard.  That will get the software installed, but in terms of drivers, I'm really not sure.  Someone here should be able to help you though!  Honestly, I have linux, and I'm almost positive it can be done, you just have to play with it a bit.  Just install the software with wine, and do as normal (if u were in windows according to the instructions), and everything should work out.

---

### Post by tech66147 on 2008-06-29
Thank you I shall try that and let you know.

---

### Post by tech66147 on 2008-06-29
what do you mean code,I knew to this sorry.  

lsusb
lspci
lshw

---

### Post by pytheas22 on 2008-06-29
> what do you mean code,I knew to this sorry.


Open a terminal (under the Applications>Accessories menu) and type those three commands.  Then please post the output here.  You can copy and paste the output by right-clicking in the terminal window and selecting copy.  If you don't have any Internet connection on your Ubuntu computer, copy the output into a text file (you will also find a text editor under Applications>Accessories) and then copy it over to a Windows computer via a USB pen drive or something.

I don't think wine will be able to actually drive the modem--wine isn't designed to emulate low-level stuff like drivers, and can't communicate directly with the kernel--but it probably just comes down to figuring out which kind of chipset the modem uses and how to make it work on Linux.  The out of the commands above will tell which chipset we're dealing with.  Running the wine installer can't hurt anything, though.

---

### Post by pytheas22 on 2008-06-29
I just found this [thread]("http://ubuntuforums.org/showthread.php?t=838891") that should help you.  It looks like you can definitely make this card work on Linux with no problem.  Try following the instructions in that thread and see where you get.

---

