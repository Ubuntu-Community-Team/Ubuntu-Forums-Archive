---
title: "What will be the impact of Wayland on programming?"
date: 2011-12-19
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-12-19
So the other day I asked about making some exposé feature myself for some shell-like program, in spite of Compiz already doing that.

For this, I am planning to use Python-Xlib, to query the X WM and get the list of windows, and their respective thumbnails.

But then I remember: Wayland is coming. I'm a hobbyist and rather mediocre programmer (but nonetheless enthusiast). So I want to use the little time I give to programming well, by thinking on long term.

The problem is, I don't really grasp how Wayland will impact programming at WM level and in my case, whether it is wise to use Python-Xlib to do the job (although I don't see what else I could use).

So what will be impact of Wayland on programming? And (how) do you get prepared for it?

---

### Post by 3Miro on 2011-12-19
From what I understand you would be able to run Xorg on top of Wayland as sort of a compatibility layer. I guess it is save to keep on using the old standard, Wayland will not require for all of the graphical software to be rewritten.

---

### Post by nvteighen on 2011-12-19
Just be aware that this is a more-or-less Ubuntu-specific thing... AFAIK, neither Debian nor any other distro is going that route (yet).

---

