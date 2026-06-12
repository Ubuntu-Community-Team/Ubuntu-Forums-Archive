---
title: "C: help with pointers/structs"
date: 2009-08-22
forum: Programming Talk
---

### Post by mcweaver1 on 2009-08-22
Hi,

I have a data structure 
```

struct example {
    void  *iov_base; // points to data I need to access
    size_t iov_len; // gives the length of the data
};

```

I pass it to another function as one of its parameters, defined by:
```

const structure_type *          example,

```

Within this function I want to access the data stored in example.iov_base

I can access the length of the data with "example.iov_len" but "example.iov_base" gives me the memory address rather than the actual data at that address.  So how do I go about accessing this data?

Once I've accessed the data I need to manipulate it in blocks of 1024 bits.  I have previously been reading this data from a file using 
```

inlen = fread(inbuf, 1, 1024, in); // reading from file stream called in, reading 1024 bits at a time into inbuf, inlen giving the number of bits read

```

within a for loop, but now I need to read 1024 bits at a time from the data in example.iov_base - is there a function similar to fread that I can use to read data from this structure into an array inbuf, 1024 bits at a time?

Thanks for any help, much appreciated! :)

---

### Post by SledgeHammer_999 on 2009-08-22
> **mcweaver1 said:**
> I can access the length of the data with "example.iov_len" but "example.iov_base" gives me the memory address rather than the actual data at that address.  So how do I go about accessing this data?



iov_base is a pointer. To access the data that it points to you need to dereference it. In this case, this is done like this: ***(example.iov_base)**

---

### Post by mcweaver1 on 2009-08-22
ahh I thought I had to put an asterisk before it but got an error when I tried... turns out I'd forgotten the brackets! (dur). Thanks :D

Say there are 10240 bits of data stored in example.iov_base, I want to read this data 1024 bits at a time and then process those 1024 bits, so I would have a for loop looping 10 times to access all the data.  Is it better to read all the data at example.iov_base into a FILE * temp_file and then I can fread data from that file 1024 bits at a time, or is there a similar function which would enable me to read 1024 bits at a time directly from example.iov_base?

---

### Post by Tony Flury on 2009-08-22
> **mcweaver1 said:**
> Hi,

I have a data structure 
```

struct example {
    void  *iov_base; // points to data I need to access
    size_t iov_len; // gives the length of the data
};

```

Within this function I want to access the data stored in example.iov_base

I can access the length of the data with "example.iov_len" but "example.iov_base" gives me the memory address rather than the actual data at that address.  So how do I go about accessing this data?


if a is a pointer to the above structure then : 

```

a -> iov_len // the Length member in the structure
a -> iov_base // the address of your data 

```

assuming then that you have actually allocated the memory for the data (using malloc or similar) then : 

```

*(a -> iov_base) // use the pointer and access the first item (i think since the pointer is declared as a void, then the item will be a byte)

```

if b is the actual structure - then you can use 

```

b.iov_len
b.iov_base
*(b.iov_base)

```
to do the equivalent things.

> 
Once I've accessed the data I need to manipulate it in blocks of 1024 bits.  I have previously been reading this data from a file using 
```

inlen = fread(inbuf, 1, 1024, in); // reading from file stream called in, reading 1024 bits at a time into inbuf, inlen giving the number of bits read

```

within a for loop, but now I need to read 1024 bits at a time from the data in example.iov_base - is there a function similar to fread that I can use to read data from this structure into an array inbuf, 1024 bits at a time?

Thanks for any help, much appreciated! :)

firstly - are you sure fread is reading bits (i would have thought it will read bytes).

secondly - if you have the memory allocated for the buffer and the pointer to the memory is stored in the structure then :

```

inlen = fread(b.iov_base, 1, 1024, in) ; 

```
should work to read the first 1024 bytes in the buffer pointed to be iov_base

---

### Post by dwhitney67 on 2009-08-22
> **Tony Flury said:**
> ...
firstly - are you sure fread is reading bits (i would have thought it will read bytes).
...


Excellent observation.

OP - Is your pointer storing 10240 bytes, or is it bits?  There are (typically) 8 bits to a byte.

Assuming your mistyped (a couple of times), and really meant bytes, you can read 1024 bytes from iov_base into a preallocated array in a manner similar to the following:

```

char array[10][1024];

for (int i = 0; i < 10; ++i)
{
   memcpy(array[i], example.iov_base + 1024*i, 1024);
}

```

---

### Post by mcweaver1 on 2009-08-22
> **Tony Flury said:**
> 
firstly - are you sure fread is reading bits (i would have thought it will read bytes).

secondly - if you have the memory allocated for the buffer and the pointer to the memory is stored in the structure then :

```

inlen = fread(b.iov_base, 1, 1024, in) ; 

```
should work to read the first 1024 bytes in the buffer pointed to be iov_base

Ah yes I meant bytes. 

Surely ```

inlen = fread(b.iov_base, 1, 1024, in) ; 

``` reads the first 1024 bytes from the stream "in" into b.iov_base?  I want to either read all the data at once from b.iov_base into a file, or 1024 bits at a time from b.iov_base into a temporary buffer.

Or have I misunderstood what you said.  Thanks very much for helping!

---

### Post by dwhitney67 on 2009-08-22
> **mcweaver1 said:**
> Ah yes I meant bytes. 

Surely ```

inlen = fread(b.iov_base, 1, 1024, in) ; 

``` reads the first 1024 bytes from the stream "in" into b.iov_base?  I want to either read all the data at once from b.iov_base into a file, or 1024 bits at a time from b.iov_base into a temporary buffer.

Or have I misunderstood what you said.  Thanks very much for helping!
Your requirements, or perhaps the way you phrase them, are very confusing.  What is it that you need?  To READ data FROM a file INTO a structure, or do you need to WRITE data FROM a structure TO a file?  Please specify!

---

### Post by mcweaver1 on 2009-08-22
> **dwhitney67 said:**
> Excellent observation.

OP - Is your pointer storing 10240 bytes, or is it bits?  There are (typically) 8 bits to a byte.

Assuming your mistyped (a couple of times), and really meant bytes, you can read 1024 bytes from iov_base into a preallocated array in a manner similar to the following:

```

char array[10][1024];

for (int i = 0; i < 10; ++i)
{
   memcpy(array[i], example.iov_base + 1024*i, 1024);
}

```

Well 10240 bytes (i did mean bytes - whoops) was just an example - the amount of data held in example.iov_base changes and is most likely not a multiple of 1024.  I see what you are suggesting here with the memcpy, that seems a good idea! 

If example.iov_len (the no of bytes in example.iov_base) is not a multiple of 1024, is there an easier way to copy the last block of data into array[i] than to use example.iov_len to calculate the number of full blocks of 1024 bytes there are in example.iov_base, apply the for loop using that result, and then calculate the number of bytes left (<1024) and apply memcpy to that number of bytes...?

---

### Post by mcweaver1 on 2009-08-22
> **dwhitney67 said:**
> Your requirements, or perhaps the way you phrase them, are very confusing.  What is it that you need?  To READ data FROM a file INTO a structure, or do you need to WRITE data FROM a structure TO a file?  Please specify!

Sorry... Ideally I want to:

Read 1024 bytes at a time from example.iov_base into a temporary buffer, so that I can manipulate 1024 bytes at a time of that data until every single byte has been processed.  No external files involved.

One of the ways I thought of doing this is to read all the data from example.iov_base into a file, and then when all the data is in that file I can read from it 1024 bytes at a time using fread, and then process the data in blocks of 1024 bytes that way.  However this seems a very inefficient way of doing the above.

Thanks

---

### Post by PmDematagoda on 2009-08-22
> **mcweaver1 said:**
> Sorry... Ideally I want to:

Read 1024 bytes at a time from example.iov_base into a temporary buffer, so that I can manipulate 1024 bytes at a time of that data until every single byte has been processed.  No external files involved.

One of the ways I thought of doing this is to read all the data from example.iov_base into a file, and then when all the data is in that file I can read from it 1024 bytes at a time using fread, and then process the data in blocks of 1024 bytes that way.  However this seems a very inefficient way of doing the above.

Thanks

Then what you would need is the memcpy() example provided by dwhitney67 above, but why are you using a generic pointer for the data? If the data is of a specific type then your task would be more easier by using types with their related functions instead of trying to work with generic pointers and the low level paraphernalia you would be dealing with(atleast according to my opinion).

---

