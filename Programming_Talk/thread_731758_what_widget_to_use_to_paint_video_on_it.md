---
title: "what widget to use to paint video on it?"
date: 2008-03-22
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-03-22
I want a suggestion. I am making a media player application. And I am wondering, what widget should I use to paint the video on? I mean the "black space" totem and others use when displaying video.

thank you

---

### Post by stroyan on 2008-03-22
You can get the source to totem and other video players to see just howthey are implemented.  Totem has a BaconVideoWidgetClass that it implements as a direct subclass of GtkWidgetClass.  Getting and studying the source for other projects are vital skills for open source software development.  It is well worth your time to become comfortable with 'apt-get source' and code browsing tools like cscope.

---

### Post by SledgeHammer_999 on 2008-03-22
ok thanx. the problem is that I am not patient enough to figure out someone else's code and, of course, I am a amateur in programming.

---

