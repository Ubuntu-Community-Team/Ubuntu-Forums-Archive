---
title: "Note: Problems with gstreamer0.10-fluendo-mp3"
date: 2006-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by EvanL on 2006-08-25
Hey everyone-

I just resolved an issue that I've had for the past few days.  I had MP3 output in the gstreamer package, but the output was muddy and garbled in the midrange.  Nothing too terrible, but it bothered me enough to do somethinga bout it.

Anyway, I found that the gstreamer0.10-fluendo-mp3 package was to blame.  Uninstalling that and using the gstreamer0.10-plugins-ugly for MP3 decoding works fine, and no more problems in Rhythmbox!

For reference, this is with an Intel ICH8x0 AC'97 sound device.  Now, if only I could get 4-channel output to work in Rhythmbox...

-Evan

---

### Post by Stéphane Raimbault on 2006-09-03
I had the same problem on Dapper on the same chipset ICH5 (30mn wasted to search :mad:)

Do you know if bug report exists for this problem ?

---

