---
title: "How-To customize your fonts"
date: 2007-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Hal.9000 on 2007-03-13
I was playing around with gconf-editor when I stumbled upon a way to change the default font for all text in gnome.  This will change the font in just about everything: the panel, the menus, nautilus, and pretty much any app you run in gnome (not the font on web pages though).
This seems to work fine on my computer (I'm running Edgy Eft 6.10 32 bit) and I can't see any reason why it wouldn't work on a different version of Ubuntu as long as you have gnome and gconf-editor.

Step 1: Enter the following code in your favorite terminal
```
gconf-editor
```
Step 2: Next in gconf-editor go to the "desktop>gnome>interface" section.  Now just type your favorite font followed by the font size (its a good idea to just use 12) in the "font_name" field. There is a screenshot attached that you might want to look at since its hard to describe this in text.
Step 3: While the above will change the font in most of your gnome it won't change the font on your desktop so next you'll want to go to gconf-editor again and navigate to the "apps>nautilus>preferences" section and enter your favorite font into the "desktop_font" field. See the second screenshot for reference.
And now you're done! all the text in your gnome will now be in your favorite font, enjoy.:)

---

### Post by markl187ld on 2007-03-14
This can also be done through: System -> Preferences -> Font.

---

### Post by Hal.9000 on 2007-03-14
Lol well now I feel kinda stupid.  Thanks for telling me though.

---

