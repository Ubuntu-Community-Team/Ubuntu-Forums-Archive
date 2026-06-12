---
title: "Can't Compile C program"
date: 2007-03-01
forum: Programming Talk
---

### Post by Ne0z on 2007-03-01
Hi guys , I am new to Ubuntu Linux (just installed it yesterday) . so i tried writing this Hello World Program and i got these errors when i tried to compile it using gcc

> hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’


My program looks fine 
> #include <stdio.h>

int main()
{
  printf("Hello, world\n");
  return 0;
}


can you guys help me out !! thanks a lot 

regards

---

### Post by chewearn on 2007-03-01
You need to install the programming packages.  Do this once:
```
sudo aptitude install build-essential
```

---

### Post by WakkiTabakki on 2007-03-01
Looks like your compiler wasn't installed properly, or somethings screwie with you environment...

Do you have the directory /usr/include and can you find stdio.h in it?
What happens if you run: 
 > cpp hello.c
 
and what about

 > cpp --sysroot=/ hello.c


/N

---

### Post by Ne0z on 2007-03-01
Thank you AstalaVista

now its working

can i know what does 

> sudo aptitude install build-essential

actually do ?

---

### Post by Malac on 2007-03-01
> **Ne0z said:**
> Thank you AstalaVista

now its working

can i know what does 



actually do ?
"sudo" raises your privileges to allow admin tasks.
"aptitude" is one of the program ways to handle installing packages on Ubuntu.
"install", obvious :)
"build-essential" is the name of the package. It includes headers and certain other files essential for building stuff.

P.S. This is not meant as a Sarcastic post, having read it back it could come across that way.

---

### Post by StevenRoose3 on 2008-02-16
maybe a stupid question:
how do i run the a.out that i get out of it?

Steven

---

### Post by rzrgenesys187 on 2008-02-16
```
./a.out
```

That will work if you are in the directory the a.out file is in (note: this is run from the terminal).

---

### Post by aks44 on 2008-02-16
StevenRoose3: see [FAQ: Compiling your first C program]("http://ubuntuforums.org/showthread.php?t=689635")

---

