---
title: "[SOLVED] Noob fread() (C/C++)"
date: 2008-08-01
forum: Programming Talk
---

### Post by era86 on 2008-08-01
Ok.. so I thought I understood C/C++ pretty well.  Maybe I'm missing something... :roll:

Here is what I am confused about:

uint16_t buf[1024];

fread( buf, 2, 512, myfile );

Ok... so my array has 1024 16bit items.  I want to read in 2 bytes into each space alloted in the array.  Is my fread() correct for this?

Please let me know.  Any help is appreciated.  Thanks!

---

### Post by mike_g on 2008-08-01
IIRC then you want to be doing this instead:
```
fread(&buf, sizeof(uint16_t), 1024, myfile);
```

---

### Post by dwhitney67 on 2008-08-01
And in respect to C++,
[PHP]
std::fstream ifs( "data", std::ios::in | std::ios::binary );

uint16_t buf[1024] = {0};

ifs.read( (char*)buf, 1024 * sizeof(uint16_t) );
[/PHP]
In C++, the read() method of the ifstream container reads characters (8 bits), thus for the buffer declared above, we specify 2048 bytes because the buffer is an array of uint16_t, each of which is 2 bytes long.

---

### Post by StOoZ on 2008-08-01
yet to see this type of initialization (?) , but what does this do:
> uint16_t buf[1024] = {0};

initializes all the 1024 indexes to 0?

---

### Post by dwhitney67 on 2008-08-01
Yes, that is what is does.  It's a short-hand way to initialize an array to all zeroes (nulls).

But beware that construct does not work if you are attempting to initialize an array to a non-zero value.  In such case, it would be more prudent to use memset().

In the example below, only the first element of buf1 will be initialized (to a 10); the other elements will either be zero or some undefined value.
[PHP]uint16_t buf1[1024] = { 10 };[/PHP]
If you have an array with a small buffer size, then you can initialize like:
[PHP]uint16_t buf2[5] = { 10, 10, 10, 10, 10 };
uint16_t buf3[5] = { 10, 20, 30, 40, 50 };[/PHP]
The safest bet for large arrays is memset():
[PHP]
uint16_t buf4[1024];
memset( buf4, 10, 1024 * sizeof(uint_t) );[/PHP]

---

### Post by era86 on 2008-08-01
Thank you for the prompt response.  I managed to get it reading correctly using the sizeof() function.  I can't believe it was something so simple.

Thanks again.

---

