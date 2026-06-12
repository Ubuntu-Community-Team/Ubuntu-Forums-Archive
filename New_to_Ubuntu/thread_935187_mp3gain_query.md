---
title: "mp3gain query"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by gedzilla on 2008-10-01
I've been using mp3gain and easy mp3gain very successfully and after playing about with it thought i'd normalize the gain on my entire music directory using

find . -name *mp3 -exec mp3gain -a -k {} \;

Of course this worked great, but I was just wondering if anyone could tell me how to set my entire music directory to a different level (the default is 89db and i'd like it a bit higher - like 91.5 to 92.5db)

---

### Post by Jakadinho on 2008-10-18
I would like to know this very much also

---

### Post by vanadium on 2008-10-18
Did you look at the manual page for mp3gain? (man mp3gain)

---

### Post by Jakadinho on 2008-10-18
I tried many things including reading manula but nothinghelped untill now.

I watched some german, france, spanish sites but i got lucky on polish one




The comand that i used (and worked) is
[COLOR="DarkRed"]**find . -type f -iname '*.mp3' -print0 | xargs -0 mp3gain -r -d 6.2 {} \;**[/COLOR]

where 6.2 is how much increase of volume will be in db. Default is 89 db and this code makes it 95.2 db

---

