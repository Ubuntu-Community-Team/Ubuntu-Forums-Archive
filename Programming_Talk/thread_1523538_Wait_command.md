---
title: "Wait command"
date: 2010-07-03
forum: Programming Talk
---

### Post by Nonameman on 2010-07-03
Hi 

Trying to do some linux bash script magic

Trying to do this code: 
#get some random program that needs to get compiled
autoreconf -vi
 ./configure --prefix=/opt/v
make
make install

The problem (I think) that I have is that it seems that 'make' or 'make install' starts before configure/make is finished. I have tied using 'wait', with no luck. Program executes correct if I do it manualy, but not when I am putting it in a script. (I have a lot of programs that need to be downloaded and compiled on multiple computers)

Hope that some linux guru can give me some help :)

---

