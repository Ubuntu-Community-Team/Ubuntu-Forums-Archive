---
title: "Can a C program change directories?"
date: 2011-07-08
forum: Programming Talk
---

### Post by tomkat3 on 2011-07-08
Hello forums,

I have 5 folders that contain 5 more folders. In each of the five folders at the bottom, there's a text file containing a group of numbers that I'd like to read and copy to a text file at the top of this system of directories.

To make sure my program could move around the directories, I wrote this simple program that would pwd whenever the directory changed:

```
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int        i, j;
    char    command[100];
    double    JO[5];
    double    JB[5];
    
    JO[0] = 0.0;//Joca_oca
    JO[1] = -1.0;
    JO[2] = -2.0;
    JO[3] = -3.0;
    JO[4] = -4.0;
    
    JB[0] = 0.0;//Joca_bone
    JB[1] = -1.0;
    JB[2] = -2.0;
    JB[3] = -3.0;
    JB[4] = -4.0;
    
    for(i=0; i<5; i++)
    {
        sprintf(command, "cd Joca_oca%3.1f", JO[i]);
        printf("cd Joca_oca%3.1f\n", JO[i]);
        system(command);
        system("pwd");
        for(j=0; j<5; j++)
        {
            sprintf(command, "cd Joca_bone%3.3f", JB[j]);
            printf("cd Joca_bone%3.3f\n", JB[j]); /// Note that the bottom directories have 3 zeros
            system(command);
            system("pwd");
            system("cd ..");
        }
        system("cd ..");
    }
    return 0;
}
    
    
    
```This code basically generates a bunch of error messages when I run it, that look like:

```
 cd: 1: can't cd to Joca_bone-1.000
```I wrote another simple program that was supposed to go one level down and pwd, but even that just printed the directory I started it in.

I ended up writing a shell script to do what I needed to do, but for future reference: Is C capable of what I'm trying to do? Advice?

---

### Post by slavik on 2011-07-08
read what system() does. it doesn't do what you think it does.

---

### Post by Arndt on 2011-07-08
> **slavik said:**
> read what system() does. it doesn't do what you think it does.

The system call which does the job is 'chdir'.

---

### Post by JupiterV2 on 2011-07-08
I'm assuming this is an exercise you're trying in C, correct? Otherwise, a bash script would be infinitely easier.

---

### Post by StephenF on 2011-07-08
+1 for chdir

---

### Post by cgroza on 2011-07-08
I think there is a function in the standard library for that.

---

### Post by JupiterV2 on 2011-07-09
> **cgroza said:**
> I think there is a function in the standard library for that.

Do you mean the POSIX library unistd.h? Standard to most (all?) Unix derived systems like Linux but not a part of the C standard library. It's not portable to other non-Unix-like hosts.

That said, if the program is meant to run on {U,Li}nux systems, why not use that instead of system() calls?

---

### Post by nvteighen on 2011-07-09
FYI, the POSIX API not only provides chdir, but also data structures that can manipulate directories. I tell you this because there's no way to modify directories using the C Standard Library, which only offers procedures for file manipulation.

Simple example using chdir:
```

#include <stdio.h>
#include <string.h> /* memset */
#include <unistd.h> /* getcwd, chdir */

void print_cwd(void)
{
    /* You know, it's good to get into the habit of abstracting things. */

    char cwd[100];
    (void) memset(cwd, 0, sizeof(cwd));
    (void) printf("Current Directory: %s\n", getcwd(cwd, sizeof(cwd)));
}

int main(void)
{
    print_cwd();

    if(!chdir("/")) /* chdir returns 0 on success */
    {
        print_cwd();
    }
    else
    {
        perror("Uh, something that shouldn't happen happened!");
        return -1;
    }
    
    return 0;
}

```

I suggest you to look at the manpages for the functions you don't know. If you don't have their manpages, install the manpages-dev package, which will install them. After that, you'll be able to do e.g. *man perror* to look at what perror is (a very useful function!).

---

