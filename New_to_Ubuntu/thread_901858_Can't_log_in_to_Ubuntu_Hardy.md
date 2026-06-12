---
title: "Can't log in to Ubuntu Hardy"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by rudedoggx on 2008-08-26
Hey, I just installed Hardy Heron on my brother's Compaq Desktop PC, and he cannot seem to log in. After running the initial setup, he hasn't even been able to access the desktop. Ubuntu simply boots, then shows the wallpaper. A few seconds later, we're automatically logged out and kicked back to the sign-in screen. We haven't logged in successfully once :) Any help, please? Thanks in advance!

---

### Post by Linux_Man on 2008-08-26
Ok, what is your graphics card? Is it Intel, nVidia or ATI? Generally ATI and nVidia cards have a sticker near your CPU sticker that says ATI or nVidia, though sometimes they don't,

---

### Post by rudedoggx on 2008-08-26
It's an ATI Radeon Xpress 200

---

### Post by alienexplorers on 2008-08-26
Are you getting any error messages before you get booted back to the sign on screen?

---

### Post by rudedoggx on 2008-08-26
No, it's very strange. Part of the screen just turns black, and out we go.

---

### Post by Linux_Man on 2008-08-26
Have you tried logging in to a failsafe gnome session? I had a computer with an ATI graphics card and the live-CD for 8.04 wouldn't ever log in unless I did failsafe gnome (afterwords, I manually ran all the programs that made up gnome and they all worked)

---

### Post by rudedoggx on 2008-08-26
No, I haven't tried that. What's a failsafe gnome session?

---

### Post by Linux_Man on 2008-08-26
On your login screen, there should be a button called "Sessions" click on that and then choose "Failsafe GNOME" then try logging in. It will give you a desktop with a terminal, but it will have X running so we can see if it is a graphics problem or not.

---

### Post by rudedoggx on 2008-08-26
Alright, I've got the session up and running. What's next?

---

### Post by Rome.konig on 2008-08-26
notice of caution. ATI video drivers for linux is somehow inefficient. It gives me lots of problems as well. You can try to Xorg drivers under synaptic manager.

---

