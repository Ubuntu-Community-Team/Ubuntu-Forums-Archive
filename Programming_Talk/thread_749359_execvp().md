---
title: "execvp()"
date: 2008-04-08
forum: Programming Talk
---

### Post by Xelinis on 2008-04-08
Hey guys, doing a command interpreter for Operating Systems 1 but I can't seem to get execvp to work.  

execvp( "ls", NULL );


The PATH variable checks out just fine.  Just what am I doing wrong here exactly?

---

### Post by WW on 2008-04-08
> **Xelinis said:**
> Hey guys, doing a command interpreter for Operating Systems 1 but I can't seem to get execvp to work.  

What have you tried?  What happened? What error messages did you get?

I just tried the simplest C code that I could think of that uses that command you showed, and it worked fine:
```

#include <unistd.h>

int main(int argc, char *argv[])
    {
    execvp("ls",NULL);
    return 0;
    }

```

---

### Post by Xelinis on 2008-04-08
Did you try it in C or C++?  I'm trying to use this in C.

---

### Post by escapee on 2008-04-08
Are you remembering to include the necessary header (unistd.h) like WW has?
And have you installed the build-essential package?

---

### Post by WW on 2008-04-08
C, with the gcc compiler.

---

### Post by Zugzwang on 2008-04-09
Xelinis, you didn't answer WW's question: What happened?

BTW, Xelinis, please try the following example:
[PHP]#include <unistd.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
    execvp("ls",NULL);
    printf("\nHello world\n");
    return 0;
}[/PHP]

This one works perfectly here. Note that it doesn't say "Hello World" when executing. But this is correct! Look at the [man page]("http://opengroup.org/onlinepubs/007908799/xsh/exec.html") of execvp to see why. Maybe this is not what you expected and you may want to use system() instead?

---

