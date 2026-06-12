---
title: "music help (duplicates)"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by fknyeah on 2008-10-07
Does anyone know of two good programs that could help me with my music.

I have a large music collection(from friends and having a great internet connection and network at college).  I was wondering if there was a program that could help with the trouble of finding and taking care of duplicate files.  Also is there a good program to help with incorrectly/poorly named files?

Thanks for the help!
SFK

---

### Post by tangibleorange on 2008-10-07
> **fknyeah said:**
> Does anyone know of two good programs that could help me with my music.

I have a large music collection(from friends and having a great internet connection and network at college).  I was wondering if there was a program that could help with the trouble of finding and taking care of duplicate files.  Also is there a good program to help with incorrectly/poorly named files?

Thanks for the help!
SFK

you can re-tag and rename your music with MusicBrainz picard tagging application. it can be installed with this command:

```
sudo apt-get install picard
```

as for duplicates, you could try FSLint:

```
sudo apt-get install fslint
```

i think it has a remove duplicates option. hope that helps!

---

