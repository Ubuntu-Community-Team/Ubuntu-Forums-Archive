---
title: "[SOLVED] Fiinding a specific file"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by bilijoe on 2008-04-23
This is embarrassing; I used to be  UNIX system admin.:confused:  I know there is a trivially simple way to do this, I just can't get my old brain to recall it.  Somewhere out there on my system is a file named Anyfile.mine.  How do I find it, if I've forgotten where I put it?

---

### Post by Monicker on 2008-04-23
> **bilijoe said:**
> This is embarrassing; I used to be  UNIX system admin.:confused:  I know there is a trivially simple way to do this, I just can't get my old brain to recall it.  Somewhere out there on my system is a file named Anyfile.mine.  How do I find it, if I've forgotten where I put it?

find / -name Anyfile.mine


Also, if you have slocate or mlocate installed, do an updatedb and then "locate Anyfile.mine".

---

### Post by tamoneya on 2008-04-23
```
find / -name Anyfile.mine
```

---

### Post by bilijoe on 2008-04-23
Thanks guys--I knew it was simple.  Tried find, but think I was leaving out the "/".  I just go braindead once in a while.  That's one of many things that makes these forums, and Ubuntu, in general, so great!  Thanks again.:popcorn:

---

### Post by SOULRiDER on 2008-04-23
You can also use
```
locate <file>
```

---

### Post by Dr Small on 2008-04-23
For reference, you can use:
```
find / -name filename.ext
```

Or:
```
sudo updatedb
locate filename.ext
```

Dr Small

---

### Post by steveneddy on 2008-09-28
> **SOULRiDER said:**
> You can also use
```
locate <file>
```

One of my most used commands

---

