---
title: "APUE.3e error while running filetype.c"
date: 2016-04-03
forum: New to Ubuntu
---

### Post by Ramya_Guduru on 2016-04-03
Hi Gurus,

I'm trying to execute the below program- Within APUE.3E -> filedir -> filetype.c (this comes by default when I downloaded APUE.3E. I didn't make any changes)

but when I compile, this is the error I'm receiving: 
```
myramya~/Documents/apue.3e/filedir$ gcc filetype.c -lm -o filetype /tmp/cchPKE7K.o: In function main':
filetype.c:(.text+0x94): undefined reference toerr_ret' collect2: error: ld returned 1 exit status
```

Please help me resolve this issue.

I'm using Linux Ubuntu. I have installed APUE.3E in Documents folder. I have administrator permissions. I wrote a simple Hello.c program and executed using: 
```
$ gcc hello.c -o hello
``` 
and it worked without any issues.

Can you please help me resolve this issue? :confused:

Thank you,

---

