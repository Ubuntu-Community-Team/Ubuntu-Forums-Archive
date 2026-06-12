---
title: "[C] Weird loop-problem"
date: 2009-03-14
forum: Programming Talk
---

### Post by heamaster on 2009-03-14
Hi! Maybe I am blind but why does

> 
int main()
{

	for( int i = 0; i < 4; i++)
	{
	}
}


give me 

"for-loop initial declaration used outside C99 mode"

---

### Post by dwhitney67 on 2009-03-14
Because you are compiling with the C89 standards, which by default is offered by GCC.  Specify -std=gnu99 with your GCC options and all should be fine.

---

### Post by heamaster on 2009-03-14
Ok thanks! ;)
BTW, didn't for loops exist in C89?

---

### Post by dwhitney67 on 2009-03-14
For-loops existed in C89; what wasn't allowed was the local declaration of the variable 'i'.  That's what the error was attempting to tell you... yes, I know, it's a lame error message.

P.S.  If you want to remain with C89 standards:
```

int i = 0;

for (; i < 4; i++)
{
}

```

---

### Post by hanniph on 2009-03-14
It did, but definitions of new variables inside for loop were not allowed I guess

---

### Post by monkeyking on 2009-03-14
The problem isn't the for loop itself,
but the fact that you declare the counter in the loop itself

[PHP]
int i;
for(i=0;i<len;i++)
[/PHP]

---

### Post by jimi_hendrix on 2009-03-14
> **dwhitney67 said:**
> For-loops existed in C89; what wasn't allowed was the local declaration of the variable 'i'.  That's what the error was attempting to tell you... yes, I know, it's a lame error message.

P.S.  If you want to remain with C89 standards:
```

int i = 0;

for (; i < 4; i++)
{
}

```

ya its a lame one...but why is the default the older C?

---

