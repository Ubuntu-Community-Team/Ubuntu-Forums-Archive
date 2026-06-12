---
title: "Basic questions about metacity"
date: 2009-12-24
forum: Programming Talk
---

### Post by pedrotuga on 2009-12-24
I recently start using tilling window managers, unfortunately when one doesn't have at least one big screen they can be less practical than a 'standard' window manager.
At work I use windows, and since I can't make my Windows tile windows, I ended up using this program called [Winsplit Revolution](http://www.winsplit-revolution.com/).
I liked it so much that I decided to put together something like that that would work with gnome.

Now, I looked a bit around but didn't dig so deep into metacity documentation. I am assuming it is possible to write a program that queries metacity for windows' positions and such. And that it's possible to set windows positions and capture keyboard events. Assuming all this exists it shouldn't be so much work to put together some basic functionality such as resizing a windows with  a keybind.

Which interfaces does metacity provides?
Is there anyway to access those using like python or perl?

Where should I look? Are there any limitations i should be aware of?

If there are some sample code on how to use metacity to manipulate windows or capturing keyboard events, that would be of good use.

Thank you.

---

### Post by Can+~ on 2009-12-24
Are you sure that compiz can't do that already?

It has plugins like maximumize (maximize space use), scale plugin, and many others.

---

### Post by pedrotuga on 2009-12-24
> **Can+~ said:**
> Are you sure that compiz can't do that already?

It has plugins like maximumize (maximize space use), scale plugin, and many others.

I forgot to mention that, there are plugins for compiz that do that, yes. But i want to use metacity.
I don't use compiz. Also, it's a fun thing to do.

---

### Post by pedrotuga on 2009-12-27
Just bumping...

---

### Post by pedrotuga on 2010-01-31
again... anybody?

---

### Post by chewearn on 2010-01-31
I am not sure about manipulating window within a programming language, but within BASH script, the following proved to be useful:
xwininfo
xdotool
xprop

---

### Post by pedrotuga on 2010-01-31
> **chewearn said:**
> I am not sure about manipulating window within a programming language, but within BASH script, the following proved to be useful:
xwininfo
xdotool
xprop

Thank you chewearn. A a script or two plus a couple of keyboard shortcut definitions and I should be able to put together winsplit revolution's basic functionality.
I'll go with that to start with, but in the future something more robust and tidy (an application) would be desirable. So, though I found a quick solution which I'm thankful for, I would still be glad if anybody would point me where to read about some hypothetical metacity API.

---

