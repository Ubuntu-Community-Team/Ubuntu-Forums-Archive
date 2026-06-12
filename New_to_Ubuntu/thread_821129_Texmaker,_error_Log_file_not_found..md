---
title: "Texmaker, error Log file not found."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by link- on 2008-06-06
I installed texmaker yesterady and just to give it a try I tried to run the Hello World and click on quickbuild and it pop a window that says Log file not found. 
I'm supposed to install something else? Miktex?

---

### Post by iaculallad on 2008-06-06
Try reinstalling texmaker using the Repository:

```
sudo apt-get remove texmaker
sudo apt-get install texmaker
```

and try it again.

---

### Post by amyst on 2008-06-06
When I first started using Texmaker, I had the same problem. The solution is below: 

[http://ubuntuforums.org/showthread.php?t=720609](http://ubuntuforums.org/showthread.php?t=720609)

Basically, you need to get texlive packages from the repos.

---

### Post by link- on 2008-06-06
I still get the error "Log file not found !"

---

### Post by iaculallad on 2008-06-06
> **link- said:**
> I still get the error "Log file not found !"

Try renaming the file first but this time place the extension **.tex** - i.e: filename.tex and redo your quickbuild.

---

### Post by link- on 2008-06-06
> **iaculallad said:**
> Try renaming the file first but this time place the extension **.tex** - i.e: filename.tex and redo your quickbuild.

Nope, nothing.

---

### Post by iaculallad on 2008-06-06
> **link- said:**
> Nope, nothing.

Install MikTex and re-install TexMaker.

---

### Post by link- on 2008-06-07
Since Miktex is for windows I decide to install Texlive, and it worked well.

Thanks a lot iaculallad

-link

---

