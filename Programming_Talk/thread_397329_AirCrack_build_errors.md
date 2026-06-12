---
title: "AirCrack build errors?"
date: 2007-03-30
forum: Programming Talk
---

### Post by FlyingIsFun1217 on 2007-03-30
Hey,

So I'm trying to build Aircrack on Ubuntu edgy.
I downloaded the file from the website, unpacked it to the desktop, and did the following in the terminal:

> 
cd /home/user/Desktop/AircrackFolder/src/
./configure


doing this just gives me:

> 
bash: ./configure: No such file or directory


well, I ignored this (knowing that I wouldn't be able to build if I did), and tried doing:

> 
make: *** No targets specified and no makefile found.  Stop.


Again, ignoring this knowing that nothing would happen:

> 
make: *** No rule to make target `install'.  Stop.


So... What is it that I'm messing up? Isn't this how I should go about building it? It should be noted that I'm on a fresh install, if that matters.

Thanks for your help!
FlyingIsFun1217 :)

---

### Post by FlyingIsFun1217 on 2007-03-31
Can anybody help me here? I'm sure somebody knows whats wrong here...

FlyingIsFun1217

---

### Post by lnostdal on 2007-03-31
why are you doing this? use synaptic or aptitude when you can!

```

sudo aptitude install aircrack

```

edit:
just adding to what wieman01 mentions below that `aircrack' will actually install `aircrack-ng' .. at least here in feisty

---

### Post by wieman01 on 2007-03-31
"aircrack" is in the repositories, there is no need to compile from scratch (see post #3). I would use [aircrack-ng]("http://www.aircrack-ng.org/doku.php") instead which is way more advanced and has lots more features. It is fairly simple to "make".

---

### Post by WW on 2007-03-31
If you prefer to build the latest version from source instead of installing an older precompiled package, follow the instructions: [http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=052a66e6d52b9b09ca0ca5323023b108](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=052a66e6d52b9b09ca0ca5323023b108)

Note, in particular, that it does not use the Autotools configure command.

---

### Post by FlyingIsFun1217 on 2007-03-31
> **wieman01 said:**
> "aircrack" is in the repositories, there is no need to compile from scratch (see post #3). I would use [aircrack-ng]("http://www.aircrack-ng.org/doku.php") instead which is way more advanced and has lots more features. It is fairly simple to "make".

Well, thats what I was using, was a download of the source package of aircrack-ng, and thats when I had so much trouble using ./configure, make && make install

Thanks again for the help!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-03-31
> **WW said:**
> If you prefer to build the latest version from source instead of installing an older precompiled package, follow the instructions: [http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=052a66e6d52b9b09ca0ca5323023b108](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=052a66e6d52b9b09ca0ca5323023b108)

Note, in particular, that it does not use the Autotools configure command.

:)
Thanks for pointing that out, I seemed to not see that over at the aircrack site  :)

Thanks again!
FlyingIsFun1217

---

