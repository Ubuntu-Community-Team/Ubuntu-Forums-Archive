---
title: "Creating a personal shell"
date: 2008-11-17
forum: Programming Talk
---

### Post by 420shaggy on 2008-11-17
I am working on creating a personalized shell with some basic functionalities.  It is not meant to replace bash but merely something for me to tool around with.  One of the problems I am having is putting in a history function into it.  It is very basic but I can't seem to see where I am going wrong.  I attached what I have so far, and this is what I thought would be the right way of implementing the history:
```
	
if (strcmp("!!", *g_argv) == 0)
		execve(hist_cmd, hist_argv, hist_envp);	    

```

** !! = perform last command **

  Before that code is executed, the hist_* variables were set equal to the g_* variables in various locations.  No matter where I tried setting the hist_* variables however, upon typing '!!' in the shell it says "!! command not found."  

  What I am wondering is, am I going about doing this all wrong?  Do I have to fork upon a successful command and suspend the parent, then when I type '!!' bring the parent out of suspend?  Or is that excessive?

  Thanks for any input on the matter
    (btw I am new to fork and exec if you haven't guessed)

---

### Post by Reiger on 2008-11-18
I'm not too familiar with C or C++ to be of any down-to-earth help; but if you typea "!!" can't you make that trigger a mock arrow-up keypress?

Because the arrow-up keyn does the very same in bash as your "!!" command.

---

### Post by geirha on 2008-11-18
bash uses the readline library for this. Have you looked at that library?

---

