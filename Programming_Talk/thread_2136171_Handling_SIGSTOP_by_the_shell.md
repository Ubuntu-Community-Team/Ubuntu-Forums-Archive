---
title: "Handling SIGSTOP by the shell"
date: 2013-04-16
forum: Programming Talk
---

### Post by tkks on 2013-04-16
Hi all,

I am trying to write a simple custom shell, and I need to be able to stop processes my shell runs by sending SIGSTOP to them when the user presses CTRL+Z.
But I see in the man pages that the SIGSTOP signal cannot be handled.
So how does the real shell does it? how-come when I press CTRL+Z in BASH, BASH does not stop? how does BASH route SIGSTOP to the process it is running?

Thanks a lot.

---

### Post by slickymaster on 2013-04-16
See this: [Job Control Signals]("https://www.gnu.org/software/libc/manual/html_node/Job-Control-Signals.html")

Also, [this explanation]("http://superuser.com/questions/485884/can-a-process-be-frozen-temporarily-in-linux").

---

### Post by tkks on 2013-04-16
ohhhh, I see. I confused SIGTSTP and SIGSTOP. D'OH!!!!


Thanks!

---

### Post by slickymaster on 2013-04-16
What matters is the fact you got your doubts clarified.


EDIT: And be very welcome to the forums.

---

### Post by tkks on 2013-04-17
Thanks!

---

