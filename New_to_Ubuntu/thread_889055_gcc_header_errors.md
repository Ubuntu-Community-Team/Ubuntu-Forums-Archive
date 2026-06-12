---
title: "gcc header errors"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Mynameistaken on 2008-08-13
Xubuntu 8.04.1 Dell D610 

When I try to compile hello.c (as an example) i get the following errors.

> gcc hello.c
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:4: warning: return type of ‘main’ is not ‘int’

after looking into other threads I checked:
gcc is (freshly re-) installed
build-essential is (freshly re-) installed
headers are present in /usr/include/

Thanks

---

### Post by LinuxRocks713 on 2008-08-20
Are you using ```
void main()
```? If so, that may be one of the problems. Try again with ```
int main(int argc,char** argv)
```. Else, reinstall build essential.

Hint: use the -o option so that the filename isn't a.out.

---

### Post by Novus on 2008-08-20
And you post this in absolute beginner talk.. oh well :D
Is gcc aware of /usr/include ?
```
gcc -print-search-dirs
```
I don't have it there..
I have nothing to try with so Im just guessing here :)
but try adding ```
-B /usr/include/
```

---

### Post by Potatoj316 on 2008-08-20
everyone has this problem, simple fix...
```
sudo aptitude install build-essential
```

except that you said you already did that.  I have no idea, it looks like your missing the headers.

---

