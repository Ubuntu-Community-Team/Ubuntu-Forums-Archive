---
title: "using UTF-8 and C"
date: 2009-10-22
forum: Programming Talk
---

### Post by thantos on 2009-10-22
I am having problems getting this bit of code to compile:

```
#include <stdio.h>
#include <locale.h>

int main()
{
 if (!setlocale(LC_CTYPE, "")) {
        fprintf(stderr, "Can't set the specified locale! " \
                "Check LANG, LC_CTYPE, LC_ALL. \n");
        return 1;
 }

 printf("%ls\n", L"Schöne Grüße");
 return 0;
}
```

The code was pretty much copied and pasted from here:
[http://www.java-samples.com/showtutorial.php?tutorialid=806](http://www.java-samples.com/showtutorial.php?tutorialid=806)

gcc command:
```
gcc -std=gnu99 -Wall -Wextra -pedantic -g checkencoding.c -o checkencoding
```

compiler output:
```
learnc/checkencoding.c:12:18: error: converting to execution character set: Invalid or incomplete multibyte or wide character
```

character encoding: en_US.utf8

gcc version 4.3.3

I am doing this as a first step in understanding how to use utf-8 with C.  I am still learning C and figure that
 learning how to use unicode now is better than getting used to ascii and having to do it later.  So any tips on 
general UTF-8 implementation would be appreciated as well.

EDIT:
The character encoding in vim was wrong.  As soon as did this:
```
:set fileencoding=utf-8
```

Such a duh moment....

---

### Post by dwhitney67 on 2009-10-22
It compiles for me; strange that you are having trouble.

I am using GCC version 4.3.3

---

### Post by thantos on 2009-10-22
Well, good to know nothing is wrong with the code.  Is there anymore information I can give the would help with troubleshooting?

---

### Post by thantos on 2009-10-23
Ok, further information:

When I originally copied "Schöne Grüße" and pasted it into the code, it showed up just like it does here
(using vim to edit the code).  My environment variables where as such:

```
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
```

and I get the same response with those variables as I do with them being en_US.utf8 (LANG, is set to this
 and it gets passed down).  The only difference is that with en_US.utf8 "Schöne Grüße" is not readable in vim.

Could this be part of the problem?  And why would vim display the characters but gcc not let me use them?

---

### Post by dwhitney67 on 2009-10-23
On my systems (Linux and Mac), my LANG is set as follows:
```

LANG=en_US.UTF-8

```
I do not have any environment variables with the "LC_" prefix set on my systems.

P.S.  I tested your code on the Mac; it compiles/works too.

---

### Post by Arndt on 2009-10-23
> **thantos said:**
> Ok, further information:

When I originally copied "Schöne Grüße" and pasted it into the code, it showed up just like it does here
(using vim to edit the code).  My environment variables where as such:

```
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
```

and I get the same response with those variables as I do with them being en_US.utf8 (LANG, is set to this
 and it gets passed down).  The only difference is that with en_US.utf8 "Schöne Grüße" is not readable in vim.

Could this be part of the problem?  And why would vim display the characters but gcc not let me use them?

For what it's worth: when I set the environment variables the way you show, I can compile the program fine, but when it runs, it returns 0 and prints nothing. Without any of these variables set, the program compiles, and prints Schöne Grüße when run.

---

### Post by thantos on 2009-10-23
So, I tried changing LANG=en_US.UTF-8 and I get the same error.
I tried changing all the locale variables to nothing and I get 
the same error message.

I know the problem isn't solved yet but thanks for the help so far.

---

