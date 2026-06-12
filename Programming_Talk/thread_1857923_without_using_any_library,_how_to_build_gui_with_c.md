---
title: "without using any library, how to build gui with c code?"
date: 2011-10-11
forum: Programming Talk
---

### Post by william2011 on 2011-10-11
without using any QT or GTK+ library, how to build gui with c code after boot

---

### Post by trent.josephsen on 2011-10-11
> **william2011 said:**
> without using any library, how to build gui with c code?

Without using libraries, you can't even input or output anything, much less build a GUI.  C isn't designed that way.

---

### Post by william2011 on 2011-10-11
my meaning is without using any GUI toolkit such as Qt, GTK+

---

### Post by william2011 on 2011-10-11
i am thinking after boot loader pass handle to c code, what should i do with GUI

---

### Post by karlson on 2011-10-11
> **william2011 said:**
> my meaning is without using any GUI toolkit such as Qt, GTK+

If you are not planning to use QT, GTK+, Motif, etc..  I suggest looking at GRUB splash screen implementation or Xorg source code.

---

### Post by william2011 on 2011-10-11
it sounds no function or other simple way to display image or control touch screen input without library

---

### Post by Zugzwang on 2011-10-11
For simple stuff, you might want to have a look at the [SVGALib]("http://www.svgalib.org/jay/beginners_guide/beginners_guide.html") library - then, you don't actually need to boot up an X Server or use a GUI framework.

Doing that without any library whatsoever is possible, but probably years of work, as you'll have to replicate much of the functionality of the library you would otherwise be using.

---

### Post by william2011 on 2011-10-11
thank you very much, after reading this SVGA page, it looks simple, after thinking, i would be back to use Qt first or try this library. it sounds horrible without graphic library.

---

### Post by Zugzwang on 2011-10-11
I don't know what you are actually trying to achieve, but if you want to build some kind of "kiosk" computer on which users can only use one particular application, then there are easier ways to achieve this (in which you can use any library that you want) without circumventing the X server.

---

### Post by cgroza on 2011-10-11
I think you would need to interface directly with the X server or with the frame buffer (I think this is how command line applications like mplayer display images on the console.).
It's a little bit harder because you will have to implement and manage everything yourself.

---

### Post by nvteighen on 2011-10-12
Without linking to **any** library, you'd have no access to X11, neither to the Linux framebuffer. So, I guess you'd have to take a look on how GRUB2 does this (does GRUB1 have graphics?).

My guess is that this involves BIOS interrupts and lots of ASM... :P

(EDIT: In fact, you'd be almost implementing a graphics driver...)

---

### Post by Arndt on 2011-10-13
> **nvteighen said:**
> Without linking to **any** library, you'd have no access to X11, neither to the Linux framebuffer. So, I guess you'd have to take a look on how GRUB2 does this (does GRUB1 have graphics?).

My guess is that this involves BIOS interrupts and lots of ASM... :P

(EDIT: In fact, you'd be almost implementing a graphics driver...)

Would making direct system calls be allowed?

---

### Post by lisati on 2011-10-13
> **Arndt said:**
> Would making direct system calls be allowed?

Well...... it has been a while since I've done anything quite like that, and that was with MS-DOS........

Libraries exist for a reason, often as an aid to avoiding the need to resort to making system calls via the OS, the BIOS (or equivalent), or even directly accessing the hardware.

---

### Post by nvteighen on 2011-10-13
> **Arndt said:**
> Would making direct system calls be allowed?

Depends on whether you consider the kernel to be a library. 

I tend to consider it like that, even though the combination process between an executable and the kernel is not the same used for linking an executable with a library, but still the kernel provides an API that consists in stuff that's actually not part of what one could consider to be C, right?

I guess it's debatable, though.

---

