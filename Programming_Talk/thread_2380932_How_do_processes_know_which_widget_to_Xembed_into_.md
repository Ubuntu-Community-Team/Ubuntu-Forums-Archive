---
title: "How do processes know which widget to Xembed into a Gtkplug in C?"
date: 2017-12-23
forum: Programming Talk
---

### Post by sandman887 on 2017-12-23
I've been studying the Xembed spec, but I'm still confused on one thing. In this app I'm writing, I want to embed a menubar from another process. But Xembed doesn't say how to tell the other process which widget I want. So how is it supposed to know which widget that it should embed into the plug? I am planning on using a Gtk socket and Gtk plug. Using d-feet, I've looked at the methods available in apps like banshee and other apps that have menu bars, but didn't see any methods that looked relevant.

Googling didn't turn up any answers. After spending a long time trying to figure this out, I've been unable to, but if anyone can help, I'd greatly appreciate it!

Thanks in advance

---

