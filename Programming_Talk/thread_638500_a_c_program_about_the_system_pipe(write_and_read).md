---
title: "a c program about the system pipe(write and read)"
date: 2007-12-12
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2007-12-12
```

#include <sys/types.h>
#include <sys/wait.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
int main()
{
        char buf[4][4]={"abcd","efgh","ijkl","mnop"};
        printf("%s\n",buf);
        int aa;
        char dstbuf[5];

        pid_t childpid = 0;
        int fd[2];
        int i;

        if (pipe(fd)  == -1)
        {
                perror("Failed to create pipe.\n");
        }

        for (i = 1; i < 4; i++)
        {
                if ( (childpid = fork()) <= 0 )
                        break;

        }

        if (childpid > 0)
        {
                for(i = 0; i < 4; i++)
                {
                        if((aa=write(fd[1],buf[i],strlen(buf[i]))) != 4)
                        printf("%d,%s\n",aa,buf[i]);
                                perror("Failed to write chars to pipe.\n");

                }
        }
        else if (childpid == 0)
        {

                //bzero(dstbuf,5);
                sleep(1);
                if(read(fd[0],dstbuf,4) != 4)
                       perror("Failed to read chars from pipe.\n");

                printf("---- i:%d process id:%d parent id:%d  buf=%s\n",i,getpid(),getppid(),dstbuf);
                return 0;
        }

        printf("i:%d process id:%d  buf=%s\n",i,getpid(),buf);

        //while(waitpid(-1,NULL,WNOHANG) != -1 || errno == EINTR);
        return 0;
}

```

The result is :
abcdefghijklmnop°	@
19,abcdefghijklmnop°	@
Failed to write chars to pipe.
: Success
15,efghijklmnop°	@
Failed to write chars to pipe.
: Illegal seek
11,ijklmnop°	@
Failed to write chars to pipe.
: Illegal seek
7,mnop°	@
Failed to write chars to pipe.
: Illegal seek
i:4 process id:4626  buf=abcdefghijklmnop°	@
butterfly@musician /home/programming/OperatingSystem $ ---- i:1 process id:4627 parent id:1  buf=abcd
---- i:2 process id:4628 parent id:1  buf=efgh
---- i:3 process id:4629 parent id:1  buf=ijkl


I don't know why the variable aa is not 4.What is the problem.Help,thank you!

---

### Post by geirha on 2007-12-12
> **LaoLiulaoliu said:**
> ```

        char buf[4][4]={"abcd","efgh","ijkl","mnop"};

```


Haven't looked through all the code yet, but this one struck me immediately. You're creating an array of 4 char arrays of size 4. A char array of size 4 may only contain 4 characters including the terminator character (\0). So you need to either change it to char buf[4][5] or remove one character in each string.

---

### Post by LaoLiulaoliu on 2007-12-12
I have changed my code in the red color,but there is still some problem in the result.

```

int main()
{
        char[COLOR="Red"] buf[4][5][/COLOR]={"abcd","efgh","ijkl","mnop"};
        printf("%s\n",buf);
        int aa;
        char dstbuf[5];

        pid_t childpid = 0;
        int fd[2];
        int i;

        if (pipe(fd)  == -1)
        {
                perror("Failed to create pipe.\n");
        }

        for (i = 1; i < 4; i++)
        {
                if ( (childpid = fork()) <= 0 )
                        break;

        }

        if (childpid > 0)
        {
                for(i = 0; i < 4; i++)
                {
[COLOR="Red"]                        if((aa=write(fd[1],buf[i],strlen(buf[i])+1)) != 5) {
                                        perror("Failed to write chars to pipe.\n");
                                }
                                        printf("%d,%s\n",aa,buf[i]);[/COLOR]

                }
        }
        else if (childpid == 0)
        {

                //bzero(dstbuf,5);
                sleep(1);
                if(read(fd[0],dstbuf,[COLOR="Red"]5) != 5)[/COLOR]
                       perror("Failed to read chars from pipe.\n");

                printf("---- i:%d process id:%d parent id:%d  buf=%s\n",i,getpid(),getppid(),dstbuf);
                return 0;
        }

        printf("i:%d process id:%d  buf=%s\n",i,getpid(),buf);

        //while(waitpid(-1,NULL,WNOHANG) != -1 || errno == EINTR);

        return 0;
}

```

The result is:
[COLOR="Red"]abcd[/COLOR]
5,abcd
5,efgh
5,ijkl
5,mnop
i:4 [COLOR="Red"]process id:4530[/COLOR]  buf=abcd
butterfly@musician /home/programming/OperatingSystem $ ---- i:1 process id:4531 [COLOR="Red"]parent id:1[/COLOR]  buf=abcd
---- i:2 process id:4532 [COLOR="Red"]parent id:1 [/COLOR] buf=efgh
---- i:3 process id:4533[COLOR="Red"] parent id:1 [/COLOR] buf=ijkl

1.why the first line is not "abcdefghijklmnop"?
2.why the parent id of them is not 4394,but 1?

---

### Post by the_unforgiven on 2007-12-13
> **LaoLiulaoliu said:**
> 1.why the first line is not "abcdefghijklmnop"?
Because printf("%s"..) stops looking at the string at the NULL terminator - that's how strings are defined in C.
What used to happen earlier is since you didn't have space for the NULL byte in each string, printf() used to consider the entire array as a single string.
> **LaoLiulaoliu said:**
> 2.why the parent id of them is not 4394,but 1?
Because your parent process exits immediately after it write()s buffers to the children and printf() ing the process ID and buf.
So, as per POSIX, the children then get inherited by the init process which has process ID 1. 

HTH ;)

---

### Post by LaoLiulaoliu on 2007-12-14
thanks a lot.:popcorn:

---

