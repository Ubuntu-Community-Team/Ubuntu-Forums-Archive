---
title: "URGENT! gcc-Linker-Problem (crt1.o)"
date: 2005-05-27
forum: Programming Talk
---

### Post by Ninnghizidha on 2005-05-27
Good morning!

HELP!! I have a really horrible problem and i have no idea how to solve it by my own:

I installed some* packages (to compile vegastrike) today, but at least one of them destroyed my already working g++-Linker.  :???: 

Every time i try to link my c++-sourcecode with g++ i get:
```
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized

```

... and i have no idea why.  :-| 

i tried to remove all those packages (including gcc/g++), and reinstalled gcc/g++ but the problem remains. I was able to work with g++ without problems yesterday, and that is what i would like to have again. Please help me to compile again, 'cause a programmer without a working linker is really useless.

Liebe Grüße,
Ninnghizidha.  :cry: 

* i tried to install these packages for vegastrike today: gcc, libjpeg62-dev, libopenal0, libopenal0-dev, libopenal-dev, python2.4, python-opengl, cvs, glutg3, glutg3-dev und libsdl1.2-dev.  some were already installed, others weren't  ..

---

### Post by MWAAAHAAA on 2005-05-27
*** UPDATE ***

Seems that the broken binutils has been replaced by a new one already, just apt-get update; apt-get upgrade and you should be fine.

*** END UPDATE ***

I am glad I am not the only one here. I updated my ubuntu packages today

apt-get update; apt-get upgrade

And now I am getting the exact same problem when compiling. E.g.

int
main()
{
}

Compiling this, ala gcc thiscode.c yields:

/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status

Seems that the update broke something. Maybe it's a good idea to post this on ubuntu bugzilla (or whatever they're using)?

---

### Post by Ninnghizidha on 2005-05-27
You are right - now it works again like on the first day!   :razz:  :mrgreen: 

Thanks a lot, MWAAAHAAA, you saved my day.

Ninnghizidha.  :)

---

### Post by mamatosh on 2008-02-21
people around are trying over the same problem.......


they have either installed gcc-lib-dev package or have changed LD_PATH value..... to /usr/bin/lib

---

