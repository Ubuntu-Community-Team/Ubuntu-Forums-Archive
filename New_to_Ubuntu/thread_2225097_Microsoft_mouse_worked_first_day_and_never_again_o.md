---
title: "Microsoft mouse worked first day and never again on Ubuntu.  Works in Win 7"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by richard54 on 2014-05-19
Hello all,

I'm relatively new to ubuntu Desktop and I'm having a problem with my usb wireless microsoft mouse.  I'm hoping someone might point me in the right direction on how to fix this issue. It worked fine the first day and then while using suddenly stopped.

xinput outputs this

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; MCE IR Keyboard/Mouse (ene_ir)              id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver          id=16    [slave  keyboard (3)]

```

and the output of lsusb is:

```
Bus 002 Device 004: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 003: ID 0bb4:0ba1 HTC (High Tech Computer Corp.) 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard 4 GB Flash Drive
Bus 001 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I can see from both of these outputs that the system is seeing the mouse.  Just not sure where to go from there. I've been searching for the last couple of days trying to solve this so any information is appreciated.

---

### Post by Vladlenin5000 on 2014-05-19
You may need to reconnect the mouse with its receiver - check your user's manual - after switching OS's...

---

### Post by richard54 on 2014-05-20
Thank you so much for your reply.  When I went to do what you suggested I noticed that the laser was not on. Upon further investigation it turns out that it was actually the battery.  I feel real stupid right now.  But let that be a lesson to anyone else. Check the stupid things first.  They can save you a lot of time.  lol

---

