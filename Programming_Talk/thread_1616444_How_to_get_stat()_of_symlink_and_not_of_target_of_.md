---
title: "How to get stat() of symlink and not of target of symlink ?"
date: 2010-11-08
forum: Programming Talk
---

### Post by ronbarak on 2010-11-08
[FONT="Arial"]The below C program, on ubuntu 10.04, does not recognize symbolic links, but prints the status of the target of the link.
What should I change to get from stat() that the file is a symlink and not the status of the target of the symlink ?

Looking on google didn't give me any ideas, and other documentation I found doesn't help either.

Thanks,
Ron.
[/FONT]
[FONT="Courier New"]$ ls -lsa ./RCS_link

0 lrwxrwxrwx 1 ronbarak ronbarak 5 2010-11-08 15:47 ./RCS_link -> ./RCS

$ ./stat_ex ./RCS_link

argv[1]: ./RCS_link

directory

$ 
$ ls -lsa .bashrc

0 lrwxrwxrwx 1 ronbarak ronbarak 22 2010-11-08 14:40 .bashrc -> /home/ronbarak/.bashrc

$ ./stat_ex .bashrc

argv[1]: .bashrc

regular file

$ 

$ ls -lsa /proc/self/fd/0

0 lrwx------ 1 ronbarak ronbarak 64 2010-11-08 15:51 /proc/self/fd/0 -> /dev/pts/5

$ ./stat_ex /proc/self/fd/0

argv[1]: /proc/self/fd/0

character device

$ 


$ cat ./stat_ex.c 

[COLOR="Blue"]#include <sys/types.h>

#include <sys/stat.h>

#include <sys/dir.h>

#include <stdio.h>

#include <stdlib.h>

#include <unistd.h>

#include <string.h>

#include <errno.h>



main(int argc, char *argv[])

{

    struct stat sbuf;



    if (argc < 2) 

    {

        fprintf(stderr, "Usage: %s <pathname> [<pathname>]\n",

            argv[0]);

        exit(EXIT_FAILURE);

    }



    while (--argc)

    {

        printf("argv[%d]: %s\n", argc,argv[argc]);

        if (stat(argv[argc], &sbuf) == -1) 

        {

            perror("stat");

            exit(EXIT_SUCCESS);

        }

        switch (sbuf.st_mode & S_IFMT) 

        {

            case S_IFBLK:  printf("block device\n");

                break;

            case S_IFCHR:  printf("character device\n");

                break;

            case S_IFDIR:  printf("directory\n");

                break;

            case S_IFIFO:  printf("FIFO/pipe\n");

                break;

            case S_IFLNK:  printf("symlink\n");

                break;

            case S_IFREG:  printf("regular file\n");

                break;

            case S_IFSOCK: printf("socket\n");

                break;

            default:       printf("unknown?\n");

                break;

        }

    }

    exit(EXIT_SUCCESS);

}[/COLOR]



[/FONT]

---

### Post by dwhitney67 on 2010-11-08
Please edit your post so that the code appears in CODE tags; otherwise the proper formatting of the code is lost.

P.S.  Have you considered using lstat()?

Example:
```

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   const char* filename = (argc > 1 ? argv[1] : "Give Me a Filename!");

   struct stat buf;

   if (lstat(filename, &buf) == 0)
   {
      if (S_ISLNK(buf.st_mode))
      {
         printf("%s is a link.\n", filename);
      }
      else
      {
         printf("%s is some other entity.\n", filename);
      }
   }
   else
   {
      printf("%s\n", filename);
   }
   return 0;
}

```

---

