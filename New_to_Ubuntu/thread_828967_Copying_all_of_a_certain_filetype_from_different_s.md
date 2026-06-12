---
title: "Copying all of a certain filetype from different subdirectories into one directory."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by powerpleb on 2008-06-14
I just copied the contents of my IPOD to my hard disk and used Ex Falso to rename them to coherent file names. Is there a command with which I can delve into the myriad of subdirectories on the IPOD's structure and drag out all the mp3 and m4a files?
I tried this but it didn't work:```
cp -r /IPOD/*.mp3 .
```

---

### Post by Gannon8 on 2008-06-14
> **powerpleb said:**
> I tried this but it didn't work:```
cp -r /IPOD/*.mp3 .
```That looks like a syntax error. You aren't specifying the folder to put it in.

---

### Post by powerpleb on 2008-06-14
> **Gannon8 said:**
> That looks like a syntax error. You aren't specifying the folder to put it in.

Yes I am, the dot means the current directory

---

### Post by Gannon8 on 2008-06-14
Oh, didn't see that.

Try: ```
cp -r /IPOD/*/*.mp3 .
```

---

### Post by powerpleb on 2008-06-14
I think the problem with the command is that cp is looking only for mp3s in the /IPOD folder and not it's subdirectories where they all are. How do I make it recurse through the subdirectories and gather all the mp3s from them?

---

### Post by powerpleb on 2008-06-14
> **Gannon8 said:**
> Oh, didn't see that.

Try: ```
cp -r /IPOD/*/*.mp3 .
```

Thanks a lot:smile:, that worked.

---

### Post by Joeb454 on 2008-06-14
Try using ```
cp -R /IPOD/*/*.mp3 .
``` If you want just MP3 files :) the syntax for recursively copying is '-R' not '-r' Remember - Linux is case sensitive ;)

---

### Post by Gannon8 on 2008-06-14
> **powerpleb said:**
> I think the problem with the command is that cp is looking only for mp3s in the /IPOD folder and not it's subdirectories where they all are. How do I make it recurse through the subdirectories and gather all the mp3s from them?Yes, that is most likely the problem. My command should make it look in the subdirectories.

---

### Post by powerpleb on 2008-06-14
> **Joeb454 said:**
> Try using ```
cp -R /IPOD/*/*.mp3 .
``` If you want just MP3 files :) the syntax for recursively copying is '-R' not '-r' Remember - Linux is case sensitive ;)

Then I guess if I want to include all the m4a files too it would be
```
cp -R /IPOD/*/*.m* .
```

---

### Post by Joeb454 on 2008-06-14
I'd imagine that would work yes :)

---

