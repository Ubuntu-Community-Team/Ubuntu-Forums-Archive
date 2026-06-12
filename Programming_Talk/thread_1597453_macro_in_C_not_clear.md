---
title: "macro in C not clear"
date: 2010-10-15
forum: Programming Talk
---

### Post by jamesbon on 2010-10-15
I am making a program to understand how macros work here is the code
```

#include <stdio.h>
#include<stdlib.h>
#define LIST.H onus;

int main ()
{
         char *p,*s;
         printf(" LIST.H ");
}

```
I expect LIST.H to print onus as out put.
But this does not happen.
upon compiling I get a warning
```

temp.c:3:13: warning: missing whitespace after the macro name

```
and the output is LIST.H not onus.
How can I get desired thing printed by the above macro.

---

### Post by Zugzwang on 2010-10-15
You've got several problems in your code:

1. Don't use a character like "." in your macro name - this one is reserved for floating point stuff.
2. Macros are not expanded within string constants by the preprocessor. (I might be wrong here)
3. Ending a macro definition with ";" is normally not a good idea - in your case it would have been placed in the middle of the printf command.
4. Use the string constant concatenation function of the C compiler to achieve what you want.

```

#include <stdio.h>
#include <stdlib.h>
#define LISTH "onus"

int main ()
{
         char *p,*s;
         printf(" "LISTH" ");
}

```

---

### Post by KdotJ on 2010-10-15
Shouldn't the quotes in the printf statement be removed?

```
printf(LISTH);
```

As it's not a string literal? I may be entirely wrong...

---

### Post by spjackson on 2010-10-16
> **KdotJ said:**
> Shouldn't the quotes in the printf statement be removed?

```
printf(LISTH);
```As it's not a string literal? I may be entirely wrong...
The original code appeared to want to print the string "onus" with a space before and a space after it. Zugzwang's code does this; yours prints no spaces.

---

### Post by KdotJ on 2010-10-16
My apologies, didn't really assume the spaces were wanted, I thought it was a simple confusion with literals.

---

