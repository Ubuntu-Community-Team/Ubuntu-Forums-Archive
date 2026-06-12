---
title: "GTS installation"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by ashvin on 2008-08-28
I am trying to install the GTS library on hardy. i'm getting almost infinite error mesages and finally get these...

make[3]: *** [cdt.lo] Error 1
make[3]: Leaving directory `/media/disk/gts/gts-0.7.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/media/disk/gts/gts-0.7.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/disk/gts/gts-0.7.6'
make: *** [all] Error 2

i guess these are general installation errors not directly related to GTS. can any one get me out of here?

---

### Post by jpds on 2008-08-28
> **ashvin said:**
> I am trying to install the GTS library on hardy. i'm getting almost infinite error mesages and finally get these...

make[3]: *** [cdt.lo] Error 1
make[3]: Leaving directory `/media/disk/gts/gts-0.7.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/media/disk/gts/gts-0.7.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/disk/gts/gts-0.7.6'
make: *** [all] Error 2

i guess these are general installation errors not directly related to GTS. can any one get me out of here?

Could you please paste all the errors at [paste.ubuntu.com]("http://paste.ubuntu.com") - it looks like you have a missing library/headers.

---

### Post by Nepherte on 2008-08-28
GTS appears to be in the ubuntu repositories. You can install it in synaptic (see [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)) or with this command:
```
sudo apt-get install libgts-0.7-5
```

---

### Post by ashvin on 2008-08-28
thanks JPDS,

have done that, the message is partial but i think it gives the overall picture.

[http://paste.ubuntu.com/41177/](http://paste.ubuntu.com/41177/)

---

### Post by ashvin on 2008-08-28
have tried that Nepherte,

libgts-0.7-5 is already the newest version.
libgts-0.7-5 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

does that mean gts is completly installed?

---

### Post by Nepherte on 2008-08-28
Yes.

---

### Post by ashvin on 2008-08-28
Thanks Nepherte.

---

