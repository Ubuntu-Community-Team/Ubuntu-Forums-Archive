---
title: "A question about the use of read() in C"
date: 2009-01-30
forum: Programming Talk
---

### Post by PmDematagoda on 2009-01-30
Lately I've been taking a look at process IPC and started out by messing around with pipes, while I understand functions like pipe() and write() well enough, I don't seem to understand read() that well enough. For example:-
[PHP]#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>
#include<stdlib.h>
#include<ctype.h>

//int pipes[2];

int main(){
  int pipes[2];
  pid_t child;
  char temp_buffer[10];
  int filter_count;

  pipe(pipes);

  child = fork();

  if (child){
    close(pipes[0]);
    sleep(2);
    write(pipes[1],"Junk",strlen("Junk"));
    printf("\nParent:- \"Junk\" sent!\n");
    wait(0);
  }
  else{
    close(pipes[1]);
    while(!read(pipes[0],temp_buffer,strlen("Junk")))printf("Help!"); //sleep(1);
    for(filter_count = 0; filter_count < (strlen(temp_buffer)); filter_count++){
      if(!isalpha(temp_buffer[filter_count])) temp_buffer[filter_count] = '\0';
    }
    printf("\nChild:- \"%s\" received!\n",temp_buffer);
  }
  return 0;
}
[/PHP]
in the above code, the child is supposed to keep printing "Help!" for about 2 seconds until it receives the message from the parent, however on execution the child just waits two seconds until it receives the message and then skips the printfs completely. Which probably means that using read() on an empty pipe means that it waits until the pipe gets some message, is this what really happens?

Any light on this matter is appreciated:).

---

### Post by dwhitney67 on 2009-01-30
Unless you are using a non-blocking stream, read() will block until it receives something... and in your code, it does and the return value from read() is not zero (it's the number of bytes received).

---

### Post by PmDematagoda on 2009-01-30
> **dwhitney67 said:**
> Unless you are using a non-blocking stream, read() will block until it receives something... and in your code, it does and the return value from read() is not zero (it's the number of bytes received).

I know about the return value of read() being the number of bytes read, but I thought that reading an empty pipe would return 0 as there is nothing to be read. About the non-blocking stream, can you give me an example of doing that?

Thanks.:)

---

### Post by dwhitney67 on 2009-01-30
I do not have much experience dealing with pipes, however from what I have been able to Google, the following should work:
```

#include <fcntl.h>

...

int pipes[2];

pipe(pipes);

fcntl(pipes[0], F_SETFD, O_NONBLOCK);

...

```
The key word in the paragraph above is "should"; for some reason, I cannot get the pipe to behave as desired; the read() still blocks.

---

### Post by mdurham on 2009-01-31
> **dwhitney67 said:**
> I do not have much experience dealing with pipes, however from what I have been able to Google, the following should work:
```

#include <fcntl.h>

...

int pipes[2];

pipe(pipes);

fcntl(pipes[0], F_SETFD, O_NONBLOCK);

...

```
The key word in the paragraph above is "should"; for some reason, I cannot get the pipe to behave as desired; the read() still blocks.

Change 'F_SETFD' to 'F_SETFL' and it will work ok.
Cheers, Mike

---

### Post by PmDematagoda on 2009-01-31
Thanks for the help guys, it works beautifully now.:) 

But I have one last problem, when I use read on the pipe now, I get a return value of -1 and not 0. Could I know why read is returning a value to represent an error instead of EOF(which I assume means an empty pipe)? 

Thanks! :)

Code:-
```
#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>
#include<stdlib.h>
#include<ctype.h>
#include<fcntl.h>

int main(){
  int pipes[2];
  pid_t child;
  char temp_buffer[10];
  int filter_count;

  pipe(pipes);
  child = fork();

  if (child){
    close(pipes[0]);
    sleep(2);
    write(pipes[1],"Junk",strlen("Junk"));
    printf("\nParent:- \"Junk\" sent!\n");
    wait(0);
  }
  else{
    close(pipes[1]);
    fcntl(pipes[0],F_SETFL, O_NONBLOCK);

    while(read(pipes[0],temp_buffer,strlen("Junk")) < 0 ) printf("Help!");

    for(filter_count = 0; filter_count < (strlen(temp_buffer)); filter_count++){
      if(!isalpha(temp_buffer[filter_count])) temp_buffer[filter_count] = '\0';
    }

    printf("\nChild:- \"%s\" received!\n",temp_buffer);
  }
  return 0;
}
```

---

### Post by jpkotta on 2009-01-31
It appears that that is an interrupted read, at least according to the man page.>        Other  errors  may  occur, depending on the object connected to fd.  POSIX allows a read() that is interrupted
       after reading some data to return -1 (with errno set to EINTR) or to return the number of bytes already  read.


I recommend using perror() for a better error message.

---

### Post by jpkotta on 2009-01-31
Try this:
```

    while(1) {
	err = read(pipes[PIPE_RD],temp_buffer,strlen("Junk"));
	if (err < 0) {
	    if (errno != EAGAIN) {
		perror("read error");
		return -1;
	    }
	} 
	else {
	    break;
	}
	sleep(1);
    }

```

I should mention that EAGAIN is defined in errno.h and I defined PIPE_RD myself because I hate numeric values that aren't really numbers.

---

### Post by PmDematagoda on 2009-02-01
> **jpkotta said:**
> It appears that that is an interrupted read, at least according to the man page.

I recommend using perror() for a better error message.
The output of the below program with perror() gives:-
> Program : Success

Parent:- "Junk" sent!

Program : Illegal seek
Program : Resource temporarily unavailable

Child:- "Junk" received!
This is really strange:confused:.

The program was edited to send two messages instead of one.

This program gives the error message:-
[PHP]#include<stdio.h>
#include<string.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>
#include<stdlib.h>
#include<ctype.h>
#include<fcntl.h>

int main(){
  int pipes[2];
  pid_t child;
  char temp_buffer[10];
  char buffer_2[10];
  int filter_count;

  pipe(pipes);
  child = fork();

  if (child){
    close(pipes[0]);
    write(pipes[1],"First",strlen("First"));
    sleep(2);
    write(pipes[1],"Junk",strlen("Junk"));
    printf("\nParent:- \"Junk\" sent!\n");
    wait(0);
  }
  else{
    close(pipes[1]);
    fcntl(pipes[0],F_SETFL, O_NONBLOCK);

    sleep(1);
    read(pipes[0],buffer_2,10);
    perror("Program ");
    sleep(2);

    read(pipes[0],temp_buffer,10);
    perror("\nProgram ");

    read(pipes[0],buffer_2,10);
    perror("Program ");
	  

    for(filter_count = 0; filter_count < (strlen(temp_buffer)); filter_count++){
      if(!isalpha(temp_buffer[filter_count])) temp_buffer[filter_count] = '\0';
    }

    printf("\nChild:- \"%s\" received!\n",temp_buffer);
  }
  return 0;
}[/PHP]

---

### Post by PmDematagoda on 2009-02-01
> **jpkotta said:**
> Try this:
```

    while(1) {
	err = read(pipes[PIPE_RD],temp_buffer,strlen("Junk"));
	if (err < 0) {
	    if (errno != EAGAIN) {
		perror("read error");
		return -1;
	    }
	} 
	else {
	    break;
	}
	sleep(1);
    }

```

I should mention that EAGAIN is defined in errno.h and I defined PIPE_RD myself because I hate numeric values that aren't really numbers.


Thanks for that, after reading the read() man page a little more, that is what was supposed to happen.

But I wonder about the "Illegal Seek" error.

---

