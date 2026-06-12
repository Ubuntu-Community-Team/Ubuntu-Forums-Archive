---
title: "peculiar array behaviour in C"
date: 2009-11-12
forum: Programming Talk
---

### Post by Houman on 2009-11-12
hi folks;

I just came accidentally across a strange C behaviour;

when i do something like this:

```

char myArray[100];
printf("address of array %x\n",myArray);
printf("address of address of array %x\n",&myArray);

```

I get the same output! how could a variable and its address be the same thing :|, I came across this when I realized accidentally that if i do: gets(&myarray) it works just as gets(myarray) which is unexpected, you would not expect the first one to work;

does anyone have an explanation for this? 

thank you 

H

---

### Post by johnl on 2009-11-12
Check the answers given to this question [here](http://stackoverflow.com/questions/896379/oddities-in-c-char-arrays).

---

### Post by dwhitney67 on 2009-11-12
Also, avoid using gets(); use fgets() in its place.  The reason is that you can specify the length of the array that you are passing to the function, thus ensuring that your buffer is not overrun with malicious (or perhaps benign) data.

So, gets() is equivalent to:
```

char myArray[1000];
...
fgets(myArray, sizeof(myArray), stdin);

```

---

### Post by Houman on 2009-11-12
hi there;

thank you dwhitney67 for the heads up;

and thanks johnl for the link, i read it, and i still dont get it!

when i do: char vector[100];

doesn't vector become a pointer itself , holding a memory space where teh address of the first element is located?

is this peculiar behavior due to the compiler implementation of the standard or was this defined in the standard? because i REALLY thought "vector" is a pointer and expected it to behave as one! sorry if im not getting this but its hard to change what you have thought for so many years;

H

---

### Post by Arndt on 2009-11-13
> **Houman said:**
> hi there;

thank you dwhitney67 for the heads up;

and thanks johnl for the link, i read it, and i still dont get it!

when i do: char vector[100];

doesn't vector become a pointer itself , holding a memory space where teh address of the first element is located?

is this peculiar behavior due to the compiler implementation of the standard or was this defined in the standard? because i REALLY thought "vector" is a pointer and expected it to behave as one! sorry if im not getting this but its hard to change what you have thought for so many years;

H

(I haven't read the indicated web page.)

'vector' itself is not a pointer, but it is converted to one in almost all expression contexts (one exception being 'sizeof'). The original design of C says that using & to take the address of what is already an address has no effect. So you could earlier write vector or &vector or &&vector, etc. Same thing with functions. In C89, && is apparently a way to obtain the address of a label, but the case with one & remains.

If the declaration had been char *vector; then it's different. Then 'vector' is a variable, with a value, and with an address of its own, and those two are not the same. In that case vector and &vector are not the same thing.

---

### Post by Houman on 2009-11-13
hello Arndt;

ok i think i am getting this, so if i do:

char* vector=malloc(100);

i would have 2 things, a chunk of memory worth 100 bytes, and another spot in the memory where the address of this chunk is stored, namely the pointer vector;


but if i do:

char vector[100];

I will again get 100 bytes, but i no longer have a pointer variable anywhere, and the compiler, just to be accommodating, will casr vector as a pointer in "special" circumstances? but there will no longer be a pointer anywhere in the memory (which still begs the question how does the program know what is the address of this memory chunk if nothing holds its address)

regards

H

---

### Post by Arndt on 2009-11-13
> **Houman said:**
> hello Arndt;

ok i think i am getting this, so if i do:

char* vector=malloc(100);

i would have 2 things, a chunk of memory worth 100 bytes, and another spot in the memory where the address of this chunk is stored, namely the pointer vector;


but if i do:

char vector[100];

I will again get 100 bytes, but i no longer have a pointer variable anywhere, and the compiler, just to be accommodating, will casr vector as a pointer in "special" circumstances? but there will no longer be a pointer anywhere in the memory (which still begs the question how does the program know what is the address of this memory chunk if nothing holds its address)

regards

H

Exactly. In the second case, the linker finds out the address and inserts it in all appropriate places in the code. (When it's actually used, it may be put in some processor register first, but this register has no correspondence in C code, and also doesn't have an address as such. The PDP-10 registers actually did have addresses, namely the first 16 words of memory, but I digress).

---

### Post by Houman on 2009-11-13
thank you Arndt;

i think i finally got it :) 


H

---

