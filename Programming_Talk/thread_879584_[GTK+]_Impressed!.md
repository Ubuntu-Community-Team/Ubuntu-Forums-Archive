---
title: "[GTK+] Impressed!"
date: 2008-08-04
forum: Programming Talk
---

### Post by nvteighen on 2008-08-04
Hi!

Just wanted to say I'm really impressed on how GTK+ works. I'm writing my very first program with it and the logic behind it is that coherent and transparent that it's really worth for anyone with some programming level to try.

Of course, 50% of the great GTK+ experience comes from the great documentation it has.

Thumbs up for these nice people!

(OK, the full story: do you remember [this thread]("http://ubuntuforums.org/showthread.php?t=877245"). Well, I dropped ncurses. It has been impossible for me to work with it and decided to migrate it to GTK+...).

P.S.: I don't have any experience with Qt, so I don't have any opinion on it either positive or negative.

---

### Post by Jessehk on 2008-08-04
I'm just curious: are you using it with C, or with one languages it has bindings for (Python, Ruby, Perl, etc)?

---

### Post by Kadrus on 2008-08-04
C and Python are most used for GTK apps.
> I'm just curious: are you using it with C, or with one languages it has bindings for (Python, Ruby, Perl, etc)?
I think he's using C,[http://ubuntuforums.org/showthread.php?t=877245](http://ubuntuforums.org/showthread.php?t=877245)

---

### Post by Lux Perpetua on 2008-08-04
> **Jessehk said:**
> I'm just curious: are you using it with C, or with one languages it has bindings for (Python, Ruby, Perl, etc)?Don't forget [Vala](http://live.gnome.org/Vala). (It hasn't reached release 1.0 yet, but...it exists.)

---

### Post by nvteighen on 2008-08-04
> **Jessehk said:**
> I'm just curious: are you using it with C, or with one languages it has bindings for (Python, Ruby, Perl, etc)?

C + GTK+, the "classic" one. I'm designing the GUI by hand; it's a very basic one, so I don't think I should go for Glade. (And I want to have my hands dirty...).

The impressive part is the intelligent design it shows in every part. 

1) It doesn't rely on hidden global variables that are affected by any function you call, like ncurses. Everything is under your control and it's easily detectable what you're doing and what not. 
2) The versatile way you can pass GtkWidget objects almost everywhere with a cast.
3) The coherent function naming it's **really** appreciated. After you've learned the pattern, you just can guess how the function should be called and, if supported for that widget, it will work.
4) A precious demonstration of highly-efficient OOP in C, of course (thanks to the underlying GLib). I'm sure this is why it could be so easily ported to "native" OOP languages.
5) Finally, it's very well integrated to C. I mean: a GTK+ code will obviously look very different to Standard C, but it doesn't disturb the regular C "look & feel" (if there's such a thing).

Of course, nothing is perfect and it has drawbacks:
1) Some amount of boilerplate code... at least in C.
2) As GTK+, GLib and befriended libraries uses their own memory allocators, memory debuggers fail miserably with these libraries.
3) Code being a bit too verbous in some places, due to the effort of mainting naming coherence. OK, the priority of the GTK+ devs is clear, but maybe some shorter conventions could be interesting... Anyway, I just have to write some nice custom preprocessor macros and solved!
4) The weird way needed to compile. I've set a makefile, but it's still annoying.

So, I'm just driven by the excitement of having found a tool I'm enjoying to use :) (The last one was the CUPS library... also, a nice piece)

---

