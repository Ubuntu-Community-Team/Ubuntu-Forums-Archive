---
title: "Concatenate two cstring variables?"
date: 2010-10-31
forum: Programming Talk
---

### Post by fallenshadow on 2010-10-31
Does anyone know of a good straight to the point website for this? or can somebody provide an example.

I thought it was as simple as:

```
answer = examplestr1 + examplestr2;
```

I found that example on some website recently, however it doesnt work! I know to some this is really basic stuff but ive never learned about cstrings.

---

### Post by Arndt on 2010-10-31
> **fallenshadow said:**
> Does anyone know of a good straight to the point website for this? or can somebody provide an example.

I thought it was as simple as:

```
answer = examplestr1 + examplestr2;
```

I found that example on some website recently, however it doesnt work! I know to some this is really basic stuff but ive never learned about cstrings.

Can you show a complete program?

---

### Post by worksofcraft on 2010-10-31
try

char * [strncat]("http://www.cplusplus.com/reference/clibrary/cstring/strncat/") ( char * destination, char * source, size_t num );

---

### Post by ziekfiguur on 2010-10-31
I'd like to add, that you have to be very careful when using strcat (and strncat). 
Strcat just copies bytes from src to the end of dest, but does not check if there is room for a longer string, which might result in a buffer overflow and therefore bugs or crashes in your program. So, when using strcat make very sure that there is enough empty space left in the dest buffer.

---

### Post by dwhitney67 on 2010-10-31
> **ziekfiguur said:**
> ...when using strcat make very sure that there is enough empty space left in the dest buffer.
Never use strcat().  Use strncat().

And also for the record... never use:
[LIST]
[*]strcpy()
[*]sprintf()
[*]gets()
[/LIST]

Each of these functions, along with the aforementioned strcat(), present the possibility for buffer overruns.  Thus it is better to use their safe counterparts where one can specify the size of the destination buffer.  

P.S.  For gets(), use fgets().

---

### Post by nvteighen on 2010-11-01
Just in case you're using C++ (which I think you are... in my experience, only C++ programmers talk about "cstrings"... where C programmers talk about "strings" :P), avoid C strings in general and switch to std::string, which are designed to avoid all these issues.

Of course, that doesn't apply if you're using C. Anyway, in C you may use GLib's string data structure (GString), which is a bit like C++'s std::string... But this would mean to use a third party library and you may not want such an approach. (But it's always handy to know what possibilities there are... for future reference).

---

### Post by fallenshadow on 2010-11-02
I looked up that tutorial link that was posted but its not very useful.

I want to concatenate two variables, which are not pre-defined like this example: 

[http://www.cplusplus.com/reference/clibrary/cstring/strcat/](http://www.cplusplus.com/reference/clibrary/cstring/strcat/)

I want to do it like this:

-Ask question
-Enter variable Cstring1
-Ask question
-Enter variable Cstring2
*Concatenate variables*
-Output concatenated variable

I hope that makes sense to people. Now as for not using Cstrings, im afraid I have no choice. I personally don't want to learn them because I find them a pain to work with. However it is part of my college course, so I have to learn them. :(

---

### Post by dwhitney67 on 2010-11-02
What's wrong with...
```

#include <string.h>
#include <stdio.h>

int main(void)
{
  char  str1[10];
  char  str2[10];
  char  cat[21];
  char* newline = 0;

  /* get first string */
  printf("Enter string 1: ");
  fgets(str1, sizeof(str1), stdin);

  newline = strchr(str1, '\n');

  if (newline)
     *newline = '\0';

  /* repeat for second string using str2 */

  /* concatenate strings */
  snprintf(cat, sizeof(cat), "%s%s", str1, str2);

  printf("concatenated strings: %s\n", cat);

  return 0;
}

```
If you want something different from above, then please exercise your vocabulary so as to be more specific.  Sigh.

---

