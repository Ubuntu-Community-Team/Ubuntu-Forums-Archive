---
title: "Torrent"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Roadhog35 on 2008-11-13
I'm trying to open the torrent file in windows it was a rar file in ubuntu when I try to open it, it says 

could not open "opt-maxpayne-r5.r00
archive type not supported.

thanks for any help you guys can give me I'm great with windows my friend told my ubuntu is so much better once you get used to it so I'm trying.

---

### Post by binbash on 2008-11-13
sudo apt-get install unrar-free

---

### Post by taurus on 2008-11-13
You can install unrar (from synaptic or from a terminal).  Then, unrar it with

```
unrar x opt-**maxpayne**-r5.r00
```
Hmm...  Hope this is not something illegal activity.  :-k

---

### Post by night_fox on 2008-11-13
This looks like the output from winrar when you split it into several different archives. Are there more files?

If that doesn't work then get WINE (makes windows programs work) and install winrar on it.

---

### Post by binbash on 2008-11-13
> **night_fox said:**
> This looks like the output from winrar when you split it into several different archives. Are there more files?

If that doesn't work then get WINE (makes windows programs work) and install winrar on it.

It works ;) just unrar the first file

---

