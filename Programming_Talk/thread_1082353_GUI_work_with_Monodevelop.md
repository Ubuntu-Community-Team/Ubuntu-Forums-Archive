---
title: "GUI work with Monodevelop"
date: 2009-02-27
forum: Programming Talk
---

### Post by boombox1387 on 2009-02-27
I'm new to Monodevelop (and fairly new to programming in general), but I'd be interested in messing around with the code in some existing projects just to try things out.  I've successfully checked out the latest versions of Tasque and Banshee, and I've had fun browsing through their code, but I was wondering if there's an easy way to use the GUI editor on either of these programs.  When I build my own GUI apps, of course, I am able to use the GUI editor, but so far I have not been able to find a way to do this when working with other C# projects.  Any advice will be much appreciated.

---

### Post by jimi_hendrix on 2009-02-27
i have never used the GUI editor in mono, i know it has one, but i like to do it by hand, more control and not that hard

---

### Post by directhex on 2009-02-27
Tasque has a hand-made UI directly in the code

Banshee uses Glade in a few places (./src/Core/Banshee.ThickClient/Resources/banshee-dialogs.glade)

---

