---
title: "Does Libinklevel Work &amp; if so, How?"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-10-13
I have been looking for years for an ink level monitor for my Canon Pixma iP4300 printer.
Of course I have one in XP which works perfectly, but nothing in Ubuntu.
Sounds silly, but it is a major irritation.
Without a monitor, I can be without a printer for a week waiting for ink delivery, or even have to buy full-price ink...

Today, idly Googling around, I found Libinklevel, which is supposedly "a library for checking the ink level of your printer on a system which runs Linux".
[http://libinklevel.sourceforge.net/](http://libinklevel.sourceforge.net/)
Supported printers include Canon iP4300.

SynApt includes libinklevel5, so I installed it.
But nothing seems to happen.
Printer properties continues to say "Marker levels are not reported for this printer."

How should it work?
Where should I see the ink levels?

Thanks for any clues!

---

### Post by ikt on 2011-10-13
why not just buy the new cartridges in advance?

When I sold printer ink businesses could not rely on any printer downtime so they always had a spare ink toner waiting for the previous one to run out.

With regards to the program generally anything with "lib" in it is a library, which means it is the backend for other programs to use.

From the website: ([http://libinklevel.sourceforge.net/#installation](http://libinklevel.sourceforge.net/#installation))

> **After that install some software which makes use of libinklevel.** Currently there are the following options available:

ink (command line)
kink (KDE) and a patch to make kink work with libinklevel v0.6.6rc6
inkblot (Gnome)
gmso (Gnome)
Python bindings
Ink Level Monitor (KDE).
qink (qt4)
inq (qt4)
an OpenWrt package of libinklevel
The next version (v0.11) of MonAMI will feature libinklevel support (see this blog entry for details)
Project mso including JInkLevel Java bindings to libinklevel
pInkLevel a PHP module for accessing libinklevel


Have fun :)

---

### Post by 2CV67 on 2011-10-13
> **ikt said:**
> why not just buy the new cartridges in advance?
My iP4300 is 4 years old.
The first one I bought failed in the garantee period.
Second one - ditto.
So I am not too optimistic about when this one might fail.
When it does die, I don't want to have to write off not only all the ink inside it, but also over 60€-worth of unused ink on the shelf!

So I order my genuine Canon ink cheaply (!!!) by internet as & when cartridges get down to the first warning level (10%? 20%?).
That works OK when I get a warning (in XP) but less well when I need to think to open the lid to check for flashing & not at all when family members are printing.

So I really, really want a good GUI ink level monitor in Ubuntu.

Well - it looks as though libinklevel is a first step.
I checked the software in your quote (thanks for that) without much success yet.
I am using Gnome, so I suppose the KDE stuff will not work?
Several of the others were 404 or had other problems.

I installed "ink" via SynApt & tried running "ink -d /dev/usb/lp0" with no success at first.
After playing at root to change permissions on /dev/usb/lp0 then I did see a valid indication of all my ink levels!
So that's a good second step.

Current problem is that the permissions on /dev/usb/lp0 revert at every boot, so have to be reset each time (is that normal?).

Longer term aim would be to get "ink" to trigger at each print...

Some work to do yet.

Thanks for any further help!

---

### Post by 2CV67 on 2011-10-14
Today's efforts:

"Ink"
Added myself to "lp" group (instead of trying to give r/w permission to "others" :redface:).
"Ink" now works OK & keeps working after reboots.
I can live with that, but would like something more automatic.

Tried "Inkblot".
This also works, but does not see the photoblack cartridge.
So it says "High" even when photoblack is low.
Haven't found a way round that yet.

Tried "mtink" although it is aimed at Epson, not Canon.
Shows pretty display, but does not report levels & loops forever - need to kill it with System Monitor.

Not much else around, is there?

Funny that Printer Properties has an "Ink/Toner Levels" page, but it does not work, even after adding "libinklevel"...

---

### Post by 2CV67 on 2011-11-01
Bump - for Inkblot.

Inkblot works OK, so far as it goes.

But it only reports levels on Cyan/Magenta/Yellow & Pigment-Black cartridges.
Whereas my Canon iP4300 printer, which is supposed to be supported, has an additional Photo-Black cartridge.

Any ideas on getting Inkblot to see that one too?

---

