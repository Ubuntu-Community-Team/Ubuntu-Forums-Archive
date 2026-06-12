---
title: "Script to login to gmail and save feed"
date: 2009-09-16
forum: Programming Talk
---

### Post by MrBoxes on 2009-09-16
I'm trying to figure out how to write a script that log's into gmail and downloads a feed of unread messages the url for that is ```
https://mail.google.com/mail/feed/atom/
```

I think I'm on the right track with urllib or libgmail maby. So I don't know what to include. Looking for some help getting on the right track. Thank's in advanced.

P.S I need this to be a python script. And I'd like to do this without including anything special like libgmail. If thats possible

If this help's my goal is to emulate the wget script I have.

Trying to use
[http://www.feedparser.org/](http://www.feedparser.org/)
but I don't know how to make the script save the output in a new file.

```

wget --http-user=some.guy --http-passwd=dog "https://gmail.google.com"

```

---

### Post by MrBoxes on 2009-09-16
Bump

---

### Post by Mirge on 2009-09-17
Quick to bump there are ya? :P

[http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/)

What specifically are you having trouble with?

---

