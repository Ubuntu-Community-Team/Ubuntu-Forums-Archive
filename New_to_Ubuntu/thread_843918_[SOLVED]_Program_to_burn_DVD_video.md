---
title: "[SOLVED] Program to burn DVD video ?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Drakkor on 2008-06-28
I want to burn a copy of a DVD, which has .bup,.ifo,vob files, which program will do that ? Thanks :)

---

### Post by RomeReactor on 2008-06-28
Hi. K3B will burn the files to a DVD; look for it in Syantpic (System->Administration->Synaptic) and make sure you also install the libk3b2-extracodecs package. Or to install it from the terminal:
```
sudo aptitude install k3b libk3b2-extracodecs
```
When you open K3B, go to the 'Tools' section of the menu bar; there should be an option to burn to 'Video DVD'. Grab all the BUP, IFO, and VOB files and drop them in the VIDEO_TS folder K3B will give you, then burn the disc.

---

### Post by svk on 2008-06-28
You can try Brasero, DeVeDe, K3b, among many others, I'm sure.  Personally, K3b is my favorite.  I'm sure there's a ton of CD/DVD recording software out there: try running a search in Synaptic Package Manager, or whatever package manager you happen to use (System -> Administration -> Synaptic Package Manager).

---

### Post by Drakkor on 2008-06-28
Thanks,guys,K3b is the one,got it burned ! :)

---

