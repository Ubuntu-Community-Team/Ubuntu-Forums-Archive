---
title: "Doubt/problem using  stat()"
date: 2010-03-06
forum: Programming Talk
---

### Post by indarkness on 2010-03-06
Hi everybody!
I'm trying to make a function similar to "ls -l",but I have got a problem when I call my function,"Estadof" which tells me if a string is a directory or a file(if it's made). To do that,I use stat().Well,the problem is,when I use the function scandir() ,after call it, i give my function the name of the directory o file,and here is a problem,because I don't know why stat() gives an error.
 
What am I doing wrong?
 
Thanks!!
 
```

#include <stdio.h>
#include <sys/stat.h>
#include <sys/types.h>
#include <sys/dir.h>
#include <fcntl.h>
#include <errno.h>
#include <stdlib.h>
#include <string.h>
#include <dirent.h>
 
int Estadof(char *f)
{
int n;
struct stat st;
 
n=0;
 
stat(f,&st);//informacion del fichero y la pasa a st que tiene la estructura
 
if(stat(f, &st)==0)
{
if(S_ISDIR(st.st_mode))
{
n=0;
printf("es un directorio \n");
}
if(S_ISREG(st.st_mode))
{
n=1;
printf("es un fichero regular \n");
}
}
else
{
perror("error en stat");//stat() ha fallado y ha devuelto -1
n=-1;
}
 
return n;
}
 
int Listdir(char *d)
{
int n=0;
int i;
int s=0;
 
struct dirent **archivos;
 
n=scandir(d,&archivos,0,alphasort);
 
if(n!=0)
{
for(i=0;i<n;i++)
{
if(strcmp(archivos[i]->d_name,".")!=0 && strcmp(archivos[i]->d_name,"..")!=0)
{
printf("%s \n",archivos[i]->d_name);
 
s=Estadof(archivos[i]->d_name);//HERE IS THE PROBLEM
//printf("%u \n",s);
}
 
 
}
}
else
perror("no hay directorios");
 
 
}
int main(int argc,char *argv[])
{
int i=0;
 
i=Listdir(argv[1]);
//Estadof(argv[1]);
 
return 0;
}
 

```

---

### Post by Lux Perpetua on 2010-03-06
Put your code in [code][**/code] tags, not [quote][**/quote] tags.

---

### Post by psusi on 2010-03-06
Some questions you should be asking yourself:

1)  What is the error stat() is returning?

2)  What is the file name you are passing stat() when it fails?

---

### Post by gmargo on 2010-03-06
I don't understand what problem you're having.  Your code works for me.  The only bug I see is how you check the return code for scandir - you should check for a -1 for error.  And no need to call stat twice. And Estadof returns 0 for directory or unknown.

Update: the code worked for me because I only tested it on the current directory.

---

### Post by indarkness on 2010-03-07
> **psusi said:**
> Some questions you should be asking yourself:
 
1) What is the error stat() is returning?
 

 
First of all,thanks for answering me!!
 
The error which stat() returns,it's the element that I give the function,it is not a file or directory,and because that it returns this error
 
> **psusi said:**
> 
 
2) What is the file name you are passing stat() when it fails? 
 

 
Here it's the problem, because I think I passing stat() a correct name. And to check that I use 
```
 printf("%s \n",archivos[i]->d_name);
```
And I see that the name i give stat() are correct,I mean,they are the names of the files or directories.

---

### Post by indarkness on 2010-03-07
> **gmargo said:**
> I don't understand what problem you're having.  Your code works for me.  The only bug I see is how you check the return code for scandir - you should check for a -1 for error.  And no need to call stat twice. And Estadof returns 0 for directory or unknown.

Thanks for replying! REally does the programs work for you? Well, let me show what I do to check the program:

THe directory where I work
> 
javier@javier-desktop:~/LABSC$ ls -l
total 596
-rw-r--r-- 1 javier javier    354 2010-03-01 19:45 copy1.c
-rw-r--r-- 1 javier javier     19 2010-03-01 19:09 entrada
-rwxr-xr-x 1 javier javier   6917 2010-03-06 22:23 Estadof
-rwx------ 1 javier javier    681 2010-03-06 11:21 Estadof.c
-rwxr-xr-x 1 javier javier   7713 2010-03-06 22:25 Listdir
-rw-r--r-- 1 javier javier   1882 2010-03-06 22:25 Listdir.c
-rw-r--r-- 1 javier javier   1930 2010-03-06 22:23 Listdir.c~
-rw-r--r-- 1 javier javier     64 2010-03-01 19:55 ls1.c
-rw------- 1 javier javier 558646 2010-03-06 20:38 ProgUnix-Ficheros.pdf
drwxr-xr-x 3 javier javier   4096 2010-03-07 12:15 prueba
The directory with I want to check if my program works,it's called "prueba"
> 
javier@javier-desktop:~/LABSC$ ls -l prueba
total 8
-rw-r--r-- 1 javier javier    0 2010-03-06 20:52 archivo nuevo~
-rw-r--r-- 1 javier javier    7 2010-03-06 22:13 archivo nuevo.c
drwxr-xr-x 2 javier javier 4096 2010-03-06 11:53 carpeta sin título

Running my program and what it shows
> 
javier@javier-desktop:~/LABSC$ ./Listdir prueba
archivo nuevo.c 
error en stat: No such file or directory
archivo nuevo~ 
error en stat: No such file or directory
carpeta sin título 
error en stat: No such file or directory


---

### Post by dwhitney67 on 2010-03-07
indarkness

When passing a file (or directory) name to stat(), the name needs to include the full path that leads to the file (or directory) *if it is not in the current directory*.

By default, both scandir() and stat() only examine the _current_ directory.  If the file you want to examine is in a different directory, then you need to be explicit.

In your code, change it to do the following:
```

...

int Listdir(const char *dir)
{
   struct dirent** archivos;
 
   int n = scandir(dir, &archivos, 0, alphasort);
 
   if (n > 0)
   {
      for (int i = 0; i < n; ++i)
      {
         if (strcmp(archivos[i]->d_name, ".") != 0 &&
             strcmp(archivos[i]->d_name, "..") != 0)
         {
            char fullPath[1024] = {0};

            snprintf(fullPath, sizeof(fullPath) - 1, "%s/%s", dir, archivos[i]->d_name);

            printf("%s\n",fullPath);
 
            Estadof(fullPath);
         }
      }
   }
   else
   {
      perror("no hay directorios");
   }
}

...

```

P.S.  If you want to recursively delve into sub-directories, then you would be better served using opendir() and readdir(), versus using scandir(). (EDIT:  Actually, scandir() could be made to work).

---

### Post by psusi on 2010-03-07
> **indarkness said:**
> First of all,thanks for answering me!!
 
The error which stat() returns,it's the element that I give the function,it is not a file or directory,and because that it returns this error

I can't understand this sentence.  stat() returns an error code telling you WHY it failed.  Your code does not check that.  You should check that to get a better idea of what is going wrong.

---

### Post by indarkness on 2010-03-07
> **psusi said:**
> I can't understand this sentence.  stat() returns an error code telling you WHY it failed.  Your code does not check that.  You should check that to get a better idea of what is going wrong.
ok,I meant,I know what error is giving stat(),but I couldn't understand why it's giving it.Beacuse I think I pass a correct argument.

---

### Post by dwhitney67 on 2010-03-07
> **indarkness said:**
> ... Beacuse I think I pass a correct argument.

You're not passing the correct argument; please read my earlier post.

---

### Post by indarkness on 2010-03-07
> **dwhitney67 said:**
> indarkness

When passing a file (or directory) name to stat(), the name needs to include the full path that leads to the file (or directory) *if it is not in the current directory*.

By default, both scandir() and stat() only examine the _current_ directory.  If the file you want to examine is in a different directory, then you need to be explicit.

In your code, change it to do the following:
```

...

int Listdir(const char *dir)
{
   struct dirent** archivos;
 
   int n = scandir(dir, &archivos, 0, alphasort);
 
   if (n > 0)
   {
      for (int i = 0; i < n; ++i)
      {
         if (strcmp(archivos[i]->d_name, ".") != 0 &&
             strcmp(archivos[i]->d_name, "..") != 0)
         {
            char fullPath[1024] = {0};

            snprintf(fullPath, sizeof(fullPath) - 1, "%s/%s", dir, archivos[i]->d_name);

            printf("%s\n",fullPath);
 
            Estadof(fullPath);
         }
      }
   }
   else
   {
      perror("no hay directorios");
   }
}

...

```P.S.  If you want to recursively delve into sub-directories, then you would be better served using opendir() and readdir(), versus using scandir(). (EDIT:  Actually, scandir() could be made to work).

Thank yo very much! So my problem was,I was trying to examine other directory,not the current,wasn't I?
Watching the directories I replied to [B]gmargo,how should I invoke the function to it works correctly?


EDIT:[/B] I read your post,but I forgot to send the reply.

---

### Post by indarkness on 2010-03-07
> **dwhitney67 said:**
> 
P.S.  **If you want to recursively delve into sub-directories**, then you would be better served using opendir() and readdir(), versus using scandir(). (EDIT:  Actually, scandir() could be made to work).
wow how do you know my next step is that?

---

### Post by psusi on 2010-03-07
> **indarkness said:**
> ok,I meant,I know what error is giving stat(),but I couldn't understand why it's giving it.Beacuse I think I pass a correct argument.

You never said what the error code is and the code you posted does not check it.

---

### Post by indarkness on 2010-03-07
> **psusi said:**
> You never said what the error code is and the code you posted does not check it.
Sorry for my bad explanation:icon_frown:

---

### Post by indarkness on 2010-03-10
> **dwhitney67 said:**
> P.S.  If you want to recursively delve into sub-directories, then you would be better served using opendir() and readdir(), versus using scandir(). (EDIT:  Actually, scandir() could be made to work).

How could I o it recursively?? I'v tried whit oppendir an readdir, but I can't get it.

---

### Post by dwhitney67 on 2010-03-10
Something like:
```

void dirContents(const char* dirname)
{
   DIR* dir = opendir(dirname);

   if (dir)
   {
      struct dirent* entry = 0;

      while ((entry = readdir(dir)) != 0)
      {
         if (strcmp(entry->d_name, ".") == 0 ||
             strcmp(entry->d_name, "..") == 0))
         {
            /* skips the '.' and '..' dirs
            continue;
         }

         if (entry->d_type == DT_DIR)
         {
            /* found a directory; need to do something 'special'

            /* alloc space for the dirname, a slash char, the entry name, and a null-char */
            char* newdir = malloc(strlen(dirname) + 1 + strlen(entry->d_name) + 1);

            /* build full path for the new entry found */
            sprintf(newdir, "%s/%s", dirname, entry->d_name);

            /* recursively call dirContents() with the new path
            dirContents(newdir);

            /* if here, clean up */
            free(newdir);
         }
         else
         {
            switch (entry->d_type)
            {
               case DT_REG:
                   printf("%s: regular file\n", entry->d_name);
                   break;

               /* cases for other DT types */

               case DT_UNKNOWN:
               default:
                  printf("%s: unknown type\n", entry->d_name);
                  break;
            }
         }
      }
   }
}

```

---

