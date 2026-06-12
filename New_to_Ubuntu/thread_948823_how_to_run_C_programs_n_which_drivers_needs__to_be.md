---
title: "how to run C programs n which drivers needs  to be installed."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by prasad280 on 2008-10-15
hello guys i am computer engg student have an problem in running the C programs on my ubuntu...
i have tried to install all possible updates for it but still cant run them properly.........
i am able to run shell programs but not C..
Pls help me out as soon as possible ae my exms r near by...:confused:

---

### Post by porchrat on 2008-10-15
have you got the C libraries?

package is called "glibc" I think

---

### Post by Sarmacid on 2008-10-15
To install a c compiler

```
sudo apt-get install gcc
```

to compile 

```
gcc -g -o output input.c
```

---

