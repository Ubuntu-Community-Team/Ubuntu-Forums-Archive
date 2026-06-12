---
title: "system(&quot;&quot;) vs bash"
date: 2008-08-17
forum: Programming Talk
---

### Post by |{urse on 2008-08-17
hi there just wondering if anyone has a definite answer on this.
If I need to run a bunch (30 or so) shell commands, is it any less cpu intensive to invoke the commands from bash vs. c?

```
#include <iostream>
#include <stdio>    
#include <stdlib>

using namespace std;
void main()
{
char y;
printf("run top? press y or n");
cin >> y;
if(y==y);
{
system("top");
}
else
{
return 0;
}
}

```

From what i've read it's overkill but if i need to do system calls in the program isn't it better to call them this way rather that exec a bash script from the already running C prog? Or does it not matter at all?

---

### Post by jinksys on 2008-08-17
If the script/program's only job is to start 30 processes, then the difference will be neglegable.  The processes themselves will be the CPU hogs.

Also, the code you posted will launch exactly zero programs since it won't compile.

---

### Post by LaRoza on 2008-08-17
> **|{urse said:**
> hi there just wondering if anyone has a definite answer on this.
If I need to run a bunch (30 or so) shell commands, is it any less cpu intensive to invoke the commands from bash vs. c?

From what i've read it's overkill but if i need to do system calls in the program isn't it better to call them this way rather that exec a bash script from the already running C prog? Or does it not matter at all?

You'd be better of using a shell script for that.

---

### Post by |{urse on 2008-08-17
> **jinksys said:**
> If the script/program's only job is to start 30 processes, then the difference will be neglegable.  The processes themselves will be the CPU hogs.

Also, the code you posted will launch exactly zero programs since it won't compile.

It's just an example, ignore the typos. Maybe i wasn't clear it would be doing a lot more than system("") stuff. Is better to just have the program launch a script when it is necessary or list a buttload of system("").

---

### Post by jinksys on 2008-08-17
> **|{urse said:**
> It's just an example, ignore the typos. Maybe i wasn't clear it would be doing a lot more than system("") stuff. Is better to just have the program launch a script when it is necessary or list a buttload of system("").

If it is just going to launch a bunch of programs, use a bash script.  If only for the ease of future modifications.  If you need simple flow control, like IF THEN ELSE etc, I'd still use a bash script.  It's hard to say for sure unless you give a more detailed example of what you want to do.

---

### Post by |{urse on 2008-08-17
really its just a simple server side C prog i will run through reverse ssh to gather info and administrate a few linux boxes remotely. The host machine will usually be a linux box so i could do it in bash or w/e but in the odd chance that it's a win machine i need to work from i want it in C.

```
none yet.
just thinking this through.
```

---

### Post by kpatz on 2008-08-17
One system() call to call a bash script is better than 30 system() calls invoking the processes separately.

Why?

Because system() calls the shell to run the command.  So, 1 shell vs. 30 shells.

Of course, you would be even more efficient using fork()/exec() calls, bypassing the shell entirely, to launch the processes, but that's a discussion for a different thread.

---

### Post by jinksys on 2008-08-17
> **kpatz said:**
> One system() call to call a bash script is better than 30 system() calls invoking the processes separately.

Why?

Because system() calls the shell to run the command.  So, 1 shell vs. 30 shells.

Of course, you would be even more efficient using fork()/exec() calls, bypassing the shell entirely, to launch the processes, but that's a discussion for a different thread.

I was under the impression the comparison was between a bash script with all the processes listed and a C program with thirty system() calls.

---

### Post by kpatz on 2008-08-17
> **jinksys said:**
> I was under the impression the comparison was between a bash script with all the processes listed and a C program with thirty system() calls.Still applies.  One shell launching 30 processes vs. 30 shells (invoked by system() calls) launching 30 processes...

This is assuming the 30 processes are all binary executables and not bash scripts themselves.  If any of those processes are bash scripts, then shells would have to be spawned to run those as well.  If all 30 are bash scripts, then it's a wash.

---

### Post by |{urse on 2008-08-18
This is exactly what i figured so ill just write those calls in.

thx man

---

