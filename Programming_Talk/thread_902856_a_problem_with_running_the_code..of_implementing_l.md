---
title: "a problem with running the code..of implementing ls using system calls.."
date: 2008-08-27
forum: Programming Talk
---

### Post by shredder12 on 2008-08-27
This is the code that i have written to implement ls using system calls..
```
#include<sys/types.h>
#include<dirent.h>
#include<unistd.h>
#include<iostream.h>
int main(int argc, char *argv[])
        {
                DIR* dirp;
                char* direc;
                dirent* d;
                getcwd(direc,100);
                if ((dirp=opendir(direc))!=NULL)
                {
                        while((d=readdir(dirp))!=NULL)
                        {
                                cout<<"pause";
                                cout<<d->d_name<<endl;
                        }
                }
                return 0;
        }

```
I compile it using the command....
g++ file.cpp -Wno-decrepated...
it gets compiled without any problems..but the problem that i m having is htat it doesn't output any results..
i.e. the result of opendir is NULL.
so it doesn't show any result..
but just switches to another prompt..
help me please..

---

### Post by crdlb on 2008-08-27
You are supposed to pass getcwd an array on the stack, not a pointer (particularly not one that is uninitialized). That's why it has a length parameter (it doesn't want to overflow the buffer). So direc should be: ```
char direc[100];
``` and you would call getcwd as you did.

You could also use get_current_dir_name, which is a GNU extension that will malloc the string (so you'd need to free it when you're done).

---

