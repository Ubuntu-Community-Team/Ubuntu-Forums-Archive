---
title: "C++ system() command"
date: 2009-06-13
forum: Programming Talk
---

### Post by froggyswamp on 2009-06-13
Folks,
from my little C++ app I'm trying to launch (say) "gedit /somedir/file.txt" and I use the system() call for that. Problem is, my app freezes until I close gedit.
Is there any simple way to launch a program with args without freezing my app?

PS: I don't need any interaction with the launched program from my app, just to launch it and forget about it.

---

### Post by dwhitney67 on 2009-06-13
Run the program (eg. gedit) in the background.  To do that, use something like:
```

#include <cstdlib>
int main()
{
  system("gedit text.txt &");   //   note the &
}

```

---

### Post by froggyswamp on 2009-06-13
So easy! Thanks a lot!! And it works!

PS: May I know where you found it out from (the ampersand)? I've googled and only found suggestions about using another process.

---

### Post by benj1 on 2009-06-13
its something used by the shell to run in the background, most reasonable bash guides will have something on it.

eg gedit foo.txt will lock up your terminal until you exit

gedit foo.txt & will allow you to carry on using that terminal.

---

### Post by abhilashm86 on 2009-06-13
> **dwhitney67 said:**
> Run the program (eg. gedit) in the background.  To do that, use something like:
```

#include <cstdlib>
int main()
{
  system("gedit text.txt &");   //   note the &
}

```

well i remember now linux concept, & means we are forcing our bash shell to run a foreground process in background(& symbol).............
its great thing to switch between background and foreground process...

---

### Post by soltanis on 2009-06-13
The more formal reason that your program locks up is because system() waits for the specified process to exit. To run programs, what it first does is fork(), then in the child process, runs execve(), replacing the process image with the process you specified. In the parent process, it wait()s for the child to finish, and collects the exit status.

Adding the & causes the shell that is executed in the child process to fork again, then run execve() again and actually execute your program. The parent process then returns immediately (and the child process is inherited by init).

---

### Post by froggyswamp on 2009-06-13
Thanks a lot for all your replies!

---

