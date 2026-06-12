---
title: "C Code to scan file of doubles?"
date: 2009-03-10
forum: Programming Talk
---

### Post by jsmidt on 2009-03-10
I know how to do this in C++, but am trying to learn how to do this in C.

I have a file called "acbar2007_v3_corr_1" which has contents that look like this: 

```

560   2.186
561   2.886
562   3.667
563   4.218
564   4.917

```

I want to write a code that scans in the whole files as doubles and immediately prints out the contents.  Currently I have this:

```

FILE *file;
double l, data;

file = fopen("acbar2007_v3_corr_1", "r");

while(!feof(file)) {
    fscanf(file, "%F %F", &l, &data);
    printf("%F %F\n", l, data);
}

fclose(file);

```

For some reason this isn't working.  Could anybody help point me in the right direction to get this to work?  Thanks.

---

### Post by Krupski on 2009-03-10
> **jsmidt said:**
> I know how to do this in C++, but am trying to learn how to do this in C.

I have a file called "acbar2007_v3_corr_1" which has contents that look like this: 

```

560   2.186
561   2.886
562   3.667
563   4.218
564   4.917

```

For some reason this isn't working.  Could anybody help point me in the right direction to get this to work?  Thanks.

Try this:

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>


int main(void)
{
    FILE *file;
    double l, data;
    char buf[BUFSIZ];
    char *p1;

    file = fopen("acbar2007_v3_corr_1", "r");

    while(! feof(file)) {
        // null buffer, read a line
        buf[0] = 0; fgets(buf, BUFSIZ, file);
        // if it's a blank line, ignore
        if(strlen(buf) > 1) {
            // p1 is pointer to first element in line
            p1 = strtok(buf, " ");
            // get double value of first element & print
            l = atof(p1);
            fprintf(stdout, "%f ", l);

            // p1 is pointer to second element in line
            p1 = strtok(NULL, " ");
            // get double value of second element & print
            data = atof(p1);
            fprintf(stdout, "%f\n", data);
        }
    }
    fclose(file); // done
    return 0;
}

```

I'm not a "good" C programmer, so I probably did it the hard way. Others please comment.

-- Roger

---

### Post by dwhitney67 on 2009-03-10
> **Krupski said:**
> ...

I'm not a "good" C programmer, so I probably did it the hard way. Others please comment.

-- Roger

I hate to say it, but you are right... you did it the hard way!

@ OP -

In your fscanf() and printf() statements, replace the %F with a %lf.  Here's the first reference doc I got when I googled for "fscanf format specifiers":  [http://beej.us/guide/bgc/output/html/multipage/scanf.html](http://beej.us/guide/bgc/output/html/multipage/scanf.html)

---

### Post by jsmidt on 2009-03-11
Thanks.

---

### Post by Krupski on 2009-03-11
> **dwhitney67 said:**
> i hate to say it, but you are right... You did it the hard way!

:)

---

### Post by stroyan on 2009-03-11
Your original code is very close to working.  You just need to use "%lf" instead of "%F" for the fscanf and printf formats.
(And you need "#include <stdio.h>", which you probably have and just didn't show.)

---

### Post by Can+~ on 2009-03-11
> **Krupski said:**
> I'm not a "good" C programmer, so I probably did it the hard way. Others please comment.

-- Roger

That's not the hard way, that's overkill.

---

