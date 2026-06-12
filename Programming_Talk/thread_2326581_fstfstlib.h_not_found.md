---
title: "fst/fstlib.h not found"
date: 2016-06-02
forum: Programming Talk
---

### Post by paulpo on 2016-06-02
Hello everyone,


 I tried to install OpenFst to use it with SphinxTrain and recompile  it with g2p enabled, and it seem to work but I got stuck with the  following error :
 checking fst/fstlib.h usability... 
no checking fst/fstlib.h presence... 
no checking for fst/fstlib.h... 
no configure: error: fst/fstlib.h header not found
 But the OpenFst binaries are well installed in /usr/local/lib/fst and the headers too in /usr/local/include/fst ;


 Can anyone give me a clue about the issue ?

---

### Post by Rocket2DMn on 2016-06-03
It may sound silly, but did you verify that the headers are actually there and have the correct (644) privileges?  Double check that the /usr/local/include/fst directory itself has 755 privileges.

---

### Post by T.J. on 2016-06-08
Assuming you are using something like an autoconf script, you will need to tell it where the headers are located.

---

