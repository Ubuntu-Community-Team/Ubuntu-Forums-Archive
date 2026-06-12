---
title: "[SOLVED] DVD drive problem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by shadowber on 2008-05-26
My cd/dvd rw drive just stopped working out of the blue.... any suggestions (I use hardy heron)

---

### Post by HotShotDJ on 2008-05-26
> **shadowber said:**
> My cd/dvd rw drive just stopped working out of the blue.... any suggestions (I use hardy heron)Internal? External? Old? New?  What happens when you insert a disk?  Does it spin up?

---

### Post by shadowber on 2008-05-26
> **HotShotDJ said:**
> Internal? External? Old? New?  What happens when you insert a disk?  Does it spin up?
Internal, about 8 months old (Never had a problem before) the disk does spin up, but nothing else.
(thanks for the quick reply)

---

### Post by Paqman on 2008-05-26
Check all the cables running from the back of the drive to the mobo, sometimes they work loose.

---

### Post by HotShotDJ on 2008-05-26
> **shadowber said:**
> Internal, about 8 months old (Never had a problem before) the disk does spin up, but nothing else.
(thanks for the quick reply)Ok.. that gives us something to work with. :)  Open Applications --> Accessories --> Terminal and type in:```
dmesg | grep CD
```Please post the output.

---

### Post by shadowber on 2008-05-26
> **HotShotDJ said:**
> Ok.. that gives us something to work with. :)  Open Applications --> Accessories --> Terminal and type in:```
dmesg | grep CD
```Please post the output.
I copy pasted that, and nothing came up...

---

### Post by shadowber on 2008-05-26
> **Paqman said:**
> Check all the cables running from the back of the drive to the mobo, sometimes they work loose.
I will try that just as soon as I finish dl'ing something so I can shut off the comp...

---

### Post by logos34 on 2008-05-26
> **shadowber said:**
> My cd/dvd rw drive just stopped working out of the blue.... any suggestions (I use hardy heron)

Mine did too--right after installing 55 mb worht of the new updates incl. kernel.

It deleted the existing symlinks in /dev.  Made a real mess.  I had to redo them

---

### Post by HotShotDJ on 2008-05-26
> **shadowber said:**
> I copy pasted that, and nothing came up...Ok, check the cables as suggested by paqman.  If that does not solve the problem, I'd like you to run the following in the terminal:```
dmesg > dmesg.text
```Now you can go to Places --> Home Folder to find the file and open it.  Inspect it closely for hints as to what might be going on with the drive.

---

### Post by shadowber on 2008-05-26
will do as soon as it finishes DL'ing & Installing a few stuff...
thanks again

---

### Post by shadowber on 2008-05-26
Ok, I guess it was a loose connection, thanx everyone!!!

---

