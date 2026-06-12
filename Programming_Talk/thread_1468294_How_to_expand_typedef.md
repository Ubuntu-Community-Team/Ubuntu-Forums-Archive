---
title: "How to expand typedef?"
date: 2010-05-01
forum: Programming Talk
---

### Post by huangyingw on 2010-05-01
Hello, I have following codes.
```

typedef char* pStr;
int main(void)
{
	char string[4]="abc";
	const pStr p2 = string;
	p2++;
	return 0;
}

```
I would like it to be expanded to be following:
```

typedef char* pStr;
int main(void)
{
	char string[4]="abc";
	const char* p2 = string;
	p2++;
	return 0;
}

```
But I found that following compilation option could not help me.
```

g++ -c -E -P const.cpp

```
Could someone provide me with an appropriate option to realize my goal?

---

### Post by tookyourtime on 2010-05-01
Why not just do a search and replace for all pStr occurrences?

---

### Post by Compyx on 2010-05-01
What you're looking for is a preprocessor #define:
```

#define pStr char*

```

The preprocessor does expansion, a typedef just creates another name for a type.

---

### Post by nvteighen on 2010-05-01
Ok, I don't get what's wrong there. This works perfectly fine for me:
```

#include <stdio.h>

typedef char * string;

int main(void)
{
    const string a = "abc";
    printf("%s", a);

    return 0;
}

```

Of course it won't show up after the preprocessor stage, because typedef works on compiling. Actually, probably the difference between #define and typedef in such a case is just a matter of style.

---

### Post by huangyingw on 2010-05-01
> **Compyx said:**
> What you're looking for is a preprocessor #define:
```

#define pStr char*

```

The preprocessor does expansion, a typedef just creates another name for a type.
Yes, this works for me. While I am not quite understand the difference between define and typedef

---

### Post by huangyingw on 2010-05-01
> **tookyourtime said:**
> Why not just do a search and replace for all pStr occurrences?
Sorry, I take this as a raw method:).

---

### Post by huangyingw on 2010-05-01
> **nvteighen said:**
> Ok, I don't get what's wrong there. This works perfectly fine for me:
```

#include <stdio.h>

typedef char * string;

int main(void)
{
    const string a = "abc";
    printf("%s", a);

    return 0;
}

```
Of course it won't show up after the preprocessor stage, because typedef works on compiling. Actually, probably the difference between #define and typedef in such a case is just a matter of style.
Thanks. Of course your code would not generate any error. I just write my codes to demo the usage of "const" key word, and try to deepen my understanding of "const". 
However, thanks for pointing out the difference between typedef and define to me.

---

