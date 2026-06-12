---
title: "Netbean problem Ubuntu 12.04"
date: 2012-05-09
forum: Programming Talk
---

### Post by Reynaldo2333 on 2012-05-09
i did this on windows, having so much problems to test on ubuntu..After some research i found netbeans, got the compilers ready and everything.. but i get this error when trying to build and run.
Here's the code, made it on windows, dont know if i need to change anything since windows is windows and well ubuntu is linux.

```
#include <stdio.h>

int main(void)
{
    printf("Fundamentos de Programacion \n");
    printf("Nombre: Reynaldo Jose Ramirez \n");
    printf("Carrera: Psicologia\n");
    printf("Trimestre actual: Mayo-Julio 2012\n");
    getch();
    return(0);
}

```

now here's the error
: java.util.missingresourceexception: bin/nativeexecution/Linux-x86_64/pty
RUN FAILED

i tried to search on google, tried search feature here, nothing.. Please show me the way.

---

### Post by r-senior on 2012-05-10
The getch() function not standard C. The one I suspect you are trying to use is from [conio.h]("http://en.wikipedia.org/wiki/Conio.h"), or there's also one in the curses library.

Depending what you need to do, you could substitute getchar() but that echoes the character that was typed.

Given that most command-line programs on Linux systems are run from a command line, rather than opening their own command window, the 'press key to continue' idea is not as important.

---

### Post by Reynaldo2333 on 2012-05-11
on one of my trys, i commented the getch, but then still.. the error persist.

i posted on netbeans forums and i got this

[quote="soldatov"]Yes. Ubuntu 12.04 has invalid NetBeans build (some files are absent). Valid NetBeans can be downloaded from [http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)[/quote]

link: [http://forums.netbeans.org/viewtopic.php?t=48020](http://forums.netbeans.org/viewtopic.php?t=48020)

right now im downloading the bundle, ill post the outcome.

EDIT: i had to download the all in bundle and it worked like a charm.

---

### Post by nmaybyte on 2013-01-24
[http://xkcd.com/979/](http://xkcd.com/979/)

Did you figure this out?

---

