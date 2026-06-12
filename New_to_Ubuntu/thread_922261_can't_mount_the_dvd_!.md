---
title: "can't mount the dvd !"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by medya on 2008-09-17
I burnt a DVD some months ago , I could easily read it in windows or in pervious ubuntus...

now after months I put it and I get this error when I click on it in Comptuer :
[B]
Invalid mount option when attempting to mount the volume[/B]

---

### Post by Pro-reason on 2008-09-17
Do other DVDs work OK?

---

### Post by Bucky Ball on 2008-09-17
Were these DVDs made on a Vista machine or are 'off the rack' ... ie: bought ones?

---

### Post by medya on 2008-09-17
other DVDs work fine , just this one .
I belive I burnt them on xp or ubuntu . (no vista for sure)

---

### Post by Pro-reason on 2008-09-17
If just this DVD has a problem, then there is nothing we can do.  A physical problem with that DVD has developed.  You could try techniques for cleaning or smoothing the surface.  Google for them.

---

### Post by Bucky Ball on 2008-09-18
Sounds like a dead DVD to me. Check for scratches or greasy fingerprints if you haven't already. :)

---

### Post by medya on 2008-09-18
> **Bucky Ball said:**
> Sounds like a dead DVD to me. Check for scratches or greasy fingerprints if you haven't already. :)

it is so clean and new, I hardly used it, and it works very well in windows .

so it is not that .

---

### Post by Bucky Ball on 2008-09-18
Well, there must be something different about this one. If all your others work in Windoze and Ubuntu, but this one and this one only doesn't, the plot thickens. Anything you can think of? Burnt on someone elses machine? Different file compression, speed, application? You might find a clue here. This is why I asked about Vista before, but apparently XP can do this too (possibly one of the 'improvements' of Service Pack 3 (SP3)).

[http://ubuntuforums.org/showthread.php?t=650697&page=2](http://ubuntuforums.org/showthread.php?t=650697&page=2)

---

### Post by Pro-reason on 2008-09-18
This could be an issue with Windows’ new way of doing UDF DVDs.  (Solution: install the latest UDF support.)

It could be a minor burn error that Windows is tolerating, but Ubuntu is not (and should).

You could use the “dd” command to put an exact image of the DVD on your hard drive, and then use [file-recovery techniques]("https://help.ubuntu.com/community/DataRecovery") to extract the files.

---

