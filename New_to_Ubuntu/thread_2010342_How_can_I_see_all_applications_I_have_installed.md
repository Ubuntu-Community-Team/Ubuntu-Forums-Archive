---
title: "How can I see all applications I have installed?"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by temuhin on 2012-06-25
Hello,

I 'm running Ubuntu 12.04.
Is there a way to see everything I have installed on my system?   Everything from music players , to configure tools like Compiz Config and mpc encoders etc.

In case I ever need to reinstall, I would like to have this kind of a list of what I need....

regards
t

---

### Post by PCNetSpec on 2012-06-25
```
dpkg -l > ~/dpkg-list.txt
```You'll then have a file called dpkg-list.txt in your Home directory.

But it may be easier/better to install the synaptic package manager .. then export your package markings.

That way, you could import them if you ever need to reinstall.

---

### Post by temuhin on 2012-06-25
THanks.

I will try the "Synaptic" solution.
The text file was far too big for my tase.

regards
t

---

