---
title: "warning in a double pointer"
date: 2010-12-26
forum: Programming Talk
---

### Post by jamesbon on 2010-12-26
```


            
            if (lstat(filepath, &statBuf) != 0) ;
            {
            }
}
```When I compile the above code I get following warning
[CODE]cc scandir.c

---

### Post by GeneralZod on 2010-12-26
Add string.h to your list of included headers.

---

### Post by Arndt on 2010-12-26
> **jamesbon said:**
> ```
#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
int main()
{
    struct dirent **namelist;
    int i, j;
    char userd[20],*filepath;
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &namelist, 0, alphasort);

    if (i < 0)
        perror
            ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
**         filepath = malloc(strlen(userd)+strlen(namelist[j]->d_name)+2);**
            printf("%s\n", namelist[j]->d_name);
            if (lstat(filepath, &statBuf) != 0) ;
            {
            }
            if (S_ISDIR(statBuf.st_mode)) {
                //       printf("Is dir %s\n",namelist[j]->d_name);
            }
            free(namelist[j]);
        }
    }
    free(namelist);
}
```When I compile the above code I get following warning
```
cc scandir.c
scandir.c: In function ‘main’:
scandir.c:21: warning: incompatible implicit declaration of built-in function ‘strlen’

```Here I used a double pointer namelist.
I am not able to understand what do I do so that I get rid of this warning.

"man strlen":

NAME
       strlen - calculate the length of a string

SYNOPSIS
       #include <string.h>

       size_t strlen(const char *s);

---

### Post by jamesbon on 2010-12-26
Ohh thanks for pointing that out.
Here is one small issue 
```

#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
#include<unistd.h>
#include<string.h>
int main()
{
    struct dirent **namelist;
    DIR *dp;
    int i, j,t;
    char userd[20],*filepath;
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &namelist, 0, alphasort);
    t=0;
    printf("Total no of directories is %d\n",i);
    if (i < 0)
        perror ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
        if(strcmp(".",namelist[j]->d_name)==0||strcmp("..",namelist[j]->d_name)==0)
        continue;    
        filepath = malloc(strlen(userd)+strlen(namelist[j]->d_name)+2);
sprintf(filepath,"./%s",namelist[j]->d_name);
            dp=opendir(filepath);
            printf(" %s ", namelist[j]->d_name);
            [B]if(dp)
            printf("Is a directory \n");[/B]
        
            
            free(namelist[j]);
        }
    }
    free(namelist);
}
```When I compile and run the above code the section within if statement is not getting executed inspite of content in filepath being a directory.
What could be error here ?

---

### Post by Arndt on 2010-12-26
> **jamesbon said:**
> Ohh thanks for pointing that out.
Here is one small issue 
```

#include<dirent.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>
#include<unistd.h>
#include<string.h>
int main()
{
    struct dirent **namelist;
    DIR *dp;
    int i, j,t;
    char userd[20],*filepath;
    struct stat statBuf;
    printf("Enter a directory ");
    scanf("%s", userd);
    printf("the dir is %s\n", userd);
    i = scandir(userd, &namelist, 0, alphasort);
    t=0;
    printf("Total no of directories is %d\n",i);
    if (i < 0)
        perror ("Scandir failed to open directory I hope you understand \n");
    else {
        for (j = 0; j < i; j++) {
        if(strcmp(".",namelist[j]->d_name)==0||strcmp("..",namelist[j]->d_name)==0)
        continue;    
        filepath = malloc(strlen(userd)+strlen(namelist[j]->d_name)+2);
            dp=opendir(filepath);
            printf(" %s ", namelist[j]->d_name);
            [B]if(dp)
            printf("Is a directory \n");[/B]
        
            
            free(namelist[j]);
        }
    }
    free(namelist);
}
```

When I compile and run the above code the section within if statement is not getting executed inspite of content in filepath being a directory.
What could be error here ?

Do use the debugger. Filepath is allocated two lines earlier, but you haven't put anything there yet.

---

### Post by jamesbon on 2010-12-26
> **Arndt said:**
> Do use the debugger. Filepath is allocated two lines earlier, but you haven't put anything there yet.
Yes you are right just when you messaged I had catched that error.
Thanks for message.

---

### Post by GeneralZod on 2010-12-26
You probably want something like:

```

filepath = malloc(strlen(userd)+strlen(namelist[j]->d_name)+2);
          sprintf(filepath,"%s/%s",userd, namelist[j]->d_name);

```

Edit:

Oh, you edited your code out :)

---

### Post by jamesbon on 2010-12-26
Ok I have modified the program by all means.
Here is a directory structure which I am passing on to my program
[http://rapidshare.com/files/439322576/mnirahd.tar](http://rapidshare.com/files/439322576/mnirahd.tar)
here is a code
```

    return nF;
}

```When I compile it then upon first iteration this runs successfully.
But then while returning from recursive function it gives me some memory dump.(it crashes)
I am not clear as what is the reason.
I have uploded the directory structure if you want to check what I am saying.
Compile it and 
the link I gave download and extract it.
You will get a directory name dir0.
Suppose in /home/ubuntu/
are two files this_code.c mnirahd.tar
Now cc this_code.c and tar -xvf mnirahd.tar
The same directory you compile this program
./a.out
when it asks to give directory name give dir0 to it.
You will see what I am saying.

---

### Post by Arndt on 2010-12-26
> **jamesbon said:**
> Ok I have modified the program by all means.
Here is a directory structure which I am passing on to my program
[http://rapidshare.com/files/439322576/mnirahd.tar](http://rapidshare.com/files/439322576/mnirahd.tar)
here is a code
```

#include<dirent.h>
#include<unistd.h>
#include<string.h>
#include<sys/stat.h>
#include<stdlib.h>
#include<stdio.h>
char *directs[20], *files[20];
int i = 0;
int j = 0;
int count = 0;

void printdir(char *);
int count_dirs(char *);
int count_files(char *);
int main()
{
    char startdir[20];
    printf("Scanning user directories\n");
    scanf("%s", startdir);
    printdir(startdir);
}

void printdir(char *dir)
{

//    printf("printdir called %d directory is %s\n", ++count, dir);
    DIR *dp = opendir(dir);
    int nDirs, nFiles, nD, nF;
    nDirs = 0;
    nFiles = 0;
    nD = 0;
    nF = 0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        nDirs = count_dirs(dir);
        nFiles = count_files(dir);
//        printf("The no of subdirectories in %s is %d \n", dir, nDirs);
//        printf("The no of files in %s is %d \n", dir, nFiles);

        /*while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath =  malloc(strlen(dir) + strlen(entry->d_name) + 2);
            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);

                if (lstat(filepath, &statBuf) != 0) {
                }

                if (S_ISDIR(statBuf.st_mode)) {
                    nD++;
                    if ((nDirs - nD) < 3) {
                        printf("The directory is %s\n",entry->d_name);
                    }
                } else {
                    nF++;

                    if ((nFiles - nF) < 3) {
                        printf("The files are %s\n",entry->d_name);
                    }    //if

                }    //else

                free(filepath);
            }    //if(filepath)

        }    */    //while

//########################################################

      struct dirent **namelist;
        DIR *dop;
        int i, j,t,re;
    //re is 2 less than i so that . and .. is ensured 
        char userd[20],*filepath;
      //  struct stat statBuf;
        //printf("Enter a directory ");
        //scanf("%s", userd);
        //printf("the dir is %s\n", userd);
        i = scandir(dir, &namelist, 0, alphasort);
        t=0;

        //printf("Total no of directories is %d\n",i);
        if (i < 0)
                perror ("Scandir failed to open directory I hope you understand \n");
        else {
                for (j = 0; j < i; j++) {
                if(strcmp(".",namelist[j]->d_name)==0||strcmp("..",namelist[j]->d_name)==0)
                continue;
                filepath = malloc(strlen(userd)+strlen(namelist[j]->d_name)+2);
                  sprintf(filepath,"%s/%s",dir,namelist[j]->d_name);
                        dop=opendir(filepath);
                //      printf(" %s ", namelist[j]->d_name);
                        if(dop)
                         {
                         //printf("Is a directory \n");
                nD++;
                if ((nDirs-nD)<3)    
                printf("%s ",namelist[j]->d_name);
                          }     
                     else {
                nF++;
                if ((nFiles-nF)<3)    
                printf("%s ",namelist[j]->d_name);
              }

                        free(namelist[j]);
                }
        }
        free(namelist);
    free(filepath);
   
//################################################

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }
//            printf("In second while loop *entry=%s\n", entry->d_name);
            char *filepath = malloc(strlen(dir) + strlen(entry->d_name) + 2);
            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);
                if (lstat(filepath, &statBuf) == 0) {
                    if (S_ISDIR(statBuf.st_mode)) {
                    printdir(filepath);
                        }
                    else {
                    }
                }

            }    //else

            free(filepath);
        }        //2nd while

        closedir(dp);
    }

    else {
        fprintf(stderr, "Error, cannot open directory %s\n", dir);
    }

}                //printdir

int count_dirs(char *dir)
{
    DIR *dp = opendir(dir);
    int nD;
    nD = 0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath =  malloc(strlen(dir) + strlen(entry->d_name) + 2);

            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);

                if (lstat(filepath, &statBuf) != 0) {
                    fprintf(stderr, "File Not found? %s\n",filepath);
                }

                if (S_ISDIR(statBuf.st_mode)) {
                    nD++;

                } else {
                    continue;
                }

                free(filepath);
            }
        }

        closedir(dp);
    } else {
        fprintf(stderr, "Error, cannot open directory %s\n", dir);
    }
    return nD;
}

int count_files(char *dir)
{
    DIR *dp = opendir(dir);
    int nF;
    nF = 0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath =
                malloc(strlen(dir) + strlen(entry->d_name) + 2);

            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);

                if (lstat(filepath, &statBuf) != 0) {
                    fprintf(stderr, "File Not found? %s\n",    filepath);
                }

                if (S_ISDIR(statBuf.st_mode)) {

                    continue;
                } else {
                    nF++;

                }

                free(filepath);
            }
        }

        closedir(dp);
    } else {
        fprintf(stderr, "Error, cannot open file %s\n", dir);
    }
    return nF;
}

```When I compile it then upon first iteration this runs successfully.
But then while returning from recursive function it gives me some memory dump.(it crashes)
I am not clear as what is the reason.
I have uploded the directory structure if you want to check what I am saying.
Compile it and 
the link I gave download and extract it.
You will get a directory name dir0.
Suppose in /home/ubuntu/
are two files this_code.c mnirahd.tar
Now cc this_code.c and tar -xvf mnirahd.tar
The same directory you compile this program
./a.out
when it asks to give directory name give dir0 to it.
You will see what I am saying.

You take strlen(userd) without storing anything in 'userd'. 'valgrind' fairly easily finds this error. The compiler doesn't, though, even with -O -Wall -Wextra, but it does say that 'filepath' defined on line 79 may be used uninitialized, which is true - you allocate it sometimes but free it always.

---

### Post by GeneralZod on 2010-12-26
At least one major bug is due to the fact that, in printdir, the malloc'ing and free'ing of filepath don't happen in pairs, so you have a) a memory leak and b) the possibility of free'ing uninitialised memory (the latter of which I found by using gdb - have you tried this, yet?)

---

### Post by jamesbon on 2010-12-26
> **Arndt said:**
> You take strlen(userd) without storing anything in 'userd'. 'valgrind' fairly easily finds this error. The compiler doesn't, though, even with -O -Wall -Wextra, but it does say that 'filepath' defined on line 79 may be used uninitialized, which is true - you allocate it sometimes but free it always.
Thanks Arndt I did not noticed this part.

> **GeneralZod said:**
> At least one major bug is due to the fact  that, in printdir, the malloc'ing and free'ing of filepath don't happen  in pairs, so you have a) a memory leak and
I get this point.
> **GeneralZod said:**
> 
 b) the possibility of free'ing uninitialised memory (the latter of  which I found by using gdb - have you tried this, yet?)
Hi thanks I finally was able to solve the entire problem.Thanks all.

---

