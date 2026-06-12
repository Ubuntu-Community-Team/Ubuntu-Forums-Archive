---
title: "FujiXerox CP105b Printer Driver"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by LesPeters2 on 2012-11-02
I'm a newbie to Linux with very little prior programming experience.
I have a perfectly good Fuji Xerox cp105b printer that works great with a Windows 7 computer. I can't find any drivers to make it work under Ubuntu/Linux. Can anyone help me?

Cheers

Peter L

---

### Post by Anthony Fok on 2013-09-01
Hello,

You might also like to read this thread:
[INDENT]Fuji Xerox DPCM205FW laser multifunction: [http://forums.whirlpool.net.au/archive/1792647](http://forums.whirlpool.net.au/archive/1792647)[/INDENT]

And search for "CP205", "foo2hbpl", and "13.04" for some of the relevant posts.

It turns out that, in Ubuntu 13.04, the **printer-driver-foo2zjs** package comes with **/usr/bin/foo2hbpl2** and has experimental support for CP205 (and presumably CP105b and CP205w too).

See also the upload to Debian (hence Ubuntu) which added CP205 support:
[INDENT][http://lists.debian.org/debian-printing/2013/03/msg00030.html](http://lists.debian.org/debian-printing/2013/03/msg00030.html)[/INDENT]

I was considering getting this printer myself, but was worried about support in Linux, and was glad to read some new success report from Ubuntu users in the Whirlpool forum.

Hope this helps!

Cheers,
Anthony

---

### Post by Anthony Fok on 2013-09-01
Sorry, I should have read more carefully... I just noticed on [http://foo2hbpl.rkkda.com/](http://foo2hbpl.rkkda.com/) this piece of information:

[INDENT]Fuji-Xerox cp105b: Unsupported. Uses HBPL version 1[/INDENT]

Don't know if there is new development since then, but worth trying to see if CP105b works or not...

Nevertheless, if it indeed does not yet work, sorry for giving you false hope.

But perhaps you could help with development using /usr/bin/hbpldecode ?  :-)  <grin, duck, run>...

---

### Post by Iowan on 2013-09-01
Old thread - Closed.

---

