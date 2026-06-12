---
title: "Makefile: compiling separate source file"
date: 2011-02-07
forum: Programming Talk
---

### Post by hsmak_linux on 2011-02-07
I'm taking a UNIX System Programming course. It's required to have some experience on how to write a Makefile and run the make command.
The book used in teaching this course is "Advanced Programming in the UNIX Environmentt 2 Edition"..

Currently I'm stuck with solving the following:
                     p { margin-bottom: 0.08in; }  
[LIST=1]
[*]
[LIST=1]
[*]Copy [[FONT=Courier New, monospace]http://www.apuebook.com/src.tar.gz[/FONT]]("http://www.apuebook.com/src.tar.gz") to your         homework directory [FONT=Courier New, monospace]~[/FONT]
[*]Unzip and then         untar it
[*]Go into directory         [FONT=Courier New, monospace]apue.2e[/FONT]
[*]Modify         platform-dependent makefile [FONT=Courier New, monospace]Make.defines.linux[/FONT]
[LIST]
[*]Change WKDIR to             your own (full path for [FONT=Courier New, monospace]apue.2e[/FONT])
[/LIST]
         
[*]Type [FONT=Courier New, monospace]make[/FONT]         to install the package
[*]Testing:
[LIST]
[*]Create a             subdirectory called [FONT=Courier New, monospace]test[/FONT]
[*]Go into the test
[*]Copy previous             makefile [FONT=Courier New, monospace]Make.defines.linux             [/FONT]over and rename it to [FONT=Courier New, monospace]Makefile[/FONT]
[*]Copy [FONT=Courier New, monospace]fig1.3[/FONT]             file (in [FONT=Courier New, monospace]apue.2e[/FONT]             directory) to here and rename it so that the extension name will             be [FONT=Courier New, monospace]“.c”[/FONT]
[*]**[COLOR=Red]Use the new             Makefile (but you don’t need to change the Makefile further; we             use the suffix rules here) to compile this new C program[/COLOR]** (check             texbbook page 5)
[*]Run the executable             file
[/LIST]
     
[/LIST]
 
[/LIST]
 
I found a Chinese [website]("http://translate.google.com/translate?hl=en&sl=zh-CN&tl=en&u=http%3A%2F%2Fhi.chinaunix.net%2F%3Fuid-14367145-action-viewspace-itemid-22373") illustrating how to compile a separate source file for the same files mentioned earlier. However, it didn't compile it using the Makefile..

I'm trying to figure out a way to compile that file using Makefile..
Does anyone have an idea about this??

Thanks..

---

### Post by dwhitney67 on 2011-02-07
Try
```

cd ~

wget http://www.apuebook.com/src.tar.gz

tar xzvf src.tar.gz

cd apue.2e

make WKDIR=~/apue.2e

mkdir test

cd test

cp ../Make.defines.linux Makefile

cp ../fig1.3 fig1.c

make WKDIR=~/apue.3e fig1

./fig1 $HOME/apue.3e/test   # or whatever directory you want

```

If you want to follow the instructions given for your homework assignment, then edit the Make.defines.linux so that WKDIR is set to $(HOME)/apue.3e.

Then when you perform each 'make', do not specify a value for WKDIR, since this would be redundant.

---

### Post by hsmak_linux on 2011-02-07
Thank you so much for your help. I think I misunderstood what Suffix Rule is!!
But I got it from the steps you wrote here..

I appreciate your help.
Thank you so much :)

> **dwhitney67 said:**
> Try
```

cd ~

wget http://www.apuebook.com/src.tar.gz

tar xzvf src.tar.gz

cd apue.2e

make WKDIR=~/apue.2e

mkdir test

cd test

cp ../Make.defines.linux Makefile

cp ../fig1.3 fig1.c

make WKDIR=~/apue.3e fig1

./fig1 $HOME/apue.3e/test   # or whatever directory you want

```If you want to follow the instructions given for your homework assignment, then edit the Make.defines.linux so that WKDIR is set to $(HOME)/apue.3e.

Then when you perform each 'make', do not specify a value for WKDIR, since this would be redundant.

---

