---
title: "Help me to look at this snippet"
date: 2009-01-12
forum: Programming Talk
---

### Post by huangyingw on 2009-01-12
Hello, 
	I am debugging this following snippet, it return me no result in GCC. It seems that the right value could not be passed to the left operand: s[dest - s - 1].
	While it works if I change s[dest - s - 1] = c; expression to *dest++=*src++; &#61516;
=================================================================
#include <stdlib.h>
#include <stdio.h>

char *
myStrcpy (
     char *dest,
     const char *src
     )
{
  int c;
  char * s = (char*)src;

  do
  {
    c = *s++;
    s[dest - s - 1] = c;
  }
  while (c != '\0');

  return dest;
}

int main()
{
	char* source="123456";
	char* target=(char *)malloc(100 * sizeof(char)); 
	myStrcpy(target,source);
	printf("%s \n",target); 	
 	return 0;
}

---

### Post by Zugzwang on 2009-01-12
So you already traced one execution of the program with a debugger?

---

### Post by huangyingw on 2009-01-12
> **Zugzwang said:**
> So you already traced one execution of the program with a debugger?

thank you for attention. Yes, I have debuged it. And it seems that the s[dest - s - 1] is not writable...

---

### Post by Zugzwang on 2009-01-12
> **huangyingw said:**
> thank you for attention. Yes, I have debuged it. And it seems that the s[dest - s - 1] is not writable...

Great, now think about why that could be the case. Hint: Ask yourself what  using an address in an expression fpr array index calculation would cause.

---

### Post by huangyingw on 2009-01-18
> **Zugzwang said:**
> Great, now think about why that could be the case. Hint: Ask yourself what  using an address in an expression fpr array index calculation would cause.
Yes, thank you. I have found the root.
it should be:
s[dest - src - 1] = c; //instead of s[dest - s - 1] = c;

---

