---
title: "[SOLVED] Weird Rythmbox problem"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-11-27
Whenever I start Rythmbox it prompts me with a message saying it doesn't have the suitable codecs and offering me to search for them. If I accept, nothing pops up. The thing is, after the message is gone, it can play all my music files just fine. How do I make it a little more self-aware and stop this message from popping up?


Thanks in advance for all replies,

Paulo.

---

### Post by Michael.Godawski on 2008-11-27
What type of audio file do you mean?

Do you have installed the restricted extras and the other gstreamer plugins like bad and ugly?

---

### Post by Bucky Ball on 2008-11-27
> **Michael.Godawski said:**
> 

Do you have installed the restricted extras and the other gstreamer plugins like bad and ugly?

System->Administration->Synaptics

Search for and install:

ubuntu-restricted-extras

---

### Post by GepettoBR on 2008-11-27
Yes, I already have the restricted extras, w64 codecs and the gstreamer plugins: the Good, the Bad and the Ugly (BTW I love the maintainers for naming the plugin sets like that).

Most of my collection consists of VBR MP3s, but I also have some AAC and OGG-encoded files, and possibly a few dozen MP3s I might have accidentally ripped as ABR or CBR. One album is encoded in FLAC. But I have no playback problems. Like I said, I can play all my music files, but the pop-up still apears.

---

### Post by Michael.Godawski on 2008-11-27
Try this (taken from [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566))
> 
You can always uncheck  EDIT/PREFERENCES/MUSIC(tab) / "watch my library for new files" for a quick workaround. It stops the "searching of codecs". Of course if you add new music you will need to recheck it once , but then turn it back off. At least it stops the searching for codecs every time...


---

### Post by GepettoBR on 2008-11-27
It's a crude workaround, but it had the desired effect. Thank you. Thread solved.

---

