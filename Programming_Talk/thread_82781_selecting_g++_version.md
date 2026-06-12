---
title: "selecting g++ version"
date: 2005-10-27
forum: Programming Talk
---

### Post by kroiz on 2005-10-27
hi, 
I got something I that need to be compiled with g++ 3.3 but I got g++ 4 installed.
can I apt-get g++ 3.3 and then somehow instruct the make to use it?
or maybe just uninstall g++ 4?

---

### Post by darth_vector on 2005-10-27
it should be backwards compatible. have you tried building the source with 4.0?

---

### Post by kroiz on 2005-10-27
[QUOTE=darth_vector]it should be backwards compatible. have you tried building the source with 4.0?[/QUOTE]

yes I did but I get some compiling errors. I guess 4 is more strict.

---

### Post by toojays on 2005-10-27
You can install the package g++-3.3, and get your project to use it by setting the environment variable CXX=g++-3.3 before you run the configure script.

---

### Post by thumper on 2005-10-27
Don't forget to export it.
```
export CXX=g++-3.3
```

---

### Post by kroiz on 2005-10-27
[QUOTE=toojays]You can install the package g++-3.3, and get your project to use it by setting the environment variable CXX=g++-3.3 before you run the configure script.[/QUOTE]
great thanks. I dont have a configure script but I managed to do it like this:

```
make target CXX=g++-3.3
```

---

