---
title: "[SOLVED] can't open &amp;quot;___.part1.rar&amp;quot;"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by agreatguy6 on 2008-10-20
I just downloaded some amazing music (I've had Ubuntu before, but i wiped my harddrive, so it's like i'm starting from scratch again) and they're in the form:

"This_is_my_music_blah_blah_blah.part1.rar" and
"This_is_my_music_blah_blah_blah.part2.rar" et cetera.

Problem is, it's not extracting it :/

what can I do? D: :(

---

### Post by aeiah on 2008-10-20
do normal .rar archives work? if not, you havent installed rar or unrar. if they do, perhaps the problem lies in you not having all the .rar archives. you can still perhaps extract some stuff if you only have a few of the archives. try running unrar or rar from the command line

---

### Post by jamesrl on 2008-10-20
Install rar by
```

sudo apt-get install rar

```

---

### Post by ww711 on 2008-10-20
```
 cat ___.part1.rar ___.part2.rar ___.part3.rar ___.part4.rar > somenewfile.rar
```

---

### Post by agreatguy6 on 2008-10-21
Thank you :)

i figured it out ^_^


if someone could mark this [solved]?

---

### Post by H.Callahan on 2008-10-21
> **agreatguy6 said:**
> Thank you :)

i figured it out ^_^


if someone could mark this [solved]?

You can mark it as solved yourself by choosing the "Thread Tools" option located at the top of the page, just above your original post and a little to the right.

---

### Post by agreatguy6 on 2008-10-21
ohhhhhh
lol, it's good to read the directions, isn't it? 
gracias :)

---

