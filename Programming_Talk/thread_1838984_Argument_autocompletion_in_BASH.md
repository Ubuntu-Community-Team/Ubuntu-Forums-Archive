---
title: "Argument autocompletion in BASH?"
date: 2011-09-04
forum: Programming Talk
---

### Post by hakermania on 2011-09-04
How is this possible?
```

alex@MaD-pc:~$ bzr g [TAB-TAB HERE]
gannotate       gcheckout       gconflicts      ginit           gpraise         graph-ancestry  gstatus         
gblame          gci             gdiff           gmerge          gpreferences    gsend           gtags           
gbranch         gcommit         get             gmissing        gpush           gst             
alex@MaD-pc:~$ bzr g

```*Very* nice, how do I do this to my own program?

---

### Post by sisco311 on 2011-09-04
I didn't found any good guides yet. In the meantime check out:
```
man bash | less +/"^ +Programmable Completion"
```

It's called: (bash) programmable completion if you want to search the Net for it. :evil:

---

### Post by Toz on 2011-09-04
Here are a couple of links that help to explain how it works:

[http://www.debian-administration.org/articles/316]("http://www.debian-administration.org/articles/316")
[http://www.debian-administration.org/articles/317]("http://www.debian-administration.org/articles/317")

---

### Post by hakermania on 2011-09-05
Thanks guys, I am having a look right now.

---

### Post by hakermania on 2011-09-05
Wow, super easy, thanks :)

---

