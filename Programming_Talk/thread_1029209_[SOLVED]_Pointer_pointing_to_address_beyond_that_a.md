---
title: "[SOLVED] Pointer pointing to address beyond that allocated by malloc() ?"
date: 2009-01-03
forum: Programming Talk
---

### Post by ProgramErgoSum on 2009-01-03
Hi,
C question

I have allocated a int pointer with size as 20 bytes. Therefore, it has a capacity to hold 5 integers. If the starting address of allocated 20 bytes was manipulated such that it is greater than starting address plus 20 bytes, shouldn't it be flagged as an exception ? I know that the pointer holds an address value that can be manipulated endlessly, but shouldn't the manipulation be for only that range to which the pointer was pointing to ?
```

int main(void) {
	int *p = malloc(20);  /* Obtained the starting address for a chunk of 20 bytes */

	*p = 138; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 295; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 377; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 473; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 575; printf("Value : %i at : %p \n", *p, p); ++p ; /* Shouldn't this be an exception ? */
	*p = 609; printf("Value : %i at : %p \n", *p, p);

	return (0);
}

```

What have I not understood ?

---

### Post by Martin Witte on 2009-01-03
The programmer is responsible to avoid [buffer overflows]("http://en.wikipedia.org/wiki/Buffer_overflow"), see the [specification of malloc]("http://www.opengroup.org/onlinepubs/009695399/functions/malloc.html")

---

### Post by ProgramErgoSum on 2009-01-03
Thanks !

---

### Post by dwhitney67 on 2009-01-03
> **ProgramErgoSum said:**
> Hi,
C question

I have allocated a int pointer with size as 20 bytes. Therefore, it has a capacity to hold 5 integers. If the starting address of allocated 20 bytes was manipulated such that it is greater than starting address plus 20 bytes, shouldn't it be flagged as an exception ? I know that the pointer holds an address value that can be manipulated endlessly, but shouldn't the manipulation be for only that range to which the pointer was pointing to ?
```

int main(void) {
	int *p = malloc(20);  /* Obtained the starting address for a chunk of 20 bytes */

	*p = 138; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 295; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 377; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 473; printf("Value : %i at : %p \n", *p, p); ++p ;
	*p = 575; printf("Value : %i at : %p \n", *p, p); ++p ; /* Shouldn't this be an exception ? */
	*p = 609; printf("Value : %i at : %p \n", *p, p);

	return (0);
}

```

What have I not understood ?

You have allocated 20 bytes of storage.  An int occupies 4 bytes.  You should be able to store up to 5 int values at the storage area you allocated.

Thus storing 575 will be ok, and incrementing the pointer 'p' will also be ok.  However when you store 609, then you are trampling onto other memory.  This may cause an "exception" to occur (if the address is beyond that of your app's program space) or if some other part of your application depended on the data that was trampled upon.

In short, beware of your storage buffer sizes.

---

### Post by ProgramErgoSum on 2009-01-03
> However when you store 609, then you are trampling onto other memory. This may cause an "exception" to occur (if the address is beyond that of your app's program space) or if some other part of your application depended on the data that was trampled upon.
Yes, I was thinking the same when I started this thread. I was thinking that some sort of protection would be offered 'natively'.

I guess, I will have to stick to my good programming practices ! :D

---

### Post by Wybiral on 2009-01-03
lol, exceptions and bounds-checks in C? Nope, just bugs and crashes.

---

### Post by dwhitney67 on 2009-01-03
> **Wybiral said:**
> lol, exceptions and bounds-checks in C? Nope, just bugs and crashes.

Pretty much the same with any other language too.  The application will not do anything other than what the programmer instructs it to do.

---

### Post by nvteighen on 2009-01-03
I don't see the problem... What you did there is to declare an int array of size 5 allocated in heap... so it behaives as any other regular array.

Of course, a more readable (and common way) to do that would be:
```

int *p = (int *)malloc(5 * sizeof(int));

```

The (int *) cast is optional, as malloc() returns (void *)... I just like to have it there :p

---

### Post by dwhitney67 on 2009-01-03
> **nvteighen said:**
> I don't see the problem... What you did there is to declare an int array of size 5 allocated in heap... so it behaives as any other regular array.

Of course, a more readable (and common way) to do that would be:
```

int *p = (int *)malloc(5 * sizeof(int));

```

The (int *) cast is optional, as malloc() returns (void *)... I just like to have it there :p
The problem, or I should say experiment the OP was attempting to do, was to see if there were any effects when attempting to insert a sixth value into the "array".

---

### Post by ProgramErgoSum on 2009-01-03
> The problem, or I should say experiment the OP was attempting to do, was to see if there were any effects when attempting to insert a sixth value into the "array".
That's right !

---

### Post by shadylookin on 2009-01-03
C will gladly give you the rope to hang yourself with, which is why it's almost universally disliked as a programing language for beginners

---

### Post by dwhitney67 on 2009-01-03
> **shadylookin said:**
> C will gladly give you the rope to hang yourself with, which is why it's almost universally disliked as a programing language for beginners
This utter nonsense.  Other programming languages provide the same tools for the developer to screw up as well.  The only different is how the application reacts.  In Java, an exception is thrown and then the stack trace is dumped.

---

### Post by Wybiral on 2009-01-04
> **dwhitney67 said:**
> This utter nonsense.  Other programming languages provide the same tools for the developer to screw up as well.  The only different is how the application reacts.  In Java, an exception is thrown and then the stack trace is dumped.

But you can catch the exceptions, because it has exception handling, C does not. In C you can just ruthlessly write over memory that could be used by something else, in Java/Python a catchable exception is thrown and no memory is corrupted.

---

### Post by dwhitney67 on 2009-01-04
> **Wybiral said:**
> But you can catch the exceptions, because it has exception handling, C does not. In C you can just ruthlessly write over memory that could be used by something else, in Java/Python a catchable exception is thrown and no memory is corrupted.
I agree. But *generally* the end result is the same; the application goes 'poof' because a desired functionality could not be met, and the programmer must go back and fix the code.

Some programming languages offer the programmer hints as to where the error occurred, others such as C do not, and hence could make the job of finding the source of the error more difficult.  Regardless of the language employed, it is the programmer that is at fault (for writing shoddy code), and not the language itself.

---

### Post by mdurham on 2009-01-04
> **Wybiral said:**
> But you can catch the exceptions, because it has exception handling, C does not. In C you can just ruthlessly write over memory that could be used by something else, in Java/Python a catchable exception is thrown and no memory is corrupted.

This is why C runs faster, error checking takes time.

---

### Post by ProgramErgoSum on 2009-01-05
So all this got me thinking and I wrote something which I can probably replicate elsewhere. Would you think this is un-necessarily complicated or some attempt at bounds checking when playing with pointers ?

Disclaimer : I am still learning. :-)

```

#include <stdio.h>
#include <stdlib.h>
/*
 * NewPointer.c
 *
 *  Created on: 4 Jan, 2009
 */

struct new_ptr {
	int *ptr;
	int limit_Address;
};

struct new_ptr *assign_int_ptr(struct new_ptr *np, int n) {
	np->ptr = malloc(sizeof(int) * n);
	np->limit_Address = (int) np->ptr + (sizeof(int) * n) ;
	return (np) ;
}

short bound_check_add (struct new_ptr *np, int n, char c) {
	short test_rc = 0 ;
	int *target_address_P = NULL ;
	int target_address_I = 0 ;
	switch (c) {
	case 'P' :
		/* Pointer addition. n*sizeof(int) added */
		target_address_P = np->ptr + n ;
		if (((int)target_address_P > np->limit_Address) || (target_address_P < np->ptr)) {
			test_rc = 1 ;
		}
		break ;

	case 'I' :
		/* Integer addition. n added */
		target_address_I = (int)np->ptr + n ;
		if (((int)target_address_I > np->limit_Address) || (target_address_I < (int)np->ptr)) {
			test_rc = 1 ;
		}
		break ;

	case 'X' :
		/* Hexa-decimal addition. n added but n was provided in hex notation so similar to case 'I' above. */
		if (((int)target_address_I > np->limit_Address) || (target_address_I < (int)np->ptr)) {
			test_rc = 1 ;
		}
		break ;

	default :
		/* Invalid input */
		printf("Invalid input. \n");
		break ;
	}
	return test_rc ;
}

int main (void) {

	struct new_ptr *np = (struct new_ptr *) malloc(sizeof(struct new_ptr));
	np = assign_int_ptr(np, 10) ; /* Allocate memory for 10 integers */
	short test_rc = 0 ;

	test_rc = bound_check_add(np, 5, 'P') ;
	if (test_rc) {
		printf("Limit exceeded !! \n") ;
	} else {
		printf("Limit not exceeded \n");
	}

	test_rc = bound_check_add(np, 80, 'I') ;
	if (test_rc) {
		printf("Limit exceeded !! \n") ;
	} else {
		printf("Limit not exceeded \n");
	}

	test_rc = bound_check_add(np, 0x20, 'X') ;
	if (test_rc) {
		printf("Limit exceeded !! \n") ;
	} else {
		printf("Limit not exceeded \n");
	}


	return (0);
}


```

---

