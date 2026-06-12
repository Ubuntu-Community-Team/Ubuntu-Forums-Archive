---
title: "what is meaning of &quot;sin&quot; in sin_port?"
date: 2010-06-01
forum: Programming Talk
---

### Post by vksingh on 2010-06-01
struct sockaddr_in {
    short            *sin_family*;   // e.g. AF_INET, AF_INET6
    unsigned short   *sin_port*;     // e.g. htons(3490)
    struct in_addr   *sin_addr*;     // see struct in_addr, below
    char             *sin_zero*[8];  // zero this if you want to
};

In the above code, **sin** has been used. What is the meaning of this word "sin" with respect to 
above code?

Thanks,

Vivek

---

### Post by trent.josephsen on 2010-06-01
I don't know where this code comes from or what it's used for, but I'd guess from context that it's just an abbreviation for sockaddr_in.

---

### Post by MadCow108 on 2010-06-01
As it is the internet family structure I guess: **s**ocket **in**ternet
makes sense as e.g. unix family has sun_ -> **s**ocket **un**ix
and link layer has sll_ -> **s**ocket **l**ink **l**ayer
etc.

---

