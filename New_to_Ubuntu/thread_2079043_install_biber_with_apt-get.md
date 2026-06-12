---
title: "install biber with apt-get"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by tobstar on 2012-11-01
Hi,

I am new to the world of Ubuntu (coming from Apple ;-)).

I am using latex and I was able to install texlive and biblatex using apt-get install texlive* rsp. biblatex* (worked perfectly).

Now biber is missing and it is not contained as a package in apt-get (anymore as it seems to me). Why not? Some days ago I was able to install it using apt-get install biber (under xubuntu) and everything worked fine.

How could I install biber manually? Which steps would I have to take using files from [https://github.com/plk/biber](https://github.com/plk/biber) ?

I am sorry but I am not used to install software manually :(.

kind regards

---

### Post by GreatDanton on 2012-11-01
Try to install Biblatex via Ubuntu software center. Sometimes programs has different names (for example Video player = Totem)

Also just in case update your Ubuntu:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Regards.

---

### Post by tobstar on 2012-11-01
Many thanks for your answer.

I found a solution, I just had to remove the reference to biber from my main.tex

\usepackage[backend=biber, style=footnote-dw]{biblatex}

\usepackage[style=footnote-dw]{biblatex}

Then it works fine with bibtex. On Apple I had to use biber with the new texlive.

I do not have any clue about the differences between biblatex, bibtex and biber. I am just happy that it works fine now.

Thanks again!

---

