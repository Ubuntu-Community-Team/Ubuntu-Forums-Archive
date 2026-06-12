---
title: "sscanf is ugly"
date: 2009-03-23
forum: Programming Talk
---

### Post by Schitso on 2009-03-23
So, I'm parsing an HTML file with lines that look like this (variable data in caps):
[HTML]&nbsp;&nbsp; <a href=conversation?time=UNIXTIME&id=HEXID >STRING</A>(INTEGER)<BR>[/HTML]

And I came up with the following line of code to do so:
```
sscanf(line, "&nbsp;&nbsp; <A HREF=conversation?time=%*d&id=%x >%[^<]</A>(%d)",&id, username, &unread)
```

Is there a cleaner/nicer(/shorter) way I could do this? I'm told that I should be avoiding *scanf anyway.
(I wish I could use Perl :( )

---

### Post by crazyfuturamanoob on 2009-03-23
Maybe use an existing XML parsing library?

---

### Post by Simian Man on 2009-03-23
That's not so bad.  Try doing the same with C++'s cin if you want ugly!

---

### Post by Schitso on 2009-03-23
The page isn't even HTML compliant, would an XML parser work?

---

### Post by nvteighen on 2009-03-23
This is exactly what you would use Perl for... :p

No great deal, really: you're using what you have available.

---

