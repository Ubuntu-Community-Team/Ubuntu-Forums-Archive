---
title: "pipe in C++"
date: 2009-06-25
forum: Programming Talk
---

### Post by Mirge on 2009-06-25
```

/*
** pipe1.c -- a dumb pipe example
*/

#include <iostream>
#include <string>
#include <errno.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <cstdlib>

using namespace std;

int main()
{
    int pipe_fd[2]; // an array of 2 elements for pipe file descriptors.
    string buf = "test";
    
    if (pipe(pipe_fd) == -1) {
        perror("pipe error");
        return 1;
    }
    
    if(!fork()) {
        cout << "CHILD: writing to the pipe!" << endl;
        
        int count = 0;
        while(count < 5) {
            write(pipe_fd[1], buf.c_str(), buf.length());
            sleep(1);
            count++;
        }
        
        
        write(pipe_fd[1], buf.c_str(), buf.length());
        return 0;
    } else {
        cout << "PARENT: reading from pipe!" << endl;
        
        **char buffer[30];**
        
**        while(read(pipe_fd[0], buffer, buf.length())) {**
            cout << "PARENT: read: " << buf << endl;
        }
        wait(NULL);
    }
    
    return 0;    
}

```Couple questions if it's not too big a bother...

1.) Is there a more "C++"-style way of going about this? IE: char buffer[30]... I tried using a string, but it complained about void* in read()... so I had to switch to a char array.

2.) This works, but it doesn't work how I was trying to get it to work... it reads & reads (obviously).. but never STOPS reading. How can I make it continue to read & read UNTIL the child process is done?

Thanks folks!

---

### Post by PmDematagoda on 2009-06-26
I only know C very well, but there shouldn't be a problem in this case.

I think the problem is that you are using the return value of read() incorrectly, the read() man states:-
> On error, -1 is returned, and errno is set
       appropriately.  In this case it is left unspecified  whether  the  file
       position (if any) changes.
now if the pipe is a non-blocking one, then an error of EAGAIN is set when there is no data and -1 is returned.

---

### Post by Mirge on 2009-06-26
bump.. I basically just want to be able to read/write to an external process (ie: ssh). Wait for it to ask for password, send password, wait for success/fail... then quit. Would I even need to fork() for that? Starting to think I wouldn't need to.

---

### Post by monkeyking on 2009-06-26
If you just want to use ssh,
you should consider using expect.

---

### Post by Mirge on 2009-06-26
Well, I was just using ssh as an example, I want to learn how to read/write to external processes.

---

### Post by monkeyking on 2009-06-26
I haven't looked at your code to closely,
but it seems you are only using 2 filedesc.
one for sending a msg, and one for resc.

If you want 2way communication you need to have 4 fds.

one pipe have 2 ends, but direction is uniform.
[http://unixwiz.net/techtips/remap-pipe-fds.html](http://unixwiz.net/techtips/remap-pipe-fds.html)


good luck

---

### Post by Mirge on 2009-06-26
Thanks, I'll give that a read & try some more.

---

