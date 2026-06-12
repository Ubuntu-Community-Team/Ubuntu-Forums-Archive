---
title: "On-system Dictionary?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-18
Are there any dictionary programs for Ubuntu that I could use to replace the internet-enabled dictionary that comes as a default? My campus has so-so WiFi, so often I don't have access to the internet when I need to find the meaning of (a) word(s).

---

### Post by C.S.Cameron on 2008-09-18
Have you tried stardict from the repositories?

---

### Post by Pro-reason on 2008-09-18
I don't think there is a decent, up-to-date, open-source English dictionary (word lists don't count).  It would require so much work.

P.S. This stardict seems rather focussed on Chinese.

---

### Post by C.S.Cameron on 2008-09-18
The Webster's Revised Unabridged Dictionary (1913) 	RPM 	tarball 	GPL, 28M, 160161 words
is pretty big, I'll let you know if I can get it to work, sort of old though.

stardict works great, you can load a few different dictionaries at:
[http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php](http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php)
I tried Merriam Webster 10th dictionary, I think it is from 1998 and only 2.5M

---

### Post by querent on 2008-09-24
i cannot for the life of me figure out how to install a dictionary i downloaded from the sourceforge site.  i go to 'manage dictionaries', and click 'add', and just get this blank, unresponsive window with an 'ok' and 'cancel' button at the bottom.  Neither the original .tar.bz2 nor any of the contents therein (including a .dict.dz file that archive manager doesn't know what to do with) will drag and drop into this window.  and i cannot type there.

i promise a 'thank' if someone can help!  (is that legal?)

---

### Post by Denestria on 2008-09-24
I installed stardict with
```
sudo apt-get install stardict
```
then downloaded the Merriam Webster 10th dictionary from the sourceforge page.
Extracted the archive and moved the 3 files to the right directory.
```
sudo mv merriam* /usr/share/stardict/dic
```
Open stardict and it shows up in the dictionary list.

---

### Post by Grimhound on 2008-09-24
Is there any way to kill the popup window that appears when words are highlighted with Stardict?

---

