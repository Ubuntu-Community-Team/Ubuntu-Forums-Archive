---
title: "programming help"
date: 2010-09-29
forum: Programming Talk
---

### Post by Anthony_25802580 on 2010-09-29
i am making a program for my cs class and cant remember how to round the decimal to the hundreths. i have everything else done but cannot remember how to make it round a double. if anyone can help it would be much appreciated. thanks!

---

### Post by lisati on 2010-09-29
Moved to [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by s.fox on 2010-09-29
Hello,

Which language are you using?

-Silver Fox

---

### Post by Anthony_25802580 on 2010-09-29
i am using c++

---

### Post by Bachstelze on 2010-09-29
Do you need to round the value internally, or just display a rounded value? If you just want to display it rounded, the printf format is %.Nlf, where N is the number of decimals to show:

```
firas@aoba ~ % cat test.c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    double a = 1.234, b = 1.236;
    printf("%.2lf %.2lf\n", a, b);
    return EXIT_SUCCESS;
}

firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test
1.23 1.24

```

---

### Post by pbrane on 2010-09-29
Or if you're using cout:
```

**std::cout.precision(2);**

```

---

### Post by MarkieB on 2010-09-29
no longer participating in ubuntuforums.org

---

