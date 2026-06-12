---
title: "No transparency for panel icon?"
date: 2008-01-12
forum: Programming Talk
---

### Post by kripkenstein on 2008-01-12
I can't figure this out. I have a simple panel applet in Python, it shows an icon. The icon has transparency (I can see it when I look at the image in GIMP or an image viewer), but it appears without the transparency on the panel - it has a white background.

What is weird is that I've tried all sorts of things: I tried using the same icon the CPU frequency applet has, which has good transparency - but when I show the exact same icon, no transparency. I've read the source code to other panel applets, and I do the same commands as them - create a pixbuf from the file, create an image from that, show the image. Very standard. I even tried calling get get_has_alpha() for the pixbuf, and of course, I get 'True' in return - it has an alpha channel. It just doesn't apply it :confused: The only difference I can think of that I can't easily switch to see if it is relevant is that I'm writing in Python, and other applets I can find are all in C. But that would be paranoid to suspect the language is the issue, I hope...

Any ideas?

---

### Post by xlinuks on 2008-01-12
I have no clue whether it's Pythons fault or not, but this issue exists also in Java (at least  when running on Linux) and it's Java's fault. I have a Java app that uses a transparent PNG for the system tray but the transparent pixels render into opaque gray ones for some unknown reason.

---

### Post by kripkenstein on 2008-01-13
> **xlinuks said:**
> I have no clue whether it's Pythons fault or not, but this issue exists also in Java (at least  when running on Linux) and it's Java's fault. I have a Java app that uses a transparent PNG for the system tray but the transparent pixels render into opaque gray ones for some unknown reason.
Thanks for the info. Is this using GTK in Java, or some other widget toolkit?

---

### Post by xlinuks on 2008-01-13
For now Java is based on GTK, on the PC and mobile. Since QT seems to be GPLed as well I wish they moved to QT.. but that's off-topic.
There's an awkward workaround, for instance take a look at the "GMail Notify" application which is in Python (AFAIK) and uses the system tray as well, so what the author(s) do? They just use an image as big as it can fit into the system tray, and there's no transparent pixel in the image, thus it looks rather natural..

---

### Post by kripkenstein on 2008-01-13
> **xlinuks said:**
> For now Java is based on GTK, on the PC and mobile. Since QT seems to be GPLed as well I wish they moved to QT.. but that's off-topic.
There's an awkward workaround, for instance take a look at the "GMail Notify" application which is in Python (AFAIK) and uses the system tray as well, so what the author(s) do? They just use an image as big as it can fit into the system tray, and there's no transparent pixel in the image, thus it looks rather natural..

Yeah, I tried some more, but no luck on solving this. So I guess that's what I'll have to do as well, have icons that fill the area, without transparency. Going to go draw them now...

Thanks again.

---

