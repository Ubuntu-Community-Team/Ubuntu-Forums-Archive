---
title: "The application software updater has closed unexpectedly"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by Vitor_Hugo on 2014-07-08
Hello, 


I'm Vitor Hugo, i'm new to  linux and have already a problem :/

I can't use the repositories or software updater by any means .... when i try to run the software updater says " The application software updater has closed unexpectedly" this happened to me about a week or two, but only know get my attention because i think is not a big problem at all, until i want to install something 
from the repos and failing...
I i choose to see details this is what i get

[IMG]http://i59.tinypic.com/11hwhgx.png[/IMG]




my lubuntu version is 14.04 LTS. i read here in the forum to do this on the terminal:   sudo apt-get install -f 
This is what i get.




[IMG]http://i58.tinypic.com/vyop1.png[/IMG]






Help  ?!?!?





Vitor Hugo

---

### Post by ubudog on 2014-07-08
Hi Vitor,

Try this:
```
sudo rm /var/lib/apt/lists/*
```
```
sudo apt-get update
```

---

### Post by Vitor_Hugo on 2014-07-08
Hi Ubudog, 

When i execute the first command it says 

rm: cannot remove '/var/lib/apt/lists/partial': Is a diretory


(EDIT)


after i input the 2nd command magically it's working know ( the software updater) O.o

Plz can u explain to me what i done wrong  ?

---

### Post by ubudog on 2014-07-08
Whoops, my bad, try:
```
sudo rm /var/lib/apt/lists/* -vf
```

And then:
```
sudo apt-get update
```

---

### Post by Vitor_Hugo on 2014-07-08
ok done ! sorry for being slow , but i have a slow connection and it takes time to read the repo..

and software updater already downloading/installing updates...


Shoul i try to install something from the repo ?

---

### Post by ubudog on 2014-07-08
No problem, I know how you feel.  :D

---

### Post by Vitor_Hugo on 2014-07-08
Thanks Man ;)

---

