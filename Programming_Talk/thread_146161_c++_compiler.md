---
title: "c++ compiler"
date: 2006-03-17
forum: Programming Talk
---

### Post by sniperweydz on 2006-03-17
i need a c++ compiler for my ubuntu to do school projects....thx

---

### Post by John.Michael.Kane on 2006-03-17
Removed.

---

### Post by rplantz on 2006-03-17
What do you use at school? What does your instructor use?

As a retired CS Prof., I suggest that you try to match what is being used at your school as closely as you can. No two compilers do exactly the same thing to every C++ source. You can prevent possible hassles by using the same thing that your instructor uses.

---

### Post by jrib on 2006-03-17
install the 'build-essential' package and use g++.  Example: to compile hello.cc:

```
g++ hello.cc -o hello
```

then to run your program, assuming you are in the same directory you issued the above command:
```
./hello
```


rplantz makes a good point though.

---

