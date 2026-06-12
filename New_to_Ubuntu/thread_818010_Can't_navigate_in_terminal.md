---
title: "Can't navigate in terminal"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by thedon_1 on 2008-06-04
I am trying to navigate to a folder on my desktop called floola-linux but terminal does not let me go there. Or anywhere to be honest!

param@param-desktop:~$ is what shows up in terminal.

I type ls and it lists folders in my home directory. I type cd desktop and i get no such file or directory.

I have tried cd/desktop e.t.c and no such luck.

I'm probably missing something really simple, any ideas?


Thanks

---

### Post by sayakb on 2008-06-04
```
cd ~/Desktop/floola-linux
```D should be a block letter. (It is case sensitive)

The **~/** in the code can be replaced by **/home/username/**
Where username is your User name.

---

### Post by thedon_1 on 2008-06-04
perfect, just one more question, why do you put the ~ in there, what does it mean?

---

### Post by wdaniels on 2008-06-04
> **thedon_1 said:**
> perfect, just one more question, why do you put the ~ in there, what does it mean?

The tilde (~) is a shortcut meaning your home directory, it is equivalent to /home/<user>.

---

### Post by atomkarinca on 2008-06-04
It means your home directory. Instead of typing /home/yourusername you can type ~ and be done with it.

---

### Post by hyper_ch on 2008-06-04
well, it depends where your home folder is. Root for example has it's homefolder at /root so issuing cd ~ will make you go to /root if you're logged in as root.

---

### Post by sayakb on 2008-06-04
Read here about bash commands:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Keep bash tutorials handy. The CLI in linux is somewhat different from the ugly DOS/COMMAND. :)

---

