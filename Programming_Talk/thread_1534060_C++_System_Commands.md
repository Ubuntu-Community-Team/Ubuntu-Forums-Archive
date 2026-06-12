---
title: "C++ System Commands"
date: 2010-07-18
forum: Programming Talk
---

### Post by Goveynetcom on 2010-07-18
Hello all.
I recently got back into programming (I started but then gave up, and now that I have free time I got back into it). I am C++ programmer, and am still learning the ropes. I have a question, how do I get the system commands to work under Linux? I can't seem to get them to work. I want to be able to let the user clear the text so they can easily read the new output. Reading various things, on windows I should just to have to do this;
```

int main()
{
//code
system("CLS");
//code
}

```I read for Linux that I need to do this;
```

int main()
{
//code
system("clear");
//code
}

```But anytime I do that in my program, I just get an undefined error in g++. I'll assume the command should work but I am not using a correct library. Anyone want to help me out here?

---

### Post by Some Penguin on 2010-07-19
You're not including stdlib.h

That said, you shouldn't be using system() that way, since it's expensive (takes two processes -- shell and clear) and is not very robust.  Use something like ncurses instead.

---

### Post by Goveynetcom on 2010-07-19
> **Some Penguin said:**
> You're not including stdlib.h

That said, you shouldn't be using system() that way, since it's expensive (takes two processes -- shell and clear) and is not very robust.  Use something like ncurses instead.
Well, since I am starting out hopefully you can forgive me. I'll take a look at ncurses though, thanks.

---

### Post by dwhitney67 on 2010-07-19
<cstdlib>, not <stdlib.h>

---

### Post by nvteighen on 2010-07-19
> **Some Penguin said:**
> 
That said, you shouldn't be using system() that way, since it's expensive (takes two processes -- shell and clear) and is not very robust.  Use something like ncurses instead.

Let's generalize that to the following Law:

```

Whenever you feel the need to interact with some external application using system(), 

1. First research whether a library can do the same.

2. If there's none, use popen(). 

3. If popen() isn't possible, use system() or implement it yourself.

```

Use system() as a very last resort. It's better to have your program "inherit" the desired functionality from a library, so that it becomes "its own" and doesn't have to call another shell that you just don't control at all. popen() at least creates a new process to which you can feed input and from you can get output on demand... but not all programs use pipes.

---

