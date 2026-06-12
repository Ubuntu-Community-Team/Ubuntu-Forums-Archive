---
title: "Extract images drawn with Cairo?"
date: 2009-07-09
forum: Programming Talk
---

### Post by Fzang on 2009-07-09
I really like the background of Gnome-do's docky form and thought it'd look slick in other themes. Problem is, it's "drawn by Cairo" as I was told on the IRC.

I have tried isolating the dock background in GIMP but it doesn't quite look like the original BG.

So is it somehow possible to extract the image from the Cairo code to a normal .png image?

PS: I know nothing about coding :D

---

### Post by monraaf on 2009-07-09
As a matter of fact, cairo surfaces do have a write_to_png method. Since Gnome-do is written in C#, I can't really help you any further though.

---

