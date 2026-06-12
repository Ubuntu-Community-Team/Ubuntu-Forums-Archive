---
title: "Encoding problem"
date: 2009-05-07
forum: Programming Talk
---

### Post by MeLight on 2009-05-07
Didn't find a more suiting forum for this, sorry in advance if I insult anyone ;). 
Anyway, we are working on a text processing software, and a specific part of it takes the text only in utf8 encoding. We have an Arabic large text corpus which is supposedly encoded in utf8 - and when opened in [Kate]("http://kate-editor.org/kate") (or our soft) it says that PART of the file has problematic encoding, we narrowed down the problematic range to 2000 lines. 
Now the surprise:
When the 2000 lines file is split in to two separate files neither of them has the encoding issue! Thus we can not really find the problematic part. Any help on what might be causing this or workarounds to finding the problematic part would be greatly appreciated.

I'm attaching the short file.

---

### Post by mdurham on 2009-05-07
There is no problem using gedit

---

### Post by MeLight on 2009-05-07
I should have mentioned it. Gedit, FireFox, IE etc don't show this. But our not-utf8-sensitive soft rejects it and Kate which is more advanced in the encodings issue then gedit detects the problem also.

---

