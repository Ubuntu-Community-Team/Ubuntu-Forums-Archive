---
title: "std::string not defined?"
date: 2009-09-05
forum: Programming Talk
---

### Post by tom66 on 2009-09-05
Following code throws errors:

```

#include <stdarg.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int __PyPrintFormat(FILE *stream, std::string fmt, ...)
{
	va_list ap;
	va_start(ap, fmt);
	char *buffer;
	
	if(vasprintf(&buffer, fmt, ap) != -1)
	{
		fputs(buffer, stream);
		free(buffer);
		return 0;
	}
	
	return 1;
}

int main()
{
	__PyPrintFormat(stdout, "int output: %d\n", 5928);
	return 0;
}

```

(yes I know I'm mixing C & C++, but it usually comes out for the better.)

I get errors compiling this:

```

simpletest.cpp:14: error: ‘std::string’ has not been declared
simpletest.cpp: In function ‘int __PyPrintFormat(FILE*, int, ...)’:
simpletest.cpp:20: error: invalid conversion from ‘int’ to ‘const char*’
simpletest.cpp:20: error:   initializing argument 2 of ‘int vasprintf(char**, const char*, char*)’
simpletest.cpp: In function ‘int main()’:
simpletest.cpp:177: error: invalid conversion from ‘const char*’ to ‘int’
simpletest.cpp:177: error:   initializing argument 2 of ‘int __PyPrintFormat(FILE*, int, ...)’

```

I have declared std::string by #including string.h... right?

I'm compiling with [font=monospace]g++ simpletest.cpp[/font].

All help appreciated!

---

### Post by MadCow108 on 2009-09-05
no its defined in <string>
c++ standard headers have no extension
and the c headers have a added c in front:
```

#include <cstdarg>
#include <cstdlib>
#include <cstring>
#include <cstdio>
#include <string>

```
if you have this from a book/tutorial, use a different one because yours is outdated

---

### Post by socool274 on 2009-09-05
With strings, strings are not compatible as a parameter of char *. Instead of passing the string, use myString.data(). The data() function returns a char *. This is the first of what I can see. Also, it should be included as <string>. What he ^ said.

---

### Post by MadCow108 on 2009-09-05
data() does not return a null terminated string
mostly c_str() is the better choice

---

### Post by tom66 on 2009-09-05
Thanks, solved problem :).

---

