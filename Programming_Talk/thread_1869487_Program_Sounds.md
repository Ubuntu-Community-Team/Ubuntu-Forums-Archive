---
title: "Program Sounds?"
date: 2011-10-25
forum: Programming Talk
---

### Post by CoffeeRain on 2011-10-25
How do you program sounds? Is there a way to use midi codes, or frequency or something to do this? Maybe a python or c module? Any other way would work too. I was thinking something like this...

[www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp](www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp)

...but I was told this wasn't possible with modern computers. :confused:

---

### Post by Zugzwang on 2011-10-26
The simple answer is to use a library that provides the functionality that you need. The library does the communication with a sound device driver for you. Popular choices are "gstreamer", "libSDL", or if you program using the QT framework anyway, the QT framework.

If you want to circumvent binary dependencies, you can also just call some external command line audio player from your program, although this is less efficient and a bit prone to security bugs.

---

### Post by 11jmb on 2011-10-26
Perhaps this can be a good starting point on your question about Python modules

[http://wiki.python.org/moin/Audio](http://wiki.python.org/moin/Audio)

---

