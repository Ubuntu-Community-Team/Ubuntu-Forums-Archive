---
title: "C interprocess communication"
date: 2009-06-03
forum: Programming Talk
---

### Post by Mirge on 2009-06-03
Anybody know of a good guide that demonstrates the use of IPC with C?

Example, I use sshfs... and I want to be able to write a C program that waits for the "enter password" prompt, then sends the password to the process with a newline... basically "automatically" mounting a remote filesystem.

Thanks!

---

### Post by Volt9000 on 2009-06-03
Here are a couple of links I found on another forum. Not sure if this will accomplish what you want, but it's a start. :)

[http://linuxgazette.net/104/ramankutty.html](http://linuxgazette.net/104/ramankutty.html)
[http://linuxgazette.net/105/ramankutty.html](http://linuxgazette.net/105/ramankutty.html)

PS. Google is your friend.

---

### Post by Mirge on 2009-06-03
Heh, I've done a TON of searching before even posting. I'll give those a read as well. Beej's guide looks pretty promising.

---

### Post by johnl on 2009-06-03
If you don't actually need/want to write a program to do this, [expect](http://en.wikipedia.org/wiki/Expect) can do it for you.

---

### Post by Mirge on 2009-06-03
> **johnl said:**
> If you don't actually need/want to write a program to do this, [expect]("http://en.wikipedia.org/wiki/Expect") can do it for you.

Wow, that's really neat! Bookmarked that.

I also want to build this C app for practice & learning. I dabbled with C years ago, but I'm trying to refresh my memory now and progress. It's frustrating because a lot of my Google searches turn up with C++ references rather than C lol.

---

### Post by SledgeHammer_999 on 2009-06-03
Maybe you should give D-bus a try.
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

---

### Post by Mirge on 2009-06-03
> **SledgeHammer_999 said:**
> Maybe you should give D-bus a try.
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

Now that looks really cool too... reading about it. Thanks folks :). And if I come up with a solution I'll be sure to post it back here.. an example anyway haha.

---

### Post by ThinkBuntu on 2009-06-03
[deleted]

---

### Post by alternatealias on 2009-06-04
There's a book by W. Richard Stevens on the topic of IPC in C for Unix which is quite good.

[http://www.kohala.com/start/unpv22e/unpv22e.html](http://www.kohala.com/start/unpv22e/unpv22e.html)

His "Networking API's" book is also a "must have" for network programming on Unix systems.

I know the books are costly ($60 when I bought mine a number of years ago), but you will never regret buying them.

---

### Post by alternatealias on 2009-06-04
> **SledgeHammer_999 said:**
> Maybe you should give D-bus a try.
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

I don't think D-Bus will help him in this particular case since he's trying to communicate with an already-existing process (presumably he would like to do so without modifying the other process).

---

### Post by alternatealias on 2009-06-04
> **Mirge said:**
> Anybody know of a good guide that demonstrates the use of IPC with C?

Example, I use sshfs... and I want to be able to write a C program that waits for the "enter password" prompt, then sends the password to the process with a newline... basically "automatically" mounting a remote filesystem.

Thanks!

The following code is untested, but should be fairly close to correct:

The easiest way to do this is probably to use popen():

FILE *sshfs = popen ("sshfs -o password_stdin", "w");
int fd = fileno (sshfs);
struct pollfd fds[1];

fds[0].fd = fd;
fds[0].events = POLLOUT;
fds[0].revents = 0;

/* wait for the sshfs to become ready to accept the passwd on stdin */
poll (fds, 1, -1);

if (fds[0].revents & POLLOUT)
    fwrite ("MyP@$$w0rd\n", 1, 12, sshfs);

pclose (sshfs);


Now, granted, you should do proper error checking and you may want to put a timeout on the poll (-1 is infinite), but this general approach should work.

---

### Post by Mirge on 2009-06-04
> **alternatealias said:**
> There's a book by W. Richard Stevens on the topic of IPC in C for Unix which is quite good.

[http://www.kohala.com/start/unpv22e/unpv22e.html](http://www.kohala.com/start/unpv22e/unpv22e.html)

His "Networking API's" book is also a "must have" for network programming on Unix systems.

I know the books are costly ($60 when I bought mine a number of years ago), but you will never regret buying them.

Nice thanks, I'll definitely look into that.

I printed off a PDF version of:
[http://beej.us/guide/bgipc/](http://beej.us/guide/bgipc/)

And have been reading it. I've gone through most of it before, but this was several years ago, so it's all pretty "new" to me again.

---

### Post by Mirge on 2009-06-04
parent.c
```

#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>


int main(){

    pid_t pid;
    int rv;
    int    commpipe[2];        /* This holds the fd for the input & output of the pipe */

    /* Setup communication pipeline first */
    if(pipe(commpipe)){
        fprintf(stderr,"Pipe error!\n");
        exit(1);
    }

    /* Attempt to fork and check for errors */
    if( (pid=fork()) == -1){
        fprintf(stderr,"Fork error. Exiting.\n");  /* something went wrong */
        exit(1);        
    }

    if(pid){
        /* A positive (non-negative) PID indicates the parent process */
        dup2(commpipe[1],1);    /* Replace stdout with out side of the pipe */
        close(commpipe[0]);        /* Close unused side of pipe (in side) */
        setvbuf(stdout,(char*)NULL,_IONBF,0);    /* Set non-buffered output on stdout */
        sleep(2);
        printf("Hello\n");
        sleep(2);
        printf("Goodbye\n");
        sleep(2);
        printf("exit\n");
        wait(&rv);                /* Wait for child process to end */
        fprintf(stderr,"Child exited with a %d value\n",rv);
    }
    else{
        /* A zero PID indicates that this is the child process */
        dup2(commpipe[0],0);    /* Replace stdin with the in side of the pipe */
        close(commpipe[1]);        /* Close unused side of pipe (out side) */
        /* Replace the child fork with a new process */
        if(execl("child","child",NULL) == -1){
            fprintf(stderr,"execl Error!");
            exit(1);
        }
    }
    return 0;
}

```

child.c
```

#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
    char string[100];
    
    printf("Child Process\n");
    printf("-------------\n");
    do{
        printf("Enter Command: ");
        fflush(stdout);                /* Must flush to see command prompt */
        fgets(string, 100, stdin);
        printf("%s\n",string);        /* No flush necessary because new line flushes */
    }while(!strstr(string,"exit"));
    
    return 0;
}

```

Found this example at:
[http://www.gidforums.com/t-3369.html](http://www.gidforums.com/t-3369.html)

Just googled around some more and finally ran into that.

It does what I want it to, sort of. It'd be nice to be able to "wait" for specific text to appear before sending output to the external process. But it DOES send data to the external process. Not sure how it works, but at least I have a functional example now.. so I'm continue studying. Thought I'd share that while it was fresh on my mind.

---

### Post by Mirge on 2009-06-04
```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main(int argc, char** argv)
{
    int pipe_fd[2];
    char buf[31];
    pid_t pid;
    
    if(pipe(pipe_fd) == -1) {
        perror("Error pipe()'ing...");
        exit(1);
    }

    
    if( (pid = fork()) == -1 ) {
        perror("Error fork()'ing...");
        exit(1);
    }
    
    if(pid) {
        // Parent.
        // Read from pipe we made.
        // Remember, 1=write, 0=read.
        read(pipe_fd[0], buf, 30);
        printf("PARENT: read... %s\n", buf);
        
        wait(NULL);
    } else {
        // Child.
        // Write to the pipe we made, so the parent has something to read!
        // Again, 1=write, 0=read.
        write(pipe_fd[1], "Hello, parent??", 16);
        exit(0);
    }

    return 0;
}

```

Following Beej's IPC guide... threw that together (not optimal code).. works. Just trying to grasp IPC again. Throwing up samples as I find time to do 'em lol.

---

### Post by Mirge on 2009-06-04
Heh, I still can't wrap my mind around it... writing to another process. I get seg faults when I try, after execl() errors. Meh.

---

### Post by Mirge on 2009-06-04
Can someone point me in the direction of a good pipe() and fork() tutorial... maybe something more explanatory than Beej's guide? Or maybe try to explain it to me? Thanks in advance...

---

### Post by slavik on 2009-06-05
fork() is a really simple command what questions do you have about it?

---

### Post by Mirge on 2009-06-05
Yeah, I guess not really so much about fork(), but about pipe().

I understand what fork() is doing, but what I don't understand I guess is the pipe()'ing portion of this tidbit:

```

#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>


int main(){

    pid_t pid;
    int rv;
    int    commpipe[2];        /* This holds the fd for the input & output of the pipe */

    /* Setup communication pipeline first */
    if(pipe(commpipe)){
        fprintf(stderr,"Pipe error!\n");
        exit(1);
    }

    /* Attempt to fork and check for errors */
    if( (pid=fork()) == -1){
        fprintf(stderr,"Fork error. Exiting.\n");  /* something went wrong */
        exit(1);        
    }

    if(pid){
        /* A positive (non-negative) PID indicates the parent process */
[U][B]        dup2(commpipe[1],1);    /* Replace stdout with out side of the pipe */
        close(commpipe[0]);        /* Close unused side of pipe (in side) */
[/B][/U]        setvbuf(stdout,(char*)NULL,_IONBF,0);    /* Set non-buffered output on stdout */
        sleep(2);
        printf("Hello\n");
        sleep(2);
        printf("Goodbye\n");
        sleep(2);
        printf("exit\n");
        wait(&rv);                /* Wait for child process to end */
        fprintf(stderr,"Child exited with a %d value\n",rv);
    }
    else{
        /* A zero PID indicates that this is the child process */
[U][B]        dup2(commpipe[0],0);    /* Replace stdin with the in side of the pipe */
        close(commpipe[1]);        /* Close unused side of pipe (out side) */
[/B][/U]        /* Replace the child fork with a new process */
        if(execl("child","child",NULL) == -1){
            fprintf(stderr,"execl Error!");
            exit(1);
        }
    }
    return 0;
}

```

The parts I'm fuzzy on are the bold/underlined lines.

---

