---
title: "gcc updates !"
date: 2011-02-13
forum: Packaging and Compiling Programs
---

### Post by med linux on 2011-02-13
[CENTER][COLOR=Red][SIZE=5]good morning,
i have a problem with gcc
in my code source i used 
#include <conio.h>
but this unit is not found
how to resolve this problem !

[/SIZE][/COLOR][/CENTER]

---

### Post by linuxsyst on 2011-02-13
To Compilie put the file on desktop write ```
cd Desktop
``` then```
gcc -o filename that you want filename.cpp
```
then```
new filename and it's ready
```

---

### Post by med linux on 2011-02-13
the same problem !
```

user@hp:~/c$ more source.cpp
#include <stdio.h>
#include <conio.h>
void main()
{
int a, b, somme ; 
puts("BONJOUR"); 
a = 10 ; 
b = 50 ; 
somme = (a + b)*2 ; 
printf(« Voici le resultat : %d\n », somme) ;
puts("Pour continuer frapper une touche...");
getch(); 
}

user@hp:~/c$ gcc source.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory



```

---

### Post by MadCow108 on 2011-02-13
conio is an old msdos header not available under linux
unless you are doing complex terminal stuff you usually do not need it anyway. things like getch are included in the C standard under the name getchar (defined in stdio.h)

the closest relative to it under linux is ncurses
[http://www.gnu.org/software/ncurses/](http://www.gnu.org/software/ncurses/)

---

### Post by med linux on 2011-02-15
> **MadCow108 said:**
> conio is an old msdos header not available under linux
unless you are doing complex terminal stuff you usually do not need it anyway. things like getch are included in the C standard under the name getchar (defined in stdio.h)

the closest relative to it under linux is ncurses
[http://www.gnu.org/software/ncurses/](http://www.gnu.org/software/ncurses/)

aaahhhhh thenk you verry much !

---

