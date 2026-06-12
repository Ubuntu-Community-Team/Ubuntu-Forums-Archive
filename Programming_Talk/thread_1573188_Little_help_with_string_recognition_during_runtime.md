---
title: "Little help with string recognition during runtime of compiled gnu C"
date: 2010-09-12
forum: Programming Talk
---

### Post by uraraika on 2010-09-12
Hi. I'm a bit new here at the forums and recently jumped into Ubuntu to also test out GNU C. I'm just wondering what will be the syntax in the code or what will be used to recognize some string or link, etc.

For example, I compiled "file.c" to "file". I want "file.c" to recognize the string after it type "./file". Like if I run the file at the terminal I type 

```
./file I want this to be recognized in the program
```

The part where "I want this to be recognized in the program" can really be put to the program as a string.

I've searched for hours and hours using google but can't find hot to write the code for it. I might be wrong though as I probably just do not know what will be the keywords in the search. Also searched the forums here. So I thought it's best to ask instead of wasting more time.

Hope you guys can help me. Thank you :)

---

### Post by spjackson on 2010-09-12
Something like this?
```

#include <stdio.h>

int main(int argc, char * argv[])
{
   int index;

   for (index=1; index < argc; ++index) {
      printf("\"%s\"\n", argv[index]);
   }
   return 0;
}

```

---

### Post by Bachstelze on 2010-09-12
Any reason why you can't just put it between quotes?

---

