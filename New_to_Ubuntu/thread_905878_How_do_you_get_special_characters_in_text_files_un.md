---
title: "How do you get special characters in text files under Linux?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by hvac3901 on 2008-08-30
I have used for a long time now ALT + 248 to get a degree symbol inserted into a text document. it has been hit or miss in linux, as i have used it.

But i never figured out how to insert the triangle symbol, it is listed under unicode???, and the keystroke combo never yields the triangle.

Anyone know how to get the unicode characters?

---

### Post by Pro-reason on 2008-08-30
> **hvac3901 said:**
> I have used for a long time now ALT + 248 to get a degree symbol inserted into a text document. it has been hit or miss in linux, as i have used it.

But i never figured out how to insert the triangle symbol, it is listed under unicode???, and the keystroke combo never yields the triangle.

Anyone know how to get the unicode characters?

You're trying to use Windows-specific tricks, there.  They won't work on any other system.

Open up your keyboard preferences.  You can find this in the menus, or simply type “gnome-keyboard-properties” on the command line.

Go to the Layouts tab, and set up your keyboard to use the USA-International layout, with AltGr dead keys.

Refer to [http://en.wikipedia.org/wiki/US-International](http://en.wikipedia.org/wiki/US-International) to see what each key allows you to input.

The degree sign (°) is obtained by pressing Shift-AltGr-semicolon.

For even more obscure stuff (e.g. IPA symbols, Chinese characters), read up on SCIM.

Another thing you can do is to add the “Character Palette” applet to your GNOME panel.  It provides you with a customisable palette of characters.  Click on the character you want in order to copy it to your clipboard.

---

