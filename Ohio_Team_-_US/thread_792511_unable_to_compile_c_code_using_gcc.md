---
title: "unable to compile c code using gcc"
date: 2008-05-13
forum: Ohio Team - US
---

### Post by sailend on 2008-05-13
Hi,
I have installed ubuntu 8.04 to my notebook. 
when i am trying to compile the c-code using gcc, i am getting error as unable to find stdio.h header file.

please let me know how i will ptroceed.
also i am unable to find scanf, fgetc, fpritf etc through man page.
but i am able to see the gcc path.

please help me in solving this issue.
/Sailendra

---

### Post by MaindotC on 2008-05-13
Hi, sailend.  Can you post the contents of your .c file please?

---

### Post by ad_267 on 2008-05-13
```
sudo apt-get install build-essential
```

---

### Post by sailend on 2008-05-13
Thanks StrAlan for your quick reply.

Actually my c file is very simple one like to "print hello world". My intention is to see  gcc is working on ubuntu 8.04 or not.

ex- #include<stdio.h>
    int main()
    {
      printf("Hello World"); return 0;
    }

The problem is: I think the setting of path or something like this becuse gcc is unable to detect header file <stdio.h> and also all other header file. 

so please let me know how i set this path or should i install the new gcc. if so please tell me the way to proceed.

Thanks you again in advance...

/sailendra

---

### Post by MaindotC on 2008-05-13
Yeah make sure you have build-essential installed.

---

### Post by MaindotC on 2008-05-14
Did it work for you?

---

