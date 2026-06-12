---
title: "starting a C++ program from launcher"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-05-10
Hi,

i wrote a C++ program that either connects or disconnects from the internet using PPPoE (i.e. pon dsl-provider or poff)

it is a console program, and when i start it from the terminal i just type

```
./C++/connectPPPoE
```

i try to do that through a launcher on my desktop, but i get the error

```
There was an error creating the child process for this terminal
```

how do i start a C++ program from a launcher? thanks for your help.

---

### Post by Nachtengel on 2008-05-10
The link to launch your program should be in the form 

```
sh fully/qualified/path/to/exe.ext
```

note: this means you have to start at / and work your way up through /home and /home/yourusername and so on in the fully qualified path.

---

