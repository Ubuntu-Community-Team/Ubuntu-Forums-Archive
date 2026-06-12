---
title: "What compiler comes with ubuntu"
date: 2006-04-18
forum: Programming Talk
---

### Post by Muag on 2006-04-18
Ok, I need to know what compiler comes with ubuntu for c++ and what is the command to run it...in my programming class we use vi for programming and g++ to compile...thanks

---

### Post by jrib on 2006-04-18
just install the build-essential package using synaptic, or from the command line:
```
sudo aptitude install build-essential
```

Then you can use vi and g++ in probably the same fashion you are used to:
```
g++ -o myprogram myprogram_source.cc
```

and that should create a file name 'myprogram' in the current directory, which you can run as ```
./myprogram
``` while you are in that directory

---

