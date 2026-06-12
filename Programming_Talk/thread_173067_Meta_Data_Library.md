---
title: "Meta Data Library"
date: 2006-05-09
forum: Programming Talk
---

### Post by moberry on 2006-05-09
Hi I am working on a for-fun project that involves me needing to read meta-data from audio files. I found a library called tunepimp which does this. However, tunepimp looks to be overkill for what I need to do. Does anyone know what library to use to go about reading meta data from multiple audio formats? I suppose i could use the standard vorbis, and mpeg libraries to do this, but I was hoping there was a multi-purpose library for doing this. Thanks in advance.

-jordan

---

### Post by LordHunter317 on 2006-05-09
I think tunepimp may be your best bet.  Tag reading for say, MP3 is incredibly and stupidly difficult.  I'm not even sure anyone truly gets it 100% correct, because of the way the ID3 standards are written.  

I could be mistaken.  I'm sure it's overkill, but it's probably better than doing it yourself.

---

### Post by moberry on 2006-05-09
Thanks I was leaning towards that till i was going through the GStreamer documentation. Gstreamer has support for meta tag reading, and since its format-independent I can use the same function calls for both mpeg, vorbis, etc. Which was what I was aiming for.

---

