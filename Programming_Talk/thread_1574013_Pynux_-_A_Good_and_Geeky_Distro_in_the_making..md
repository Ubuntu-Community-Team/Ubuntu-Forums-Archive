---
title: "Pynux - A Good and Geeky Distro in the making."
date: 2010-09-13
forum: Programming Talk
---

### Post by carlsmith on 2010-09-13
I'm using Server 10.4 with nothing on it, but the basic install.
What I'd like to do is be able to display graphics, but only ever in fullscreen mode and I only want one graphical output at a time. So a windows manager seems spurious and a desktop environment would be ridiculous. 
I intend to get it set up and then whack it on a little Atom netbook, with a greatly expanded python library. I'd like to end up with a pythonic, programmable calculator on steroids, but, without any graphical output, I can't even display a piechart, a pretty generic demand on a computer.
I'm thinking I might be best to use X anyway and freestyle from there, but I don't properly understand how this works and so, I could really do with some pointers before learning a ton of stuff so as to be able to thoroughly understand that it's the wrong stuff.
Further, python modules must work with this set-up essentially as is.

Deep down, I only want a text-based OS, but I want it to do graphics and keep networking.

---

### Post by Bachstelze on 2010-09-13
Unless you are running on 32 MB of RAM, there's no real reason not to use X.

---

### Post by carlsmith on 2010-09-13
Nice one.
Can you point me in the right direction? If I install X, then display an image, say I use python with pygame to display a jpg as the screen background, what would happen?
How much do I have to do to get this to work?

---

### Post by Bachstelze on 2010-09-13
> **carlsmith said:**
> Nice one.
Can you point me in the right direction? If I install X, then display an image, say I use python with pygame to display a jpg as the screen background, what would happen?
How much do I have to do to get this to work?

It depends whether you want to run X alone, or with a window manager. A window manager is technically not required, but will make your life much easier if you need to have several windows.

If you run X alone, you will have to start your programs in it from another terminal using the $DISPLAY environment variable. With a WM, you can juste use its menu.

---

### Post by carlsmith on 2010-09-13
OK, cheers mate. I'll have to look into it further. Thanks for your help.

---

