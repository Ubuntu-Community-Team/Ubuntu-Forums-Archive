---
title: "Kile not finding .sty files"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Azrael84 on 2011-10-05
Hi,

I just updated TexLive to the 2011 version from the native one Ubuntu comes with that is supposed to be 2 years behind. However my LaTeX editor Kile is having issues finding  .sty files now. For example it can't find tensor.sty or beamer.sty etc

These style files do exist in /usr/local/texlive/2011/texmf-dist/tex/latex/tensor etc however. I tried updating the PATH variable as mentioned on the Texlive installation guide (i.e. by typing PATH=/usr/local/texlive/2011/bin/i386-linux:$PATH ) but this doesn't seem to have done anything for Kile's recognition.

Are these in the correct place? or is it just that Kile needs its path updating or something?

thanks for any help

---

### Post by duphenix on 2011-11-11
There are two things you should check.

1) use synaptic package manager and double check that ALL ubuntu packages for latex and texlive are removed

2)look here [http://www.tug.org/pipermail/tex-live/2011-January/028357.html]("http://www.tug.org/pipermail/tex-live/2011-January/028357.html"), After reading this I put 

```
PATH=/usr/local/texlive/2011/bin/x86_64-linux:$PATH
```

as the first line in  (I'm running a 64 bit version of ubuntu, hence the x86_64

```
/etc/profile
```


I am using texworks though.  Hint: Use ppa:texworks/ppa for texworks with texlive 2011

---

