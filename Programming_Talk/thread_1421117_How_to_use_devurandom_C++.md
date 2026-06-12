---
title: "How to use /dev/urandom C++"
date: 2010-03-03
forum: Programming Talk
---

### Post by nirvana21 on 2010-03-03
Hello,
I am trying to get some decently random numbers and thought I would try to read from /dev/urandom. From what I understand /dev/urandom should be read just like a file. So I am not really sure exactly how to do this correctly. Here is what I have been tinkering with:
[PHP]
        char * block;
	short size = 1;
	ifstream urandom("/dev/urandom", ios::in|ios::binary);
	urandom.open("/dev/urandom");
	urandom.read(block,size);//size in bytes?
	urandom.close();
[/PHP]
I just put 1 for size because I am not sure really what to do. I don't really think my code is correct. Somehow I need to cast it to a large number. I have implemented the GMP library. I realize I am just reading one thing and later when I understand what is going on I will use a loop to generate my large numbers.

How can I fix my mess? Thank you for help in advance.

---

### Post by psusi on 2010-03-03
You don't need .open() when you already told it what file to open in the constructor.  You also did not initialize your block pointer, so it is invalid when you pass it to .read().

---

### Post by nirvana21 on 2010-03-03
> **psusi said:**
> You don't need .open() when you already told it what file to open in the constructor.  You also did not initialize your block pointer, so it is invalid when you pass it to .read().

I missed the second .open() call. That was dumb on my behalf. I got it to do what I wanted now. I am just too tired. Thanks psusi.

---

