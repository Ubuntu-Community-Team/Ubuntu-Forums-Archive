---
title: "Extracting info from a struct"
date: 2009-06-23
forum: Programming Talk
---

### Post by Rij on 2009-06-23
Hello,

I need some help with the following.

I have a buffer of 200 characters. Of that, I am interested only in the first 4 bytes. I want to cast the 1st two bytes in short s1 and the second two in short s2. How can I do it? I tried the following but it doesn't work.

```

struct My_Struct {
  short s1;
  short s2;
  void *ptr;
};

char buf[200];
struct My_Struct *sptr;

s_ptr = (My_Struct *)buf;

```

This is not the way it seems. Can someone please suggest something?

TIA

---

### Post by dwhitney67 on 2009-06-23
Try something like this:
```

struct MyStruct ms;
memcpy(&ms.s1, buf, sizeof(ms.s1));
memcpy(&ms.s2, buf + sizeof(ms.s1), sizeof(ms.s2));

```
If you require that your struct be allocated on the heap, then something like:
```

struct MyStruct* ms = malloc(sizeof(struct MyStruct));
memcpy(&ms->s1, buf, sizeof(ms->s1));
memcpy(&ms->s2, buf + sizeof(ms->s1), sizeof(ms->s2));
...
free(ms);

```

If you comprehend the above, then you will be one step closer to understanding the concepts of de-serialization of data (which is the opposite of serialization).

P.S.  I know of people who prefer to cast as you demonstrated in your OP.  I'm surprised that it did not work.  Could it be that your data bytes are reversed?  Nothing like ntohs() to the rescue.

P.S.S.  This works fine...  Just decide which of the results you like best; the original or the one altered with the ntohs().
```

#include <stdio.h>
#include <arpa/inet.h>     /* for ntohs() */

struct MyStruct
{
  unsigned short s1;
  unsigned short s2;
  void*          ptr;
};

int main()
{
  const unsigned char buf[10] = { 0x31, 0x32, 0x33, 0x34, 0x00, 0x00, 0x00, 0x00, 0x00, 0x01 };

  struct MyStruct* ms = (struct MyStruct*) buf;

  printf("ms->s1 = 0x%04x\n", ms->s1);
  printf("ms->s2 = 0x%04x\n", ms->s2);

  printf("ms->s1 = 0x%04x\n", ntohs(ms->s1));
  printf("ms->s2 = 0x%04x\n", ntohs(ms->s2));

  return 0;
}

```

---

### Post by Can+~ on 2009-06-23
Other way is to use a union.

[PHP]#include <stdio.h>
#include <string.h>

typedef union 
{
	char word[4];
	unsigned short int s[2];
}shortchar;

struct myStruct
{
	shortchar value;
	void *ptr;
}

int main(int argc, char **argv)
{
	// From char to shorts
	shortchar x;
	char sample[] = "hello";
	
	memcpy(x.word, sample, 4);
	
	printf("%d %d\n", x.s[0], x.s[1]);
	
	return 0;	
}[/PHP]

It's basically the same as Dwhitney's (after all, you're just stepping on memory), but it might be more "friendly".

---

### Post by Can+~ on 2009-06-23
> **dwhitney67 said:**
> Try something like this:
```

struct MyStruct ms;
memcpy(&ms.s1, buf, sizeof(ms.s1));
memcpy(&ms.s2, buf + sizeof(ms.s1), sizeof(ms.s2));

```

Oh, btw, this is just like stepping directly:

[PHP]struct mystruct {
	unsigned short s1, s2;
	void *ptr;
};

.....

struct mystruct *myst = malloc(sizeof(struct mystruct));	
memcpy(&(myst->s1), astring, sizeof(short)*2);[/PHP]

Unsafe? hell yes. It will only work when s2 is immediately after s1. You could even insert over myst and it will still work (because s1 and s2 are immediately there)

---

### Post by fr4nko on 2009-06-24
Your cqst does not works because the C compiler is free to add extra padding spaces between fields of a structure. So, in your example you cannot be sure that the s2 field of My_Structs is just two bytes away from s1.

In my opinion you don't need to use memcpy if you just want to read the informations. You can do something like that:
```

const char *
get_buffer_info (const char buffer[], short *s1, short *s2)
{
  const char *ptr = buffer;
  
  *s1 = *(const short *) ptr;
  ptr += 2;

  *s2 = *(const short *) ptr;
  ptr += 2;

  /* return the pointer to the remaining part of the buffer */
  return ptr;
}

```If you need to do this kind of unpacking with many kinds of structures you can consider to define a class and implement some methods like 'get_short', 'get_word' or something like that. You can keep the information about the current position by using a pointer as a class attribute or otherwise you can store it like an external pointer.

Finally the cast into C structures is tricky because you cannot made any assumptions about data alignment. You can use memcpy but only if you need to make some copies. I believe also that direct access with casting and referencing is mode efficient then calling memcpy to copy just two bytes.

In python there is a pretty good implementations of this kind of stuff with the [struct]("http://docs.python.org/library/struct.html") module. It does use a simple format string to describe the packing and it is very handy to use. I don't know if the C++ equivalent exists but may be you can implement by youself a similar subset of functionalities.

Francesco

---

