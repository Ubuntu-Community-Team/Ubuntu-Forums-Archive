---
title: "Import IE bookmarks into Chromium Info"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by sherrillsml on 2012-02-13
Brand new to lubuntu. Installed11.1 with Windows XP dual boot onto ageing netbook and it is once again useful. One problem that I had was importing bookmarks from IE into Chromium 16. After much searching I finally found this solution:

In the IE bookmark exported html file insert the following line just above
<TITLE>Bookmarks</TITLE>

<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">

Then use Chromium's Bookmarks->Bookmark Manager and select Organise->Import Bookmarks from HTML file.

What a relief and the netbook is no longer a XP dog :D

---

### Post by Rodney9 on 2012-02-13
Well Done.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by sherrillsml on 2012-02-14
> **Rodney9 said:**
> Well Done.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

Thanks Rodney, the past 10yrs I have had to live in Bill's world. I was a geophysics application developer using Solaris, Xwindows/Motif over a decade ago and I appreciate all the help in getting back up to speed on a real OS again. :D

---

### Post by Megaptera on 2012-02-14
I find Xmarks a great way to back up and sync my bookmarks/favourites. Hope it's of interest:
[http://www.xmarks.com/about/features](http://www.xmarks.com/about/features)

---

