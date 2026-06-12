---
title: "update screwed my resolution"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by imT on 2008-05-06
update screwed my resolution, wtf ? (hardy)

---

### Post by shifty_powers on 2008-05-06
first things first, have you tried the simple system>preferences>screen resolution?

---

### Post by chewearn on 2008-05-06
second thing, what's your graphics hardware?

---

### Post by imT on 2008-05-06
> **shifty_powers said:**
> first things first, have you tried the simple system>preferences>screen resolution?
yes, is just 800x600, it sucks, also the nVidia proprietary drivers are missing :confused:



> **AstalaVista said:**
> second thing, what's your graphics hardware?
nVidia geforce 5500 128mb (hope i get these right)

---

### Post by subzero316 on 2008-05-06
Install envy
```
sudo apt-get install envy
```

---

### Post by imT on 2008-05-06
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package envy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  envyng-qt envyng-gtk envyng-core
E: Package envy has no installation candidate

```
well, any ideas ? what now ?:(

---

### Post by imT on 2008-05-06
oh shyt the sound dosen't work also, well f*ck this i'm downgrading to gutsy for a while.
thanks y'all i really appreciate the help :KS

---

### Post by chewearn on 2008-05-06
Did you dist-upgrade from Gutsy to Hardy?  Or fresh install Hardy?

If you change your mind and want to try Hardy again, I suggest fresh install.  I have seen some threads here problem of nvidia restricted driver fubar-ed after dist-upgrade.

.

---

### Post by muteXe on 2008-05-06
I'd do a fresh install everytime tbh.

---

### Post by shifty_powers on 2008-05-06
> **imT said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package envy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  envyng-qt envyng-gtk envyng-core
E: Package envy has no installation candidate

```
well, any ideas ? what now ?:(

sudo apt-get install envyng-gtk

---

### Post by imT on 2008-05-06
> **AstalaVista said:**
> Did you dist-upgrade from Gutsy to Hardy?  Or fresh install Hardy?

If you change your mind and want to try Hardy again, I suggest fresh install.  I have seen some threads here problem of nvidia restricted driver fubar-ed after dist-upgrade.

.

was a clean install, and i went back to gutsy cus also the sound was f*uck*d up, "gstream not installed" after the update. :lolflag: i'm an end user so i choose the easiest and simplest way to do things...gutsy dose that :)

---

