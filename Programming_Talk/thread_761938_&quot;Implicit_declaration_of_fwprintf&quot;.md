---
title: "&quot;Implicit declaration of fwprintf&quot;"
date: 2008-04-21
forum: Programming Talk
---

### Post by Ginswich on 2008-04-21
Hello, 
I need to use the wchar_t data type, and I've done a simple test program to see how it works. I paste it here:

```

#include <stdio.h>
#include <stdlib.h>
#include <wchar.h>
#include <wctype.h>
#include <stdarg.h>
#include <stddef.h>

int main(int argc, char *argv[]) {

	wchar_t *wstring1, *wstring2;
	int rc;


	wstring1 = (wchar_t *) malloc(sizeof(wchar_t) * 20);
	wstring2 = (wchar_t *) malloc(sizeof(wchar_t) * 20);

	wmemcpy(wstring1, L"Türkiye, resmî", 15*sizeof(wchar_t));
	wmemcpy(wstring2, L"Elniñomelóóóón", 15*sizeof(wchar_t));

	fwide(stdout, 1);
	fwprintf(stdout, L"%ls y %ls", wstring1, wstring2);

        free(wstring1); free(wstring2);

	return 0;
}
```

But when I compile it, gcc says "Warning: implicit declaration of 
function fwprintf" and the same for fwide...

I've compiled it with -g -Wall -pedantic -ansi -Wchar-subscripts flags, and with different subsets of them, but doesn't work...

Any idea? 

Thanks.

---

### Post by WW on 2008-04-21
I don't know why it prints that warning. If I compile it with no options (in particular, without -Wall), I don't get the error message, but I know that is not very helpful--it is a good idea to use -Wall.

So I am not posting to answer your question, but to point out a different problem in your code. The third argument to wmemcpy() is the number of wide characters, so you should not multiply 15 by sizeof(wchar_t).

---

### Post by Ginswich on 2008-04-22
Thanks, that was the routine of using memcpy instead of wmemcpy. I still don't know why gcc shows that warning 'cause fwide, wcslen, wcswidth, wprintf... seems to work correctly. 

One more doubt... if I do wprintf(L"hello world!"); i get "hello world!" at the console (of course), but if I try to print something more _rare_, such as "î", "ü" or something like this, what I obtain at the console is "?"...

I'm now using this "extremely complicated" program to test what I've said...

```

#include <stdio.h>
#include <wchar.h>

int main(int argc, char *argv[]) {

	wchar_t wc;

	if(fwide(stdout, 0) == 0) {
		if(fwide(stdout, 1) <= 0) {
			fprintf(stdout, "could not switch to wide char mode!\n");
		}
		else {
			wprintf(L"switched to wide char mode!\n");
		}
	}


	wc = L'ü';
	wprintf(L"%lc\n", wc);

	return 0;
}
```

At first I thought it was 'cause of the "implicit declaration" warning, but, as I said, fwide works fine... may be I'm skipping some format options in wprintf?

Ty...

---

### Post by lnostdal on 2008-04-22
wprintf is C99

```

lars@ibmr52:~/programming/c$ cat hello.c
#include <stdio.h>
#include <wchar.h>

int main() {
  wprintf(L"Hello World\n");
  return(0);
}
lars@ibmr52:~/programming/c$ gcc -Wall -std=c99  -o hello hello.c
lars@ibmr52:~/programming/c$ ./hello
Hello World

```

---

### Post by Ginswich on 2008-04-22
Thanks! That worked to remove the warning messages, but, when wprinting characters like "í", "û" ... it still prints "?"

---

### Post by Ginswich on 2008-04-22
I found it! 

```


#include <stdio.h>
#include <wchar.h>
#include <errno.h>
#include <locale.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {

	wchar_t wc;
	char *locale;
	
	if (!(locale = setlocale(LC_ALL,""))) {
		printf("locale not supported by glibc\n");
		exit(1);
	}

	if(fwide(stdout, 0) == 0) {
		if(fwide(stdout, 1) <= 0) {
			fprintf(stdout, "could not switch to wide char mode!\n");
		}
		else {
			wprintf(L"switched to wide char mode!\n");
		}
	}

	wc = L'&#23478;';
	wprintf(L"%lc", wc);
	
	return 0;
}

```

---

### Post by Vorona on 2009-03-05
I know that this is a pretty old thread, but I would like to thank the people here anyway. I had been searching for a long time for how to make C code to print UTF-8 characters, it's now working on my machine, though maybe not very portable (what about binary length of wchar_t on Linux and Windows ?).

By the way, let me post another piece of code that will print geometric shapes from the UTF-8 chart. I have noticed that only the side-effects of the functions which are used in the code are necessary, though the messages were useful for testing purpose.

The arguments of function "main" were not useful either.

When compiling, I still get warning messages about implicit declarations of functions, but it does'nt seem to prevent it from working.

```
#include <stdio.h>
#include <wchar.h>
#include <errno.h>   /*is it useful ?*/
#include <locale.h>
#include <stdlib.h>

int main(void) {

	wchar_t wc;
	char *locale;
	
	locale = setlocale(LC_ALL,"") ;

	fwide(stdout, 1) ;

	for (wc = L'\x25A0';wc<L'\x2600';wc++) {

	wprintf(L"%lc ", wc);
	}
	wprintf("\n");
	
	return 0;
}
```

regards !

---

