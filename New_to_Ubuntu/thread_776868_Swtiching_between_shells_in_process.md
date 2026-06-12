---
title: "Swtiching between shells in process"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by bluehue on 2008-05-01
Hello everyone,

I would like to know how to switch between shells which are currently-running process. For instance my current shell is bash:
```

spiral@spiral-desktop:~$ ps
  PID TTY          TIME CMD
 8247 pts/1    00:00:00 bash
 8264 pts/1    00:00:00 ps
spiral@spiral-desktop:~$ 

```
Now I switch to c-shell:
```

spiral@spiral-desktop:~$ csh
% ps
  PID TTY          TIME CMD
 8247 pts/1    00:00:00 bash
 8266 pts/1    00:00:00 csh
 8267 pts/1    00:00:00 ps
% 

```
Now my question is as follows: how do I switch back to bash without killing csh?

---

### Post by Monicker on 2008-05-01
You could use install and use screen.

[http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/")

---

### Post by bluehue on 2008-05-01
> **Monicker said:**
> You could use install and use screen.

[http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/")
Hey, thanks for the suggestion, but I was looking for a simpler solution which I figured out. It turns out that simply typing `exit` after switching to csh takes me back to bash. Previously while in csh I was typing `bash` to take me back to the previously shell, but that created several bash processes like so:
```

spiral@spiral-desktop:~$ ps
  PID TTY          TIME CMD
 8634 pts/1    00:00:00 bash
 8655 pts/1    00:00:00 ps
spiral@spiral-desktop:~$ csh
% ps
  PID TTY          TIME CMD
 8634 pts/1    00:00:00 bash
 8656 pts/1    00:00:00 csh
 8657 pts/1    00:00:00 ps
% bash
spiral@spiral-desktop:~$ ps
  PID TTY          TIME CMD
 8634 pts/1    00:00:00 bash
 8656 pts/1    00:00:00 csh
 8658 pts/1    00:00:00 bash
 8674 pts/1    00:00:00 ps
spiral@spiral-desktop:~$ 
```
And to fix this and go back to your original shell from the above running processes:
```

spiral@spiral-desktop:~$ exit
exit
% ps 
  PID TTY          TIME CMD
 8634 pts/1    00:00:00 bash
 8703 pts/1    00:00:00 csh
 8722 pts/1    00:00:00 ps
% exit
% exit
spiral@spiral-desktop:~$ ps
  PID TTY          TIME CMD
 8634 pts/1    00:00:00 bash
 8723 pts/1    00:00:00 ps
spiral@spiral-desktop:~$

```
Nothing to it ;)

---

