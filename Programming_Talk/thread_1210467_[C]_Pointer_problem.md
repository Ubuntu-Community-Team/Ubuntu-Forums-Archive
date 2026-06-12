---
title: "[C] Pointer problem"
date: 2009-07-11
forum: Programming Talk
---

### Post by psld on 2009-07-11
Hi!
I have a little problem.
The struct msgPacket contains a void* named packetStart. packetStart points at a place. I want the second byte that packetStart points at to be an adress to a char.
I've tried this:

**msg.packetStart **           *is void*, points at place, contains adress*
**msg.packetStart[1]**        *is void, is sizeof(void) away from packetStart (yes I know I cant use sizeof(void)*
**(char)msg.packetStart[1]**      *is char, 1 byte away from packetStart*
**&(char)msg.packetStart[1]**    *is &char, should work? It dont. *

The error is:
"pointer of type <void *> used in arithmetic"

The goal is to pass a &char over to strcpy();

---

### Post by MadCow108 on 2009-07-11
is that what you want?
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

struct bla
{
	void * pk;
};
int main (int argc, char *argv[])
{
	struct bla test;
	char c[] = "bkd";
	test.pk = (void*)&c;
	printf("%s\n",c);
	char * n = malloc(3*sizeof(char));

	//one
	strcpy(n,&(((char*)test.pk)[1]));
	printf("%s\n",n);
	//two
	char * pointer =((char*)test.pk)+1;
	strcpy(n,pointer);
	printf("%s\n",n);
	//three
	pointer =((char*)test.pk);
	strcpy(n,++pointer);
	printf("%s\n",n);
	free(n);
	return 0;
}

```
output
```

bkd
kd
kd
kd

```

---

### Post by fr4nko on 2009-07-11
Whay you should do is a cast to a (char *) before any pointer arithmetic:
```

char *ptr = msg.packetStart;

/* ptr+1 gives the address of packetStart by skipping 1 byte */
strcpy (mybuffer, ptr + 1); 

```or, equivalently
```

strcpy (mybuffer, (char *) msg.packetStart + 1);

```The logic of this latter expression is

[LIST]
[*]cast to (char *): consider msg.packetStart as a pointer to an array of char
[*]add to this latter point +1. Since it is a char array +1 means +1 char
[/LIST]
Note that it works because the cast operator has an higher precedence that addition.

Francesco

---

