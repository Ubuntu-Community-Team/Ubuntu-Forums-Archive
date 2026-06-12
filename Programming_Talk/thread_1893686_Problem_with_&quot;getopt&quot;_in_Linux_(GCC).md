---
title: "Problem with &quot;getopt&quot; in Linux (GCC)"
date: 2011-12-10
forum: Programming Talk
---

### Post by Krupski on 2011-12-10
Hi all,

I have this little snippet of test code:

```

#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <getopt.h>

int main (int argc, char **argv)
{
    int c, w, aflag, bflag, cflag;
    c = w = aflag = bflag = cflag = 0;

    **[COLOR="Red"]opterr = 0;[/COLOR]**

    while ((c = getopt (argc, argv, "abc")) != -1) {

        w++; /* debug count how many times we go through */

        switch (c) {

        case 'a':
            aflag = 1;
            break;
        case 'b':
            bflag = 1;
            break;
        case 'c':
            cflag = 1;
            break;
        case '?':
            fprintf(stdout, "Help shown here\n");
            return 1;
        default:
            fprintf(stdout, "Default: Should not see\n");
            return 1;
        }
    }

    fprintf(stdout, "While loop count = %d\n", w);

    for (c = 0; c < argc; c++) {
        fprintf(stdout, "argv[%d] = %s\n", c, argv[c]);
    }
    return 0;
}

```Note the line in red... setting "opterr" to zero is supposed to suppress the built in error messages from getopt, yet it does not.

Running the code with an invalid option SHOULD simply print the help line, yet I get this:

root@michael:~/c-progs# ./getopt -x
**[COLOR="Red"]./getopt: invalid option -- 'x'[/COLOR]**
Help shown here

The line in red isn't supposed to display.

I tried setting "opterr" to 1, -1 and leaving it out... no difference. What the heck? Anyone know?

Thanks.

-- Roger

---

### Post by GeneralZod on 2011-12-10
Hmmmm ... works fine here - the -x flag gives no error, and just the "Help shown here" message.  Has your ./getopt executable definitely been re-compiled since you added the "opterr = 0;" line?

---

### Post by MadCow108 on 2011-12-10
works fine here:
```
$ gcc test.c && ./a.out  -x
Help shown here
```

please provide more information on your system.

---

### Post by Krupski on 2011-12-10
> **MadCow108 said:**
> works fine here:
```
$ gcc test.c && ./a.out  -x
Help shown here
```

please provide more information on your system.

Well... interesting. I compiled it exactly like you did above and it works. If I compile it with my script, it fails.

And I found out why..... my script runs "strip" to clean out un necessary junk out of the code.

This was the offending option (for strip):

-R .gnu.hash

Argh..........!

Thanks all... you nudged me in the right direction!

-- Roger

---

