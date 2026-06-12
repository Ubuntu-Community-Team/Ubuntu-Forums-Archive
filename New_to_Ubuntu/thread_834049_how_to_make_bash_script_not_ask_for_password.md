---
title: "how to make bash script not ask for password?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by -random on 2008-06-19
hello.. i've made a bash script that uses a sudo command, so everytime i run the script it asks for a password,

> how can i make it so that it doesn't ask for a password? <

(for example when you click on quit > restart, it doesn't ask for a password)

*x-scuze my engliszh lol*

---

### Post by dark_harmonics on 2008-06-19
If you trust the script then you can remove all sudos from it and just run it as root to begin with. Sudo ./script.sh

---

### Post by kaiju on 2008-06-19
> **-random said:**
> hello.. i've made a bash script that uses a sudo command, so everytime i run the script it asks for a password...

based on what it looks like you are trying to achieve, you might find [this thread]("http://ubuntuforums.org/showthread.php?t=342763") useful. or you could use gksudo for a password box.

---

### Post by -random on 2008-06-19
awesome thnkx guys i'll give it a shot and report what i did a.s.a.p.

*(gonna watch narnia now with the gf bleh.. ;P)*

---

