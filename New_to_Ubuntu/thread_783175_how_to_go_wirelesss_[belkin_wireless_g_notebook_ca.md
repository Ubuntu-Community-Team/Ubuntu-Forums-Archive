---
title: "how to go wirelesss [belkin wireless g notebook card]"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by hazman on 2008-05-05
hi,
still having trouble getting on net with my belkin wireless g notebook ver.7000uk card.Total newbie installed original driver with windows wireless thing and saya hardware presnt:yes .now what? plz help

---

### Post by kwacka on 2008-05-05
First find which chipset you are using.

If its an internal card open a terminal (click on Accessories --> Accesories --> Terminal and type ```
lspci
```
For a usb card type" ```
lsusb
```

Did you use ndiswrapper; what does ```
ndiswrapper -l
``` give?

---

### Post by hazman on 2008-05-05
only thing connected to belkin on last line 
ethernet controller:belkin unknown device 701f [rev20]
 or do you need all of it and ndiswrapper -l gave 
blkwgnv7:driver installed device[1799:701f]present

---

### Post by kwacka on 2008-05-05
So your card is present and recognised.

```
lsmod
```will tell you if the ndiswrapper is installed running.

Can you see the connection at System --> Administration --> network?

If its present you can configure for your network.

You may prefer to install wicd, see [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by hazman on 2008-05-05
it comes up with a lot of stuff does this mean its running.also the connection is not present just dialup modem

---

### Post by kwacka on 2008-05-05
When you run 'lsmod'  do you see 'ndsiwrapper' in the list?

Also if you type```
iwconfig
``` do you see any wireless connections mentioned?

e.g. 
eth0      no wireless extensions.
eth1      IEEE 802.11g  ESSID:""  Nickname:"unknown"

(may not be ethX, could be wlanX, athX)

---

### Post by hazman on 2008-05-05
no ndiswapper not presentand iwconfig gave
lo no wireless extensions

---

### Post by kwacka on 2008-05-05
Did you load the module ```
  sudo depmod -a
  sudo modprobe ndiswrapper
```

Run 'iwconfig' again; is the wireless connection seen?

---

### Post by hazman on 2008-05-05
looks like i've broke my system again .read an article that said add ndiswrapper to modules and system is now hung in no mans land after reboot nothing doing.i am really p*ssed off.i have been trying now for weeks to get this working ,only want to get on net so then i can update and really get a feel for ubuntu but i'm slow being drawn backto windows

---

### Post by hazman on 2008-05-05
hi,
back into system took card out and rebooted. sudo depmod didn't show anythng is it suppose to i feel a right twit cos i no nothing thanks for all your but bare with me plllllzzzz

---

### Post by Vegadark on 2008-05-05
Hello, I am having the same issue. I have tried several tutorials to get wireless working, all with out success.

I have done all the staps listed above and get the exact responses hazman is getting.

ndiswrapper is installed
I have installed the driver from the CD that came with the adapter. Mine is a USB belkin wireless G plus MIMO. 

I cannot for the life of me get it to show up in the network screen. Only the dialup modem is shown.

what does the lo mean in the response from iwconfic that says lo   no wireless extensions?

---

### Post by Vegadark on 2008-05-05
BTW, i wanted to add that the chipset is Ralink RT73

---

### Post by Vegadark on 2008-05-06
ok, so i have gone completely through the tutorial in [http://ubuntuforums.org/showthread.php?t=400236&highligrt73ht=]("http://ubuntuforums.org/showthread.php?t=400236&highligrt73ht=") and cannot get it to work. i am at a complete loss here. Is it possible I need to reinstall Ubuntu again and start over? Perhaps I have messed with too many things and now cannot get back to the starting point?

---

