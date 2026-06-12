---
title: "doubt in reading from stdout"
date: 2012-10-15
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-15
Hey,
I tried searching and this is what I have written from many sources put together.

```

#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>
#include <string.h>

#define LEN 512
int main()
{
        char buffer[LEN];
        int fd[2];
        pipe(fd);

        pid_t pid = fork();

        /***I understand that the child is writing***/
        if(pid == 0)
        {
                dup2(fd[1], STDOUT_FILENO);
                close(fd[0]);

                //execlp("ls", "ls", NULL);
                printf("\nHello world");
        }

        /***I understand that the parent is reading***/
        else
        {
                dup2(fd[0], STDIN_FILENO);
                close(fd[1]);

                while (fgets(buffer, LEN, stdin))
                {
                    printf("%s", buffer);
                }
                waitpid(pid, NULL, 0);
        }

        return 0;
}

```

_I tried reading the man pages for a)pipe, b)fork, c)dup/dup2 and d)waitpid. But I still have a couple of questions._

1.I understand that pipe(fd) creates an array of 2 fd's where fd[0] is used for reading and fd[1] for writing. **But in the code, where do we mention that it has to read from stdout? and not from some other file in the hard disk ?**

2.In dup2(fd[1], STDOUT_FILENO);, the oldfd is fd[1] and newfd is STDOUT_FILENO right ?(from the man pages). But I don't get this. What is STDOUT_FILENO ? It's not even declared. I just don't get this line, I have atleast 4-5 doubts in this line, but I'll wait for a reply so that I'll know what to ask.

3.```
while (fgets(buffer, LEN, stdin))
                {
                    printf("%s", buffer);
                }
```
You are reading in a loop and going on printing it ? Didn't understand.

4.What does watitpid do ? It waits until the state of the parent changes ? changes to ?

I'm sorry to be asking 4 doubts in around 10 lines of code. But this is my first try at IPC.

Thanks.
Please advise.

---

### Post by Bachstelze on 2012-10-15
You are trying to do a lot of new things at once. Before you try to use fork(), pipe(), dup2(), etc. in a single program, use them each in a separate program and experiment with them until you understand exactly what they do.

---

### Post by ofnuts on 2012-10-17
1) a pipe is a pipe and isn't associated to a specific hard disk file (this is the "|" you use to connect commands together). See it as some memory somewhere on which you can write using one handle and read using the other.

2) ```

find /usr/include -name "*.h" -exec grep -H "STDOUT_FILENO" {} \;
/usr/include/unistd.h:#define   STDOUT_FILENO   1       /* Standard output.  */

```
"unistd.h" is likely included directly or indirectly by "stdio.h"

3) it reads form the pipe (which has been copied to stdin) and echoes it to the stdout of the parent process. Not sure this always works, though, because it changes the stdin handle without telling the code that handles the buffered stdin. You can instead create an input stream from the pipe handle (fdopen()). Likewise the dup2() on stdout in the child makes me suspicious. That may be OK if the child exec's some other code though (it will create a new buffered stream with stdout).

4) waiting for the child to terminate.

---

