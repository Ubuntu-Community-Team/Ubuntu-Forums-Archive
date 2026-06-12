---
title: "System Preferences"
date: 2010-10-27
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-27
On the panel is a menu 
System->Preferences->Appearance...

I'm wondering if there is an API for programs to find out what the user's selected preferences actually are? I want the application I'm writing (in this case a terminal emulator) to use the chosen background color and monospace font.

Also, there doesn't seem to be a preferred foreground color which I find strange because for instance color blind people might need to configure this so they can actually get some contrast!

---

### Post by GregBrannon on 2010-10-27
What language?

---

### Post by worksofcraft on 2010-10-27
> **GregBrannon said:**
> What language?
I'm using C++ atm.

---

### Post by nvteighen on 2010-10-28
AFAIK, it's libgnomeui-0...

---

### Post by worksofcraft on 2010-10-28
> **nvteighen said:**
> AFAIK, it's libgnomeui-0...

TYVM :)

I've had a quick look but am a bit depressed about it all atm:

[http://library.gnome.org/devel/libgnomeui/unstable/libgnomeui-gnome-ui-init.html](http://library.gnome.org/devel/libgnomeui/unstable/libgnomeui-gnome-ui-init.html) says:

The initialization functions in this module are **deprecated** in favour of calls to gnome_program_init() in the libgnome library.

and [http://library.gnome.org/devel/libgnome/](http://library.gnome.org/devel/libgnome/) says:

This module is heading towards planned deprecation. It will continue to be supported and API/ABI stable throughout the GNOME 2.x series, but** we do not recommend using it in new applications** unless you require functionality that has not already been moved elsewhere.

I seem to be having a really bad week ](*,)

---

