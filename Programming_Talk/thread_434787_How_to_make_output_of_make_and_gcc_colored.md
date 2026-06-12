---
title: "How to make output of make and gcc colored"
date: 2007-05-06
forum: Programming Talk
---

### Post by casperl82 on 2007-05-06
I installed color-gcc on my kubuntu system and tried to set this "export CC="colorgcc" on my .bashrc file.
This did not work and i created soft links for colorgcc in the following way:

c++  -> colorgcc 
cc  -> colorgcc 
g++  -> colorgcc 
gcc -> colorgcc 

My PATH is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" and i created these soft links inside "/usr/local/sbin" directory which was empty initially. What am i doing wrong? This still does not work!! 

Thanks.

---

### Post by surhudm on 2007-05-06
Can you directly try to use colorgcc and see that it works? One can deal with aliases later...

Cheers.

---

### Post by casperl82 on 2007-05-06
Yes, colorgcc works when i run it directly.

---

### Post by casperl82 on 2007-05-07
Any suggestions?

---

### Post by ssam on 2007-05-07
what program is calling gcc?

if you are using make, does the makefile call /usr/bin/gcc explicitly?

maybe change the CC variable in the Makefile

===

ok i had a play with this. to get it to work i

set up simlinks to gcc and g++ that point to /usr/bin/colorgcc
```
lrwxrwxrwx 1 sam sam     17 2007-05-07 17:19 g++ -> /usr/bin/colorgcc
lrwxrwxrwx 1 sam sam     17 2007-05-07 17:19 gcc -> /usr/bin/colorgcc
```

this are in my ~/bin, but /usr/local/bin should be the same

then i edited
```
/etc/colorgcc/colorgccrc
```
and uncommented the
```
g++: /usr/bin/g++
gcc: /usr/bin/gcc

```
lines

---

### Post by casperl82 on 2007-05-08
Hello ssam,

I guess i have a path problem. Where is ~/bin in your PATH? At the begining or at the end?

My PATH is like this:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

My gcc and g++ links are in /usr/local/bin and sth like this:

lrwxrwxrwx 1 root root       7 2007-04-30 15:23 /usr/bin/g++ -> g++-4.1
lrwxrwxrwx 1 root root       7 2007-04-30 03:15 /usr/bin/gcc -> gcc-4.1

And my colorgcc links are in /usr/local/sbin:

lrwxrwxrwx 1 root root 8 2007-05-04 15:24 c++ -> colorgcc
lrwxrwxrwx 1 root root 8 2007-05-04 15:24 cc -> colorgcc
lrwxrwxrwx 1 root root 8 2007-05-04 15:24 g++ -> colorgcc
lrwxrwxrwx 1 root root 8 2007-05-04 15:24 gcc -> colorgcc

Should i move "/usr/local/sbin" to the end of the PATH variable from the begining of it?

---

### Post by casperl82 on 2007-05-09
Any more ideas?

---

### Post by ssam on 2007-05-09
you /usr/local/bin should be at the start of you path.

have you made the change to /etc/colorgcc/colorgccrc ?

do you get an error message?

---

### Post by casperl82 on 2007-05-09
I changed PATH like this by overwriting on the PTH variable on my .bashrc. It looks correct now:

> /usr/local/bin:/usr/local/sbin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

And my /etc/colorgcc/colorgccrc file has the following lines:

> g++: /usr/local/sbin/g++
gcc: /usr/local/sbin/gcc
c++: /usr/local/sbin/c++
cc:  /usr/local/sbin/cc

But it still does not work. Anything wrong?

---

### Post by ssam on 2007-05-09
your /etc/colorgcc/colorgccrc needs to have the paths to the real gcc and g++. it tell what colorgcc what command to use to actually compile your program

```

g++: /usr/bin/g++
gcc: /usr/bin/gcc
c++: /usr/bin/c++
cc:  /usr/bin/cc

```

====
when you run make, it looks for the first gcc (or g++ or whatever) in you path.

it should find /usr/local/gcc

this is a sym link to colorgcc, so colorgcc gets run.

colorgcc check what name it was called with, and finds /usr/local/gcc. then it looks at its config file and see that for gcc it needs to run /usr/bin/gcc to compile the code.

so colorgcc runs /usr/bin/gcc and filters the output to add colours.

---

### Post by casperl82 on 2007-05-09
Thanks for the answer but unfortunately it still does not work.

I changed the paths in /etc/colorgcc/colorgccrc but it still does not work. :( I am opening a new shell all the time to make sure everything is reloaded but nothing changes..

Any ideas?

---

### Post by bLUEbYTE on 2007-05-09
try redirecting /usr/bin/cc to your wrapper script

---

### Post by casperl82 on 2007-05-09
Yes as i have listed in a previous post, i have a link from /usr/bin/cc to colorcc!

---

### Post by ssam on 2007-05-09
> **casperl82 said:**
> Yes as i have listed in a previous post, i have a link from /usr/bin/cc to colorcc!

if you have sym linked /usr/bin/cc and friends to colorgcc then where is you real gcc that you want to use? are they just at

/usr/bin/gcc-4.1 ...

if so then the settings in /etc/colorgcc/colorgccrc need to point at those. if the settings in  /etc/colorgcc/colorgccrc point to something that points back to colourgcc then you get stuck in a loop

---

### Post by casperl82 on 2007-05-10
> if you have sym linked /usr/bin/cc and friends to colorgcc then where is you real gcc that you want to use? are they just at

Yes, i did what you said. But result did not change :(

---

### Post by kmads on 2008-11-24
> **casperl82 said:**
> Yes, i did what you said. But result did not change :(

The thread is old - but anyway.. I had the same problem and solved it by adding:

print("\0");

right before the call to initDefaults() in the colorgcc-script.

Hope it helps somebody.

Best regards,
kmads

---

### Post by kmads on 2008-11-24
> **kmads said:**
> The thread is old - but anyway.. I had the same problem and solved it by adding:

print("\0");

right before the call to initDefaults() in the colorgcc-script.

Hope it helps somebody.

Best regards,
kmads

Oops, I meant print(" ")

---

