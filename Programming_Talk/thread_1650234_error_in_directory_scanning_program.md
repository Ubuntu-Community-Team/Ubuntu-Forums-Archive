---
title: "error in directory scanning program"
date: 2010-12-21
forum: Programming Talk
---

### Post by jamesbon on 2010-12-21
My program to scan directory is giving me error.
It is not able to go inside subdirectories which begin with a .
```
#include<dirent.h>
#include<unistd.h>
#include<string.h
int main(int argc, char *argv[])
{
    char *startdir;

    scanf("%s", argv[0]);
}


```Can someone point me as to what might be the problem?

---

### Post by Arndt on 2010-12-21
> **jamesbon said:**
> My program to scan directory is giving me error.
It is not able to go inside subdirectories which begin with a .
```
#include<dirent.h>
#include<unistd.h>
#include<string.h>
#include<sys/stat.h>
#include<stdlib.h>
#include<stdio.h>
char *directs[20];
int i = 0;
void printdir(char *dir);
int main(int argc, char *argv[])
{
    char *startdir;
    printf("Scanning user directories\n");
    scanf("%s", argv[0]);
    printf("We are  starting from  %s \n", argv[0]);
    printdir(argv[0]);
    printf("\t%s\n", directs[0]);
}

void printdir(char *dir)
{
    DIR *dp;
    struct dirent *entry;
    struct stat statbuf;
    if ((dp = opendir(dir)) == NULL) {
        fprintf(stderr, "cannot open directory: %s\n", dir);
        return;
    }

    chdir(dir);
    while ((entry = readdir(dp)) != NULL) {
        lstat(entry->d_name, &statbuf);
        if (S_ISDIR(statbuf.st_mode)) {
                if(strcmp(".",entry->d_name)==0||strcmp("..",entry->d_name)==0)
         continue;
            directs[i] = entry->d_name;
        i++;
        printdir(entry->d_name);
        }
    //chdir("..");
    //closedir(dp);
        //printf("\n the directory we are entering is %s\n", entry->d_name);
    }            //while loop

    //system("pwd");
}                //printdir
```
Can someone point me as to what might be the problem?

Why on earth do you use argv[0] as a temporary variable?

```
    scanf("%s", argv[0]);
```

Why is the chdir("..") commented out?

---

### Post by jamesbon on 2010-12-21
I uncommented chdir and removed argv but it still gives me segmentation fault.
```

#include<dirent.h>
#include<unistd.h>
#include<string.h>
#include<sys/stat.h>
#include<stdlib.h>
#include<stdio.h>
char *directs[20];
int i = 0;
void printdir(char *dir);
int main()
{
    char *startdir;
    printf("Scanning user directories\n");
    scanf("%s", startdir);
    printf("We are  starting from  %s \n", startdir);
    printdir(startdir);
    printf("\t%s\n", directs[0]);
}

void printdir(char *dir)
{
    DIR *dp;
    struct dirent *entry;
    struct stat statbuf;
    if ((dp = opendir(dir)) == NULL) {
        fprintf(stderr, "cannot open directory: %s\n", dir);
        return;
    }

    chdir(dir);
    while ((entry = readdir(dp)) != NULL) {
        lstat(entry->d_name, &statbuf);
        if (S_ISDIR(statbuf.st_mode)) {
                if(strcmp(".",entry->d_name)==0||strcmp("..",entry->d_name)==0)
         {
        printf("What goes in is %s\n",directs[i]);}
            directs[i] = entry->d_name;
        i++;
        printdir(entry->d_name);
        }
    chdir("..");
    //closedir(dp);
        //printf("\n the directory we are entering is %s\n", entry->d_name);
    }            //while loop

    //system("pwd");
}                //printdir
```

but it still gives me a seg fault.

---

### Post by Arndt on 2010-12-21
> **jamesbon said:**
> I uncommented chdir and removed argv but it still gives me segmentation fault.
```

#include<dirent.h>
#include<unistd.h>
#include<string.h>
#include<sys/stat.h>
#include<stdlib.h>
#include<stdio.h>
char *directs[20];
int i = 0;
void printdir(char *dir);
int main()
{
    char *startdir;
    printf("Scanning user directories\n");
    scanf("%s", startdir);
    printf("We are  starting from  %s \n", startdir);
    printdir(startdir);
    printf("\t%s\n", directs[0]);
}

void printdir(char *dir)
{
    DIR *dp;
    struct dirent *entry;
    struct stat statbuf;
    if ((dp = opendir(dir)) == NULL) {
        fprintf(stderr, "cannot open directory: %s\n", dir);
        return;
    }

    chdir(dir);
    while ((entry = readdir(dp)) != NULL) {
        lstat(entry->d_name, &statbuf);
        if (S_ISDIR(statbuf.st_mode)) {
                if(strcmp(".",entry->d_name)==0||strcmp("..",entry->d_name)==0)
         {
        printf("What goes in is %s\n",directs[i]);}
            directs[i] = entry->d_name;
        i++;
        printdir(entry->d_name);
        }
    chdir("..");
    //closedir(dp);
        //printf("\n the directory we are entering is %s\n", entry->d_name);
    }            //while loop

    //system("pwd");
}                //printdir
```

but it still gives me a seg fault.

'startdir' isn't allocated any memory.

---

### Post by dwhitney67 on 2010-12-21
My $0.02...

1) the chdir() calls are not necessary;

2) remove code that has been commented out (it clutters the real code)

3) when calling printdir() recursively, you will need to provide the *full-path* relative to where it is currently searching; merely passing entry->d_name is not sufficient!  The same can be said for when calling lstat().

4) for now, in lieu of using 'startdir' and scanf() (which btw you should _never_ use to read strings), consider using argv[1].
```

int main(int argc, char** argv)
{
   /* perform error checking here to ensure command-line arg is given */

   printdir(argv[1]);

   return 0;
}

```

---

### Post by jamesbon on 2010-12-21
> **dwhitney67 said:**
> My $0.02...



3) when calling printdir() recursively, you will need to provide the *full-path* relative to where it is currently searching; merely passing entry->d_name is not sufficient!  The same can be said for when calling lstat().



Giving full path how can that be possible?

---

### Post by dwhitney67 on 2010-12-21
```

void printDir(const char* dirname)
{
   DIR* dp = opendir(dirname);

   if (dp)
   {
      struct dirent* entry = 0;
      struct stat    statBuf;

      while ((entry = readdir(dp)) != 0)
      {
         if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0)
         {
            continue;
         }

         **char* filepath = malloc(strlen(dirname) + strlen(entry->d_name) + 2);**

         if (filepath)
         {
            **sprintf(filepath, "%s/%s", dirname, entry->d_name);**

            if (lstat(filepath, &statBuf) == 0)
            {
               if (S_ISDIR(statBuf.st_mode))
               {
                  printDir(filepath);
               }
               else
               {
                  fprintf(stdout, "Found file: %s\n", filepath);
               }
            }
            else
            {
               fprintf(stderr, "File Removed? %s\n", filepath);
            }

            free(filepath);
         }
      }

      closedir(dp);
   }
   else
   {
      fprintf(stderr, "Error, cannot open directory %s\n", dirname);
   }
}

```

---

### Post by jamesbon on 2010-12-22
> **dwhitney67 said:**
> [code]
         **char* filepath = malloc(strlen(dirname) + strlen(entry->d_name) + 2);**

 why did you added 2 in above?

---

### Post by dwhitney67 on 2010-12-22
> **jamesbon said:**
> why did you added 2 in above?

2 = 1 + 1

One additional space for the / character, and another space for the terminating NULL character that sprintf() will add to the string.

---

### Post by jamesbon on 2010-12-22
I want to know why you said to pass on the path in printdir? What was getting wrong in my code?
In your program you do a malloc to filepath but in the next statement you used an if(filepath)
Where did filepath got modified/manipulated that you need to add 2 for the reason above cited.
As far as I understand malloc declaration will just give memory to filepath and not initialize it and in your code immediately after declaring filepath you used an if statement so why was that condition not false?

---

### Post by Arndt on 2010-12-22
> **jamesbon said:**
> I want to know why you said to pass on the path in printdir? What was getting wrong in my code?
In your program you do a malloc to filepath but in the next statement you used an if(filepath)
Where did filepath got modified/manipulated that you need to add 2 for the reason above cited.
As far as I understand malloc declaration will just give memory to filepath and not initialize it and in your code immediately after declaring filepath you used an if statement so why was that condition not false?

malloc will either fail, and then return 0, or succeed and return a pointer with uninitialized memory which you can then fill in. Look at the man page for malloc.

If it failed, of course we can't fill anything in. One may want to issue a warning message and/or abort the program completely.

If it succeeds, we fill the memory with the string we want, and as dwhitney already pointed out, we need to have space for the string material and a final byte for the Nul character.

Why your code failed we still don't know. The chdir was not incorrect as such, just a somewhat inferior way of doing it. Mostly, you will find yourself needing the full path of the files anyway at some point. It depends on what you want to do the traversal for, of course.

Did you act on my latest comment before this one?

---

### Post by dwhitney67 on 2010-12-22
> **jamesbon said:**
> I want to know why you said to pass on the path in printdir?

It is helpful to know the entire path leading to the file(s) that are discovered.

> **jamesbon said:**
> 
What was getting wrong in my code?

I lost track of what you were attempting to do in your code.  One moment you are checking if the entry is either "." or "..", and if so, recursively calling printdir() again.  It doesn't make sense to be calling printdir() under those circumstances.

> **jamesbon said:**
> 
In your program you do a malloc to filepath but in the next statement you used an if(filepath)
Where did filepath got modified/manipulated that you need to add 2 for the reason above cited.
As far as I understand malloc declaration will just give memory to filepath and not initialize it and in your code immediately after declaring filepath you used an if statement so why was that condition not false?
The variable filepath is initialized with a string value, via sprintf(), _after_ I have verified that the malloc() was successful.

These are equivalent in my universe:
```

char* filepath = malloc(...);

if (filepath)
{
   /* use filepath */
}

```
or
```

char* filepath = malloc(...);

if (filepath != NULL)
{
   /* use filepath */
}

```
To summarize, I'm checking if filepath is pointing to a valid memory location.  I have not written any data to that location yet, and I shouldn't, until I verify that I have a valid address.

---

### Post by jamesbon on 2010-12-25
Hi,
I am trying to improve this code.(Experiment)
The complete list of directories and file which we get I want that only last 2 directories and files come at each level.So for this the logic that came to my mind was I make 2 stacks and in each of the stack I store the directory name and file name along with level.

Is this logic a good logic because when I started implementing then I realized it is not as simple as it seems.If there is some better idea which is coming to some ones mind then let me know.I am just asking because of complexity of my logic.

---

### Post by Arndt on 2010-12-25
> **jamesbon said:**
> Hi,
I am trying to improve this code.(Experiment)
The complete list of directories and file which we get I want that only last 2 directories and files come at each level.So for this the logic that came to my mind was I make 2 stacks and in each of the stack I store the directory name and file name along with level.

Is this logic a good logic because when I started implementing then I realized it is not as simple as it seems.If there is some better idea which is coming to some ones mind then let me know.I am just asking because of complexity of my logic.

Show a example of a file structure and what you want as output.

---

### Post by jamesbon on 2010-12-25
suppose directory bond0 contains
bond1, di2, bond3, bond4, bond5 and my_file1, my_file2, my_file3, my_file4, my_file5, my_file6
and
bond1 contains bond6 my_file7 my_file8 my_file9 my_file10
program should output -
bond3, bond4, bond5, my_file4, my_file5, my_file6, bond6, my_file8, my_file9, my_file10

I have written some more code by the time you replied.
Here is the code it is working.
I have just added 2 functions which are counting the number of subdirectories and files in the existing directory.

```

#include<dirent.h>
#include<unistd.h>
#include<string.h>
#include<sys/stat.h>
#include<stdlib.h>
#include<stdio.h>
char *directs[20],*files[20];
int i=0 ;
int j=0;
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
    DIR *dp = opendir(dir);
    int nDirs,nFiles;
    nDirs=0;nFiles=0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath = malloc(strlen(dir) + strlen(entry->d_name) + 2);

            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);

                if (lstat(filepath, &statBuf) != 0) {
                }

                if (S_ISDIR(statBuf.st_mode)) {
                nDirs=count_dirs(dir);
                 nFiles=count_files(dir);            
                printf("The no of subdirectories in %s is %d \n",dir,nDirs);
                printf("The no of files in %s is %d \n",dir,nFiles);
            
                    printdir(filepath);
                } else {
                }

                free(filepath);
            }
        }

        closedir(dp);
    } else {
        fprintf(stderr, "Error, cannot open directory %s\n", dir);
    }

}                //printdir

int count_dirs(char *dir)
{
    DIR *dp = opendir(dir);
    int nD;
    nD=0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath = malloc(strlen(dir) + strlen(entry->d_name) + 2);

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
    nF=0;
    if (dp) {
        struct dirent *entry = 0;
        struct stat statBuf;

        while ((entry = readdir(dp)) != 0) {
            if (strcmp(entry->d_name, ".") == 0 || strcmp(entry->d_name, "..") == 0) {
                continue;
            }

            char *filepath = malloc(strlen(dir) + strlen(entry->d_name) + 2);

            if (filepath) {
                sprintf(filepath, "%s/%s", dir, entry->d_name);

                if (lstat(filepath, &statBuf) != 0) {
                    fprintf(stderr, "File Not found? %s\n",filepath);
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

```
Currently I was not getting the logic so it is only upto here.
What I see is when you compile and run the above code then the output you get is twice.I am trying to figure out what is wrong.
In the mean time if you can suggest some idea as how to deal with the file system I gave you above.

---

### Post by Arndt on 2010-12-25
> **jamesbon said:**
> suppose directory bond0 contains
bond1, di2, bond3, bond4, bond5 and my_file1, my_file2, my_file3, my_file4, my_file5, my_file6
and
bond1 contains bond6 my_file7 my_file8 my_file9 my_file10
program should output -
bond3, bond4, bond5, my_file4, my_file5, my_file6, bond6, my_file8, my_file9, my_file10


I'm afraid I don't understand what you want to do. I don't see any system in the above.

---

### Post by jamesbon on 2010-12-25
> **Arndt said:**
> I'm afraid I don't understand what you want to do. I don't see any system in the above.
This is a simple programming puzzle.I am trying to solve.

---

