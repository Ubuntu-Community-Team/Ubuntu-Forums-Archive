---
title: "How to setup GCC compiler environment"
date: 2007-08-08
forum: Programming Talk
---

### Post by jnorthr on 2007-08-08
Any tips please on how to make the linux header files visible to the gcc compiler ? Do i need to download the ubuntu source to test device drivers  or are the header files part of the ubuntu 7.0.4. install ?
Thanx

---

### Post by apetresc on 2007-08-08
Yup, you need to explicitly install the kernel headers. The two main things you need are ```
sudo apt-get install build-essential
```for the GCC build tools, and ```
sudo apt-get install linux-headers-`uname -r`
``` for the kernel headers.

---

### Post by jnorthr on 2007-08-10
Have checked ubuntu 7.0.4 and both appear to be installed. i can gcc and run sample tcp client and server modules ok so i know the compilers & network are ok. But when i try to compile samples using /linux/headers the compiler fails to find the headers. Do I need to include the header folder  in $PATH or some such ?

---

### Post by LaRoza on 2007-08-10
gcc is there, but not the headers, run 
```

sudo aptitude install build-essential

```

---

