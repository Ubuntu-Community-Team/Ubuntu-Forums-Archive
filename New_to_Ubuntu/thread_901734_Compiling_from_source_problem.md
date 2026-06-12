---
title: "Compiling from source problem"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Dark006 on 2008-08-26
I've been using Ubuntu for about 2-3 months now, and I've always had a problem installing programs from source (I think thats the term, and I always have success if I use Synaptic or apt-get install). I've been trying to get one in particular (conky) and can't seem to get it working correctly. 

I do the usual ```
tar -xzf program_name
``` to untar it. Usually from there your supposed to ./configure in that directory, followed by a "make" and "make install"

I usually always get to the ./configure part (and it works) but after that for some reason "make" (and make install) never does. 

Which is what leads me to this, do certain types of files have to be put in certain directories? 

Also, does anyone have a list or anything that shows where to put certain types of files etc.?

---

### Post by halitech on 2008-08-26
conky is in the repos and works fine when installed from there

for more help on installing from source (yes you had the right term) read here
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by kk0sse54 on 2008-08-26
```
sudo apt-get install conky
``` will do fine for you :)

---

### Post by Sinkingships7 on 2008-08-26
And for the future, I think you're missing the build-essential package. Be sure to have that before attempting compilations.
```
sudo aptitude install build-essential
```

---

