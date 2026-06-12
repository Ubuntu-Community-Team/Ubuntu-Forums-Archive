---
title: "creating a tar of a directory"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-05-12
I want to create a tar of my music directory, what is be best way to do this, also I would like to burn it to dvd and it would span more than one dvd, is this possible?

---

### Post by billgoldberg on 2008-05-12
> **Mick8882003 said:**
> I want to create a tar of my music directory, what is be best way to do this, also I would like to burn it to dvd and it would span more than one dvd, is this possible?

Right-click on the top folder (for example the "Music" folder) and press "create archive".

About the mutltiple dvd's, I never tried it before, but I sure it can be done.

---

### Post by pedro_orange on 2008-05-12
If you insist on using gzip:

```
tar czf myfile.tar.gz dirname
```

Which should pack the directory 'dirname'.

---

### Post by Mick8882003 on 2008-05-12
ne thing better than gzip? needs to be compatible with windoz 2

---

### Post by pedro_orange on 2008-05-12
Well gzip is standard for tarballs...

You can use gzip; compress (old style UNIX); zcat (system std zipper); bzip2; uuencoded or......zip

zip is the Windows style zip.

Eg;

```
zip -r myfile.zip dirname
```

I think you need to tell zip to recursively go through all the files in a directory to pack a whole directory. I'm probably wrong tho. Just how I'd do it.

Thing I like about zip; is that it doesn't delete the old files like gzip and bzip2 does.

---

