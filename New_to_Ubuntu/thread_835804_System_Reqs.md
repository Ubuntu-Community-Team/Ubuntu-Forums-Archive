---
title: "System Reqs"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by tubawxman on 2008-06-20
I've been searching all over for system requirements to run Ubuntu and have been unable to locate any.  The company I work for is selling some PCs for cheap and I was considering buying one to run Ubuntu on.  It has a Celeron processor, which I am not familiar with at all.  Given the following specs, could the PC run Ubuntu?  If so, which distro would be best.

Dell GX260 
1.7 to 2.0 GHz Celeron Processor 
20GB Hard Drive 
512 MB Memory Ram 

I could upgrade the memory and HD, I'm concerned about the processor mainly.

Thanks in advance!

---

### Post by RomeReactor on 2008-06-20
Hi. That system should be able to run Ubuntu without problems. The system requirements are at the bottom of [this page]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition").

---

### Post by tubawxman on 2008-06-20
Thanks!  I knew it was probably there somewhere!

---

### Post by RomeReactor on 2008-06-20
No problem. Welcome to the forums :D

---

### Post by Bigtime_Scrub on 2008-06-20
Just some food for thought, I was running Ubuntu with about those specs. I like all of the full featured apps like amaroK, azuerus, open office, etc. When you do that things run a little on the slow side. I switched Xcfe Xubuntu and I got the performence speed I was looking for. I love me some Xubuntu :)

---

### Post by mivo on 2008-06-20
I have a laptop with very similar specs, and I found Ubuntu to be a little sluggish. I then tried out Xubuntu, and it was significantly more responsive. My recommendation would be to give Xubuntu a try. :) The community and the repositories (application databases) are the same.

---

### Post by sagor71 on 2008-06-20
hi there just new to ubuntu but interested. 1Ghz, 384MB,40GB suitable ? may system is Dell Latitude C600. desktop effects doesnt work on my system. any advice please?

---

### Post by RomeReactor on 2008-06-20
Hi. Your laptop most likely has an Intel integrated gpu, in which case it *may* be difficult to enable the effects; please open a terminal and paste:
```
lshw -C display
```
then press ENTER, and post the output here.

---

### Post by sagor71 on 2008-06-20
thanks but that didnt work.yes it has an intel display

---

### Post by RomeReactor on 2008-06-21
> **sagor71 said:**
> thanks but that didnt work.yes it has an intel display

Sorry about that; run it using sudo:
```
sudo lshw -C display
```
And post the complete output.

We need to know exactly which model of Intel gpu you have, as some Intel models are more diffcult to configure to get direct rendering--and in some cases, not possible at all. Also post the ouput of this:
```
cat /etc/X11/xorg.conf
```

---

