---
title: "GCC Hates NULL"
date: 2007-10-14
forum: Programming Talk
---

### Post by ankursethi on 2007-10-14
I've been trying to create a simple linked list implementation. This is one of the functions I wrote. The compiler seems to bitch when I give NULL as the default values to the three arguments.

```
struct Node* newnode (struct Node* next = NULL, struct Node* prev = NULL, void* data = NULL) {
	struct Node* nn = NULL ;
	nn = malloc (sizeof(nn)) ;
	
	if (nn != NULL) {
		nn->prev = prev ; 
		nn->next = next ;
		nn->data = data ;
	}
	
	return nn ;
}

```

This is the error I get :
```
linkedlib.c:22: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;=&#8217; token
```

What's the problem? I'm compiling with *gcc -Wall -c FILENAME.c* since this file does not contain a main(). I'll link the object file with my executable once this implementation works.

---

### Post by duff on 2007-10-14
C doesn't support default function arguments.

---

### Post by ankursethi on 2007-10-14
Dang. Silly me. So I need to make them all NULL in the beginning of the function? Dang.

---

### Post by Lux Perpetua on 2007-10-14
> **ankursethi said:**
> Dang. Silly me. So I need to make them all NULL in the beginning of the function? Dang.No, that wouldn't work either. The caller is going to have to specify all the arguments.

---

### Post by smartbei on 2007-10-14
You do realize that in the really odd case that GCC actually hated NULL, it only would have been one define away?

```

#define NULL 0

```

---

### Post by tageiru on 2007-10-14
> **smartbei said:**
> You do realize that in the really odd case that GCC actually hated NULL, it only would have been one define away?

```

#define NULL 0

```

#define NULL (void *) 0

---

### Post by aks44 on 2007-10-15
> **tageiru said:**
> #define NULL (void *) 0

#define NULL ( (void*) 0 )

:p

---

### Post by tageiru on 2007-10-15
> **aks44 said:**
> #define NULL ( (void*) 0 )

:p
touché

---

