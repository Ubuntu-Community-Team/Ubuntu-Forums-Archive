---
title: "Bizzare compiler behaviour"
date: 2008-12-18
forum: Programming Talk
---

### Post by portaldude on 2008-12-18
Goodday everyone.

I recently took up learn the C programming language, using the excellent book "The C programming language". I am only a few pages in and have encountered following example
```

#include <stdio.h>

main()
{
    int c;

    while ((c = getchar()) != EOF)
        putchar(c);
}

```
Courious as I am, I wanted to play around with the program a bit and such, I copied it, saved it in a .c file format and compiled, using the GCC compiler that came with my Ubuntu distrubution, using the command
```

gcc myfile.c

```

 There after, I ran the program and to my big surprise, it started to behave bizzarly.

If I wrote something in the terminal window like "I am testing this program", the program would output "PPPPPPPPPPPPPPPPPPPPPPPPPP"(that exact output), or a long lines of blanks.

I tried the GCC compiler in Windows, and there it would output my input flawless.

Does anyone know what is going on? Is there a bug in the compiler?

---

### Post by Bachstelze on 2008-12-18
The program behaves as expected here. Which commands exactly did you use to compile and run it?

---

### Post by portaldude on 2008-12-18
I simply used the command gcc myfile.c to compile it. Then ./a.out to run it. No axtra options, just thoose.

---

### Post by Bachstelze on 2008-12-18
Well, it does work fine here... Do you have all the necessary stuff installed?

```
sudo apt-get install build-essential
```

---

### Post by nvteighen on 2008-12-18
> **portaldude said:**
> 
```

#include <stdio.h>

main()
{
    int c;

    while ((c = getchar()) != EOF)
        putchar(c);
}

```


That code is outdated... well, "The C Programming Language" is an outdated book, as the C language has changed a bit since that book was published.

Try using:
```

#include <stdio.h>

int main(void)
{
    int c = 0;

    while ((c = getchar()) != EOF)
        putchar(c);

    return 0;
}

```

This code works for me...

Just a note: always compile using the -Wall option. It will show all warnings so you'll have it easier to detect any issue you may get.

---

