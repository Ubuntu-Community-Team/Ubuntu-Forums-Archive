---
title: "Compile Error in C programmes using command line interface"
date: 2009-02-15
forum: Programming Talk
---

### Post by Electricalkhukuma on 2009-02-15
Whenever i try to write some code in "nano" using command line, my code doesn't compile.
e.g 

```
#include<stdio.h>
int main(void){

printf("TEST CODE");
return 0;
}

```


whenever i try to compile it, the error shows up like this:

Error: "stdio.h" no such file or directory exists.

---

### Post by Yellow Pasque on 2009-02-15
```
sudo apt-get install libc6-dev
```

---

### Post by bapoumba on 2009-02-15
Moved to PT.

---

### Post by jimi_hendrix on 2009-02-15
```
sudo apt-get install build-essential #if this doesnt work try build-essentials...i cant remember wich
```

---

### Post by WW on 2009-02-15
> **jimi_hendrix said:**
> ```
sudo apt-get install build-essential #if this doesnt work try build-essentials...i cant remember wich
```

[build-essential](http://packages.ubuntu.com/intrepid/build-essential) is the "meta-package" to install.  Installing it will install gcc, g++, the C libraries and headers, make, and some other stuff.

---

### Post by jimi_hendrix on 2009-02-15
> **WW said:**
> [build-essential](http://packages.ubuntu.com/intrepid/build-essential) is the "meta-package" to install.  Installing it will install gcc, g++, the C libraries and headers, make, and some other stuff.

right, and the forum advises installing it first (check sticky)

---

