---
title: "GNOME broadcasts/events API?"
date: 2010-08-12
forum: Programming Talk
---

### Post by v1nsai on 2010-08-12
I just started using suspend on my laptop instead of hibernating (man its faster) but I'm worried about how much power it uses while suspended.  I wanna write myself a program that will listen for the suspend command, and record the battery percentage and the current time.  Then when the laptop is brought out of suspend, it will record the current time and battery percentage again, then tell me how much battery I lost and how long it was suspended.

However, I'm having trouble finding interfaces to listen on to get these broadcasts, I've tried the GNOME documentation but it all seems to be about GTK interface design.  How do I use GNOME events in my programs?

---

### Post by interval1066 on 2010-08-12
Take a look at the dbus interface and libnotify.

---

### Post by v1nsai on 2010-08-15
Cool, thanks looks like thats exactly what I was looking for.

What bus would I want to listen on for battery info and time?  I'm trying to find a good bus reference but haven't found one yet.

---

