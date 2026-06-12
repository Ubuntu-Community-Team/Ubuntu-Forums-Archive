---
title: "Looking for Analog clock for taskbar"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2013-07-05
One thing I really like about windows is that when you click on the time in the taskbar out pops a calender *and* an **analog** clock. You can even set up analog clocks for another time zone right next to your main clock. Perfection!
Why has Ubuntu always been bereft of an analog clock? They are great for visualizing a calculation you are trying to do in your head. Digital clocks are worthless for this.
I really want an analog clock that hides in the task bar. So I can click on it regardless of where I am and see it. I don't like docky things that sit on the desktop or get in the way. I like ones that hide in the taskbar until you need it.

Any suggestions?

---

### Post by Zill on 2013-07-05
Arwen17evenstar:  Have you tried [xclock]("http://manpages.ubuntu.com/manpages/precise/man1/xclock.1.html") or [oclock]("http://manpages.ubuntu.com/manpages/precise/en/man1/oclock.1.html")? These are both part of the [x11-apps]("http://packages.ubuntu.com/lucid/x11-apps") package so may well be already installed.  If not then run:
```
sudo apt-get install x11-apps
```
Then just add a launcher to your panel to open your preferred clock.

---

### Post by Arwen17evenstar on 2013-07-05
They load instantly from the terminal, but very very slowly from the unity launcher. Also, there doesn't seem to be any way to make the clock face show numbers?
I wonder why ubuntu is so lacking when it comes to clocks.

---

### Post by Zill on 2013-07-05
> **Arwen17evenstar said:**
> They load instantly from the terminal, but very very slowly from the unity launcher.
I don't use unity here but they also load instantly from a Gnome2 launcher.  It must be a unity thing. :-(
> **Arwen17evenstar said:**
> Also, there doesn't seem to be any way to make the clock face show numbers?
Surely if you need numbers then you *really* want a digital clock. ;-)

---

### Post by su:bhatta on 2013-07-06
The xfce actually gives a nice analog clock option which can be added to the panel.... Here is mine:

'....there is something inherently ridiculous about digital watches...' : Douglas Adams
 [ATTACH=CONFIG]244442[/ATTACH]

---

### Post by Arwen17evenstar on 2013-07-08
> **Zill said:**
> I don't use unity here but they also load instantly from a Gnome2 launcher.  It must be a unity thing. :-(

Surely if you need numbers then you *really* want a digital clock. ;-)

It just drives me insane when there aren't any numbers on the clock face. Personal quirk.

Thank you both for replying. I hope someday someone gives us more options for clocks in ubuntu.

---

### Post by Frogs Hair on 2013-07-08
Try the following or check out screenlets . ```
sudo apt-get install cairo-clock
```

---

