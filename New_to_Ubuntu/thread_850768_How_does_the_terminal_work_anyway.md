---
title: "How does the terminal work anyway?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-07-05
I started to wonder this tonight.  I've used the terminal to launch programs, compile a program, and install additional software from the internet (example, SDL).  How does the terminal know where to download from or compile stuff correctly?

---

### Post by overdrank on 2008-07-05
> **LinuxFox said:**
> I started to wonder this tonight.  I've used the terminal to launch programs, compile a program, and install additional software from the internet (example, SDL).  How does the terminal know where to download from or compile stuff correctly?

Hi and maybe this can help
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by bodhi.zazen on 2008-07-05
Well the terminal runs $BASH as a lot of what your are asking are called "environmental variables"

When you compile an application the programmer set a default, you can change that with the ./configure command

./configure --prefix=/new/location

:)

See also : 

    [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by LinuxFox on 2008-07-05
Thanks for the link overdrank.  I took a quick look through it and it answered my questions about where it downloads from.  Heh, I also learned about other commands and what they do. :D

bodhi.zazen, I didn't know you can change the default with the configure command.  Thanks for telling me that.

---

