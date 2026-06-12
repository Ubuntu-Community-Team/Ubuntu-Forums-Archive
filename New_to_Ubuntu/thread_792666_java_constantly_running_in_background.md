---
title: "java constantly running in background"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by stueau on 2008-05-13
hey all, I've just noticed a small albeit annoying problem.

I've been noticing that my laptop (inspiron 1501, running hardy 64-bit vers) keeps chugging away even when idle. Looking at the system monter, it appears java is constantly running, taking up around 20-30% of my CPU.

I can easily stop the process but it just stats up again after a few minutes. I slightly wary of killing it all the time because of the scary message that comes up about killing active processes...

Any help, or anybody experiencing the same thing?

Many thanks.

EDIT: uninstalling 'Freenet' appears to have solved the problem.... for now anyway

---

### Post by Bloch on 2008-05-13
I had a buggy version of amarok once, and it would often crash and leave java running n the background.

Some programs call up java. It doesn't just start itself.
So does this problem exist as soon as you boot the laptop? Or does it first occur after using some particular application?

There must be some program that starts java. It is not an essential part of the system - you can solve your problem by uninstalling java.

There are only a limited number of common apps that use java
amarok
OpenOffice (when chosen in preferences)
Firefox (only when a java applet is hit on)
frostwire / limewire
azureus
...


aaargh - I just read your post again and you mention freenet. Freenet uses java. That's the culprit. So maybe it's a buggy freenet or else there are some settings you can change. Did you set freenet to start automatically?
Does java continue to run after you close freenet in the normal manner? Freenet is still beta software in any case, so will have problems.

---

### Post by stueau on 2008-05-13
hey thanks for the reply. Yeah the problem was freenet, in the sense that the problem has gone once freenet was removed. I installed t a week ago but couldn't be bothered with it in the end and had just left it on the system since I had no idea how to uninstall it.

Even after a reboot, java was still running and when looking into it the java process mentioned a lot of 'freenet' named processes/files/whatever.

Anyway, I got onto an IRC node and found out how to uninstall and it's fine since.

It was particularly annoying since it just meant everything really sluggish. I don't have a particularly slow computer, but some background "sleeping" process taking up a quarter of my processing power was a real pain.

All's well that ends well anyway.

---

