---
title: "Help creating RSS feed"
date: 2008-04-17
forum: Programming Talk
---

### Post by acvwJosh on 2008-04-17
Hello, I'm hoping someone can help me out with this:

I've got a script that records a streaming internet radio program everyday.  I'd like to transfer the saved file to my iPod through Amarok (which I also use to sync several playlists on a daily basis).  Rather than finding the new file everyday and manually transferring it to the iPod, I was thinking that I could create an RSS feed that would link to the file, and point Amarok to the feed as a podcast.  The script that records the program could easily be extended to update the RSS file.  This way every day the new file would be automatically be waiting to sync.

The problem:  The enclosure field of the RSS file can't link to a local file (unless I'm just doing something wrong).  So, how would I go about linking to the file?

Any suggestions would be greatly appreciated!

---

### Post by mssever on 2008-04-17
What about the file: scheme? file:///foo/bar.baz

Alternately, you could install a web server (such as apache), configure it to only accept connections from 127.0.0.1, and set the DocumentRoot to wherever you keep your files. Then you can go to [http://localhost/foo/bar.baz](http://localhost/foo/bar.baz)

---

### Post by nanotube on 2008-04-18
go to the source:
rss specification: [http://www.rssboard.org/rss-specification#ltenclosuregtSubelementOfLtitemgt](http://www.rssboard.org/rss-specification#ltenclosuregtSubelementOfLtitemgt)

which says that as of rss 2.0, any [iana-specified uri scheme]("http://www.iana.org/assignments/uri-schemes.html") is allowed in the enclosure url field (which includes file:, as suggested my msserver.

not using amarok, so don't know if it will play nice with file, but according to the spec, if it supports rss2, it should. :)

otherwise, just install a localhost-only webserver, also as msserver suggests. only thing i would add, for a simple task such as this, using lighttpd might be easier than configuring apache...

---

### Post by mssever on 2008-04-18
> **nanotube said:**
> for a simple task such as this, using lighttpd might be easier than configuring apache...Yes. The reason I mentioned apache is that's the server I know. But you should be able to handle a really simple server. Look through Synaptic, and you might be able to find one that's simpler even than lightppd. I've even seen basic webservers written in just a few lines of Python code.

---

### Post by nanotube on 2008-04-18
> **mssever said:**
> Yes. The reason I mentioned apache is that's the server I know. But you should be able to handle a really simple server. Look through Synaptic, and you might be able to find one that's simpler even than lightppd. I've even seen basic webservers written in just a few lines of Python code.

yea, python ftw! :)

---

### Post by acvwJosh on 2008-04-20
> **mssever said:**
> What about the file: scheme? file:///foo/bar.baz

Alternately, you could install a web server (such as apache), configure it to only accept connections from 127.0.0.1, and set the DocumentRoot to wherever you keep your files. Then you can go to [http://localhost/foo/bar.baz](http://localhost/foo/bar.baz)

Brilliant ideas -- Thanks guys!  I knew that the Ubuntu Forums would come through for me.  I'll try using file:, and if that doesn't play nice with Amarok I'll try setting up a web server in Python.  Much thanks!

---

### Post by mssever on 2008-04-20
By the way, I ran across the smallest webserver I've seen; just two lines of Python issues as a single command: ```
python -c 'import SimpleHTTPServer; SimpleHTTPServer.test()'
```

---

### Post by nanotube on 2008-04-22
> **mssever said:**
> By the way, I ran across the smallest webserver I've seen; just two lines of Python issues as a single command: ```
python -c 'import SimpleHTTPServer; SimpleHTTPServer.test()'
```

tried it - works! very nice :)

---

