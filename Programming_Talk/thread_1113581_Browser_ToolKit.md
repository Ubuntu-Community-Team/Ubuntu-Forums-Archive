---
title: "Browser ToolKit"
date: 2009-04-01
forum: Programming Talk
---

### Post by WitchCraft on 2009-04-01
Hi, question:

I am writing a MAN 2 html converter to display man pages.
Now unzipping man pages in memory and converting them to html really is not a problem, but the problem is wxHTML only supports a very limited range of html tags.

Now I basically need to embed a browser in my application.
I tried Mozilla, unfortunately, this does not compile, and every attempt of me to correct the configure file / installing libraries failed.

Now I tried wxWebKit, which is very cool (once I got it compiling), apart from the fact that it is 230 MB in size... - as a dynamic library...


I need a WebKit/Browser in C++ that I can embed in my application (it should work on Windows, too).
Max size i would say about 10 MB, statically linked.

Anybody knows of a working alternative?

---

### Post by MaxIBoy on 2009-04-01
Try using gecko:
[https://developer.mozilla.org/en/Gecko_Embedding_Basics](https://developer.mozilla.org/en/Gecko_Embedding_Basics)
It's a rendering engine used by Firefox, Thunderbird, Galeon, Epiphany, and many more applications.

---

### Post by Vadi on 2009-04-01
Gecko or Webkit will both work for you.

---

### Post by smartboyathome on 2009-04-01
I'd recommend Webkit for this type of thing. Geck would weigh down your program a lot more than Webkit would, with not much benefits over Webkit in this situation.

---

### Post by Vadi on 2009-04-01
I'd chime in that Liferea is also switching from Gecko to Webkit for their next release.

---

### Post by Sinkingships7 on 2009-04-01
I'm going to chime in with another vote for WebKit. Fast, as well as more lightweight than its contender, Gecko. As stated, there's no good reason for choosing the latter over the former.

---

### Post by WitchCraft on 2009-04-02
Fine, mozilla doesn't compile as already said, and webkit is very large.
I'm gonna use the source of kazehakase, it uses gecko, and it compiles.

---

### Post by Vadi on 2009-04-02
Um, interesting outcome. Good luck!

---

