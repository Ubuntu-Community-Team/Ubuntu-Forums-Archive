---
title: "sorted order of file names in a directory"
date: 2010-12-27
forum: Programming Talk
---

### Post by jamesbon on 2010-12-27
Hi here is a program to scan directories and files in a subdirectory.This is a working code.
```

#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
#include<unistd.h>
#include<string.h>
int main()
{
    struct dirent **somest;
    DIR *dp;
    int i, j,t,nDd,nFf;
    char userd[20],*filepath,*directs[20],*files[20];
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &somest, 0, alphasort);
    nDd=0;nFf=0;
    
    printf("Total no of directories is %d\n",i);
    if (i < 0)
        perror ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
        if(strcmp(".",somest[j]->d_name)==0||strcmp("..",somest[j]->d_name)==0)
        continue;    
        filepath = malloc(strlen(userd)+strlen(somest[j]->d_name)+2);
        if(filepath)
          {
            sprintf(filepath,"%s/%s",userd,somest[j]->d_name);
            dp=opendir(filepath);
            printf(" %s ", somest[j]->d_name);
            if(dp)
             {
                directs[nDd]=somest[j]->d_name;
                        // printf("Is a directory \n");
                
                nDd++;
                   }
            else
              {    files[nFf]=somest[j]->d_name;
                nFf++;}

        free(filepath);
         }    
            free(somest[j]);
        }
    }
    free(somest);
}
```How ever I have one observation which I could not understand.
Let us say there is a directory
/home/ubuntu/
where this program is and a another directory named bond0 exists.
So ```

ls /home/ubuntu 
program.c bond0
```Inside bond0 I have following subdirectories and files
```
bond1 bond2 bond3 bond4 file1 file2 file3 file file7 file10
```When I run the above program and  upon being asked 
./a.out
Enter a directory bond0
the dir is bond0

```
  bond1  bond2  bond3  bond4  bond5  file1  **file10**  file2  file3    file7
```Note in above output file10 is before file2.Why file10 comes after file10 and not after file7.
How can I get it in a sorted way so that I get 
file1 file2 file3 file7 file10

---

### Post by Some Penguin on 2010-12-27
Lexicographic sorts compare by prefixes, and 1 comes before 7.  You wouldn't expect 'alpha' to come /after/ 'baker', even though 'l' comes after 'a', would you?  Same deal.  You want custom sorting behavior, use a sort method that takes a custom comparator and write one that understands that you're expecting <letters><numbers>.

---

### Post by dwhitney67 on 2010-12-27
If you are working under Linux, and don't care about portability, use the versionsort() function in lieu of alphasort().

Btw, you need to call closedir() each time opendir() is successful.  Also, I'm not sure why you chose to use opendir(); you should have stuck to using lstat().


P.S.  You're code will NOT work for all situations.  If the directory you are scanning has more than 20 files or directories in it, you will overwrite the bounds of your storage arrays.

---

### Post by Arndt on 2010-12-27
> **jamesbon said:**
> Hi here is a program to scan directories and files in a subdirectory.This is a working code.
```

#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
#include<unistd.h>
#include<string.h>
int main()
{
    struct dirent **somest;
    DIR *dp;
    int i, j,t,nDd,nFf;
    char userd[20],*filepath,*directs[20],*files[20];
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &somest, 0, alphasort);
    nDd=0;nFf=0;
    
    printf("Total no of directories is %d\n",i);
    if (i < 0)
        perror ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
        if(strcmp(".",somest[j]->d_name)==0||strcmp("..",somest[j]->d_name)==0)
        continue;    
        filepath = malloc(strlen(userd)+strlen(somest[j]->d_name)+2);
        if(filepath)
          {
            sprintf(filepath,"%s/%s",userd,somest[j]->d_name);
            dp=opendir(filepath);
            printf(" %s ", somest[j]->d_name);
            if(dp)
             {
                directs[nDd]=somest[j]->d_name;
                        // printf("Is a directory \n");
                
                nDd++;
                   }
            else
              {    files[nFf]=somest[j]->d_name;
                nFf++;}

        free(filepath);
         }    
            free(somest[j]);
        }
    }
    free(somest);
}
```


Since you (quite properly) dislike the appearance of warnings, you may want to take care of the ones we get if we subject the program to gcc -O -Wall -Wextra:

```
d.c: In function ‘main’:
d.c:13: warning: unused variable ‘statBuf’
d.c:11: warning: unused variable ‘t’
d.c:15: warning: ignoring return value of ‘scanf’, declared with attribute warn_unused_result
d.c:50: warning: control reaches end of non-void function

```

Besides, I find the indentation a bit chaotic (making it harder to read than otherwise). Does it appear nicely indented in your editor?

---

### Post by jamesbon on 2010-12-27
> **dwhitney67 said:**
> If you are working under Linux, and don't care about portability, use the versionsort() function in lieu of alphasort().

Btw, you need to call closedir() each time opendir() is successful. Also, I'm not sure why you chose to use opendir(); you should have stuck to using lstat().


P.S. You're code will NOT work for all situations. If the directory you are scanning has more than 20 files or directories in it, you will overwrite the bounds of your storage arrays.



Ok I have taken a note of all the points raised by you.


Here is a modified code 
```

#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
#include<unistd.h>
#include<string.h>
int main()
{
    struct dirent **somest;
    DIR *dp;
    int i, j,t,nDd,nFf;
    char userd[20],*filepath,*directs[20],*files[20];
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &somest, 0, versionsort);
    nDd=0;nFf=0;
    
    printf("Total no of directories is %d\n",i);
    if (i < 0)
        perror ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
        if(strcmp(".",somest[j]->d_name)==0||strcmp("..",somest[j]->d_name)==0)
        continue;    
        filepath = malloc(strlen(userd)+strlen(somest[j]->d_name)+2);
        if(filepath)
          {
            sprintf(filepath,"%s/%s",userd,somest[j]->d_name);
            dp=opendir(filepath);
            printf(" %s ", somest[j]->d_name);
            if(dp)
             {
                directs[nDd]=somest[j]->d_name;
                        // printf("Is a directory \n");
                
                nDd++;
                   }
            else
              {    files[nFf]=somest[j]->d_name;
                nFf++;}

        free(filepath);
         }    
            free(somest[j]);
        }
    }
    free(somest);
}

```

When I compile the above I get a error

```

scandir.c: In function ‘main’:
scandir.c:17: error: ‘versionsort’ undeclared (first use in this function)
scandir.c:17: error: (Each undeclared identifier is reported only once
scandir.c:17: error: for each function it appears in.)

```

How can I get rid of this error.
I will incorporate the points you have raised.




> **Arndt said:**
> Since you (quite properly) dislike the appearance of warnings, you may want to take care of the ones we get if we subject the program to gcc -O -Wall -Wextra:

Ok is it a good practise to use -O -Wall -Wextra always
> **Arndt said:**
> 
```
d.c: In function ‘main’:
d.c:13: warning: unused variable ‘statBuf’
d.c:11: warning: unused variable ‘t’
d.c:15: warning: ignoring return value of ‘scanf’, declared with attribute warn_unused_result
d.c:50: warning: control reaches end of non-void function

```Besides, I find the indentation a bit chaotic (making it harder to read than otherwise). Does it appear nicely indented in your editor?
Yes it appears nice in  my editor.I use vim.

---

### Post by dwhitney67 on 2010-12-27
> **jamesbon said:**
> 
When I compile the above I get a error

```

scandir.c: In function &#8216;main&#8217;:
scandir.c:17: error: &#8216;versionsort&#8217; undeclared (first use in this function)
scandir.c:17: error: (Each undeclared identifier is reported only once
scandir.c:17: error: for each function it appears in.)

```

AFAIK, versionsort is only available under Linux; you will need to compile your code with the -D_GNU_SOURCE option, or define that flag within your code.  For example:
```

#define _GNU_SOURCE

#include <dirent.h>
...

```

> **jamesbon said:**
> 
Yes it appears nice in  my editor.I use vim.

Undoubtedly, you are using tabs in your source code, which for whatever reason, do not render well when posting to this forum.  The code that you have posted is ill-formatted; when I post code which I develop using vim, I have no such issues.

---

### Post by jamesbon on 2010-12-29
> **dwhitney67 said:**
> AFAIK, versionsort is only available under Linux; you will need to compile your code with the -D_GNU_SOURCE option, or define that flag within your code. 
Ok this has worked very well.
I never knew about this option.After using as you mentioned the other code which I was trying with similar features have worked very well.

---

### Post by Vox754 on 2010-12-29
> **Arndt said:**
> ...

Besides, I find the indentation a bit chaotic (making it harder to read than otherwise). Does it appear nicely indented in your editor?

Lol.

Wrong question, because "nicely indented" is completely subjective.

I am pretty sure the code does not use tabs, and in fact it is his original indentation, only to him it is "nice".

---

### Post by Arndt on 2010-12-29
> **Vox754 said:**
> Lol.

Wrong question, because "nicely indented" is completely subjective.

I am pretty sure the code does not use tabs, and in fact it is his original indentation, only to him it is "nice".

What's your point here, actually? He already answered the question, two days ago.

---

### Post by Vox754 on 2010-12-29
> **Arndt said:**
> What's your point here, actually? He already answered the question, two days ago.

In the future, never ask a person if his indentation is beautiful, nice or correct.

That's like asking a mother if her newborn is pretty... well duh.

---

### Post by Arndt on 2010-12-29
> **Vox754 said:**
> In the future, never ask a person if his indentation is beautiful, nice or correct.

That's like asking a mother if her newborn is pretty... well duh.

I think it was established that it's fine in his editor, and atrocious here, so we'll look forward to his next piece of code, and if need be, give advice towards rectifying the matter.

---

