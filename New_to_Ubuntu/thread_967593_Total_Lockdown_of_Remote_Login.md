---
title: "Total Lockdown of Remote Login"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Chrissd on 2008-11-02
Hi

I don't know if this is possible or not, but I want to restrict remote login for someone to just two commands (one to start a program and the other to logout). I definitely don't want to give them the ability to su or browse the file system outside of their home directory.

Is this possible?

---

### Post by Peter09 on 2008-11-02
You can build a chroot SSH

see here

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

### Post by Chrissd on 2008-11-02
Following that, on the first page, I got an error, like this..

```
example.c:504: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:506: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘main’:
example.c:524: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:524: error: ‘stderr’ undeclared (first use in this function)
example.c:525: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:528: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:531: warning: incompatible implicit declaration of built-in function ‘printf’
example.c:534: warning: incompatible implicit declaration of built-in function ‘calloc’
example.c:541: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [example.o] Error 1

```

and 

```

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

```

Any clue? :confused:

---

### Post by tangibleorange on 2008-11-02
> **Chrissd said:**
> Following that, on the first page, I got an error, like this..

```
example.c:504: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:506: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘main’:
example.c:524: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:524: error: ‘stderr’ undeclared (first use in this function)
example.c:525: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:528: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:531: warning: incompatible implicit declaration of built-in function ‘printf’
example.c:534: warning: incompatible implicit declaration of built-in function ‘calloc’
example.c:541: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [example.o] Error 1

```

and 

```

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

```

Any clue? :confused:

the second error usually means you haven't installed the build-essential package:

```
sudo apt-get install build-essential
```

---

### Post by Chrissd on 2008-11-02
Well, definately got a lot further and looked a lot better, but after 

```

 ./configure --exec-prefix=/usr --sysconfdir=/etc/ssh --with-pam

```
I got a load of yes's, and then.
```

configure: error: PAM headers not found

```

Sorry, how do I get PAM headers?

---

