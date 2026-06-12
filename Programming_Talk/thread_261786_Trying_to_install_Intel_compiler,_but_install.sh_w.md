---
title: "Trying to install Intel compiler, but install.sh won't run"
date: 2006-09-20
forum: Programming Talk
---

### Post by EmmDoubleEw on 2006-09-20
When I double clicked it from the browser it asked if I wanted to run it, run it from the terminal, etc... I choose to simply run it and nothing happens. So I went to the terminal and ran it from there and it says there is already an instance of the script is running. I go to the processes and the script is "sleeping", so I kill it. Then I try running it from the terminal again it still says the script is already running.

So I tried restarting and running it from the terminal in the first place, and the only thing it does is close the terminal.

Am I doing something wrong? Why doesn't anything happen?

Also, are there any better free alternatives to the Intel C++ compiler?

Thanks. :cool:

---

### Post by darrenm on 2006-09-20
Not sure about whether GCC is any better than the Intel compiler but if you finally kill the script then just run it with sh:

```
sh install.sh
```

---

### Post by po0f on 2006-09-20
Make sure that the script is executable, and try running head on the file to get the very top to make sure that it's trying to invoke a valid command.

---

### Post by EmmDoubleEw on 2006-09-20
> **darrenm said:**
> Not sure about whether GCC is any better than the Intel compiler but if you finally kill the script then just run it with sh:

```
sh install.sh
```



Thanks, that worked.

---

