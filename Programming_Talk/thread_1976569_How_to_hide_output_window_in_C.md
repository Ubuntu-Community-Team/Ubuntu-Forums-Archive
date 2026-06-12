---
title: "How to hide output window in C ?"
date: 2012-05-08
forum: Programming Talk
---

### Post by prismctg on 2012-05-08
Is there any way to hide output window (shell) ???

---

### Post by codemaniac on 2012-05-09
Please mention your requirements clearly so that we can try helping you better .However you dont want printing values you can turn of your printf functions that are responsible for sending program output to the screen .

---

### Post by prismctg on 2012-05-09
i want to write a program which will run as background process like this one :```
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int a=0;
    while(a<=1)
    {
        system("nautilus");
        a=a+1;

    }
}
```

---

### Post by dwhitney67 on 2012-05-09
In the bash shell, to run a program in the background, use the '&' symbol.  For example:
```

nautilus &

```

If you do not want to see any output on the terminal, then redirect all output to /dev/null.  For example:
```

nautilus >& /dev/null

```
To combine the two concepts described above:
```

nautilus >& /dev/null &

```
Now, as for your C program, what is its purpose?  If you require two nautilus dialogs, just repeat the last command shown above twice in the same terminal.

---

