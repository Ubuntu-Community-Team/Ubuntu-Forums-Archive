---
title: "[GTK] listen to style_set signal without creating a visible widget"
date: 2010-07-07
forum: Programming Talk
---

### Post by smani on 2010-07-07
Hello, I have the following question: I'd like to create some sort of background service which monitors style changes of gtk applications, i.e. basically listen to the style_set events (and then syncs the styles to kde applications). 
A working approach is to create some widget and connect the style_set listener, but it would be more elegant if the service would be purely in background, i.e. no visible widget and so on. Can anyone give me some hints on how to create an object (gobject subclass I guess) which can listen to the style_set events?
Thanks,
smani

---

### Post by nvteighen on 2010-07-07
> **smani said:**
> Hello, I have the following question: I'd like to create some sort of background service which monitors style changes of gtk applications, i.e. basically listen to the style_set events (and then syncs the styles to kde applications). 
A working approach is to create some widget and connect the style_set listener, but it would be more elegant if the service would be purely in background, i.e. no visible widget and so on. Can anyone give me some hints on how to create an object (gobject subclass I guess) which can listen to the style_set events?
Thanks,
smani

Events are always associated to some object: an event is something that happens to something. If your program is a service, the logical thing IMO is to look whether GDK or some lower level instance of the GTK+ library has something that allows you to detect the style change or something related to that.

---

