---
title: "command line completion with environment variables."
date: 2013-05-28
forum: New to Ubuntu
---

### Post by jvsrvcs on 2013-05-28
Command line completion did not work when opening a terminal so I googled and figured that out (uncommenting lines in /etc/bash.bashrc.

it works when I start with a full path like / or relative path,

but when I type something like:

 $cd $HOME/D<tab>

I do not get command line completion when using environment variables.  How to fix this?

---

### Post by papibe on 2013-05-28
Hi jvsrvcs.

Unfortunately, bash completion does not work that way. Bash would have to evaluate variables as you type them instead of waiting for an enter.

If you are trying to get something else to work (writing an script for example), may be there's another way to accomplish what you want.

Let us know how it goes.
Regards.

---

### Post by aromo on 2013-05-28
> **jvsrvcs said:**
> 
but when I type something like:

 $cd $HOME/D<tab>

I do not get command line completion when using environment variables.  How to fix this?

For this particular scenario try:
```
$ cd ~/D<tab>
```

---

### Post by jvsrvcs on 2013-07-09
I am at a Terminal command prompt.  I type:   $cd $HOME/

and then hit  the tab key and instead of the directory contents being displayed, I get:
   $cd \$HOME/     <= it just inserted a \ in front of the $ 

now I have to backspace and erase that \ in front of the $, my command line completion is broken.  I have worked with Unix/Linux since the early 1920's and I have never seen this happen in all my years.  Who programmed that into the command line completion?  How do I find the person responsible?  How do I fix this?

---

### Post by dannyboy79 on 2013-07-09
why do you have the dollar signs? auto-completion works for names close to what you typed, so if you want to change directory to your /home/ folder you would type in
```
cd /home/
``` and then you would hit tab and it would show you all the contents of whats in your home.

---

### Post by ajgreeny on 2013-07-09
In fact just **cd** will take you back to your home folder from anywhere in the filesystem, unless you have run **sudo -i** or **sudo su** to get to a root prompt, when it will just take you back to **root@hostname** instead of **user@hostname**.

---

### Post by Bucky Ball on 2013-07-09
> **ajgreeny said:**
> ... unless you have run **sudo -i** or **sudo su** to get to a root prompt, when it will just take you back to **root@hostname** instead of **user@hostname**.

... in which case you will need to type 'exit' to become a normal user again.

```
cd /home
```

Will put you to the /home directory, if you aren't already in it.

```
dir /home
```

Will show its contents (or the tab, apparently, although that's a newie on me, thanks). I'm presuming you are following a guide to do something in a terminal, possibly to learn more?

---

### Post by dannyboy79 on 2013-07-09
oh, and it's impossible you were working on Unix or Linux in the 1920's since Unix wasn't around till 1969 and Linux in 1983 but anyway, hope we all answered your question

---

### Post by Zill on 2013-07-09
> **jvsrvcs said:**
> ...I have worked with Unix/Linux since the early 1920's and I have never seen this happen in all my years...
:confused:

---

### Post by Bucky Ball on 2013-07-09
> **jvsrvcs said:**
> I have worked with Unix/Linux since the early 1920's ... 

Time traveller? :-k ;)

---

### Post by ajgreeny on 2013-07-09
> **Bucky Ball said:**
> ... in which case you will need to type 'exit' to become a normal user again.That's why I have always used an alias in my home .bash_aiases file with q=exit, just for speed, and also in /etc/bash.bashrc for the same reason; one key press instead of four!

> ```
cd /home
```

Will put you to the /home directory, if you aren't already in it. but not in your own home, so not very useful?

> ```
dir /home
```

Will show its contents (or the tab, apparently, although that's a newie on me, thanks). I'm presuming you are following a guide to do something in a terminal, possibly to learn more?Yes I was trying to figure out "Why do this at all; what is it for.?"
It would be interesting to know.

---

### Post by papibe on 2013-07-09
**Threads merged**.

---

### Post by oldos2er on 2013-07-09
Hi jvsrvcs, we ask forum users not to create duplicate threads because 1) it dilutes community effort, and 2) it's confusing for those offering help as well as for those asking for help. It would've been acceptable for you to bump the original thread, we just ask that you do so not more than once every 24 hours. Thanks!

---

