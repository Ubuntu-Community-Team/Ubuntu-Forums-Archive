---
title: "Can't compile anything."
date: 2007-12-12
forum: Packaging and Compiling Programs
---

### Post by stabbymctwist on 2007-12-12
So I made the simplest c/++ program I could think of, compiled it, and tried to run it.  I get "bash: ./sillystring.o: cannot execute binary file".  

```

int main () {
return 1;
}

```

build-essential is installed.  I did search the forums, too.  Google, as well.  Sorry if it's a repost.  Using gcc outputs no errors at all.

Am I missing something important?

---

### Post by geraldm on 2007-12-12
# check for syntax; create object *.o file
gcc -c -I. hello.c
# compile to executable
gcc -o hello -I. hello.c
# test
./hello

# for C++,  suffix differs; use g++ instead of gcc; *.cpp instead of *.c
Gerald

---

### Post by stabbymctwist on 2007-12-13
Wow,  Thanks a lot, seriously.  I feel dumb now, heh.

---

