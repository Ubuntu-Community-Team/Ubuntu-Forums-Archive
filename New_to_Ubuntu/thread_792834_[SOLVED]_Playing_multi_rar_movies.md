---
title: "[SOLVED] Playing multi rar movies"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by forseti42 on 2008-05-13
How do you go about playing multi rar movies on ubuntu?

Where I download the movie from told me to just unpack the first one and play that movie, but its not wanting to unpack.  What it partially unpacks won't play either.

7zip displays this error in the terminal after trying to unpack.  However I k now the password is correct.

```
CRC Failed in encrypted file. Wrong password?
```

---

### Post by mali2297 on 2008-05-13
Try the *nonfree* unrar package. To install,
```

sudo apt-get install unrar

```
Then, if the files are called example.part1.rar, example.part2.rar etc, run
```

unrar e example.part1.rar

```
It should be possible to extract through Fileroller as well.

---

### Post by Monicker on 2008-05-13
Have you considered purchasing the movie legally?

---

### Post by spydon on 2008-05-13
> **Monicker said:**
> Have you considered purchasing the movie legally?

Why would it be an illegal movie?? There are lots of legally spread movies out there packed in rar...

---

### Post by Monicker on 2008-05-13
Right. And I suppose you have a bridge you want to sell me.  :)

---

### Post by aeiah on 2008-05-13
have a look here:
[http://youtube.com/watch?v=gXFTt1u3EJg&feature=related](http://youtube.com/watch?v=gXFTt1u3EJg&feature=related)

this guy is piping to vlc, but it may work with other media players

```
unrar p -inul Batman.rar | vlc -
```

---

### Post by forseti42 on 2008-05-13
Thank you!  This works perfectly!  It turns out one of my parts was corrupt.

---

