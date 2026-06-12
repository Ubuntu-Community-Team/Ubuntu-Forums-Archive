---
title: "forks and C - help !"
date: 2011-03-16
forum: Programming Talk
---

### Post by cap10Ibraim on 2011-03-16
```

#include <unistd.h>
#include <stdio.h>
int main(){
int x;
if( (x=fork())==-1 ) exit(1);
if( (x=fork())==-1 ) exit(2);
if( (x=fork())==-1 ) exit(3);
printf("\nI'm the process with id=%d and parent ID=%d\n",getpid(),getppid());
return 0;
}

```
why the execution didn't return and how to display the tree of the processes with ```
system("pstree") 
``` for one time

---

### Post by slavik on 2011-03-17
you do realise that you fork 3 times and then just exit ... right?

---

### Post by Arndt on 2011-03-17
> **cap10Ibraim said:**
> ```

#include <unistd.h>
#include <stdio.h>
int main(){
int x;
if( (x=fork())==-1 ) exit(1);
if( (x=fork())==-1 ) exit(2);
if( (x=fork())==-1 ) exit(3);
printf("\nI'm the process with id=%d and parent ID=%d\n",getpid(),getppid());
return 0;
}

```
why the execution didn't return and how to display the tree of the processes with ```
system("pstree") 
``` for one time

What do you mean by "didn't return"?

---

### Post by Portmanteaufu on 2011-03-17
The parent process needs to call wait(...) or waitpid(...) for each of the forked child processes. 

If the parent doesn't wait for the children to complete, it will exit before they get a chance to run. If the parent exits, any child processes die with it (unless you take special measures.)

---

### Post by Arndt on 2011-03-17
> **Portmanteaufu said:**
> The parent process needs to call wait(...) or waitpid(...) for each of the forked child processes. 

If the parent doesn't wait for the children to complete, it will exit before they get a chance to run. If the parent exits, any child processes die with it (unless you take special measures.)

Did you run the program?

---

### Post by cap10Ibraim on 2011-03-17
I need an example to show a tree of processes when calling n forks (2^n processes)
I've come up with this the program is called ex4 
```

#include <unistd.h>
#include <stdio.h>
int main(){
int x;
if( (x=fork())==-1 ) exit(1);
if( (x=fork())==-1 ) exit(2);
if( (x=fork())==-1 ) exit(3);
system("sleep 30");
return 0;
}

```
then ```
pstree -p 1906
```
showed 
```

bash(1906)&#9472;&#9472;&#9472;ex4(2024)&#9472;&#9516;&#9472;ex4(2025)&#9472;&#9516;&#9472;ex4(2027)&#9472;&#9516;&#9472;ex4(2037)&#9472;&#9472;&#9472;sh(2045)&#9472;&#9472;&#9472;sleep(2+
                       &#9474;           &#9474;           &#9492;&#9472;sh(2039)&#9472;&#9472;&#9472;sleep(2043)
                       &#9474;           &#9500;&#9472;ex4(2029)&#9472;&#9472;&#9472;sh(2035)&#9472;&#9472;&#9472;sleep(2040)
                       &#9474;           &#9492;&#9472;sh(2031)&#9472;&#9472;&#9472;sleep(2033)
                       &#9500;&#9472;ex4(2026)&#9472;&#9516;&#9472;ex4(2036)&#9472;&#9472;&#9472;sh(2044)&#9472;&#9472;&#9472;sleep(2046)
                       &#9474;           &#9492;&#9472;sh(2038)&#9472;&#9472;&#9472;sleep(2042)
                       &#9500;&#9472;ex4(2028)&#9472;&#9472;&#9472;sh(2034)&#9472;&#9472;&#9472;sleep(2041)
                       &#9492;&#9472;sh(2030)&#9472;&#9472;&#9472;sleep(2032)


```
is there a way to show the tree of ex4 only without the sleep ?

---

### Post by Arndt on 2011-03-17
> **cap10Ibraim said:**
> I need an example to show a tree of processes when calling n forks (2^n processes)
I've come up with this the program is called ex4 
```

#include <unistd.h>
#include <stdio.h>
int main(){
int x;
if( (x=fork())==-1 ) exit(1);
if( (x=fork())==-1 ) exit(2);
if( (x=fork())==-1 ) exit(3);
system("sleep 30");
return 0;
}

```
then ```
pstree -p 1906
```
showed 
```

bash(1906)&#9472;&#9472;&#9472;ex4(2024)&#9472;&#9516;&#9472;ex4(2025)&#9472;&#9516;&#9472;ex4(2027)&#9472;&#9516;&#9472;ex4(2037)&#9472;&#9472;&#9472;sh(2045)&#9472;&#9472;&#9472;sleep(2+
                       &#9474;           &#9474;           &#9492;&#9472;sh(2039)&#9472;&#9472;&#9472;sleep(2043)
                       &#9474;           &#9500;&#9472;ex4(2029)&#9472;&#9472;&#9472;sh(2035)&#9472;&#9472;&#9472;sleep(2040)
                       &#9474;           &#9492;&#9472;sh(2031)&#9472;&#9472;&#9472;sleep(2033)
                       &#9500;&#9472;ex4(2026)&#9472;&#9516;&#9472;ex4(2036)&#9472;&#9472;&#9472;sh(2044)&#9472;&#9472;&#9472;sleep(2046)
                       &#9474;           &#9492;&#9472;sh(2038)&#9472;&#9472;&#9472;sleep(2042)
                       &#9500;&#9472;ex4(2028)&#9472;&#9472;&#9472;sh(2034)&#9472;&#9472;&#9472;sleep(2041)
                       &#9492;&#9472;sh(2030)&#9472;&#9472;&#9472;sleep(2032)


```
is there a way to show the tree of ex4 only without the sleep ?

There's a library function 'sleep', too.

---

### Post by cap10Ibraim on 2011-03-17
> **Arndt said:**
> There's a library function 'sleep', too.
is there a way to call pstree from the program but for one time 
- just one process should call it so it can show once ?

---

### Post by Arndt on 2011-03-17
> **cap10Ibraim said:**
> is there a way to call pstree from the program but for one time 
- just one process should call it so it can show once ?

If you want to see the whole tree, all processes that were created, you need to ensure that one doesn't exit before another one is created, and the program is too simple now for that, without the sleep. With the sleep, you have the full picture.

What do you actually want to achieve?

---

### Post by cap10Ibraim on 2011-03-23
why printf("I'm the parent with pid=%d",pid); is not executed ? 
```

#include <unistd.h>
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>
int main(){
int x1,x2,x3,status;
if( (x1=fork())==0 ){
	sleep(10);
	exit(0);
}
if( (x2=fork())==0 ){
	sleep(10);
	exit(0);
}
if( (x3=fork())==0 ){
	sleep(5);
	exit(0);
}
int pid=getpid();
printf("I'm the parent with pid=%d",pid);
char *command="pstree -p ";
char command_long[20];
sprintf(command_long,"%s%d",command,pid);
system(command_long);
return 0;
}

```

---

### Post by Arndt on 2011-03-23
> **cap10Ibraim said:**
> why printf("I'm the parent with pid=%d",pid); is not executed ? 
```

#include <unistd.h>
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>
int main(){
int x1,x2,x3,status;
if( (x1=fork())==0 ){
	sleep(10);
	exit(0);
}
if( (x2=fork())==0 ){
	sleep(10);
	exit(0);
}
if( (x3=fork())==0 ){
	sleep(5);
	exit(0);
}
int pid=getpid();
printf("I'm the parent with pid=%d",pid);
char *command="pstree -p ";
char command_long[20];
sprintf(command_long,"%s%d",command,pid);
system(command_long);
return 0;
}

```

You may need to output a newline too, in order for the output to reach the terminal. Try "I'm the parent with pid=%d\n".

---

### Post by trent.josephsen on 2011-03-23
Oops, too slow

---

### Post by Portmanteaufu on 2011-03-24
> **Arndt said:**
> Did you run the program?

No, I didn't. I was commenting on how fork() works in Linux. If the OP wants to guarantee that the child processes get an opportunity to run, (s)he needs to use wait().

Causing the parent program to sleep for some time after forking will increase the odds the child programs complete, but it's not a certainty.

---

### Post by Arndt on 2011-03-25
> **Portmanteaufu said:**
> No, I didn't. I was commenting on how fork() works in Linux. If the OP wants to guarantee that the child processes get an opportunity to run, (s)he needs to use wait().

Causing the parent program to sleep for some time after forking will increase the odds the child programs complete, but it's not a certainty.

The reason I asked was that if you had, you would have noticed that what you said about "If the parent exits, any child processes die with it" is not true. The parentless processes get 1 as their parent pid and continue running.

---

### Post by Portmanteaufu on 2011-03-27
Huh! Welp, I learned something today.

I thought that what I was describing was the default behavior because shells send SIGHUP to their child processes when they die -- turns out you have to set that up with prctl().

Good work, Arndt.

---

