---
title: "Bash debugger"
date: 2008-11-29
forum: Programming Talk
---

### Post by abcuser on 2008-11-29
Hi,
using Ubuntu 8.10 I wonder if there are some kind of bash debugger commands. I know I can write in first line of bash command the following switches:
```
#!/bin/bash -xv
```
-x is debug mode
-v is verbose (displays commands that are executed).

I would like to have some kind of pause and next functionality. How?

BTW, I know I can use [bashdb](http://www.linux.com/feature/153383), but this debugger is too geeky. I need something more simple.
Thanks,
Abcuser

---

### Post by reality1011 on 2008-11-29
I normally create a function and variable called debug:

> 
DEBUG = "true" 


debug(){
if [ $DEBUG = "true" ];
     echo "$1"
fi
}



Then just call this function throughout your script to debug things, all you would need to do is set DEBUG to anything and nothing will echo out

---

### Post by geirha on 2008-11-29
Copy and paste the lines to an interactive shell.

---

### Post by drl on 2008-11-30
Hi.

See [http://www.linux.com/feature/153383](http://www.linux.com/feature/153383) It has several examples on how to use bashdb.  Sometimes things look more difficult than they are... cheers, drl

---

### Post by caljohnsmith on 2008-11-30
One thing you can do is add:
```
#!/bin/bash
[COLOR="Blue"]set -x[/COLOR]
```
To the beginning of your script, and then when you execute the script, it displays each command as it is executed. For more info about it just type "help set" in the terminal.

---

