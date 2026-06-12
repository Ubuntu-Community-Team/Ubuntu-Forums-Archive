---
title: "Bit level or byte level access in C?"
date: 2010-06-23
forum: Programming Talk
---

### Post by bluedalmatian on 2010-06-23
Im a little confused about how to do bit level access to blocks of memory in C.

Ive allocated some memory in a device driver using kmalloc which is 12 bytes long, however I dont really want to access it in bytes I want individual bits.

as I understand it the copy_to_user function works at the byte level?  How can I access individual bits?

thanks
Aw

---

### Post by dwhitney67 on 2010-06-23
The smallest addressable unit is a byte (as I suppose you already know).  To get the state of a bit (or bits) within a byte you could use a "mask" to get the appropriate bit(s) or employing bit-shifting to examine a particular bit.

Here's some examples:
```

const int MASK = 0x04;   /* same is 00000100 in binary */

unsigned char byte = buffer[5];

if (byte & MASK)
{
   /* bit 2 is set (note, bits range from 0-7) */
}
else
{
   /* bit not set
}

```
```

unsigned char byte = buffer[5];

if ((byte >> 2) & 0x1)
{
   /* bit 2 is set (note, bits range from 0-7) */
}
else
{
   /* bit not set */
}

```
I hope this helps.

---

### Post by donsy on 2010-06-23
You can also use bit fields:
```
struct {
  unsigned int b1 : 1;
  unsigned int b2 : 1;
  unsigned int f1 : 3;
  unsigned int f2 : 3;
} test;
...
test.bit1 = 1;
if (test.b1) {...}
test.f2 = 7; // or any value 0..7
//etc.

```

---

### Post by bluedalmatian on 2010-06-23
that helps thanks.

is copy_to_user supposed to be called in a loop, once for each byte?

im a bit confused what the loff_t* ppos argument to the read system call is for:

```
read(struct file* filp, char* userbuf, size_t count, loff_t* ppos)
```

Am I supposed to run in a loop repeatedly calling copy_to_user until ppos has been incremented count times.

the compiler wont let me index the data source using ppos e.g this doesnt work

```
copy_to_user(tobuf,frombuffer[*ppos],count);
(*ppos)+=count;

```

Hope that makes sense?

---

### Post by nvteighen on 2010-06-24
> **bluedalmatian said:**
> that helps thanks.

is copy_to_user supposed to be called in a loop, once for each byte?

im a bit confused what the loff_t* ppos argument to the read system call is for:

```
read(struct file* filp, char* userbuf, size_t count, loff_t* ppos)
```

Am I supposed to run in a loop repeatedly calling copy_to_user until ppos has been incremented count times.

the compiler wont let me index the data source using ppos e.g this doesnt work

```
copy_to_user(tobuf,frombuffer[*ppos],count);
(*ppos)+=count;

```

Hope that makes sense?

Hm... what OS are you using? The GNU/Linux read syscall has the following signature:

```

#include <unistd.h>
ssize_t read(int fd, void *buf, size_t nbytes);

```

Or am I a bit confused?

---

### Post by bluedalmatian on 2010-06-24
its a linux char device driver

---

### Post by dwhitney67 on 2010-06-24
Where is this function defined/implemented?
```

read(struct file* filp, char* userbuf, size_t count, loff_t* ppos)

```
I searched the Linux (RHEL) kernel source, and I could not find this particular "flavor" amongst the various other read functions.

---

### Post by bluedalmatian on 2010-06-24
According to my book 'Linux Device Drivers' by O'Reilly (3rd Ed for the 2.6 kernel) a char driver has to write its own implementation of that function which is called when ever a process tries to read from the /dev file.

You also have to implement open() release() and optionally write()

---

### Post by jpkotta on 2010-06-25
I like to make macros or functions that access bits.

```

#include <stdint.h>
#include <stdio.h>

#define bit_in_byte(b,n) (((b) >> ((n)&7)) & 1)
#define bit_in_array(a,n) bit_in_byte(*((uint8_t *)(a)+((n)>>3)), n)

int main(void)
{
	uint32_t x = 0xDEADBEEF;
	uint8_t y = 0xa5;
	int i;

	for (i = 0; i < 8; i++) {
		printf("bit %d = %d\n", i, bit_in_byte(y,i));
	}
	
	for (i = 0; i < 32; i++) {
		printf("bit %d = %d\n", i, bit_in_array(&x, i));
	}
	
	return 0;
}

```

---

