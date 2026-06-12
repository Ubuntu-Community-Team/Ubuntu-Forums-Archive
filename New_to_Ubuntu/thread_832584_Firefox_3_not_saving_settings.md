---
title: "Firefox 3 not saving settings"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-06-17
I updated to the the latest version of firefox today as I had updates notification.

now it doesn't want to save settings, for example I'll choose not to show my web developer toolbar, I close and reopen and it'll be showing.

its the same with all the other firefox options.....

I assume this is some sort of bug, but does anyone know of a fix for this?

---

### Post by Primefalcon on 2008-06-17
Ok I've tried a complete reinstall, even tried changing the persmissions of the folders, no joy firefox 3 will simply not remember any settings

---

### Post by kansasnoob on 2008-06-17
And I'll bet you have Pre-Released updates checked in your Software Resources.

In just a few days it should be ready for prime time and then you'd get the new  FF from Recommended Updates.

---

### Post by Primefalcon on 2008-06-17
in the software sources under updates

all I have ticked is important and recommended, neither  pre-released or unsupported are ticked

---

### Post by Primefalcon on 2008-06-17
though I might try the pre-released it might solve my problem for the time being

---

### Post by kansasnoob on 2008-06-17
OK, I jumped to conclusions, which is a bad thing.

Don't change that yet. Go to Synaptic, click on reload, and see if you have any "broken packages".

---

### Post by Primefalcon on 2008-06-17
no none

---

### Post by kansasnoob on 2008-06-17
OK at the upper FF toolbar go to Tools > Error Console and click on whatever link(s) it shows.

Sometimes that will lead to a fix. Not often, but sometimes.

---

### Post by Primefalcon on 2008-06-17
dang I don't know if it's something I did that fixed it or not but....

I cleared the error log, and change some settings and reopened, and now after having this problem all day, its just working now.

well I don't know what to say except errr thank you obviously something had an effect, I just don't know what, weird

---

### Post by cariboo on 2008-06-17
I'd export the bookmarks and then just delete the default directory in .mozilla/firefox

Jim

---

### Post by kansasnoob on 2008-06-17
If it ain't broke no more stop fixing it.

---

### Post by Primefalcon on 2008-06-17
I chmodded that to 777 which never had an effect but.... either way I'll leave it be now since it seems to be working, but if it acts up again I'll do that

---

### Post by Primefalcon on 2008-06-17
I have it back to standard level defaults but have mysself listed as the owner instead of root, still going good, and I'm done for messing now :-S

---

