---
title: "Troubles when compiling pHash"
date: 2012-06-10
forum: Packaging and Compiling Programs
---

### Post by msoftprogramming on 2012-06-10
Hi all, 
here is some (probably) very simple problem: I'm trying to use the perceptual hashing library pHash with Ubuntu 11.10. I already had ffmpeg installed, by the way this is what I've done: 

```
sudo apt-get install libphash0
sudo apt-get install libphash0-dev
```Then tried to compile this program:

```
#include <iostream>

#include <pHash.h>

using namespace std;

int main()
{
    ulong64 myhash=0;
    
    ph_dct_imagehash("test.jpg", myhash);
    cout<<myhash<<endl;
}
```When compiling, it just prints out:
```
undefined reference to `ph_dct_imagehash'
```Any suggestion? What should I do?
Thanks in advance!

Matteo Monti

---

### Post by MadCow108 on 2012-06-10
libraries need to be behind objects needing them:
```
$ g++ file.c -lpHash

```

---

### Post by SevenMachines on 2012-06-10
Most likely you're linking libraries after objects, ie
```
#g++  -lpHash test.cpp  # Wrong!
/tmp/cclknlvN.o: In function `main':
test.cpp:(.text+0x1d): undefined reference to `ph_dct_imagehash'
collect2: ld returned 1 exit status
#g++ test.cpp  -lpHash # Right!
```

For the reason why...
[http://www.gentoo.org/proj/en/qa/asneeded.xml](http://www.gentoo.org/proj/en/qa/asneeded.xml)
Note, --as-needed is default these days, perhaps a well written explanation should go down as a sticky :)

---

