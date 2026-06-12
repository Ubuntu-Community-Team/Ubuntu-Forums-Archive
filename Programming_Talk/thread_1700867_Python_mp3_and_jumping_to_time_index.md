---
title: "Python: mp3 and jumping to time index"
date: 2011-03-05
forum: Programming Talk
---

### Post by m'vee on 2011-03-05
Hello,

I'm looking for a way to do the following with Python: Open an mp3 file and play a section of it, not necessarily the whole file. Sort of like accessing a large mp3 with a cue sheet.

I know there are some sound libraries for Python (not all supporting mp3) but before going deeper into one I'd like to know which one is best suited. I had a look at the pygame mixer, but it doesn't seem to support seeking within a file. I tried mplayer in slave mode which is not bad but there are some unpleasant sound glitches when jumping to a certain time index. Also you have to start playback before you can jump to a time index.

So, any ideas?

Regards
m'vee

---

### Post by cgroza on 2011-03-05
Did you take a look at gstreamer?
[http://pygstdocs.berlios.de/pygst-tutorial/playbin.html](http://pygstdocs.berlios.de/pygst-tutorial/playbin.html)

---

### Post by m'vee on 2011-03-06
I looked at some of the gstreamer examples and this looks promising. Thank you! :)

---

