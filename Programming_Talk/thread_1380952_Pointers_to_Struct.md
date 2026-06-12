---
title: "Pointers to Struct"
date: 2010-01-14
forum: Programming Talk
---

### Post by lewisforlife on 2010-01-14
Here is my code:

```
#include <stdio.h>

typedef struct
{
	int a;
} MYSTRUCTURE;

void indirect (MYSTRUCTURE *ns)
{
	MYSTRUCTURE ms = *ns;

	ms.a = 10;
}

int main (int argc, char *argv [])
{
	MYSTRUCTURE ms;

	ms.a = 5;
	printf ("%d\n", ms.a);

	indirect (&ms);

	printf ("%d\n", ms.a);

	return 0;
}
```

I would expect this to output:

5
10

But it instead outputs 

5
5

How can I make this work how I want it.  My intent was to pass the structure defined in main () to indirect () and be able to change the values of the variables indirectly.

---

### Post by Zugzwang on 2010-01-14
```
#include <stdio.h>

typedef struct
{
	int a;
} MYSTRUCTURE;

void indirect (MYSTRUCTURE *ns)
{
	ns->a = 10;
}

int main (int argc, char *argv [])
{
	MYSTRUCTURE ms;

	ms.a = 5;
	printf ("%d\n", ms.a);

	indirect (&ms);

	printf ("%d\n", ms.a);

	return 0;
}
```

The line "MYSTRUCTURE ms = *ns;" creates a copy of "*ns" and thus "ms.a = ..." only changes the value in this copy.

---

### Post by lewisforlife on 2010-01-14
> The line "MYSTRUCTURE ms = *ns;" creates a copy of "*ns" and thus "ms.a = ..." only changes the value in this copy.

I see what you are saying.  I have tried:

```
*ns->a = 10;
```

and I get the following when compiling:

```

main.c: In function 'indirect':
main.c:10 error: invlaid type argument of 'unary *' (have 'int')

```

How can I make this work?  I want to access all of the variables in "ms" which is defined in main ().  I want to change the variables by pointers in other functions.  I don't want "ms" to be defined globally outside of a function.  Any help is much appreciated :D

---

### Post by dwhitney67 on 2010-01-14
Try
```

ns->a = 10;

/* OR */

(*ns).a = 10;

```

---

### Post by lewisforlife on 2010-01-14
> **dwhitney67 said:**
> Try
```

ns->a = 10;

/* OR */

(*ns).a = 10;

```

LOL, things seem so simple in hindsight.  I thought I tried everything.  I guess I tried everything but your solution.  This worked great.  Thanks!  :D

---

### Post by dwhitney67 on 2010-01-14
> **lewisforlife said:**
> LOL, things seem so simple in hindsight.  I thought I tried everything.  I guess I tried everything but your solution.  This worked great.  Thanks!  :D

You should have paid more attention to Zugzwang's post, which came before mine.

Anyhow, you are welcome.

---

### Post by lewisforlife on 2010-01-14
> **Zugzwang said:**
> ```
#include <stdio.h>

typedef struct
{
	int a;
} MYSTRUCTURE;

void indirect (MYSTRUCTURE *ns)
{
	ns->a = 10;
}

int main (int argc, char *argv [])
{
	MYSTRUCTURE ms;

	ms.a = 5;
	printf ("%d\n", ms.a);

	indirect (&ms);

	printf ("%d\n", ms.a);

	return 0;
}
```

The line "MYSTRUCTURE ms = *ns;" creates a copy of "*ns" and thus "ms.a = ..." only changes the value in this copy.

Thanks zugswang, I missed your solution somehow.  I really appreciate the help.  Thread Solved!

---

