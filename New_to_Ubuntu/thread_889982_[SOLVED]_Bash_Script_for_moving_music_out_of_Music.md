---
title: "[SOLVED] Bash Script for moving music out of Music/artist/album and into Just Music"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-08-14
I thought this would be a simple exercise for me in scripting but I am at a loss at the moment.
I have many individual folders in my music and video directories each containing one, or a very small number of files. I thought I could write a simple bash (or, less likely since I am JUST learning it, Python) script which would copy the contents of a folder into the parent Music folder and then move on to the next folder and continue until all my individual files are at the top level (only one folder). It doesn't necessarily need to delete the folder when done, since it would be easy enough to just highlight them and delete them once emptied.

I know this is probably exceedingly easy for even a moderately experienced scripter. I am ashamed that I myself am at loss as to how I could do it.
Thanks.

---

### Post by finer recliner on 2008-08-14
how about you post what you have so far, and one of us can point out some problems or add suggestions to your original idea. you're not going to learn if you just ask someone else for the whole answer ;)

---

### Post by freak42 on 2008-08-14
some people manage to do this kind of things with a single command line. I however am not one of them, but you might becoming one of them anyhow
look into the xargs command 'man xargs' especially the samples at the bottom, with this you can do your task in no time.

hth

---

### Post by JohnGalt131 on 2008-08-20
> **freak42 said:**
> some people manage to do this kind of things with a single command line. I however am not one of them, but you might becoming one of them anyhow
look into the xargs command 'man xargs' especially the samples at the bottom, with this you can do your task in no time.

hth

Thanks finer recliner for giving me a challenge. and thanks freak42 for pointing me to xargs. I hadn't heard of it.

I played with the 'find' and the 'xargs' commands and came up with this:
~/Music$ find . -type f -print0 | xargs -0 -I a mv a ./
This was exactly what I needed. By the way, it didn't take me this long to figure it out :) ... It just took me this long to realize that others may find my answer helpful.

---

