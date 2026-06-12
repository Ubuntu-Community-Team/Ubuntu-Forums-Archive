---
title: "notify-osd updates, timing"
date: 2009-12-08
forum: Programming Talk
---

### Post by tars_ac on 2009-12-08
I've written a simple script in Python using pynotify to be triggered when the caps lock is pressed to pop up a notifier bubble.  It works great, except that the bubbles take way too long to go away, so they queue up and aren't actually super helpful in figuring out your current caps lock state.  I see that there's an update mechanism that replaces the bubble - this is actually what I want to happen, but short of writing a daemon for this, which is overkill, I can't find a way to access the previous popup.  I also can't find a way of controlling the expiration time, either on a per-bubble basis or system-wide.  I would really like to find a system wide method in addition to this, because several other bubbles on my system take too long as well.

Does notify-osd support anything that would let me do this?  I noticed that the brightness control and volume control seem to be able to update.  Can someone point me to how they manage to do this, or even the source?  I'm hoping it's not just some daemon running in the background...

---

### Post by tars_ac on 2009-12-09
Anyone have any experience with this?

---

### Post by sisco311 on 2009-12-09
> **tars_ac said:**
>  I noticed that the brightness control and volume control seem to be able to update.  Can someone point me to how they manage to do this, or even the source?

(only) icon notifications are updated in real-time.

[https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD") 

```
notify-send -i /path/to/icon -h "string:x-canonical-private-synchronous:true" -h "string:x-canonical-private-icon-only:true" " "
```

---

### Post by tars_ac on 2009-12-12
Interesting.  I'll play around with this.

Thanks.

---

### Post by bornagainpenguin on 2010-01-21
> **tars_ac said:**
> Interesting.  I'll play around with this.

Thanks.

Has your playing around yielded any results?  Personally I'm shocked that Ubuntu (or Gnome) doesn't have the ability to somehow hook into ACPI events like the numbers lock and caps lock keys and display an onscreen overlay like the way they do for volume control or brightness.  Something that worked like iKey does on Windows would be a great boon for those of us on laptops or using wireless keyboards that no longer include a hardware indicator of this status.

--bornagainpenguin

---

### Post by tars_ac on 2010-01-23
I'm still using rev 1 of the script.  I've found that it kind of grows on you - you get used to the delay.  Not ideal, but I couldn't find a good way to get the bubble to replace.  It looks like it's possible, but I don't have enough time right now to make it happen.

---

