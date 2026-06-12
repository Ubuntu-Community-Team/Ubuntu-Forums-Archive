---
title: "Why Synaptic search is so slow?"
date: 2007-06-14
forum: Programming Talk
---

### Post by Laterix on 2007-06-14
I'm not sure is this a right forum for this post, but I thought that here people have more knowledge about programming.

I'm just wondering why Synaptic Package Manager search is so slow as it is at the moment. For example "apt-cache search" is almost instant. It seems that synaptic doesn't use any cache and I think it really should! It's so frustrating to wait between every search...

---

### Post by Soybean on 2007-06-14
When you search in Synaptic, if you switch the "search in" drowpdown to "Name" instead of "Name and Description", it should be pretty much exactly as fast as apt-cache (which doesn't search the descriptions by default).

---

### Post by Laterix on 2007-06-14
> **Soybean said:**
> When you search in Synaptic, if you switch the "search in" drowpdown to "Name" instead of "Name and Description", it should be pretty much exactly as fast as apt-cache (which doesn't search the descriptions by default).
Are you sure that apt-cache doesn't search in description text? I tested **apt-cache search pygtk** and **comix** package showed up. There is no **pygtk** in the name, but there is **pygtk** string in it's description. Anyway, package cache for synaptic would be appriciated.

---

### Post by Tundro Walker on 2007-06-15
I've noticed this too, and just attributed it to all the overhead that comes when using a GUI-based program (IE: manipulating the on-screen forms, filling in text areas, etc.)  Still annoying though.

---

