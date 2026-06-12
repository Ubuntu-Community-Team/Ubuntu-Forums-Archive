---
title: "pano e-launch ang app after 'make install'?"
date: 2008-11-17
forum: Philippine Team
---

### Post by adredz on 2008-11-17
am i starting to be a bit geeky? i dreaded this before..:)

so pano bah? after ./configure, make, make install, ano next? d ko alam pano patakbuhin ang app..hehe

---

### Post by the yawner on 2008-11-17
Anong application yang sinubukan mo i-compile?

---

### Post by Nhatz on 2008-11-17
Yup ano bang apps yung kinompile mo?
for example you compiles vlc from source, open mo terminal then just type vlc. pero alam ko pag installed na sya nasa menu mo na yun.. hehehe :)

ASTIG!:guitar:

---

### Post by adredz on 2008-11-17
it's a rare app.. aria2 ang name. it's a download manager. wla kc sa docu nor sa readme file kung pano eh.. wla din sa menu ang icon..

---

### Post by Nhatz on 2008-11-17
try typing ari.. then hit the tab key...kung nag auto complete yun na yun! hehehe :)

ASTIG! :guitar:

---

### Post by adredz on 2008-11-17
san? 
i guess it's a command line tool lang kaya ganun?

---

### Post by Nhatz on 2008-11-17
malamang.... hehehehe :)

ASTIG! :guitar:

---

### Post by adredz on 2008-11-17
hahaha. i am about to download debian kc and test it. nirecommend kc dun na use aria2 or wxDownloadFast download manager to avoid corruption of image. maiba nga, ano kaya maganda... Debian Testing or Stable? gusto ko lang matuto hehe.. more.. beyond what ubuntu can teach me..

---

### Post by loell on 2008-11-17
nakuh.. **wget** lang ang katapat nyan. :guitar:

---

### Post by adredz on 2008-11-17
> **loell said:**
> nakuh.. **wget** lang ang katapat nyan. :guitar:

oo pero mas maganda pag gamit ka nung tools kc pwede mo e-pause at e-resume at direct download pah inde torrent na mabagal hehe. so ano kaya sir loell, testing or stable? hehe

---

### Post by the yawner on 2008-11-17
Kung gusto mo ng mas bagong packages, dun ka sa testing.

---

### Post by ragadanga63 on 2008-11-17
> **adredz said:**
> oo pero mas maganda pag gamit ka nung tools kc pwede mo e-pause at e-resume at direct download pah inde torrent na mabagal hehe. so ano kaya sir loell, testing or stable? hehe

Huh?  Hindi mo magawa yan sa wget?  Install mo kaya Graphical front gwget.  Nasa Synaptic yan.

---

### Post by adredz on 2008-11-18
> **ragadanga63 said:**
> Huh?  Hindi mo magawa yan sa wget?  Install mo kaya Graphical front gwget.  Nasa Synaptic yan.

pde poh.. wget + aria2 tool. wget -c URL the first download. to resume the download after you pause it (which is done by simply closing the terminal) just do aria2c -c URL. nothing breaks, just like torrent download.. :)

---

### Post by kiminaiseah on 2008-11-21
./configure --help <-- see all extra params

eg.
./configure --prefix=/root && make && make install

then punta ka sa /root and u see /usr/local or /usr/sbin/ or /usr/bin, the yun folder name nung apps na na compile u.. tpos execute sya ./appsname

---

