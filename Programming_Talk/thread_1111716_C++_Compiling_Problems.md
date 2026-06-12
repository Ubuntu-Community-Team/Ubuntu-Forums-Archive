---
title: "C++ Compiling Problems"
date: 2009-03-30
forum: Programming Talk
---

### Post by BrandonND on 2009-03-30
I made a simple Hello World Script, as a *.cpp file. I sed the following command

g++ <source file> -o <desired output>

but the file I get I cant run for the life of me, how can I get it to run?

---

### Post by krazyd on 2009-03-30
Have you tried ```
./<desired output>
```

Also, usually the g++ command is given with the -o option first and sources last eg:

```
g++ -o <desired output> <source file1> <source file2>
```

---

### Post by sujoy on 2009-03-31
nope, -o works on either side of input source files.

---

### Post by zjagannatha on 2009-03-31
g++ -o <output> <source1> <source2> ...
g++ <source1> <source2> ... -o <output>

Both will compile just fine.

---

### Post by TheBuzzSaw on 2009-03-31
Try typing this:
```
./a.out
```

---

### Post by dwhitney67 on 2009-03-31
> **BrandonND said:**
> I made a simple Hello World Script, as a *.cpp file. I sed the following command

g++ <source file> -o <desired output>

but the file I get I cant run for the life of me, how can I get it to run?
Show us the program, and show the result of attempting to compile it.

---

