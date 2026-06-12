---
title: "modifying the source code for ubuntu..."
date: 2012-04-28
forum: Programming Talk
---

### Post by katty14cool on 2012-04-28
Hey Guys.... i am new to Ubuntu and its forums....
I have made a simple snake game which runs on windows, but now wish to modify its code so that it runs on Ubuntu.... 
what all do i need to know for achieving this?? 
The game has a proper installation process and an application that runs it... and i wish the same outlook for Ubuntu... please help me

---

### Post by Paqman on 2012-04-28
What's it written in?

---

### Post by The Cog on 2012-04-28
Moved to programming talk.

For a start, what language is it written in, and what GUI widgets does it use?

---

### Post by Barrucadu on 2012-04-28
"Proper installation process", as in, an installer program? No, that's not the Linux way. You'll want to (when it works) make a deb package.

---

### Post by katty14cool on 2012-04-29
Its in C with standard windows header files.... maybe i'll find alternatives for them in Ubuntu but what about graphics.h??

---

### Post by DaviesX on 2012-04-29
You might use Gtk instead of Windows GDI, graphics.h is only for turbo c's command line graphics library, however, in Linux you might use GCC. I suggest you to change it to Gtk's because Gtk also provides abundant libraries that you need :)

---

### Post by pbrane on 2012-04-29
I would suggest you look at the cairo graphics library or even SDL if you need something more. cairo graphics is a 2D graphics library. Gtk has been ported to this library.

[http://cairographics.org/]("http://cairographics.org/")
[http://www.libsdl.org/]("http://www.libsdl.org/")

As DaviesX pointed out you could port your code to Gtk, for the window management side.

---

