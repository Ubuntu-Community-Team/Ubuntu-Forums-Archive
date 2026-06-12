---
title: "Checking a version number from ftp site part 2"
date: 2010-08-03
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-08-03
*Smiles*. This 'issue' is the same as here: ```
http://ubuntuforums.org/showthread.php?p=9664432#post9664432
```
.. except the link being:
[html]http://downloads.videolan.org/pub/videolan/testing/[/html]
;).

---

### Post by Bachstelze on 2010-08-03
You should be able to figure out something from what I've told you in the other thread, only the grep lines will need some adjusting.

---

### Post by Intrepid Ibex on 2010-08-03
Well, that's just it. The output needs to be [number].[number].[number]-pre/-rc/-test.[number]. The number parts are easy but the "-pre/-rc/-test" is not so.

---

### Post by Bachstelze on 2010-08-03
```
'[0-9]+\.[0-9]+\.[0-9]+-(test|pre|rc)[0-9]*'
```

---

### Post by Intrepid Ibex on 2010-08-04
Ok, well that wasn't so bad.

---

