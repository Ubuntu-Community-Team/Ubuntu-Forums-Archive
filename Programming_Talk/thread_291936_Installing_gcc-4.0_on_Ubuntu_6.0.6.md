---
title: "Installing gcc-4.0 on Ubuntu 6.0.6"
date: 2006-11-03
forum: Programming Talk
---

### Post by reghuram on 2006-11-03
Hello,

I just installed gcc-4.0 using Synaptic. However when I typed gcc, it could not find the command. So I created a sym link in /usr/bin to point to gcc-4.0.

In my home dir I created the file helloworld.c . Code as follows:
#include <stdio.h>

int main()
{
printf("Hello World. \n");
return 0;
}

I compiled this file using the command: gcc helloworld.c
The compiler gave me an error saying that it couldn't find "stdio.h". I checked in the /usr/include dir and I couldn't find any of the standard c header files.

Could someone please tell me where I went wrong?

Thank you.

---

### Post by loell on 2006-11-03
perhaps do

sudo aptitude install build-essential

;)

---

### Post by drunkenrobot on 2006-11-03
thank you thank you thank you thank you thank you thank you

---

### Post by reghuram on 2006-11-06
Thank you. :D

---

