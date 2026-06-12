---
title: "Program for joystick"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by jon555 on 2008-10-24
On windows I used nice program Xpaddler or something like that, what allowed me to **assign keyboard keys and mouse to my 10 button game controller**. I could use my USB game controller to read e books and watch movies while sitting on couch:popcorn:. I moved cursor around with LR UD axes and used some buttons for enter, tab, space, and so forth. So, is there any program like that in Ubuntu? 

P.S. This question is trivial so, if you are busy, you don't have to answer it.

---

### Post by CJ Master on 2008-10-24
Hello,

Found something that looks like you want in synaptic, never tried it though. (Never had a working joystick. :P)

```
sudo apt-get install joy2key
```

---

### Post by jon555 on 2008-10-25
joy2key Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

---

### Post by SunnyRabbiera on 2008-10-25
a lot of joysticks should work with Ubuntu, though if you are using ibex then you might be facing issues right now.

---

### Post by jon555 on 2008-10-25
This is supported - I play games with it on ubuntu. But that's not the question. Q = How to controle keyboard and mouse with it?

---

### Post by CJ Master on 2008-10-25
Odd. Does this happen while your installing?

---

### Post by dizzy1kenobi on 2008-10-25
> **CJ Master said:**
> Hello,

Found something that looks like you want in synaptic, never tried it though. (Never had a working joystick. :P)

```
sudo apt-get install joy2key
```

would that command install a joystick if I had one?

---

### Post by CJ Master on 2008-10-26
I don't think so dizzy, that command installs a program that allows you to use your joystick or gamepad like a mouse/keyboard. If you have a joystick then ubuntu should recognize it immediately.

---

### Post by jon555 on 2008-10-27
yea, that message appeared in terminal while installing.

---

### Post by CJ Master on 2008-10-29
Alright try these in this order:

1) Load terminal
2) use this:
```
sudo apt-get clean
```
That'll clean up the unused packages and such.
3) use this:
```
sudo apt-get update
sudo apt-get upgrade
```
This'll upgrade your old packages. (note: use update and upgrade in that order.)
4) If there's any updates in your update manager, install them.
5) Reboot your computer.

Now try it by downloading in synaptic rather then apt-get.

---

### Post by jon555 on 2008-10-31
Is this the usual way how I can clean some unworking aplication and is it safe?

---

### Post by CJ Master on 2008-11-01
Sorry for late reply,

Yes, its completly safe. (Unless somethings reaaaaly messed up in your system.)

And its how I clean stuff up, I can't quite rely on synaptic for cleanup duty. :lol:

---

### Post by jon555 on 2008-11-26
It didn't worked. After running from command line I got asked if I have joystick support in my kernel and thats all.   (ubuntu 8.4)

---

