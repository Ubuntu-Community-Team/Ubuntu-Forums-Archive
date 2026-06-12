---
title: "User information"
date: 2008-08-20
forum: Programming Talk
---

### Post by someone_yeah on 2008-08-20
I am writing a function in C that takes the user's information as it is in /etc/passwd. How do you get C to return the user's group id,home directory and login shell?
I know about <unistd.h>, but when I start the program as root and do seteuid() with a user's id number, and then ask it to return his group, it returns the group of root despite that now the effective id is the user's.
Help will be greatly appreciated

---

### Post by cmay on 2008-08-20
this example will return many informations.
i am not sure how to get the /etc7passwd myselve.

```
#include <stdio.h>

int main(argc, argv, envp)
int argc;                /* Number of args */
char *argv[];            /* Argument ptr array */
char *envp[];            /* Environment ptr array */
{
    int a;

    printf("The command name (argv[0]) is %s\n", argv[0]);
    printf("There are %d arguments:\n", argc-1);
    for (a=1; a<argc; a++)
                         printf("\targument %2d:\t%s\n", a, argv[a]);

    printf("The environment is as follows:\n");
    a = 0;
    while (envp[a] != NULL)
                         printf("\t%s\n", envp[a++]);
}
```
anhoter thing i found is printf("%s user name",getenv("USERNAME"));
hope it helps.

---

### Post by jinksys on 2008-08-20
> **someone_yeah said:**
> I am writing a function in C that takes the user's information as it is in /etc/passwd. How do you get C to return the user's group id,home directory and login shell?
I know about <unistd.h>, but when I start the program as root and do seteuid() with a user's id number, and then ask it to return his group, it returns the group of root despite that now the effective id is the user's.
Help will be greatly appreciated

You don't need to be root to access /etc/passwd

---

### Post by someone_yeah on 2008-08-20
Thanks, that does return some useful information. However, I doesn't allow me to declare char *envp[] in my function as it is in your code. Also, there must be a way when some library commands or functions return that information, which will be better for my function. But still, thanks.

To jinksys: yes,but the program I am writing is to be executed as root. So, I want it to return the user's information, not the root's

Any other ideas?

---

### Post by someone_yeah on 2008-08-20
[QUOTE=someone_yeah;5626876]Thanks, that does return some useful information. However, I doesn't allow me to declare char *envp[] in my function as it is in your code. Also, there must be a way when some library commands or functions return that information, which will be better for my function. But still, thanks.

To jinksys: yes,but the program I am writing is to be executed as root. So, I want it to return the user's information, not the root's

Any other suggestions?

---

### Post by cmay on 2008-08-20
[QUOTE]> **someone_yeah said:**
> Thanks, that does return some useful information. However, I doesn't allow me to declare char *envp[] in my function as it is in your code. Also, there must be a way when some library commands or functions return that information, which will be better for my function. But still, thanks.
as i am newbie in c i have as the first program i tried to write in c wanted to write a simple little program that prints out all information i could retrieve. i found out this much up to now. so here is what i use as my own function in this program. i see that you are way more experienced than me so all i did was to point you towards the envp[] as i suspect or hope there is a functione somewhere. i was maybe to quick to reply.
anyway i hope that it somehow works out for you.good luck.

```
#include <stdio.h>
#include <stdlib.h>
void my_function();
int main(){
my_function();
return 0;
}
void my_function(){
if(getenv("/etc/passwd")==0){
printf("%s",getenv("LOGNAME"));
}
else
printf("arrgghhh\n");
}
```

---

### Post by someone_yeah on 2008-08-20
Thanks. Anyway, I found it out. One has to use the "getpwuid_r" function. Again, thanks for all your help and sorry for the two messages in a row

---

### Post by cmay on 2008-08-20
thanks.
whit that little information i can have my first newbie program a lot better. good luck to you.

---

### Post by someone_yeah on 2008-08-20
Write if you need more info or help about the getpwuid_r()

---

### Post by LaRoza on 2008-08-20
> **cmay said:**
> ```

int main(argc, argv, envp)
int argc;                /* Number of args */
char *argv[];            /* Argument ptr array */
char *envp[];            /* Environment ptr array */
{

```

That is a really old way of writing C. Are you aware of the current standards? (At least, the 89 standard...)

---

### Post by ghostdog74 on 2008-08-20
Some of the libraries you can use are pwd.h,  grp.h

---

### Post by cmay on 2008-08-20
> That is a really old way of writing C. Are you aware of the current standards? (At least, the 89 standard...
yes i know.
i have the kerninghan c programming book.all tutorials i encounter uses this oldstyle and most older than that. my book from danish comp-science uses it. i would be happy if i could find the new standards. i have googled a lot on c but found only above tutorials .

---

