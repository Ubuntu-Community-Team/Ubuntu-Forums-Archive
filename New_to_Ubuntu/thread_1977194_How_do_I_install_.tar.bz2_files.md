---
title: "How do I install .tar.bz2 files?"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by iMurshaq on 2012-05-09
I'm trying to install AssaultCUBE but I'm not too familiar with .tar.bz2 files.

---

### Post by papibe on 2012-05-09
Hi iMurshaq.

A 'tar.bz2' file is like a rar file. First thing you need to do is extract its contents. To do that open a terminal, go to the directory where the file is and run:
```
tar xvjf filename.tar.bz2
```
(replace 'filename' with the actual file name).

After that, a directory will be created, where you have to look for instructions on how to install the software. Look for files that are named README, FAQ, Instructions, etc.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by iMurshaq on 2012-05-09
I tried that but got this output:
```
tyler@tyler-desktop:~$ tar xvjf assaultcube_v1.1.0.4.tar.bz2
tar: assaultcube_v1.1.0.4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
```

---

### Post by Enigmapond on 2012-05-09
Too much headache...just add the getdeb/games ppa and install it through the software center.


[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

---

### Post by Curtis6767 on 2012-05-09
Just open up the software center, type in AssaultCube

---

### Post by iMurshaq on 2012-05-09
> **Enigmapond said:**
> Too much headache...just add the getdeb/games ppa and install it through the software center.


[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

And how do I add getdeb/games?

---

### Post by Curtis6767 on 2012-05-09
> **iMurshaq said:**
> And how do I add getdeb/games?


Why bother? It's in the sofware center.

Click on the icon to your left that looks like a shopping bag full of stuff.

Type in AssaultCube.  Hit "Install." Viola'. Easy as pie.

---

### Post by Enigmapond on 2012-05-09
The site tells you but...here.
Add this line to your software sources:
```
deb http://archive.getdeb.net/ubuntu lucid-getdeb games
```

Then open a terminal and do:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

Then run an update and you will be able to install from the software center.

---

### Post by iMurshaq on 2012-05-09
Alright I got it thanks everyone.

---

### Post by Shadius on 2012-05-09
> **papibe said:**
> Hi iMurshaq.

A 'tar.bz2' file is like a rar file. First thing you need to do is extract its contents. To do that open a terminal, go to the directory where the file is and run:
```
tar xvjf filename.tar.bz2
```
(replace 'filename' with the actual file name).

After that, a directory will be created, where you have to look for instructions on how to install the software. Look for files that are named README, FAQ, Instructions, etc.

I hope that helps, and tell us how it goes.
Regards.

Would you also be able to extract the file using Archive Manager? Just curious about other methods besides the CLI method.

---

### Post by jerome1232 on 2012-05-09
> **Shadius said:**
> Would you also be able to extract the file using Archive Manager? Just curious about other methods besides the CLI method.

Right click, extract here, easy as cake. But honestly, who want's to go mucking about with an archive when you can use the Software center?


Cake is much better than pie.

---

### Post by Shadius on 2012-05-09
> **jerome1232 said:**
> Right click, extract here, easy as cake. But honestly, who want's to go mucking about with an archive when you can use the Software center?


Cake is much better than pie.

Cake is indeed much better than pie. LOL Thanks.

---

