---
title: "[SOLVED] apt-get unable to find any packages"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by capnfabs on 2008-06-20
Hi

I just installed Hardy. Upon trying to install various packages via apt-get (e.g. "sudo apt-get install texlive-latex-recommended") I keep getting the error message "Couldn't find package". However, If I attempt to install the same packages with Synaptic, it works perfectly. Any ideas as to why this is happening?

Thanks heaps!

---

### Post by wormser on 2008-06-20
That is a strange problem.  Here are some things to try.  Double check that the repositories are open.  Try updating apt-get.

```
sudo apt-get update
```

---

### Post by neurostu on 2008-06-20
You might want to check your spelling. Apt requires you to spell things exactly right.... to seach using apt (find the exact name) use:
```

aptitude search <packagename>

```

---

### Post by capnfabs on 2008-06-20
Hey, thanks for the suggestions.... I did check that I was spelling everything correctly :D and updating seems to have resolved the problem.

Thanks again! :) Much appreciated.

---

### Post by wormser on 2008-06-20
> **capnfabs said:**
> Hey, thanks for the suggestions.... I did check that I was spelling everything correctly :D and updating seems to have resolved the problem.

Thanks again! :) Much appreciated.

Glad it is working.

---

### Post by hyper_ch on 2008-06-20
and you can also use tab completion:
```

sudo apt-get install apach

```
Press once the tab key to complete it or twice to show a list of possible packages ;)

---

