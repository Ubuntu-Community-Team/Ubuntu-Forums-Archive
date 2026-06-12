---
title: "[SOLVED] questions about intel 82865G integrated graphics"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Lorodynamic on 2008-11-09
I am a new user to ubuntu, and my first impressions have revealed admirable qualities about this particular operating system.  although I am still a little shaky about ubuntu,  I have encountered little encumbrance while using the OS.  As a matter of fact, the only issue is this:

 There seems to be a glitch/bug with the display.  when I change the screen resolution either to a lesser or greater setting it appears the resolution has in fact changed,but a  part of the desktop display does not resize properly, and is clipped, because when I attempt to move my mouse past the right and bottom edge of the screen, I can move outside of the the actual display. also, these edges do not display the entirety of the desktop. my "power button", workspace switcher and trash icon is not displayed, and on occasion, the all of the bottom desk bar may not be displayed as well.

I do have a simple workaround - I can simply reset the desktop (ctrl-alt-bksp) and the desktop properly adjusts to the new resolution, however, I was hoping to find a more direct approach, and find a way to ensure that the desktop ges reset, without having to back al the way out and log back in.

my current system:
ubuntu hardy - 8.04
linux kernel 2.6.24-21 (generic)
gnome 2.22.3

Dell optiplex 170l
intel 82865G integrated graphics
618 MiB ram
intel celeron processor 2.4 g Hz

any advise on this topic would be most appreciated, and I will gladly answer questions if needed to resolve this matter.

---

### Post by randy78 on 2008-11-09
open a terminal and type: sudo xfix

logout and login... see if this helps

---

### Post by Lorodynamic on 2008-11-09
thank you very much for the prompt response! however, I have tried to enter:

[FONT="Lucida Console"]sudo xfix[/FONT]

and I receive a "command not found" error.

---

### Post by randy78 on 2008-11-09
Sorry my mistake... 

Try this: sudo dpkg-reconfigure xserver-xorg

---

### Post by nerfdooker on 2008-11-09
What resolution are you running at now?
Are you using a crt or lcd display?
LCDs can only properly display the resolution that their built for,so if your trying to set it the resolution higher than the monitor can display its normal for the monitor to cut it off.

---

### Post by Lorodynamic on 2008-11-09
reconfiguring the x server seemed to work, but there is still some issues going from a lesser to a greater resolution, but I simply hit 'apply' again, and the clipping area seems to revert to fit the resolution.

nerfdooker, I appreciate your questions, and I do have some answers for you!

I am using a CRT, a Phillips 107s that was recovered from an archaeological dig... with LightFrame 2(a feature that jacks the total brightness up to that of an incandescent light bulb) :)
and, The problem I am having is the opposite of what you are describing. the right and bottom edges are clipped, but desktop occupies only the upper left corner.

---

### Post by nerfdooker on 2008-11-09
Hmmmmmmm..... I also have a old ghetto 20' dell crt that i got for free.:) i don't know why you have to restart x to apply your screen res, i don't have any computers with Intel chips.  Probably not that big of a problem though, since you'll only apply the resolution once.:)

---

### Post by glennric on 2008-11-09
This was a bug in the driver in Hardy that has been fixed in the driver for Intrepid.  However if you use compiz there is a good chance that won't work in Intrepid.  There is a new bug that causes gnome to completely lock up if you try to run compiz.

---

### Post by Lorodynamic on 2008-11-11
It appears that I have compiz installed, but I do not know if I am using it.  I checked my synaptic package manager, and I have several packages related to compiz installed, apparently as part of a standard Ubuntu installed.  I even when as far as using a 'compiz-check' script to see if my machine can run it! any MORE help would be fantastic.

thank you all!

---

### Post by DougieFresh4U on 2008-11-11
I can not really help you out, but I also have the same Intel chip and I do not expect to much from it as it can not handle doing fancy things like compiz and other 'cool' things. I do run Google Earth with out to much trouble. My advice would be to get a better graphics card.
Good Luck.

---

### Post by Lorodynamic on 2008-11-11
I am well aware of the abilities of my current setup, and its inabilities.  Please note that I am not trying to do anything fancy with this graphics card, and I simply have spotted something buggy.  I figure that since such resolutions were supported with windows, and without much hindrance on my system's  performance, I  want to know what I can do to solve this.

a little more about my problem:

[LIST]
[*]after a change in the resolution, my system does not crash, therefore, Ubuntu is working correctly.
[*]the resolutions that I am trying to use were available to me in windows, so it must not be the chip set itself(I think).
[*]I have checked to see if the correct driver for the chip set I have and it is correct.
[/LIST]

based on this, what can be done?

---

