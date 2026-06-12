---
title: "C (not C++) : pointer inside struct"
date: 2011-03-14
forum: Programming Talk
---

### Post by myhieu on 2011-03-14
It's my simple 64bit integer written in C. Inside the struct, is it possible to replace "struct BigInt *" by "BigInt_T" inside the struct?

```

typedef struct BigInt {
	int value;

	struct BigInt* (*add) (struct BigInt * a, struct BigInt * b);
} BigInt;

typedef struct BigInt * BigInt_T;

BigInt_T new_BigInt();

BigInt_T add (BigInt_T a, BigInt_T b) {
	BigInt_T c = new_BigInt();
	c->value = a->value + b->value;
	return c;
}

BigInt_T new_BigInt() {
	BigInt_T t = malloc(sizeof *t);

	if ( t == NULL ) {
		printf("BigInt::New BigInt: Unable to allocate memory.");
		exit( EXIT_FAILURE );
	}

	t->add = add;

	return t;
}


int main(void) {
	BigInt_T t1 = new_BigInt();
	BigInt_T t2 = new_BigInt();

	t1->value = 10;
	t2->value = 5;

	t1 = t1->add(t1,t2);

	printf("%d", t1->value);


	getchar(); getchar();
	return 0;
}


```

---

### Post by rnerwein on 2011-03-14
high
i want to help you but for your example ( i called it ub.c ) my gives me:
cc     ub.c   -o ub
ub.c: In function &#8216;add&#8217;:
ub.c:7: error: dereferencing pointer to incomplete type
ub.c:7: error: dereferencing pointer to incomplete type
ub.c:7: error: dereferencing pointer to incomplete type
ub.c: In function &#8216;new_BigInt&#8217;:
ub.c:12: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
ub.c:12: error: dereferencing pointer to incomplete type
ub.c:14: error: &#8216;NULL&#8217; undeclared (first use in this function)
ub.c:14: error: (Each undeclared identifier is reported only once
ub.c:14: error: for each function it appears in.)
ub.c:15: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
ub.c:16: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ub.c:16: error: &#8216;EXIT_FAILURE&#8217; undeclared (first use in this function)
ub.c:19: error: dereferencing pointer to incomplete type
ub.c: In function &#8216;main&#8217;:
ub.c:29: error: dereferencing pointer to incomplete type
ub.c:30: error: dereferencing pointer to incomplete type
ub.c:32: error: dereferencing pointer to incomplete type
ub.c:34: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
ub.c:34: error: dereferencing pointer to incomplete type
make: *** [ub] Fehler 1
no way for me to help you
ciao

---

### Post by 3Miro on 2011-03-14
I hope this is not your homework problem, although if it is and you come to forums for help, you will fail the class anyway.

First some observations:

1. The code didn't compile for me. I had to use:
```
BigInt_T t = (BigInt*) malloc(sizeof *t);
```
The original code could compile on an older version of gcc, but you should probably use something newer.

2. You have a memory leak. The code calling malloc three times, however, you have only two pointers.
```
t1 = t1->add(t1,t2);
```
drops one reference, it should be something like:
```
BigInt_T t3 = new_BigInt();
t3 = t1->add(t1,t2);
```

3. I am not sure what you are actually trying to achieve. If you want a 64-bit Integer, you should use a long int on a 64-bit Ubuntu. Otherwise, this code only creates a "wrapper" around regular 32-bit int and ties it to a function add. This looks like someone was trying to write Object Oriented code on a non-Object Oriented platform. However, it may be a good toy example.

As an answer to the original question, you cannot access a datatype before it has been declared. Pointers make an exception, since they are all technically the same "type" (i.e. 32-bit or 64-bit number associated with an address in memory). Here is how you can do this:

```
typedef struct BigInt * BigInt_T;

typedef struct BigInt {
	int value;

	BigInt_T (*add) (struct BigInt * a, struct BigInt * b);
} BigInt;

```

Again, this can only be a toy example as definition of BigInt_T doesn't really make sense here, you should just use BigInt* and not clutter your code with too many names/variables.

---

### Post by nvteighen on 2011-03-14
Just invert the order of the typedef's :)

```

typedef struct BigInt * BigInt_T;

typedef struct BigInt {
	int value;

	BigInt_T (*add) (BigInt_T a, BigInt_T b);
} BigInt;

/* etc. */

```

This works because typedef's don't need the type to be defined in the module. When you do a typedef, all you're saying is that some type is expected to exist and that it will aliased to a certain name. It works almost like a preprocessor macro, except for that typedef's enable type-safety checks for the alias you created.

Now, on the "good practices" side of things. I personally don't like "hidden pointer types", i.e. typedefs that hide the fact that something is actually a pointer. It makes the interface a bit obscure, specially when you're interested on knowing whether something is being stored in the stack or in the heap. If I were given your interface without any further documentation, I wouldn't know whether the value returned by new_BigInt() is going to need manual deallocation or not. If you clearly showed what's a pointer and what isn't, I wouldn't have that issue: if a pointer is returned it's allocated in the heap (I'd be assuming you're not returning a dangling pointer)... and if it isn't a pointer, it's allocated in the stack.

BTW, I could compile your code setting gcc to a very strict setup (-Wall -Wextra -pedantic -std=c99)... after #include'ing stdio.h and stdlib.h, of course (which you forgot to copy into the snippet). I don't get why people are having issues when compiling this.

EDIT: I haven't looked into the memory leaks. But yeah, there are some issues with that too. The easiest solution would be to make your add "method" to be just a normal procedure... Don't try to imitate C++ when doing OOP C... Having add as a procedure will also be OOP, even if it doesn't use the dot/arrow notation to show it as "part" of your struct.

---

### Post by myhieu on 2011-03-14
Thanks nvteighen and 3Miro for your detailed helps, I'll consider your advices about not using hidden pointer types, memory leaks, etc.

It's actually my assignment, but it requires me to build a simple 64bit integer library, not getting into C language, so your help is still acceptable, I think.

---

