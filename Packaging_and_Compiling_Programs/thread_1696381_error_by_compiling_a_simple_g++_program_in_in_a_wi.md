---
title: "error by compiling a simple g++ program in in a windows share folder connect by samba"
date: 2011-02-27
forum: Packaging and Compiling Programs
---

### Post by gicnivad on 2011-02-27
Hi everyone,
I had installed Lubuntu in vmware.It connected to a windows shared folder by samba client.The problem is, after I cd into the folder and try to compile the program by typing "g++ my_program.cpp", I got an error,

cc1plus: fatal error: my_program.cpp: Value too large for defined data type
compilation terminated.

However, the complilation can be done properly in my local directorys.

Please give me some suggestions, thanks :)

---

### Post by MadCow108 on 2011-02-27
can you show the line which causes the error?
it seems you assign a to large value to a type, possibly because of 32/64 bit differences

---

### Post by gicnivad on 2011-02-27
it's just a simple testing program:

#include<cstdio>
using namespace std;
int main(){
    printf("test\n");
    return 0;
}

---

### Post by LongDong on 2011-06-06
Hi gicnivad,

to fix this you have to add
,nounix,noserverino

to your mount options. I found the solution at:
[https://wiki.archlinux.org/index.php/Samba](https://wiki.archlinux.org/index.php/Samba)

Regards
LongDong

---

