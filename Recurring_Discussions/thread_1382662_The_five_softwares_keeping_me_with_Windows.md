---
title: "The five softwares keeping me with Windows"
date: 2010-01-16
forum: Recurring Discussions
---

### Post by Glaucous on 2010-01-16
Hello.
This the kind of thread I have no idea where it belongs the best, feel free to move it in case there's a much better subforum.

I'm using Ubuntu on my laptop and I love it, I'd really like to make Ubuntu my main operating system on my stationary as well, but there are a few programs I really need an alternative to.

SpeedFan, using this to control my fans obviously and it's very important. I heard lmsensors and a combination of another program worked quite well, I tried it on Wubi without success. But I guess I should be able to get it working.

K10Stat, using this to change the powersaving/Cool and Quiet states of my Phenom 2 x4 940. There are four states to change, which I undervolt and underclock depending on profiles. This is quite important as well to keep the PC very cool and most importantly - saving power.

Ati tray tools, clocking and volting the graphics card. The only real this I need is to be able to downvolt the card with a software. And if there's a good alternative on Ubuntu which supports it - I'd also like to automatically change between Idle Clocks and Performance clocks for gaming.

Xpadder, this isn't as important. I'm using my Xbox 360 controller and with Xpadder I can't simulate mouse movement and keyboard presses. This is useful when watching movies, music and other kind of things in front of the sofa.

Bitperfect support. On Vista/7 there's a great way to get bitperfect sound when using Foobar2000, WASAPI. I should be able to use ASIO as well, which I think exists in Ubuntu? My integrated card does not support ASIO natively, but there's a software which simulates it at [http://www.asio4all.com/](http://www.asio4all.com/) .

Throw me some ideas, do there exist alternatives for these softwares in Ubuntu?

---

### Post by k64 on 2010-01-16
First of all, there is an ATI Catalyst Control Center for Linux, and you can run ```
aticonfig --od-enable
``` to enable ATI Overdrive. That said, I don't know of any other overclocking program for Linux. However, if you access /sys you gain full access to clock configuration files - and can edit them - including fan speed - as you wish.

---

### Post by Glaucous on 2010-01-16
ATI Catalyst Center does not have undervolting, sadly. The /sys part sounds interesting though, but not very userfriendly I guess?

---

### Post by juancarlospaco on 2010-01-18
Theres a Python program to control Fan Speed.

CoolNquiet its a simple Freq Scaling GUI, there are avaliable on linux too *(the GUI lies about scale used %,volts,hz,petahertz,cookies,and such).*

Theres a program to redirect Joystick to Keyboard too.

i dont know Bitperfect.

*(i dont provide links or names because i dont remember, but exist, just search)*

---

### Post by Glaucous on 2010-01-18
Well, okay, it's good to know that it exists, sure. But I've been searching around A LOT, for hours, and I haven't found a way to edit Cool N Quiet or a Python script for Fan speed.

---

### Post by juancarlospaco on 2010-01-18
[Read this...]("http://ubuntuforums.org/showpost.php?p=8277553&postcount=1")

*Im not a guru, just typed "fan speed control" on Forum Search...*

---

