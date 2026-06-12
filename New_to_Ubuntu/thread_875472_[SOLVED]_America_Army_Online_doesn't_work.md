---
title: "[SOLVED] America Army Online doesn't work"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-07-30
After I installed America army it didn't show up under the games section and when I type ```
armyops
``` in the terminal this shows up:

```
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

How do I fix this?

---

### Post by SunnyRabbiera on 2008-07-30
well I know its possible to get it working in linux though I never did it myself.
Can you give us some details and such so we can help you?

---

### Post by Bigbob22 on 2008-07-30
Thats all that happened. I installed it and followed this guide [https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy) 

thats about it

---

### Post by SunnyRabbiera on 2008-07-30
I see, well sorry I cant personally help you as I dont use that app, but hopefully someone can help you.
I am sort of the in between person here :D

---

### Post by Bigbob22 on 2008-07-30
oh. I was hoping I could fix it. I really like this FPS. I played it when I used to have windows

---

### Post by JoneYee on 2008-07-30
> **Bigbob22 said:**
> ./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


please post result of 
```
cat armyops-bin
``` 

from the directory that contains the file.


EDIT: Also not seeing armyops or America's Army in any of my repositories

---

### Post by Bigbob22 on 2008-07-30
I don't know the directory that contains the files

---

### Post by Bigbob22 on 2008-07-30
Well I couldn't find it.

---

### Post by JoneYee on 2008-07-30
> **Bigbob22 said:**
> I don't know the directory that contains the files

What did you search for to find it?  

We need to know the directory that it is in and the text of the library reference to attempt to fix it.  I had a similar error with NWN that I solved.

---

### Post by Bigbob22 on 2008-07-30
I used the search application under the accessories section.

---

### Post by JoneYee on 2008-07-30
Ok I am downloading, it was not in a repository, but a .run file available from fileplanet.

Give me a few to get this going (putting kids in bed and all) - download progressing.

---

### Post by Bigbob22 on 2008-07-30
I think its beagle.

---

### Post by JoneYee on 2008-07-30
Just to verify you downloaded armyops250linux.run - correct?

EDIT:  Ok Installed, and got the exact same error.

```
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

---

### Post by JoneYee on 2008-07-30
SOLUTION:

```
sudo apt-get install libstdc++5
```

once installed:

```
armyops
```

---

### Post by philetus on 2008-07-31
You're one of the good guys JoneYee.

---

### Post by JoneYee on 2008-07-31
> **philetus said:**
> You're one of the good guys JoneYee.

I try.  My mama said  it's a good thing I was 55% good 45% bad when I was growing up or the world would have been in trouble.

---

### Post by philetus on 2008-07-31
> **JoneYee said:**
> I try.  My mama said  it's a good thing I was 55% good 45% bad when I was growing up or the world would have been in trouble.
Back in the 60's there was a lot of talk about California falling into the ocean.
Things calmed down when I got a little maturity.

---

### Post by Bigbob22 on 2008-07-31
Thanks  a bunch

---

### Post by JoneYee on 2008-07-31
> **Bigbob22 said:**
> Thanks  a bunch

My pleasure, I learned in the process.  

For others, Armyops installs to usr/local/games/

---

