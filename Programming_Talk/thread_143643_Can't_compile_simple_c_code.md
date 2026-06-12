---
title: "Can't compile simple c code"
date: 2006-03-12
forum: Programming Talk
---

### Post by dave_567 on 2006-03-12
I've executed "sudo apt-get install build-essential" and tried a simple c program.  I can get an a.out file.  I looked and it seems to be executable, but I can't run it.  Any ideas out there?  :confused: 
 

Me@ubuntu:~$ ls
Desktop  Documents  hello.c  Images  Internet Files  School
me@ubuntu:~$ cat hello.c
#include<stdio.h>

main()
{
  printf("\nHello World\n\n");
}
me@ubuntu:~$ gcc hello.c
me@ubuntu:~$ ls
a.out  Desktop  Documents  hello.c  Images  Internet Files  School
me@ubuntu:~$ a.out
bash: a.out: command not found
me@ubuntu:~$

---

### Post by Sutekh on 2006-03-12
Try
```
./a.out
```
if its not executable use
```
chmod +x a.out
```

---

### Post by gord on 2006-03-13
without the "./", the console will look in your binary path (ie: /usr/bin /usr/local/bin and the lot), not in your current directory

---

### Post by dave_567 on 2006-03-13
the ./ works.  The program executes now.  \\:D/ \\:D/ 

I guess that It would be better if I append my path to include this option perminently.  I'm weak on bash shell scripting.  any advice?

Also I'm using vi as the text editor.  What else is out there?  Something that is a bit more user friendly?

---

### Post by Sutekh on 2006-03-13
[QUOTE=dave_567]the ./ works.  The program executes now.  \\:D/ \\:D/ 

I guess that It would be better if I append my path to include this option perminently.  I'm weak on bash shell scripting.  any advice?[/QUOTE]Glad its working.

Try this to add a folder to your $PATH
```

nano ~/.bashrc
```
Then add these two lines to it
```

PATH=$PATH:/<your>/<path>/
export PATH

```
Changing /<your>/<path>/ to whatever is appropriate for you.

[QUOTE=dave_567]
Also I'm using vi as the text editor.  What else is out there?  Something that is a bit more user friendly?[/QUOTE]You'll get props for using vi though!  Try pico, nano for editing from the command line (no desktop environment running) and gedit for a more graphical setup.

---

### Post by toojays on 2006-03-13
And if you want to learn something useful, get to know [the one true editor](http://www.gnu.org/software/emacs).

---

### Post by Sutekh on 2006-03-13
How silly of me!  How could I forget that!

---

### Post by dave_567 on 2006-03-13
Got it all working.  Took a few minutes with nano to figure out how to save the file.  but the format is simple and works well.  I've never used emacs.  I'll give it a look also.

Thanks for the help.

---

### Post by xenmax on 2006-03-20
And if you want to run a.out from any directory it is present in , you could include '.' to your path which is obviously the present directory.
PATH=$PATH:.
export PATH

---

