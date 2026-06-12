---
title: "custom ls function, where to place for global use"
date: 2008-05-12
forum: Programming Talk
---

### Post by enixexpo on 2008-05-12
I'm fairly new to unix and was wondering where do I put the executable file for my custom program so it can be used globally (in any directory)?

*The custom ls function is from the book: Advanced Programming in the Unix Environment.

---

### Post by #Reistlehr- on 2008-05-12
move the file to either /sbin/ or /usr/bin. you can always add an alias if you use bash, to .bashrc 
```
alias ls=/path/to/file

```

---

### Post by LaRoza on 2008-05-12
> **#Reistlehr- said:**
> move the file to either /sbin/ or /usr/bin. you can always add an alias if you use bash, to .bashrc 
```
alias ls=/path/to/file

```

No, it should go in /usr/local.

"ls" is already a program, and a local implementation should be kept separate. /sbin/ is for programs that only root can run, why would a file listing program need to go there?

---

### Post by enixexpo on 2008-05-12
Thanks for the help.

I copied my ls file (name myls) to /usr/bin. Should it go to /usr/local instead?

What's the difference?

Also, I'm not familiar with creating aliases. I don't want to replace the default ls. I just created it for an example program as well as to figure out where to store my program if I wanted to use it globally.

---

### Post by LaRoza on 2008-05-12
> **enixexpo said:**
> Thanks for the help.

I copied my ls file (name myls) to /usr/bin. Should it go to /usr/local instead?

What's the difference?

Also, I'm not familiar with creating aliases. I don't want to replace the default ls. I just created it for an example program as well as to figure out where to store my program if I wanted to use it globally.

It has to be in your $PATH. $PATH can be set in your ~/.bashrc

If you want, you can have a local directory (not $HOME, but it can be in there) for your programs and add that to $PATH.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by enixexpo on 2008-05-12
> **LaRoza said:**
> It has to be in your $PATH. $PATH can be set in your ~/.bashrc

If you want, you can have a local directory (not $HOME, but it can be in there) for your programs and add that to $PATH.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Thanks for the clarification and the link.

I'll try it out.

---

