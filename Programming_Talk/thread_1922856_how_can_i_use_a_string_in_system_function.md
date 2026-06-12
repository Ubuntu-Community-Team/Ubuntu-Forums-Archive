---
title: "how can i use a string in system function"
date: 2012-02-09
forum: Programming Talk
---

### Post by yugi on 2012-02-09
hello everybody
i was trying to create a program in C which takes a path from user changes directory to it and then creates a folder which again named by user but i couldn't use system function properly to do it. can you tell me how can i do that?

---

### Post by Arndt on 2012-02-09
> **yugi said:**
> hello everybody
i was trying to create a program in C which takes a path from user changes directory to it and then creates a folder which again named by user but i couldn't use system function properly to do it. can you tell me how can i do that?

Show what you have so far.

---

### Post by yugi on 2012-02-09
its not to much i have defined and included required stuff then i did this
    printf("\nEnter the folder path\n");
    scanf("%s",path);
but i couldnt make it to
system ("cd %s",path);

---

### Post by Arndt on 2012-02-09
> **yugi said:**
> its not to much i have defined and included required stuff then i did this
    printf("\nEnter the folder path\n");
    scanf("%s",path);
but i couldnt make it to
system ("cd %s",path);

I think you should still show the whole program, but one error is obvious: not all string functions do something special with '%'; printf does, and scanf, and sprintf, which you may want to use, but not 'system'.

---

### Post by yugi on 2012-02-09
i just need help with that part if i cant use %s in system function how can i do that?

my code was something like this

#include <stdio.h>
#include <stdlib.h>
int x, xmax;
char path[150];
int main()
{
    printf("\nEnter the folder path\n");
    scanf("%s",path);
    system("cd %s", path);
    printf("\nEnter the first and last folder number with one blank each\n");
    scanf("%d %d", &x, &xmax);
    while(x<=xmax)
    {
        system("mkdir %d",x);
        x++;
    }
    return 0;
}

i need to learn correct usage of system function

---

### Post by Bachstelze on 2012-02-09
Why use system()? There is a mkdir() function that does just what you want.

```
man 2 mkdir
```

So it would look like this:

```
char buf[25];
snprintf(buf, sizeof(buf), "%d", x);
mkdir(buf, 0755);
```

*EDIT:* Misread the post earlier. Since you use an integer, you have to use snprintf() anyway.

*EDIT 2:* Likewise, don't use system("cd ..."), use chdir().

*EDIT 3:* And while I'm at it, Don't Use scanf&#8482;. Use fgets() to read a string, and sscanf() to parse it if you need to.

*EDIT 4:* Correct usage of system() is you don't use it unless you really know what you are doing. ;)

---

### Post by Arndt on 2012-02-09
> **Bachstelze said:**
> Why use system()? There is a mkdir() function that does just what you want.

```
man 2 mkdir
```

So it would look like this:

```
char buf[25];
snprintf(buf, sizeof(buf), "%d", x);
mkdir(buf, 0755);
```

*EDIT:* Misread the post earlier. Since you use an integer, you have to use snprintf() anyway.

*EDIT 2:* Likewise, don't use system("cd ..."), use chdir().

*EDIT 3:* And while I'm at it, Don't Use scanf™. Use fgets() to read a string, and sscanf() to parse it if you need to.

*EDIT 4:* Correct usage of system() is you don't use it unless you really know what you are doing. ;)

Adding to point 4: Correct usage can of course be learned by looking at the manual page for 'system'.

---

### Post by ofnuts on 2012-02-09
Adding to point 2: system("cd blah") only changes the directory of the shell created to execute the command passed to "system" (this also applies to other commands that change the environment, such as "export").

---

### Post by yugi on 2012-02-09
okay thanks for your help but what about windows?
which parts should i change?

---

### Post by ofnuts on 2012-02-10
> **yugi said:**
> okay thanks for your help but what about windows?
which parts should i change?All the remarks also apply to windows.

Btwn if you code in Windows, in the system APIs(*) the "/" is a a recognized file path separator, whihc is often much more convenient to handle than "\".

(*) and also in the command prompt, as long as it is kept out of the parameter parser's reach by proper quoting.

---

