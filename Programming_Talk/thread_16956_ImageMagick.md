---
title: "Image::Magick"
date: 2005-02-24
forum: Programming Talk
---

### Post by ebrowne on 2005-02-24
Hey I'm having trould installing Image::Magic on my system using perl can anyone tell me what packages I need installed to get this working
Thanks

---

### Post by WW on 2005-02-24
The **perlmagick** package is in warty's universe repository.  Is that what you are trying to install?

---

### Post by ebrowne on 2005-02-25
Yea that's the package I tried installing using CPAN first but that failed and now I can't get it to install using synaptic or apt-get any ideas?

"perlmagick: Depends: libmagick6 (= 5:6.0.2.5-1ubuntu1) but 5:6.0.2.5-1ubuntu1.3 is to be installed"

Is the message from both synaptic and apt-get

---

### Post by ebrowne on 2005-02-25
Hey,
sorry about that I solved the problem with anoter post by adding universe to my security line in /etc/apt/source.list


Thanks though

---

