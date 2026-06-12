---
title: "Replacing string in C"
date: 2010-01-20
forum: Programming Talk
---

### Post by sauronnikko on 2010-01-20
Hi. Let's say I have to strings in C:
```

char *c1 = "Hello";
char *c2 = "Bye";

```
c2 will always be at most as large as c1. What if I want to replace the "Hello" in c1 with the contents of c2, so c1 could be "Bye"?. Is there any way to do this? Thanks

---

### Post by Finalfantasykid on 2010-01-20
If I understand what you want, then I would recommend using strncpy.

```
c1 = strncpy(c1, c2, BUF_SIZE);
```

I think something like that would do it.  BUF_SIZE is just a macro for the maximum size of the string, maybe 256 or something less ridiculous like maybe 64.  Or you could also put strlen in there.

```
c1 = strncpy(c1, c2, strlen(c2));
```

I think that is what you meant.

---

### Post by sauronnikko on 2010-01-20
It gives me Segmentation Fault in either case. Perhaps the solution is somewhat similar but I can't see it

---

### Post by Senesence on 2010-01-20
> **sauronnikko said:**
> It gives me Segmentation Fault in either case. Perhaps the solution is somewhat similar but I can't see it

That's because this:

```
char *c1 = "Whatever"
```

Defines a character pointer to read-only memory.

If you want memory you can modify, do this:

```
char c1[] = "Whatever"
```

Example program (for testing purposes):

```

#include <stdio.h>
#include <string.h>

int main(void)
{
	char c1[] = "Hello";
	char c2[] = "Bye";

	strcpy(c1, c2);

	printf("c1: %s%s\n", c1, c1);
	
	return 0;
}

```

---

### Post by saulgoode on 2010-01-20
use 
```
  char c1[] = "Hello";
  char c2[] = "Bye";
```

---

### Post by supershin on 2010-01-20
> **sauronnikko said:**
> Hi. Let's say I have to strings in C:
```

char *c1 = "Hello";
char *c2 = "Bye";

```
c2 will always be at most as large as c1. What if I want to replace the "Hello" in c1 with the contents of c2, so c1 could be "Bye"?. Is there any way to do this? Thanks

Its clear you don't understand pointers. Don't worry its the most troublesome aspect of C. 

Using your example, c1 doesn't hold the string "hello", its a character pointer meaning it points to the address where "hello" is. So if "hello" is in the address 0x11 then c1 isn't the address 0x11, it holds/contains that address, that value, 0x11, and c1 address is something else, say like 0x33. 

To replace "Hello" with "Bye", you basically want c1 to point to bye, so it should be c1 = *c2; 

Note: I used *c2 not c2. You want "Bye" which is the address stored at c2 address. So you need to derefence it. You could also say c1=c2; creating a chain like this: c1->c2->bye but then if you let c2 point to something other than "Bye" then c1 would point to that other thing too, since it doesn't hold the address of "Bye" but of c2.

Hope you understand it. I think you should read up on pointers.

---

### Post by Senesence on 2010-01-21
> **supershin said:**
> To replace "Hello" with "Bye", you basically want c1 to point to bye, so it should be c1 = *c2;

I don't think that's right: 

If we agree that c2 holds the address of the first character in the "Bye" string, dereferencing that address would give us the actual character 'B'. So, c1 = *c2 would set c1 (which previously contained the address of 'H'), to the actual value of 66, or 'B'.

Actually, if you're using gcc, your compiler will warn you that you're trying to "make a pointer from an integer without a cast".

> You could also say c1=c2; creating a chain like this: c1->c2->bye but then if you let c2 point to something other than "Bye" then c1 would point to that other thing too, since it doesn't hold the address of "Bye" but of c2.

I'm pretty sure that's wrong, too. Here's why:

c1 and c2 are pointer variables that hold *addresses as values*. So, let's say that these pointers resolve to the following addresses:

c1: 0x11  (Address of 'H')
c2: 0x22  (Address of 'B')

c1 = c2 produces the following effects:

c1: 0x22  (Address of 'B')
c2: 0x22  (Address of 'B')

c1 is *not* a pointer to c2, it's now simply holding the same value as c2, which is the address of 'B'. So, we could say that both c1 and c2 would be independent pointers to 'B' in this case.

Anyway, if the OP just wanted to swap pointers, the code for that would look like this:

```

char *tmp;
tmp = c1;
c1 = c2;
c2 = tmp;

```

However, I think ""replace the "Hello" in c1 with the contents of c2"" implied that he wanted a copy, in which case using strcpy, as I did in my post, is appropriate.

---

### Post by supershin on 2010-01-29
Senesence i think you're talking bout your character array, char c1[], whereas i'm talking about his char *c1. 

Wonder what happened to TC.

---

### Post by supershin on 2010-01-29
> **Finalfantasykid said:**
> If I understand what you want, then I would recommend using strncpy.

```
c1 = strncpy(c1, c2, BUF_SIZE);
```

I think something like that would do it.  BUF_SIZE is just a macro for the maximum size of the string, maybe 256 or something less ridiculous like maybe 64.  Or you could also put strlen in there.

```
c1 = strncpy(c1, c2, strlen(c2));
```

I think that is what you meant.

I think the reason he got seg fault with with the 2nd one is because the size is too small, strlen(c2) gives 3 if c2 is bye, whereas the size of c2 is not 3 but probably 3*8=24. So use sizeof(c2) instead.

---

### Post by napsy on 2010-01-29
No, string literals can't be modified once they're defined, as Senesence already mentioned.

---

