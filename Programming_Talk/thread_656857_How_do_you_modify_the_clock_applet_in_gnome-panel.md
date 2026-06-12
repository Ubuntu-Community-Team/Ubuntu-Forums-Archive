---
title: "How do you modify the clock applet in gnome-panel?"
date: 2008-01-03
forum: Programming Talk
---

### Post by caclratm on 2008-01-03
I want to be able to show the calendar when I hover over the clock so that I don't need to click on the button. In order to be able to do this I figured I needed to modify the clock widget (mainly clock.c) in gnome-panel, and add a couple of functions that catch the "enter-notify-event" and "leave-notify-event" signals.

I'm able to compile and install the package all right. The thing is, none of my modifications show. I use "sudo gnome-panel" to show the gnome-panel version I just installed. Whenever I make I modification on the gnome-panel itself (changing a menu or a message, for example) I can see it, but when I change something in clock.c in the applets/clock/ section of the package I cannot, even if with the main Makefile I can compile it.

I tried testing the signals on a really simple program I built from the ground up and they work. The signals and callback should also work on the other one but they don't.

I'm pretty new at gnome developing so I don't know if I need to modify an XML, the Makefile or some other file too, but I've at this a couple of days and I can't seem to figure out a solution.

Any help would be greatly appreciated.

P.S. If you have any question that you think might clarify what I'm doing wrong for you don't hesitate.

---

### Post by caclratm on 2008-01-03
BTW, sorry about the grammar faults I just realized I made

---

### Post by kisky84 on 2009-04-22
I know it's been more than a year since you asked this question, but... have you managed to solve it?

I'm currently struggling at the same point, there's no way my modifications for clock applet will show :(


Edit: Obviously, if someone else sees this post now and can help, I'd be really grateful

---

