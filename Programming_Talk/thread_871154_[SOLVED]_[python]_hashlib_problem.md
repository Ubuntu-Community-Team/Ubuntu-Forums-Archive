---
title: "[SOLVED] [python] hashlib problem"
date: 2008-07-26
forum: Programming Talk
---

### Post by EXCiD3 on 2008-07-26
Ok so ive been teaching myself a little bit of python recently and wrote a script to download a file and calculate its md5 sum. To test it out i downloaded this file: [http://keryx.betaserver.org/src/keryx.tar.bz2](http://keryx.betaserver.org/src/keryx.tar.bz2). Now on my parents windows computer (running python 2.5.2) for some reason only on that computer does it calculate the wrong md5 sum. I get 296bb4e451c10bcd5d01972edf9355d9 instead of the correct one:  8dbf8b7214634d4dd1ad5ac1c2cf9148. The md5 sum is calculated correctly however on my friends computer, and i havent had the chance to try it on my laptop (on dialup :(). Here is the code in question:
```
import hashlib

infile = open(item[1])
data = infile.read()
infile.close()

print hashlib.md5(data).hexdigest()
```

Could this be due to something wrong with hashlib on the windows build or is there something else wrong? winmd5sum on windows calculates the correct hash, but i cannot get python to do it right. I know its nothing wrong with liburl becaue i used firefox to download the file then calculate the md5 sum and i still get the wrong one. What md5 sum to you get on this file? Thanks for the hlep!

---

### Post by ghostdog74 on 2008-07-26
check the docs [here](http://docs.python.org/lib/module-hashlib.html). You should also do an update()

---

### Post by EXCiD3 on 2008-07-26
> **ghostdog74 said:**
> check the docs [here]("http://docs.python.org/lib/module-hashlib.html"). You should also do an update()

update() is not needed because when passing the data variable to the constructor it already has the info that it will be creating the hash of. The command is correct and functions properly. It seems that its working improperly in windows, unless im doing something else wrong...

---

### Post by EXCiD3 on 2008-07-26
Solved the problem, in order to get the same hash every time the file must be opened in 'rb' mode instead because of the line endings being interpreted differently between operating systems.

---

