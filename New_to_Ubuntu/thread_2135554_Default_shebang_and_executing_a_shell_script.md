---
title: "Default shebang and executing a shell script"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by moraxu on 2013-04-14
Hi there.

I've read [on this website]("http://bash.cyberciti.biz/guide/Shebang") that:

> If  you do not specify an interpreter line, the default is usually the  /bin/sh. But, it is recommended that you set #!/bin/bash line.

And my first question is: Is  there a way to find out which shell is the default one in case of  shebang on Ubuntu? I suppose it's sh (which is linked to dash), but is there an official way to check it (and maybe change it as well)?

In Ubuntu, running a file with execute permission bit set opens a window with **Run in Terminal**, **Display**, **Cancel** and **Run** options available.

If the first one is chosen and no shebang is specified in the file, I suppose that the script will be executed by **sh->****dash** as the BASH variable is unset upon execution.

My second question is that why choosing the **Run** option produces no action? Nothing happens, regardless of whether I put the shebang line into the script or not...

---

### Post by Vaphell on 2013-04-14
does your script wait for input at the end? because terminal window closes as soon as script ends.

try this:
```
#!/bin/bash

echo this is my script
read -p "Press [ENTER] to continue "
```

running scripts from gui is lame either way ;)

---

### Post by moraxu on 2013-04-15
Yes, it does, but in case of the **Run** option still nothing happens.

---

### Post by schragge on 2013-04-15
The script prints a message on standard output which is console (terminal) by default. If you are not specifying **Run in terminal**  when running it from GUI, it will have neither terminal to write onto  nor one to read input from, so all input and output will be discarded.

---

