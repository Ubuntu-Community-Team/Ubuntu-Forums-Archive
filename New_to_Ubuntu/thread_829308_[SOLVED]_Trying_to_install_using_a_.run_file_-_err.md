---
title: "[SOLVED] Trying to install using a .run file - errors"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-14
I am using the .run file from this website: [http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/) to install Enemy territory: Quake Wars on linux. Unfortunately I am unable to as I get the following error:

```

abhiroop@vanimo:~/MyDownloads$ sudo sh ETQW-client-1.4-full.x86.run
[sudo] password for abhiroop: 
ETQW-client-1.4-full.x86.run: 1: Syntax error: ")" unexpected

```

Thanks in advance!

---

### Post by the_doc on 2008-06-14
bash versus sh?

/bin/bash ETQW-client-1.4-full.x86.run

---

### Post by abhiroopb on 2008-06-14
Trying it now, whats the difference?

---

### Post by the_doc on 2008-06-14
Basically shell scripts aimed at different shells.  The default Ubuntu shell links to dash when it used to link to bash, so running shell scripts designed to work with bash can have issues with dash and sh.  

Also from your code snippet you explicitly use sh to run the script which obviously wont work if it's a bash script.  Of course, this may not help fix your problem at all but I'm just trying to help!

Open up the script and see if it has **#!/bin/sh** or **#!/bin/bash**?

---

### Post by Dapilot1 on 2008-06-14
I installed it also, but I used this after navigating to the directory.
```
./ETQW-client-1.4-full.x86.run
```

---

### Post by abhiroopb on 2008-06-14
Thanks worked!

---

### Post by the_doc on 2008-06-15
What worked, using bash?

---

### Post by abhiroopb on 2008-06-15
./ETQW-client-1.4-full.x86.run

---

### Post by Joeb454 on 2008-06-15
.run files seem to cause a few issues when you don't think of the terminal at first :p

And you can mark your thread solved from "Thread Tools" at the top of this page :)

---

### Post by the_doc on 2008-06-15
Glad to hear it!

---

### Post by abhiroopb on 2008-06-15
In fact enemy territory quake wars works MUCH better on ubuntu, I wish all games could be ported like this :)

---

