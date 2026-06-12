---
title: "[C] Use fork to start application (pid+2)?!"
date: 2010-08-08
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-08
I start an application by using fork() then start the application from the child. Problem is that the pid of the application is not the pid return by fork() but pid+2. I'm not sure but using pid+2 don't seem reliable. Is there a better way to start an application, this is a test for Process.c in the 'real' program wont I know what application that will be started.

Process.c
[PHP]
#include <stdlib.h>
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

#include "Process.h" //

int startProcess(const char *application){
	int pid;
	if((pid=fork())==-1){
		fprintf(stderr,"Fork error. Exiting.\n");
		exit(-1);
	}

	if(pid)
		return pid;
	else{
		system(application);
		exit(1);
	}
}
[/PHP]

Main.c[LEFT][/LEFT]
[PHP]
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <signal.h>

#include "Process.h"
int main(void){
	int pid = startProcess("gedit");
	printf("%d\n",pid);
	sleep(2);
	kill(pid,9); // kill forked process
	sleep(5);
	kill(pid+2,9); //kill gedit
	return 1;
}
[/PHP]

shell output
```

9815
[COLOR="Red"]Killed[/COLOR]

```

---

### Post by StephenF on 2010-08-08
Try using exec, not system. Using system will spawn a shell from which the application is launched.

---

### Post by SpinningAround on 2010-08-08
> **StephenF said:**
> Try using exec, not system. Using system will spawn a shell from which the application is launched.

Thanks execlp solved it

---

