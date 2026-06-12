---
title: "Problem with concurrency on named pipes (threaded daemon)"
date: 2013-04-21
forum: Programming Talk
---

### Post by edu2004eu on 2013-04-21
Hey!

I'm having a little problem with concurrency on a threaded server using named pipes / FIFO. Here's my code:

```

#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
#include<sys/stat.h>
#include<sys/types.h>
#include<fcntl.h>

#define BUFF_READ 1024;

typedef struct t_arg{
	char *message;
	int line;
} thread_arg;

void *request_handler(void *t_arg);
char *fifo = "/home/ubuntu/work/my_fifo";
thread_arg arg;

int main(void){
	int i = mkfifo(fifo, 0666);
	printf("%d",i);
	char buff[1024];
	while(1){
		int srv_fifo = open(fifo, O_RDONLY);
		int a = read(srv_fifo, buff, 1024);
		pthread_t thread;
		arg.message = "Testing";
		arg.line = 2001;
		pthread_create(&thread, NULL, request_handler, &arg);
		pthread_detach(thread);
		memset(buff, 0, sizeof(buff));
		close(srv_fifo);
		usleep(10);
	}
}

void *request_handler(void *t_arg){
	thread_arg real_arg = *(thread_arg*)t_arg;
	FILE *out = fopen("/tmp/log", "a");
	fprintf(out, "what i got was: %s\n", real_arg.message);
	fclose(out);
}

```

So when I start the daemon, and execute the following command from another terminal (see below), the daemon writes 5 lines in the output file.

```

echo "test" > /home/ubuntu/work/my_fifo & echo "test" > /home/ubuntu/work/my_fifo & echo "test" > /home/ubuntu/work/my_fifo & echo "test" > /home/ubuntu/work/my_fifo & 

```

This should write 4 times, right? Anybody can tell me what problem I have in my code? Thanks in advance for any help.

Update: I've updated my code to log in the output file what it read from the FIFO, and the first 4 of the lines contain "what i got was: test" and the 5th contains "what i got was:", so there is one extra thread started, but I have no idea why.

---

### Post by MadCow108 on 2013-04-21
the code is full of race conditions, so what you get as a result is pretty much undefined.
you need to synchronize all global variables (or make them local) and make sure everything stays in scope appropriately.
also your read call will read as much as it can, it won't stop after one "test" input (again depending on the timing)

I also don't see why you are closing the fifo each time.

---

### Post by edu2004eu on 2013-04-21
I'm keeping my thread argument global and opening / closing the FIFO each time as per the answer I got on StackOverflow ([http://stackoverflow.com/a/16127448/898423]("http://stackoverflow.com/a/16127448/898423"))

Before I was opening the file outside the loop, and the read() operation kept reading and reading the same thing even when I wrote 1 line inside the FIFO. Moving the open / close inside the loop fixed this issue. I'll try to make the thread argument local and see what happens.

---

### Post by MadCow108 on 2013-04-21
I forgot about how fifos work, yeah closing it is probably right then. the read should also work then.
You may be better of using sockets if you want to serve multiple clients at the same time.

You still have a race condition on the buf variable.

---

### Post by edu2004eu on 2013-04-21
Right. I have no idea why I opted for pipes, I hate them. Will probably do as you suggested and switch over to sockets. Thanks very much.

---

