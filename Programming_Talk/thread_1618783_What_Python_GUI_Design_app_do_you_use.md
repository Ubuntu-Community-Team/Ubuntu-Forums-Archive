---
title: "What Python GUI Design app do you use?"
date: 2010-11-11
forum: Programming Talk
---

### Post by hopelessone on 2010-11-11
Hi,

I'm going to learn python, So my question is what GUI designer do you use?

Thanks.

---

### Post by Tony Flury on 2010-11-11
It depends which GUI toolkit you are planning to use. Python has bindings for all of the main ones : GTK, QT, TK (and probably many others) - and each toolkit has its own designer (or maybe more than one). GTK for instance the primary designer is Glade (others may also exist).

---

### Post by Reiger on 2010-11-11
Qt has Qt-designer.

---

### Post by StephenF on 2010-11-11
A4 pad, pen, text editor.

A rough sketch is way quicker than anything that can be created with a GUI design tool and once done can be coded up with relative ease.

I can see how using a specific design tool would be needed when working in a team.

Screenshots
[http://idjc.sourceforge.net/tour.html](http://idjc.sourceforge.net/tour.html)

---

### Post by fallenshadow on 2010-11-11
I use Glade but Im not sure what a person would use with Python.

---

### Post by StephenF on 2010-11-11
> **fallenshadow said:**
> I use Glade but Im not sure what a person would use with Python.
Python with PyGTK can import from Glade files.

---

### Post by ussndmac on 2010-11-11
I use Glade. The latest version creates xml files for your gui and then you access with the builder object.

This appears to be the way of the future. If you never build a gui, shall we say, from scratch, as Stephen mentions the mechanics are pretty much obfuscated.

This makes the environment rather confusing for the new comer and frustrating for those that know what they want to do, but now have to go through another layer of code.

Once the whole builder thing is figured out though, basic gui's are much quicker than by hand.

In general, I'd recommend learning how to do it by hand, then move to gui builders.

That said, once you get to that point, wxGlade is a bit easier to pick up than Glade. I suppose the major draw of Glade is that the xml file can be used by many programming languages.

---

### Post by Crazedpsyc on 2010-11-11
I use the GIMP and GEdit! Nothing's better that a good syntax-highlighting text editor for python!
There's also ERIC which can do some guiing (i think)

---

### Post by hopelessone on 2010-11-11
OK Everyone [you all make me feel like your family!] I really understand better now, I'll have a shot by hand first..

Thanks,

---

