---
title: "Help with fork()"
date: 2010-05-26
forum: Programming Talk
---

### Post by MrDiaz on 2010-05-26
Hi everyone,

I'm trying to accomplish the following; I need to create 2 subprocesses and each subprocess should create a process of their own.

Should look like this:
> I'm child xxxx parent xxxx
I'm the subchild xxxx parent xxxx
I'm the second child xxxx parent xxxx
I'm the second subchild xxxx parent xxxx

So far I have this:

```
#include <stdio.h>
#include <unistd.h>

int main(void) {
	int pid;
	pid = fork();
	if (pid == 0) { // Child process
		printf("I'm the child %d parent %d\n", getpid(), getppid());
		pid = fork();
		if (pid == 0) { // Subchild process
			printf("I'm the subchild %d parent %d\n", getpid(), getppid());
		}
	}
	wait();
	return 0;
}
```

So far I've only been able to create one child from a process, I need to create two childs and two subchilds. The logic is below, hope it makes sense

                     PARENT PROCESS
   CHILD PROCESS                      CHILD PROCESS
SUBCHILD OF 1ST CHILD             SUBCHILD OF SECOND CHILD

---

### Post by gmargo on 2010-05-26
> **MrDiaz said:**
> So far I've only been able to create one child from a process, I need to create two childs and two subchilds.

I don't see what your question is. You created one child and one grandchild.  Now do it again.

---

### Post by johnl on 2010-05-26
Untested.  The break is probably important (see if you can figure out why :) )
```

#include <stdio.h>
#include <unistd.h>

int main(void) {
    int pid[COLOR="Red"]**, i**[/COLOR];
    pid = fork();
    
    if (pid == 0) { // Child process
        printf("I'm the child %d parent %d\n", getpid(), getppid());
        [COLOR="Red"]**for(i = 0; i < 2; ++i) {**[/COLOR]
            pid = fork();
            if (pid == 0) { // Subchild process
                    printf("I'm the subchild %d parent %d\n", getpid(), getppid());
                    **[COLOR="Red"]break;[/COLOR]**
            }
        [COLOR="Red"]**}**[/COLOR]
    }
    wait();
    return 0;
}
```

---

### Post by MrDiaz on 2010-05-29
That's an interesting way of doing it. Anyway I did it like this

```

#include <stdio.h>

int main(void) {

	int pID;

	pID = fork();
	if (pID == 0) { // First Child Process
		printf("I am the child %d parent %d\n", getpid(), getppid());
		
		pID = fork();
		if (pID == 0)
			printf("I am the subchild %d parent %d\n", getpid(), getppid());
	}
	else {
		pID = fork();
		if (pID == 0) { // Second Child Process
			printf("I am the second child %d parent %d\n", getpid(), getppid());
		pID = fork();
		if(pID == 0)
			printf("I am the second subchild %d parent %d\n", getpid(), getppid());
		}
	}	
	return 0;
}

```

---

