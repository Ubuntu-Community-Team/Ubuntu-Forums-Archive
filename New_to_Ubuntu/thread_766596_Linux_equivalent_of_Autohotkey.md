---
title: "Linux equivalent of Autohotkey?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Megalorian on 2008-04-25
Does anyone here know if there is a Linux equivalent of [Autohotkey]("http://www.autohotkey.com/")?

---

### Post by Megalorian on 2008-04-27
From what I can see, there are 3 choices:

[http://ldtp.freedesktop.org/wiki/](http://ldtp.freedesktop.org/wiki/)
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

Has anyone used any of these? The ultimate question I have is which is the best one to use?

---

### Post by nhasian on 2008-05-01
actually in windows I used Hot keyboard Pro.  I just installed ubuntu 8.04 a few days ago on my laptop and have linux equivalent for all the programs i need except for Hot Keyboard Pro and Newsbin Pro.  Have you tried any of those linux hotkey programs yet?

---

### Post by Megalorian on 2008-05-01
Not yet. It's on my 'to do' list. I need to sort out some installation issues first. But I will post back here after I try them out.

---

### Post by SunnyRabbiera on 2008-05-01
well if you have a multimedia keyboard, there is possibly a way to make it function.
there is a built in tool under system> preferences> keyboard shortcuts.
it might work if you play around with it.

---

### Post by Pipps on 2010-01-01
For simple actions, why not use the global keybindings?

Run > gconf-editor > metacity.

---

### Post by Chase. on 2010-02-10
Hi there.
Unlike the name suggests, Autohotkey is much more powerful than simply adding Hotkey and Hotstring options. Quite a few probably use it to automize GUI tasks, which I consider dispensable, but there are some features I really don't want to miss. I'll try to make a list

I'd be glad if someone could name replacements or other solutions for these taks:

[LIST]
[*]shortcuts for system options, like sound 
(e.g. Holding Alt + mousewheel changes volume)
[*]Operating on selected text and clipboard 
(e.g. Win + G googles selection)
[*]Hardware access
(e.g. remapping power button to turn on and off all LEDs)
[*]Full Unicode support
(e.g. replace the string &#28961;&#38480; with &#8734;)
[*]Window and GUI control
(e.g. move a window to pixel 0,10 of the leftmost monitor)
[*]Layout independant shortcuts
Autohotkey uses "scan codes" and "virtual key codes" at the same time. The first refers to the actual hardware, while the latter refers to the "translated" key that is dependant on layouts. I am not sure about this on Linux, but I've been told that X only provides the virtual (mapped) key codes.
As I am switching layouts frequently, I really need some shortcuts stay layout independant, while others should correspond to a letter, rather than a physical key.
[/LIST]
Especially the last point is important to me, and I reckon it could get a little tricky on Linux.
I'd really like to switch to Ubuntu as a main system, but I need a replacement for those tasks first.. help me ;)

---

### Post by spiderwebby on 2010-07-28
i'm working on bodgeing together something to do the basic bits of AHK. i've found xvkbd for keyboard+mouse output.

i'm just aiming to temporarily bind the Fkeys to text strings at the moment

---

### Post by degarb on 2010-08-05
The power of autohotkey is absolutely awesome. It is a macro program that morphs into a programming language, depending on your level of obscession with fixing a problem and hole in available programs. Their forum helpfulness is even more impressive.  Anyone with average intelligence can read for ten minutes and start writing complex programs, compile and distribute them. 

[http://akronedge.info/wintersoft](http://akronedge.info/wintersoft)  are some of the one's I wrote just sitting down a month a year in winter.  Then, I haven't even listed here my cd batch ripper, called swap-walk, which is no human interaction book batch ripper where cddb is done optionally at end or you just list your books.

Like all things-like Linux-, you must gain some mastery or use, to appreciate and not minimilize.

---

### Post by kervin on 2011-05-29
It would be really cool if we could run .ahk files in ubuntu.. :)

---

### Post by caffeine74 on 2011-07-16
[COLOR=Blue]_[IronAHK (alpha): cross platform .NET rewrite of AutoHotkey]("http://www.autohotkey.com/forum/topic54494.html")_[/COLOR]  looks to be what we're looking for ... when it's actually ready. It seems to be having a *really long* development cycle.

You can get the [COLOR=Blue]_[alpha code]("https://github.com/polyethene/IronAHK")_[/COLOR] if you're interested in helping develop it.

---

### Post by last1 on 2011-08-18
I found AutoKey to do a good job at some of the basic capabilities that AHK does. Mapping text output to a hotkey was actually easier for me in this program, just type into the box, set a hotkey and save. It can do Python scripting macros too from what I've read.

---

### Post by aasami on 2011-09-29
> **last1 said:**
> I found AutoKey to do a good job at some of the basic capabilities that AHK does. Mapping text output to a hotkey was actually easier for me in this program, just type into the box, set a hotkey and save. It can do Python scripting macros too from what I've read.

Yes, this is what I've been looking for. Thank you man!

---

### Post by Cottonwoody on 2012-01-26
I do use AutoHotkey for Linux by starting my Linux within a Sun VirtualBox on a Windows PC. That works perfectly. 

Hope this helps somebody.

---

### Post by chickenPie4breakfast on 2012-01-28
I wish there was a AutoHotKey for linux too - its the one app I am really  missing because it became many apps to me.  If more LInux users had gotten to know it on a pc then a clever one might write something like it for Linux.  Yes there is IRonAhk but Its been so long in development and seems to have halted. I think it was being too abitious wanting to make a version that would work on any computer - as there are already 3 versions that work fine on a Windows machine there is no need for another - It would have been better if the author had just tried to make a linux only version.

---

### Post by bolocholo on 2013-01-12
From AutoKey (Desktop automation utility for Linux and X11) FAQ section:

> **Does AutoKey work with scripts which were written with the popular AutoHotKey Windows application?**

No.  AutoKey's built-in Python scripting is arguably much more powerful than  the AHK language and makes it possible to do many of the things that  AutoHotKey scripts can do on Windows, in addition to some things AHK  doesn't support. 


[http://code.google.com/p/autokey/wiki/FAQ](http://code.google.com/p/autokey/wiki/FAQ)

---

