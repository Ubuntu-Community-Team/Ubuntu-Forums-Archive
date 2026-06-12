---
title: "Which IDE should I use?"
date: 2013-03-21
forum: Programming Talk
---

### Post by BlastDV on 2013-03-21
Hi everyone. I've been asked to develop a simple Picture Editor, restricted to the .bmp format and capable of doing some simple operations to loaded pictures (rotating, getting the negative and stuff like that). Also, I can not use any library to input/output the image so I must program all this by myself. It's also requested to show the picture you've just open and the changes applied as well so an interface is needed.

Now, I've been playing around with Anjuta, trying to build a simple interface and finding a way to link my code with it but I'm not going anywhere with this, maybe is because I haven't looked enough information or tutorials but since I don't have many time to develop this (yeah, is homework :)) I would like you to reccomend me the best IDE or similar to make this. Any Idea?

Thanks for reading ;)

(By the way, I'm using C++)

---

### Post by r-senior on 2013-03-22
Do you have restrictions on the windowing toolkit or a free choice (GTK, wx, Qt, etc)? Does this eventually need to compile on Windows? Are there any other requirements about how the project should be submitted for assessment?

These could affect your choice more than ease of use.

---

### Post by BlastDV on 2013-03-22
Thanks for answering! Well, I don't have any kind of restriction but the ones I named. I'd prefer to develop it for Windows since I am more familiarized with it, but I don't have any problem on coding for Linux. I heard something about wx, and worked a little bit with Qt. As I said, I do need to develop the whole input/output and capabilities manually, so I though about the ncurses library to be able to draw and stuff like that, but I think that would be going way too basic =/

---

### Post by Jacks0n on 2013-03-23
If you're after a framework/API to develop an application and for simple image editing, I'd recommend using [Qt]("http://qt.digia.com/"). It's open source, it has a great community, and has great performance. AFAIK the image editing will be offloaded to the GPU also. Probably not a big deal, but pretty cool :-).

If you need more advanced usage (sounds like you won't in this case), you can look at [ImageMagick]("http://www.imagemagick.org/").

In terms of an IDE, [Qt Creator]("http://qt.digia.com/Product/Developer-Tools/") goes hand in hand with Qt. Porting between Linux and Windows is mostly a re-compile away.

Good luck!

---

