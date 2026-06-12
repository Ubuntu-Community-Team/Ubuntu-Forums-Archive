---
title: "exec() usage? what am I doing wrong?"
date: 2013-08-06
forum: Programming Talk
---

### Post by conradin on 2013-08-06
```

#include <sys/types.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <stdlib.h>
#include <unistd.h> //required by execl
#include <stdio.h>

int pid, ppid;

int main()
{
pid=getpid();
printf("PID of this process is: %x\n",pid);
	if (fork()==0){
		pid=getpid();
		ppid=getppid();
		printf("I'm in the Replica and my PID is: %x\n",pid);
		printf("... About to execute my Program, PID should be the same\n");
		printf("... PID of parent process is: %x\n",ppid);
		execl("./myprog", NULL);}
pid = waitpid ((pid_t)-1, NULL, WNOHANG);
return 0;
}


```
line  with: execl("./myprog", NULL);}
gets these warnings?
FEW.c:21:3: warning: null argument where non-null required (argument 2) [-Wnonnull]
FEW.c:21:3: warning: not enough variable arguments to fit a sentinel [-Wformat]

I have read the man page for execl But.. I dont know what to put in the place of null. I am not trying to pass arguments to myprog (located in the same directory).
what should I put in the place of NULL?  how do i fix these warnings?

---

### Post by conradin on 2013-08-06
Also, When i run this I see some threads with leters in them?
such as:

....
PID of this process is: 168b
I'm in the Replica and my PID is: 168c
....

Ive never seen a PID with a letter in it. is this a pruduct of bad coding? or a normal occurance?

---

### Post by spjackson on 2013-08-06
> **conradin said:**
> Also, When i run this I see some threads with leters in them?
such as:

....
PID of this process is: 168b
I'm in the Replica and my PID is: 168c
....

Ive never seen a PID with a letter in it. is this a pruduct of bad coding? or a normal occurance?

As per the man page, you want
```

    execl("./myprog", "./myprog", NULL);

```
The second argument is arg0.

When you pass %x to printf, you are asking for the PID it be displayed in hexadecimal - hence the letters.

---

### Post by Bachstelze on 2013-08-06
> **spjackson said:**
> As per the man page, you want
```

    execl("./myprog", "./myprog", NULL);

```

[font=monospace](char*)NULL[/font], please. :)

---

### Post by conradin on 2013-08-07
maybe my reading gland was ailing yesterday. 
Thank you both for the assistance

---

