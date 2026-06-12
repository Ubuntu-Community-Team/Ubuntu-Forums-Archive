---
title: "cmake help!!"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-15
hi,,
i am trying to install source package by starting with "./configure" but it says it needs "cmake". how do i use cmake to install a package?
thanks

---

### Post by appi2012 on 2008-07-15
just type:```
cmake
```
and then ```
make
```
if you haven't installed it, do:
```
sudo apt-get install cmake
```
first.

---

### Post by raedbenz on 2008-07-15
> **appi2012 said:**
> ```
sudo apt-get install cmake
```
yes i did it. but after that do i have to write:

./cmake 
make 
make install

it doesnt work this either
thanks

---

### Post by appi2012 on 2008-07-15
I edited my post. after make, type:
```
sudo make install
```

that should work

---

### Post by Bachstelze on 2008-07-15
> **raedbenz said:**
> yes i did it. but after that do i have to write:

./cmake 
make 
make install

it doesnt work this either
thanks

No you don't. You should have a README with your program, please read it. We don't even know what you are trying to install...

---

### Post by raedbenz on 2008-07-15
> **appi2012 said:**
> I edited my post. after make, type:
```
sudo make install
```

that should work

i get this output:
```
NOTE

CMake no longer configures a project when run with no arguments.  In order to
configure the project in the current directory, run

  cmake .

```

---

### Post by raedbenz on 2008-07-15
installing cute com 0.20.0

---

### Post by raedbenz on 2008-07-15
> **HymnToLife said:**
> No you don't. You should have a README with your program, please read it. We don't even know what you are trying to install...
the read me says apply cmake then make then make install.
u i still get errors. check replies
thanks

---

### Post by appi2012 on 2008-07-15
do what it says then, type:
```
cmake .
```

---

### Post by raedbenz on 2008-07-15
> **appi2012 said:**
> do what it says then, type:
```
cmake .
```

lol i did, here what is i get:
NOTE

CMake no longer configures a project when run with no arguments.  In order to
configure the project in the current directory, run

  cmake .

---

### Post by appi2012 on 2008-07-15
did you run with the period?

---

### Post by raedbenz on 2008-07-15
> **appi2012 said:**
> did you run with the period?

how?

---

### Post by appi2012 on 2008-07-15
just copy and paste:
```
cmake .
```

---

### Post by appi2012 on 2008-07-15
try running
```
cmake -i
```
that'll guide you through  process

Putting terminal output in ```

``` tags makes it easier to read. was the period ther because you were ending your sentence or because thats what it said?

---

### Post by Jahocolips on 2010-07-11
I wrote this, I think it might be helpful. Let me know what you think. [http://mathnathan.com/2010/07/11/getting-started-with-cmake/](http://mathnathan.com/2010/07/11/getting-started-with-cmake/)

---

### Post by overdrank on 2010-07-11
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

