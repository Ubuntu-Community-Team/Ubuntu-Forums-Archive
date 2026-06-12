---
title: "missing one program"
date: 2005-10-29
forum: Programming Talk
---

### Post by tom007 on 2005-10-29
dear all,

one program i've been missing from the past with linux,

no chance to find the image viewer program 'xv' in ubuntu.

My system is 'breezy-5.10' (-> "very nice, really").

The 'debian' xv...deb (or *.tgz) program has failed by trying to compile.

user tom

---

### Post by TimonVO on 2005-10-29
```
sudo apt-get install xv
```
does that work?

---

### Post by tom007 on 2005-10-29
the answer is: no,

the message was: paket not available

; for your answer thank you very much indeed!

tom

---

### Post by hugin0 on 2005-10-31
i have your solution.  i have a build binary package that requires little hand modification to get it up and working.

first install libpng3
```
sudo apt-get install libpng3
```

then you have to link libtiff.so.4 to libtiff.so.3.  this is because the binary i built was from a gentoo box that i haven't reinstalled in over a year, or done a major upgrade. mine is located in /usr/lib on breezy.  example code:
```
sudo ln -sf /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

next pull my binary from [here]("http://www.pitt.edu/~jhs3/xv.tar.bz2").

and unpack it with this:
```
sudo tar -C / -xjf xv.tar.bz2
```

hope this helps.  any probs feel free to drop me a line.


/jhs

---

### Post by tom007 on 2005-11-15
Hello 'hugin0',

... thanks for answering!

I had tried followed your instructions, but only found '/usr/lib/libtiff.so.4 and .../libtiff.so.4.1.3; so i thought linking these both but without success by installing 'xv'.

The message was: "xv: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory"

cheers  --tom

---

### Post by dlyle65535 on 2006-09-03
Hugin0- 

Works on Drake as advertised! You rock, I can now use PIL, so here's a BUMP.


-D...

---

