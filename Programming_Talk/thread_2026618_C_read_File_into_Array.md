---
title: "C: read File into Array"
date: 2012-07-15
forum: Programming Talk
---

### Post by hailholyghost on 2012-07-15
Hello,

I am attempting to read a file into an array on C:

```
#include <stdio.h>
#include <stdlib.h>

/*How to read a file into an array*/
int main() {
 double array[29999];
 double time;
 FILE *fp;
 unsigned int i = 0;
 fp = fopen("alpha2.99","r");
 if (fp != NULL) {
    while (!feof(fp)) {
       fscanf(fp,"%lf %lf",&time,&array[i]);
       printf("%lf\n",array[i]);
       i++;
    }
 }
 fclose(fp);
 return 0;
}
```

The file looks like:
```
0.0 45.344
0.1 47.464
...
2999.9 224.879
3000.0 245.080

```

I am just printing the 2nd column right now (nice and easy at first, of course).  However, it always prints an extra 0 when I do this in real life:

```
244.555000
245.338000
224.879000
245.080000
0.000000
```

The immediately obvious answer seemed to be to reduce the size of the array.  Reducing the size of the array, however, leads to:

```
244.555000
245.338000
224.879000
Segmentation fault (core dumped)
```

Is there a way I can remove that trailing zero?:confused:

Thanks for your expertise!

---

### Post by Bachstelze on 2012-07-15
Use of feof() can be a bit tricky at first. Here's what happens in your case: the first lines are read normally. When the last line is read, the end-of-file indicator is NOT set. This is because your program only reads until the last newline character. It does not "look" after it, so it does not know that there is nothing and that the line is in fact the last line of the file. Thus after it has read the last line, it enters the loop one more time, and this is where it sees that there is nothing more to read, and sets the end-of-file indicator.

One possible solution would be to check with the return falue of fscanf(). Something like

```

    while (!feof(fp)) {
       if (fscanf(fp,"%lf %lf",&time,&array[i]) != 2) {
         continue;
       }
       printf("%lf\n",array[i]);
       i++;
    }
```

This also allows to silently ignore invalid lines.

---

### Post by hailholyghost on 2012-07-15
> **Bachstelze said:**
> Use of feof() can be a bit tricky at first. Here's what happens in your case: the first lines are read normally. When the last line is read, the end-of-file indicator is NOT set. This is because your program only reads until the last newline character. It does not "look" after it, so it does not know that there is nothing and that the line is in fact the last line of the file. Thus after it has read the last line, it enters the loop one more time, and this is where it sees that there is nothing more to read, and sets the end-of-file indicator.

One possible solution would be to check with the return falue of fscanf(). Something like

```

    while (!feof(fp)) {
       if (fscanf(fp,"%lf %lf",&time,&array[i]) != 2) {
         continue;
       }
       printf("%lf\n",array[i]);
       i++;
    }
```

This also allows to silently ignore invalid lines.

Hi Bachstelze,

thanks for your reply!  It works!

So fscanf only works if it does not return a value of two?  I tried writing a program to return the value of fscanf, but it didn't work:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
 FILE *fp;
 fp = fopen("alpha2.99","r");
 int i, time, tor;
 while (!feof(fp)) {
    i = fscanf("%lf %lf",&time, &tor);
 }
 fclose(fp);
 printf("%d\n",i);
 return 0;
}
```

---

### Post by Bachstelze on 2012-07-15
> **hailholyghost said:**
> 
So fscanf only works if it does not return a value of two?

No. Check the manual page to see how the return value of fscanf() is determined.

```
man fscanf
```

Scroll down to the "Return value" section. If you don't have the man page, install [font=monospace]manpages-dev[/font].

---

### Post by hailholyghost on 2012-07-15
Thanks so much!  I wish I were able to help you out Bachstelze, lol.  If only I could.

The return value is the number of arguments according to the man page.

Merci!

---

### Post by Bachstelze on 2012-07-15
> **hailholyghost said:**
> 
The return value is the number of arguments according to the man page.


No, it is not.

> RETURN VALUE
       These  functions return the number of input items successfully matched and assigned, **which can be fewer than provided for**, or even zero in the event of an early matching failure.


If it were, then it would always return the same value in your code, so checking for it would be useless.

---

