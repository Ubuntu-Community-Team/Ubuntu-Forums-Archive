---
title: "installed gcc.. command &quot;make&quot; still not found"
date: 2006-11-11
forum: Programming Talk
---

### Post by Lotti on 2006-11-11
hello to all :) i installed gcc first from synaptic then by console with "sudo apt-get install gcc"

and all went fine. now ./configure recognize gcc and works well.

the problem is that "make" isn't recognized as a command.. and i don't know how to fix this. 

thank you :)

---

### Post by llonesmiz on 2006-11-11
I suppose you need to install build-essential. 

sudo apt-get install build-essential.

---

### Post by Lotti on 2006-11-11
thank you :) it works

---

### Post by depu on 2006-11-11
i think u need the "build-essential" package for using make
youo can get it using 

sudo apt-get install build-essential

---

