---
title: "Help debuging Javascript"
date: 2010-08-04
forum: Programming Talk
---

### Post by rigao on 2010-08-04
Hello.

I've found a javascript in the web which I want to use in a program of mine, but it is buggy. I don't know much about javascript, but I decided I would give it a try. 

The code seems to be compressed, because when I use the extension firebug (I think) it shows me the normal javascript code (which is a mess, nobody could understand it) and another option to show me another code that seems to be deduced from the first one.

There is anybody that knows how to decompress it so I can modify it, and then compress it again?

The javascript comes from the page

[http://pgnview.edicypages.com/](http://pgnview.edicypages.com/)

in the download section.

Thank you in advance.

---

### Post by era86 on 2010-08-04
Are you saying that the code isn't nice to read?  What you could do is copy and paste that code in javascript lint or some sort of validation.  Might make it more bearable to read.

---

### Post by myrtle1908 on 2010-08-04
> **rigao said:**
> Hello.

I've found a javascript in the web which I want to use in a program of mine, but it is buggy. I don't know much about javascript, but I decided I would give it a try. 

The code seems to be compressed, because when I use the extension firebug (I think) it shows me the normal javascript code (which is a mess, nobody could understand it) and another option to show me another code that seems to be deduced from the first one.

There is anybody that knows how to decompress it so I can modify it, and then compress it again?

The javascript comes from the page

[http://pgnview.edicypages.com/](http://pgnview.edicypages.com/)

in the download section.

Thank you in advance.

It's very difficult decompress/de-obsfucate as you cannot determine what variables and the like were originally named.  Normally devs provide a 'debug' or 'decompressed' version of the code.

In your case ... 'jsPgnViewerUnpacked.js' is included in the download.  Use that.

---

### Post by rigao on 2010-08-04
Thank you very much. I didn't see the uncompressed version :oops:

---

