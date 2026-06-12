---
title: "Begining linux programing 3rd edition"
date: 2012-09-05
forum: Programming Talk
---

### Post by checoimg on 2012-09-05
I'm making an exercise and I get an error.


zahory@frogui:~/C programming$ gcc -c bill.c fred.c
bill.c: In function ‘bill’:
bill.c:4:2: error: stray ‘\342’ in program
bill.c:4:2: error: stray ‘\200’ in program
bill.c:4:2: error: stray ‘\234’ in program
bill.c:4:16: error: expected ‘)’ before ‘:’ token
bill.c:4:16: error: stray ‘\’ in program
bill.c:4:16: error: stray ‘\342’ in program
bill.c:4:16: error: stray ‘\200’ in program
bill.c:4:16: error: stray ‘\235’ in program
bill.c:4:16: warning: passing argument 1 of ‘printf’ from incompatible pointer type [enabled by default]
/usr/include/stdio.h:363:12: note: expected ‘const char * __restrict__’ but argument is of type ‘void (*)(char *)’
bill.c:4:16: warning: format not a string literal and no format arguments [-Wformat-security]
fred.c: In function ‘fred’:
fred.c:4:2: error: stray ‘\342’ in program
fred.c:4:2: error: stray ‘\200’ in program
fred.c:4:2: error: stray ‘\234’ in program
fred.c:4:16: error: expected ‘)’ before ‘:’ token
fred.c:4:16: error: stray ‘\’ in program
fred.c:4:16: error: stray ‘\342’ in program
fred.c:4:16: error: stray ‘\200’ in program
fred.c:4:16: error: stray ‘\235’ in program
fred.c:4:16: warning: passing argument 1 of ‘printf’ from incompatible pointer type [enabled by default]
/usr/include/stdio.h:363:12: note: expected ‘const char * __restrict__’ but argument is of type ‘void (*)(int)’
fred.c:4:16: warning: format not a string literal and no format arguments [-Wformat-security]

---

### Post by durdenstationer on 2012-09-05
Post the code.

---

### Post by checoimg on 2012-09-05
> **durdenstationer said:**
> Post the code.

this id fred.c :

```

#include <stdio.h>
void fred(int arg)
{
printf(“fred: you passed %d\n”, arg);
}

```

and this is bill.c :


```
#include <stdio.h>
void bill(char *arg)
{
printf(“bill: you passed %s\n”, arg);
}
```

---

### Post by durdenstationer on 2012-09-05
Compiles fine as copied from your post. I googled your errors, though, and it has to do with your quotation marks in your original source file. Replace them with neutral quotations instead of left and right quotations.

---

### Post by durdenstationer on 2012-09-05
To explain further, you're feeding non-ASCII characters to the compiler with the smart quotes and it can't interpret them. Did you copy-and-paste the code?

---

### Post by checoimg on 2012-09-05
> **durdenstationer said:**
> Compiles fine as copied from your post. I googled your errors, though, and it has to do with your quotation marks in your original source file. Replace them with neutral quotations instead of left and right quotations.

Do you mean ?

	printf('bill: you passed %s\n', arg)

---

### Post by checoimg on 2012-09-05
> **durdenstationer said:**
> To explain further, you're feeding non-ASCII characters to the compiler with the smart quotes and it can't interpret them. Did you copy-and-paste the code?

Yes I copied the code

---

### Post by Odexios on 2012-09-05
What text editor are you using?

---

### Post by durdenstationer on 2012-09-05
> **checoimg said:**
> Do you mean ?

	printf('bill: you passed %s\n', arg)

No. Single quotes are for character literals. Use neutral double quotes since your copied code was using left and right handed double quotes.

---

### Post by papibe on 2012-09-05
Hi checoimg.

I think the copy/paste process screwed up your double quotes. Read [this]("http://www.giannistsakiris.com/index.php/2008/04/17/gcc-error-stray-%E2%80%98342%E2%80%99-in-program/").

Regards.

---

### Post by checoimg on 2012-09-05
Thank you everyone for your attention, the problem was that I copied the code I just compiled it and worked fine.

---

### Post by checoimg on 2012-09-05
> **Odexios said:**
> What text editor are you using?

gedit

---

### Post by lisati on 2012-09-05
> **papibe said:**
> Hi checoimg.

I think the copy/paste process screwed up your double quotes. Read [this]("http://www.giannistsakiris.com/index.php/2008/04/17/gcc-error-stray-%E2%80%98342%E2%80%99-in-program/").

Regards.

+1

I've also added [noparse]```
 and 
```[/noparse] [tags]("http://ubuntuforums.org/misc.php?do=bbcode") to [post 3]("http://ubuntuforums.org/showpost.php?p=12219916&postcount=3") of this thread, which can help us see what's going on.

---

### Post by durdenstationer on 2012-09-05
Look into gedit snippets to autoconvert the quotes when pasting so it converts smart quotes to neutral quotes.

---

