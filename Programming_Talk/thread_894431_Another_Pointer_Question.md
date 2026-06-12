---
title: "Another Pointer Question"
date: 2008-08-19
forum: Programming Talk
---

### Post by blooddrunk on 2008-08-19
Hi! I've got another pointer question. In C, if you have a pointer char *pointer that holds an integer value, how do you pass it to an integer. For example:
char *pointer=3456 (well, it's probably "3456")
int integer;
How do you make integer equal 3456???

---

### Post by hod139 on 2008-08-19
See [http://ubuntuforums.org/showthread.php?t=396479](http://ubuntuforums.org/showthread.php?t=396479).

---

### Post by jim_24601 on 2008-08-19
Your question is a little confused. Do you mean "if I have a pointer to a string containing a representation of an integer, how do I convert that string to a numeric value?"

In that case, you should investigate atoi() and strtol(). atoi() lives in <stdlib.h> and converts ASCII to integer:

```
#include <stdlib.h>

int main(void)
{
  char* pointer = "3456";
  int integer;

  integer = atoi(pointer); /* integer now holds 3456 */
}

```

strtol is more complex, and can handle different number bases as well as the '0x' notation, and also return the position in the string where the number ends.

---

### Post by blooddrunk on 2008-08-19
Big thanks, jim_24601! I've forgotten about atoi()

---

### Post by jinksys on 2008-08-19
> **blooddrunk said:**
> Big thanks, jim_24601! I've forgotten about atoi()

Be careful with atoi as it ignores errors and returns 0.  Unless you are 100% certain that the string you are to convert is a number, I would use another method.

See hod's post [here](http://ubuntuforums.org/showthread.php?t=396479) for an excellent alternative.

---

