---
title: "i need to download libglew 1.5"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by atul_thedictator on 2008-06-25
i need this package to install some software.
i have gutsy and i have its previous version that it libglew 1.4. and i have tried installing glew 1.5 but that didn't update it.
i am sounding like a beginner and that's why my question is in this section.:popcorn:

i cannot find it in synaptic and i have tried googling it a lot but that didn't help.

i need to install mania drive 1.2. i have got two deb packages for it from "get-deb" and the 4.8 mb file gives a "dependency unsatisfiable" error in gdebi however the data deb could be installed without any trouble.

---

### Post by drs305 on 2008-06-25
First I went to ubuntupackages.com . There is not a 1.5 version of the library for gutsy, only hardy. 

I found a link saying that the "Phun" download runs with the 1.4 lib in gutsy.

```
Just run the program with this command line:

LD_LIBRARY_PATH=. ./phun
```

If this makes sense, have fun.  The poster below got it to run in gutsy. If it doesn't, here is the thread:
[http://ubuntuforums.org/archive/index.php/t-704280.html]("http://ubuntuforums.org/archive/index.php/t-704280.html")

---

### Post by Kevbert on 2008-06-25
Here's another [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=705996&page=3") that may help.

---

### Post by Papenco on 2008-06-25
maybe
```
sudo apt-get upgrade "libglew-1.4"
```

By "libglew-1.4" I mean the name of the synaptic for libglew 1.4

---

### Post by atul_thedictator on 2008-06-26
seems that no one has any ideas of installing lbglew 1.5 on gutsy.
if this is not the way then can you tell me how can i install mania drive 1.2 in gutsy?:confused:

---

### Post by atul_thedictator on 2008-06-26
> **Papenco said:**
> maybe
```
sudo apt-get upgrade "libglew-1.4"
```

By "libglew-1.4" I mean the name of the synaptic for libglew 1.4
and if there was an update available then i am quite sure that i won't have got an "dependency unsatisfiable error"

---

### Post by atul_thedictator on 2008-06-26
> **drs305 said:**
> First I went to ubuntupackages.com . There is not a 1.5 version of the library for gutsy, only hardy. 

I found a link saying that the "Phun" download runs with the 1.4 lib in gutsy.

```
Just run the program with this command line:

LD_LIBRARY_PATH=. ./phun
```

If this makes sense, have fun.  The poster below got it to run in gutsy. If it doesn't, here is the thread:
[http://ubuntuforums.org/archive/index.php/t-704280.html]("http://ubuntuforums.org/archive/index.php/t-704280.html")
and i also have found this thread and many of these kind by googleing around but i have already saidthat i need to run mania drive and not phun.

---

### Post by drs305 on 2008-06-26
One of the posts I read was from a gutsy user who downloaded phun and said the correct library was installed in the phun folders. From what I could tell he was referencing libglew 1.5 although it wasn't definite. My thought was to get the phun package, install it and see if there is a libglew 1.5 version in the folders that you could use. Other than that suggestion, I don't play any games so I don't know phun from mania. :confused:

Hope you get this resolved.


This was the link: [http://ubuntuforums.org/showthread.php?t=704280#9]("http://ubuntuforums.org/showthread.php?t=704280#9")

---

### Post by atul_thedictator on 2008-06-26
> **drs305 said:**
> One of the posts I read was from a gutsy user who downloaded phun and said the correct library was installed in the phun folders. From what I could tell he was referencing libglew 1.5 although it wasn't definite. My thought was to get the phun package, install it and see if there is a libglew 1.5 version in the folders that you could use. Other than that suggestion, I don't play any games so I don't know phun from mania. :confused:

Hope you get this resolved.


This was the link: [http://ubuntuforums.org/showthread.php?t=704280#9]("http://ubuntuforums.org/showthread.php?t=704280#9")
i have tried installing phun before posting this thread but i didn't find libglew 1.5 in its package.
BTW if it had been solved by just googling around then i would have solved it but googling in my case didn't help and i need some experienced guys who have done it before also

---

