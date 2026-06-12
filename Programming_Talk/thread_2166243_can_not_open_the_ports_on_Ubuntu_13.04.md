---
title: "can not open the ports on Ubuntu 13.04"
date: 2013-08-08
forum: Programming Talk
---

### Post by nafise2 on 2013-08-08
Hello, I am so new on serial port programming.
My machine has Ubuntu 13.04, I am trying to open the "/dev/ttyS0" or "/dev/ttyS1" on that but I can not! and always the output is -1. What should I do? :(

---

### Post by ofnuts on 2013-08-08
When you don't get what you expect you should have a look at ***[FONT=courier new]errno[/FONT]***. That may tell you things :)

/dev/ttyS* aren't readable/writable by the general user... Your program may have to run with root privileges (or with an ID which is part of the "dialout" group)

---

