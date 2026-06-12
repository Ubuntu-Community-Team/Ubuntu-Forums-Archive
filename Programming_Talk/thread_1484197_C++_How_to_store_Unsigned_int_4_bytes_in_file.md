---
title: "C++ How to store Unsigned int 4 bytes in file"
date: 2010-05-15
forum: Programming Talk
---

### Post by Zaizeku on 2010-05-15
Ok guys I need your help, I'm trying to store unsigned ints in a file, but I can only manage to write 1 byte in the file

```
fstream file;

file.open("File",ios::in|ios::out|ios::binary);

unsigned int data = 1000;

file.put(data);

file.close();
```

I know put() stores only ONE byte of my 4 bytes, I don't know how can I store the whole 4 bytes in the file.

So I've come to ask you guys, how can I accomplish this task.

Thanks in advance.

---

### Post by MadCow108 on 2010-05-15
file.write(reinterpret_cast<char*>(&data), sizeof(data));

---

### Post by Zaizeku on 2010-05-15
> **MadCow108 said:**
> file.write(reinterpret_cast<char*>(&data), sizeof(data));

Thank You MadCow you are my HERO =D>

---

### Post by mmix on 2010-05-15
//this works too.
file.write((const char *)(&data),4);

---

### Post by Some Penguin on 2010-05-15
Bear in mind that the number and order of the bytes in an int() are platform-dependent.

---

### Post by Sockerdrickan on 2010-05-15
> **mmix said:**
> //this works too.
file.write((const char *)(&data),4);
Yes well that sucks compared to using reinterpret_cast.

> **Some Penguin said:**
> Bear in mind that the number and order of the **bytes** in an int() are platform-dependent.
bits even

---

### Post by rnerwein on 2010-05-16
hi 
may be you can use: 
     htonl,  htons,  ntohl,  ntohs - convert values between host and networ byte order too before and back  store the data.
ciao

---

### Post by wmcbrine on 2010-05-16
> **Sockerdrickan said:**
> Yes well that sucks compared to using reinterpret_cast.Why so?

---

### Post by LKjell on 2010-05-16
> **wmcbrine said:**
> Why so?

Casting in the C way has always been a bit magically. :)

---

