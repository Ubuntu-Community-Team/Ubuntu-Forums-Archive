---
title: "Use perl to position and resize windows - is that a suitable language?"
date: 2010-09-19
forum: Programming Talk
---

### Post by finny388 on 2010-09-19
I've had some programming experience in the past and want to get back into it if casually on linux and Windows (I'm starting a new job in a Windows environment - If you can't beat'em, well, at least don't use them at home!))

As one task I want to open, resize and position windows for various work situations (simple e.g. browser on left, document on right, calculator in corner)

I was told by a linux guru that perl is his swiss army knife of languages.

I was hoping to learn perl and use this as a useful project exercise.
Is it an appropriate way to go for this task? Will it be a chore to have a Windows version of this script too?

thanks

---

### Post by nvteighen on 2010-09-19
Hm... that'd be almost a Window Manager on its own. I'm not sure whether a program can interact with other programs' windows... Refer to your Window Manager's API (Compiz, Metacity... whatever you're using).

---

### Post by worseisworser on 2010-09-19
Yeah, this sounds like a window manager. Pretty much any language with bindings to XLib (or with a FFI so you can create these bindings yourself) can do this. If Perl doesn't already have bindings to XLib, I'm 100% sure it has a FFI facility or library.

For instance, here's a tiling window manager written in a somewhat unusual language; Common Lisp: [http://www.nongnu.org/stumpwm/](http://www.nongnu.org/stumpwm/)

---

