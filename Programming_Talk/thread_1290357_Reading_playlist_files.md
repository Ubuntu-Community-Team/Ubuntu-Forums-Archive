---
title: "Reading playlist files"
date: 2009-10-13
forum: Programming Talk
---

### Post by poisonkiller on 2009-10-13
Hello!
I'm currently developing an internet radio player in python and hit a problem. Apparently a lot of radios like to put their urls in a playlist file (m3u, pls, asx, et cetera), but I have no idea, how to parse all of them. So, maybe there is a python library, already made program (in python) or executable (in some other language which outputs the urls) out there, which can do it for me. Any suggestions? :)

---

### Post by wmcbrine on 2009-10-13
These formats are trivial to parse. I wrote my own Python code for that, but it's not really portable to another app. But if you want to look at it:

[http://repo.or.cz/w/pyTivo/wmcbrine.git?a=blob;f=plugins/music/music.py](http://repo.or.cz/w/pyTivo/wmcbrine.git?a=blob;f=plugins/music/music.py)

In its simplest form, an .m3u file is just a plain text list of files, one per line. It can also have comments, marked by '#'. That's really all you need to know, but there's an extended version that uses the comments to provide additional info, if you want it. Those lines look like:

```
#EXTINF:300,Your Title Here
```

The number is the length in seconds. Sometimes it's -1; sometimes it's omitted.

More: [http://hanna.pyxidis.org/tech/m3u.html](http://hanna.pyxidis.org/tech/m3u.html)

A .pls file is not vastly more complex. Again, it's a text file, this time in .ini-like format. Just look at some and you can pretty well understand the format. [http://en.wikipedia.org/wiki/PLS_(file_format](http://en.wikipedia.org/wiki/PLS_(file_format))

And .asx is more of the same, but in a pseudo-XML format this time. (I say "pseudo" because it doesn't have any XML declaration or doctype, but Python's XML libraries should be able to parse it.) [http://en.wikipedia.org/wiki/Advanced_Stream_Redirector](http://en.wikipedia.org/wiki/Advanced_Stream_Redirector)

---

### Post by wmcbrine on 2009-10-13
P.S. A complete parser for .m3u files:

```
[line.strip() for line in file('foo.m3u') if not line.startswith('#')]
```

:)

---

