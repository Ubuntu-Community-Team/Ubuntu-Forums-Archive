---
title: "String Array in C ---How to recursively add strings?"
date: 2011-02-17
forum: Programming Talk
---

### Post by Zacinfinite on 2011-02-17
<<I just want to use loop to enter strings in array>>

[B]char array[4];
int i=0;

for(i=0;i<=4;i++)
    {
        printf("enter the %d element",i);
        scanf("%s",&array[i]);
    }[/B]


<<THIS DOESNT WORK! HELP>>

---

### Post by worksofcraft on 2011-02-17
> **Zacinfinite said:**
> <<I just want to use loop to enter strings in array>>

[B]char array[4];
int i=0;

for(i=0;i<=4;i++)
    {
        printf("enter the %d element",i);
        scanf("%s",&array[i]);
    }[/B]


<<THIS DOESNT WORK! HELP>>

You have an array of char
what you want is an array of strings...

In C strings are done using array of char so you might might do it like so:
[php]
#include <stdio.h>

int main(int argc, char *argv[], char *envp[]) {
char array[4][120];
int i=0;

for(i=1;i<=4;i++)
    {
        printf("enter the %d element:",i);
        scanf("%s",array[i-1]);
    }
for(i=1;i<=4;i++)
    {
        printf("%d element= %s\n",i,array[i-1] );
	}
}
[/php]

---

### Post by Zacinfinite on 2011-02-17
Thanks Man

---

