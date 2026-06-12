---
title: "Printf / Sprintf - %d vs. %i - integer print formatting"
date: 2007-12-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-12-13
I go to this page:

[http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html](http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html)

and I see that "d or i	Signed decimal integer".  For example:

int one = 1;
printf("%d", one);
printf("%i", one);

Do these print the same thing?
Is there any difference at all between using %d and %i?

---

### Post by samjh on 2007-12-13
There are no differences.  %d and %i are both conversion specifiers for signed decimal integers.

Quoted from the C99 standard document, section 7.19.6.1:
> 8. The conversion specifiers and their meanings are:
d,i    The int argument is converted to signed decimal in the style [&#8722;]dddd. The precision specifies the minimum number of digits to appear; if the value being converted can be represented in fewer digits, it is expanded with leading zeros. The default precision is 1. The result of converting a zero value with a precision of zero is no characters.

---

### Post by wolfbone on 2007-12-13
> **SNYP40A1 said:**
> I go to this page:

Does no-one read local documentation anymore? ;-)

---

### Post by sh!ft on 2007-12-13
> **wolfbone said:**
> Does no-one read local documentation anymore? ;-)

:lolflag:

What's that?

---

### Post by zehdeh on 2013-02-05
yes they do 
[https://code-reference.com/c/stdio.h/printf#arguments](https://code-reference.com/c/stdio.h/printf#arguments)

---

### Post by wildmanne39 on 2013-02-05
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

