---
title: "Need to screen scrape, any languages that have this in their API?"
date: 2007-07-11
forum: Programming Talk
---

### Post by AncientPC on 2007-07-11
This is a long shot but I'm looking for any language that has methods that help screen scrape, preferably something that will match a section of the screen to a local image file but pixel matching will work as well.

---

### Post by pmasiar on 2007-07-11
Lucky you: [templatemaker](http://www.holovaty.com/blog/archive/2007/07/06/0128) for Python was introduced week ago!

---

### Post by AncientPC on 2007-07-11
Thanks, template maker looks very promising but from what I can tell it parses files and matches it against a template to extract data.  I actually was going to write something like this but for another purpose (automated torrent download for new torrents).

However I'm looking for something that screen scrapes, unless there's another way to read text off a flash files that I am unaware of.

---

### Post by boralyl on 2007-07-12
For screenscraping I use urllib2 to download the source and parse the html document with regular expressions.  However there are many options, you can check out some tutorials at [http://www.awaretek.com/tutorials.html#scrape]("http://www.awaretek.com/tutorials.html#scrape")

---

### Post by cwaldbieser on 2007-07-14
> **AncientPC said:**
> Thanks, template maker looks very promising but from what I can tell it parses files and matches it against a template to extract data.  I actually was going to write something like this but for another purpose (automated torrent download for new torrents).

However I'm looking for something that screen scrapes, unless there's another way to read text off a flash files that I am unaware of.

It sounds like you want something like a screen grabber + OCR.
ImageMagick comes with the "import" utility for grabbing pictures of windows, and there are probably lots of others.
"apt-cache search ocr" shows me several OCR tools, but I haven't used any of them.

---

### Post by AncientPC on 2007-07-14
Thank you both very much.

---

