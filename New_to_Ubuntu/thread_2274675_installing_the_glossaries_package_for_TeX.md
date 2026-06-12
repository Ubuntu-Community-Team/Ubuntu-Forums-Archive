---
title: "installing the glossaries package for TeX"
date: 2015-04-21
forum: New to Ubuntu
---

### Post by hmiersch on 2015-04-21
hi.
i just tried to install the glossaries package. in the instructions theres a line that says "remember to refresh tex's database" or something, but it doesn't say how to do that. so how do i do that?
thanks

---

### Post by Impavidus on 2015-04-21
TeX's database can be refreshed using the command```
sudo texhash
```

---

### Post by hmiersch on 2015-04-22
i tried sudo texhash, and it solved the problem. but then another one popped up: for some reason the glossaries package requires the etoolbox package. so i installed that one, and now one of them requires another package. looks like i've got my work cut out...

so the question is, why didn't glossaries require those packages the last time i installed it?

---

### Post by Impavidus on 2015-04-22
Because the dependencies of glossaries have changed. It happens occasionally.

etoolbox and glossaries are in the repositories for 14.04 (package texlive-latex-extra). Maybe not for 14.10? But I installed glossaries and some dependencies manually, because I need at least version 4.12. There exists a package manager specifically for LaTeX, handling all those dependencies automatically. Forgot its name. Anyway, it requires some hacks as it interferes with the ubuntu package manager. But it shouldn't be too hard to manage LaTeX package dependencies manually.

---

### Post by hmiersch on 2015-04-24
I've solved the problem by installing texlive. The whole shebang. Lot of stuff to download but now it works. 
I've read that the hyperref package is included in texlive. That means if I want to use it, all I have to do is learn how :-)

---

