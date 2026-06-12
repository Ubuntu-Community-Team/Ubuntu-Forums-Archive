---
title: "Using Pipes to see read and write to standard I/O of child processes"
date: 2007-12-28
forum: Programming Talk
---

### Post by donatell0 on 2007-12-28
I want to be able to both these things simultaneously. I tried it by using two pipes and using one as the input to the child process (the parent writes to this) and the other as the output collecting pipe from the child (the parent reads from this). I have no idea why, but it does not work. After the parent writes some input to the child process, the two processes simply block. Neither outputs anything. Could someone explain why this happens? Or atleast suggest a better way to try this?

i thought it was something to with buffers sizes as implemented by the kernel for the pipes, and I tried fflush()ing wherever possible. Still there was no use.

---

### Post by jaspreet on 2007-12-28
> **donatell0 said:**
> I want to be able to both these things simultaneously. I tried it by using two pipes and using one as the input to the child process (the parent writes to this) and the other as the output collecting pipe from the child (the parent reads from this). I have no idea why, but it does not work. After the parent writes some input to the child process, the two processes simply block. Neither outputs anything. Could someone explain why this happens? Or atleast suggest a better way to try this?

i thought it was something to with buffers sizes as implemented by the kernel for the pipes, and I tried fflush()ing wherever possible. Still there was no use.

where is your code??

---

### Post by donatell0 on 2007-12-29
:) 
Ok, here is the code.

Filename is: "parent.c"

```
#include <stdio.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main() {
	int fds[2],Fds[2];
	pid_t pid;
	pipe(fds); pipe(Fds);
	pid = fork();
	if( pid == (pid_t) 0) {
		printf("child\n");
		//bind to stdin of child
		close(fds[1]);
		dup2(fds[0], STDIN_FILENO);
		//bind to stdout of child
		close(Fds[0]);
		dup2(Fds[1], STDOUT_FILENO);
		execl("./tp","./tp", 0);
	}
	else {
		printf("parent\n");
		close(fds[0]);
		close(Fds[1]);
		FILE *fout = fdopen(fds[1],"w");
		FILE *fin  = fdopen(Fds[0],"r");
		int p=0,i;
                //read/write in lockstep with child process
		for(i=5;i>=0;i--) {
			fprintf(fout,"%d ",i);
			printf("got here\n");
			fscanf(fin,"%d", &p);
			printf("Read: %d\n",p);
		}
	}
	return 0;
}

```

The child program simply reads a number x and outputs (x+1) until it reads a 0. There are also some output statements. Here is the child program:

Filename: "tp.c"

```
#include <stdio.h>

FILE *fp;

void logit(char s[]) {
	fprintf(fp,"%s ",s);
}

int main() {
	int a;
	fp=fopen("logfile","w");
	logit("started");
	while(scanf("%d",&a), a!=0) {
		logit("read");
		logit("printed out");
		printf("%d\n",a+1);
	}
	logit("going away");
	return 0;
}
```

---

