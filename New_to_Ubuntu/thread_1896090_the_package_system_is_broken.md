---
title: "the package system is broken"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by cyclone_ on 2011-12-16
Hi everyone,
I recently got this error message when I tried to update my newly installed ubuntu system. 
```
'The package system is broken'
'Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:

zeitgeist: Depends: python-zeitgeist but it is not installed
zeitgeist-core: Depends: libc6 (>= 2.3.4) but 2.13-20ubuntu5 is installed
                Depends: libglib2.0-0 (>= 2.26.0) but 2.30.0-0ubuntu4 is installed
                Depends: libsqlite3-0 (>= 3.5.9) but 3.7.7-2ubuntu2 is installed
                Depends: python-zeitgeist but it is not installed
```

I think I went over my head when I installed some program. I would just like some advice before doing anything stupid. Do I just need to install python-zeitgeist?

Thanks!!

---

### Post by nothingspecial on 2011-12-16
First, try what the error suggests, open a terminal and type

```
sudo apt-get install -f
```

If that doesn't fix things then what did you install and how did you install it?

---

### Post by cyclone_ on 2011-12-16
solved... thanks. That was easier than I thought!

---

### Post by Rubi1200 on 2011-12-16
Glad you found the solution and can enjoy using the system properly.

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by errati on 2012-01-30
> **cyclone_ said:**
> solved... thanks. That was easier than I thought!
care to share how it was solved? For other people i mean.

---

### Post by oldos2er on 2012-01-30
Read post #2.

---

