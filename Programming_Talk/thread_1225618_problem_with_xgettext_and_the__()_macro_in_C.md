---
title: "problem with xgettext and the _() macro in C"
date: 2009-07-28
forum: Programming Talk
---

### Post by darkagonik on 2009-07-28
Hello everybody!

I have a problem with gettext (for translating programs).
I learn to use gettext with [this tutorial]("http://oriya.sarovar.org/docs/gettext_single.html").

If I take the program given in the tutorial and execute the command:
[FONT="System"]xgettext -d hello -s -o hello.pot hello.c[/FONT]
It works fine and *.pot is generated.

But if I take the following program, with the macrofunction _() suggested in the tutorial (and used in many software):
```

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>
#include <libintl.h>

#define _(STRING) gettext(STRING)

int
main (int argc, char *argv[])
{
    setlocale (LC_ALL, "");
    bindtextdomain ("hello", "/usr/share/locale");
    textdomain ("hello");
    printf (_("Hello, world!\n"));
    return EXIT_SUCCESS;
}

```

With the same xgettext command, the *.pot file is not generated.

Any idea?
Thanks in advance.

---

### Post by darkagonik on 2009-07-29
I have found a solution, but I don't know if it is the best way...

So I use gcc with the -E option, to stop after the preprocessing stage, so the _() macros are transformed to gettext(). Then I run xgettext with the file
```

$ gcc -E hello.c > hello2.c
$ xgettext -d hello -s -o hello.pot hello2.c

```

With a real software I don't think that it is the best way... (and I need gettext for a real project, it's not only for my pleasure ;) )

---

### Post by mali2297 on 2009-07-29
You can add underscore as a custom keyword with
```

xgettext -d hello -s -o hello.pot hello.c -k_

```

---

### Post by darkagonik on 2009-07-29
Thank you very much :D
I didn't understand this option when I read the man page.

---

