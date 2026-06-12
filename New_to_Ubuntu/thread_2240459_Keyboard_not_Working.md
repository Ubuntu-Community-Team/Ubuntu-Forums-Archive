---
title: "Keyboard not Working"
date: 2014-08-20
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-08-20
Just done a clean install of 14.04 and have a usb connected (microsoft) standard keyboard.  The keys on the right hand side of the keyboard are not working - I think these are sometimes called the number pads keys.   They were working in 12.04/10 - is there something I can do to make them active?

---

### Post by Ksiencha on 2014-08-20
Maybe try to press **NumLock** button on your keyboard.

---

### Post by Quarkrad on 2014-08-20
Doh(!) - thank you very much.

---

### Post by Sanctimonious_Ape on 2014-08-20
Most UNIX variants (which Linux is modeled after) traditionally don't turn on NumLock by default for some reason.  You may have to turn it on manually every time you boot unless you go into the settings and find the option to turn it on by default (where exactly that is will depend upon which distro you're using).

---

### Post by JKyleOKC on 2014-08-20
There's a program in the repositories called numlockx that can control this; it's not installed by default though. You can add it to your system, then include it in your autostart list, and end the problem. Note, though, that it does NOT always set the LEDs properly, so you can't trust them to tell you which state the keypad is in, once you're using numlockx...

---

### Post by snidely2 on 2014-08-21
i've used numlockx a lot and it works great; does what it suppose to do.

---

### Post by Ksiencha on 2014-08-21
I've found this **[guide]("https://help.ubuntu.com/community/NumLock")** explaining enabling numeric keypad on start-up and also look at [**this one**]("http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/"). Maybe it'll help :)

---

### Post by JKyleOKC on 2014-08-21
Excellent guides, both of them. I suspect the reason it's not enabled by default is because quite a few notebooks and tablets don't have separate keypad keys; I have no idea how numlockx would affect those and don't have one of that kind any more to test and find out...

---

