---
title: "Listen Audio Player don't open."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by rhc on 2008-04-27
I was using Listen and I'm very satisfied with.
But sometimes it doesn't open.
Then i uninstall it through Synaptic completely,and it opens again.
I dunno howto solve it.
When i run it from terminal
it gives;
> xxx@xxx-desktop:~$ listen
No musicbrainz support (musicbrainz2 missing)
No iPod support
No Audio cd support (musicbrainz2 missing)
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
Segmentation fault



What can i do with it,i like Listen Player...

---

### Post by MontelEdwards on 2009-04-30
> **rhc said:**
> I was using Listen and I'm very satisfied with.
But sometimes it doesn't open.
Then i uninstall it through Synaptic completely,and it opens again.
I dunno howto solve it.
When i run it from terminal
it gives;



What can i do with it,i like Listen Player...
Yeah I love listen too.
It looks like musicbrainz2 may be missing.
uh, ```
sudo apt-get install musicbrainz2
```
try that.

---

