---
title: "gcc giving compilation warning incompatible implicit declartion of  function printf()"
date: 2007-12-03
forum: Packaging and Compiling Programs
---

### Post by Alexpo on 2007-12-03
Hi, 

After installing Ubuntu to my laptop which is a dual boot vth XP I was trying gcc is working or not.

When I tried to compile a simple porogram naming test.c placed inmy  home directory..its gives two warnings

1) incompatible implicit declartion of built in function printf()

2) incompatible implicit declartion of built in function exit()

ussr/bin/ld: crtl.o : No such file or directory
collect2: ld returned 1 exit status

here is content of my test.c file

> #include <stdio.h>
 int main()
{
 printf("hello");
exit(1);
}

What are the things i am missing ?

Thanks for ur time,
Alexpo

---

### Post by geirha on 2007-12-03
Have you installed the build-essential package?

---

### Post by LaRoza on 2007-12-03
sudo aptitude install build-essential

---

### Post by Alexpo on 2007-12-06
Is the command is exactly like :

sudo aptitute install build-essential

I got the msg aptitute as not recognised.

I did not get any help from OS help or mannual  regarding it .

Will you pls, inform me more clearly how do i install build essentials.
(I do have a CD Desktop edn for Gusty Gibbon from internet only and no network connection).

Thanks again

---

### Post by n5kzw on 2007-12-06
Try "aptitude", not "aptitute".

Ed

---

### Post by Alexpo on 2007-12-08
It worked.
Ooops ...I am sorry for assuming aptitude as aptitude.

Thanks

---

