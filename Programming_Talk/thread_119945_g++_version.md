---
title: "g++ version"
date: 2006-01-20
forum: Programming Talk
---

### Post by sraised2the3rd on 2006-01-20
I've recently installed Ubuntu on a 64-bit platform for really the main purpose of programming. I am a full time student with a major in computer programming, so Linux I think is the best route. For one of my classes we have to tell the professor which g++ compiler we are using, as its a class in c++. So I tried a g++ -ver, and got a "no input file" message. Am I missing something here or doing this wrong?

---

### Post by hillbilly on 2006-01-20
hmm..i thght the option was -version or -v. Did you try > man g++ and grep for version ?

---

### Post by Casey on 2006-01-20
```
[prompt@computer ~]$ g++ --help | grep version
  -dumpversion             Display the version of the compiler
  -print-multi-directory   Display the root directory for versions of libgcc
  -V <version>             Run gcc version number <version>, if installed
[prompt@computer ~]$ g++ -dumpversion
3.4.4
[prompt@computer ~]$         

```

Hope that helps you.

---

### Post by sraised2the3rd on 2006-01-20
thank you both for the help, I had forgotten I could use those for information.

---

### Post by hod139 on 2006-01-20
The command  ```
g++ --version
``` also works

---

