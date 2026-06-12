---
title: "gcc optimization"
date: 2007-04-09
forum: Programming Talk
---

### Post by burgerbee on 2007-04-09
Trying to optimize gcc for my Xbox 360. Is there any other options/flags I should try before I start building stuff?

```

bongy@xbox360:~$ gcc -mpowerpc speedtest.c -o speed;./speed
10E6 RDTSC time=1862 ms
10E6 RDTSC time=1863 ms
10E6 RDTSC time=1862 ms
bongy@xbox360:~$ gcc -mpowerpc64 speedtest.c -o speed;./speed
10E6 RDTSC time=1812 ms
10E6 RDTSC time=1812 ms
10E6 RDTSC time=1812 ms
bongy@xbox360:~$ gcc -mpowerpc -Os speedtest.c -o speed;./speed
10E6 RDTSC time=708 ms
10E6 RDTSC time=709 ms
10E6 RDTSC time=708 ms
bongy@xbox360:~$ gcc -mpowerpc64 -Os speedtest.c -o speed;./speed
10E6 RDTSC time=702 ms
10E6 RDTSC time=702 ms
10E6 RDTSC time=702 ms

```

---

### Post by samjh on 2007-04-09
Looks like you've tried -Os, but have you also tried -O1, -O2, and -O3 options too?  The -O3 is probably not a good idea, but might be worth a try.

BTW, always use -Wall.  It can help prevent some serious flaws that might not otherwise get caught.

---

### Post by burgerbee on 2007-04-09
Thanx for the reply!

Not at the 360 atm, but I tested -O3 yesterday. It gave the same speed but bigger binarys then -Os.

Tried -01 and -02 aswell but I cant remember the results. Will do some more tests tonight. 

/BurgerBee

---

### Post by burgerbee on 2007-04-09
Is there any way to get dpkg-buildpackage / apt-get build-dep / apt-get -b source to do this optimization automatically? 

Man page for dpkg.cfg didn't give me any clues.

/BurgerBee

---

