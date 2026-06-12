---
title: "Handling input from multiple devices in Gtk"
date: 2012-03-19
forum: Programming Talk
---

### Post by jediborger on 2012-03-19
So first off I should just state what I want to accomplish and perhaps someone will let me know if I'm looking in the right place.

Basically I want to have multiple keyboards attached to a single computer and a Gtk app running which can differentiate input based on what keyboard it came from. So I want to capture all events from one keyboard and process them differently, leaving input from the other keyboard to be treated normally. This "second" keyboard is really a barcode scanner if that makes any difference.

So I was looking through the Gdk documentation and I can find ID's for each keybaord but I'm not really seeing a way to manipulate how the events are propagated from the device to the application. Do I need to go lower in the stack and do X calls?

Any advice would be appreciated!

---

