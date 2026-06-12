---
title: "help!very turbulent bootup"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by yssida on 2008-04-25
Basically, when I boot Ubuntu it's not a pretty picture. When I select a kernel in GRUB, I am taken to to a black screen with text. Then it flickers,brings me to a usplash, and once the bar completes, black screen again, flickers for 2-5 times,then to a GDM login. After that, music plays, and blank gnome panels show up, with black background, and then wallpaper, and then I load compiz and emerald manually.

Is there a way to make the bootups a bit smoother and more polished? Like the smooth Ubuntu boots in youtube?

link:

[an ubuntu boot that is similar to mine, but mine is actually worse]("http://www.youtube.com/watch?v=FV2kKeskPYY")

[what I want to achieve]("http://www.youtube.com/watch?v=V-4OZ2X6SLY")

---

### Post by ggaaron on 2008-08-12
I'm not sure if it can be helped... I started compiz automatically after login and it was even worse - white rectangles on my wallpaper icons in random places, and when it was loaded - normal desktop=/

Flickering after grub is because usplash isn't started fast enough, and before X - Xorg probes hardware probably. This can't be helped I think, but if there is a solution for GNOME ugly start then I'd like to know this too. Splash screen doesn't help, because it disappears before anything (panels, wallpaper) appear so it can't hide anything. Maybe someone knows a way to force spalsh screen to stay longer?

---

