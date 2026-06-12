---
title: "[SOLVED] Python wave"
date: 2007-04-17
forum: Programming Talk
---

### Post by holihue on 2007-04-17
How can i make .wav files with the wave module in python?


Thanks

---

### Post by pmasiar on 2007-04-17
did you tried [http://www.google.com/search?q=python+wave](http://www.google.com/search?q=python+wave) ?

---

### Post by holihue on 2007-04-17
Yes, but I need some kind of *data* in wave.writeframes().

I don't know what data it is.

---

### Post by snoop on 2007-04-17
The data is whatever audio you have opened up.

For example, if you want to add a wave file to the end of another wave file,

you open both files -> then take the audio (the data) from the second one and use writeframes() to add it to the first file.

---

### Post by holihue on 2007-04-17
thanks

---

