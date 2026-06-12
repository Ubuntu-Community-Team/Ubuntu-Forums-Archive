---
title: "[SOLVED] deleting trash"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Tart on 2008-05-13
Hello All,

I have a small problem with emptying trash. I copied several folders form cd and they all had read-only status on harddrive. I moved them to trash eventually, but now I cannot clear trash it tells me that I don't have permission to delete them.
How to handle this?
Thanks

---

### Post by saj0577 on 2008-05-13
```
gksudo nautilus 
```

Then try to clear trash, probavbly not the best way I admint but they way I would do it.<--Novice.

Saj

---

### Post by macaholic on 2008-05-13
You could delete them manually from a terminal like so:```
sudo rm -r ~/.local/share/Trash/files/<folder name>
```

---

### Post by macaholic on 2008-05-13
> **saj0577 said:**
> ```
gksudo nautilus 
```

Then try to clear trash, probavbly not the best way I admint but they way I would do it.<--Novice.

Saj
Problem with that is, he won't have the same trash folder unless he navigates to it manually in the location i noted.

---

### Post by Tart on 2008-05-13
Thank you that worked perfectly

> **macaholic said:**
> You could delete them manually from a terminal like so:```
sudo rm -r /home/matt/.local/share/Trash/files/<folder name>
```

---

### Post by saj0577 on 2008-05-13
> **macaholic said:**
> Problem with that is, he won't have the same trash folder unless he navigates to it manually in the location i noted.


My Bad. :)

Saj

---

### Post by newbuntuxx on 2008-05-13
just curious: couldn't you change the permissions of the folders with chmod?

---

### Post by macaholic on 2008-05-13
> **newbuntuxx said:**
> just curious: couldn't you change the permissions of the folders with chmod?
You could, but that just changes the permissions on that particular directory, and if you do it recursively, the files currently in that directory. However if you move a write-protected file into that directory, it retains its original permissions.

---

### Post by JoshuaRL on 2008-05-13
You could also try the GUI way, by right-clicking and making sure the permissions are what you want them to be.  I got a bunch of MP3s from a friend that were all read-only (who knows why) and that worked for me.

---

### Post by saj0577 on 2008-05-13
> **JoshuaRL said:**
> You could also try the GUI way, by right-clicking and making sure the permissions are what you want them to be.  I got a bunch of MP3s from a friend that were all read-only (who knows why) and that worked for me.


Yeah same happens to me all the time I always have to change the permissions otherwise i cant play them.

Saj

Added:I always thought it was my mate being awkward.

---

### Post by JoshuaRL on 2008-05-13
> **saj0577 said:**
> Yeah same happens to me all the time I always have to change the permissions otherwise i cant play them.

Saj

Added:I always thought it was my mate being awkward.

Hmm, I wonder what that's all about.  It only happened once, and to the ones I got off of a couple MP3 CDs I got.  You say it keeps happening?

But yeah, what's up with that?  "I can't alter my own MP3s?  What kind of facist state am I living, oh wait, (changes permissions) nevermind.

---

### Post by saj0577 on 2008-05-15
I dont know to be honest i wish I did.

Saj

---

### Post by deleonjavier on 2008-05-24
yeah this changed from gustsy to hardy. in gutsy it was ~/.Trash now its ~/.local/share/Trash. blah I administer a hardy server and I forgot the localtion sometimes.

---

