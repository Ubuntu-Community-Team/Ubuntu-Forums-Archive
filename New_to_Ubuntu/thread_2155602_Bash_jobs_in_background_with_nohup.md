---
title: "Bash jobs in background with nohup"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by oregonbob on 2013-06-18
I got started way back in the Unix bourne shell days. When I wanted to run a program in the background and have it continue to run even after I logged out I would use this command line in bourne shell:

**nohup myprogram &**

Then I could logout or run some other application and "myprogram" would continue to run.

Now that I have bash, when I try to do the above command line, it runs but as soon as I hit Enter it quits with "[1]+ Exit 1", myprogram stops.

How does bash handle this?

---

### Post by papibe on 2013-06-18
Hi oregonbob.

For a full interactive-like environment to run your script, I'd recommend the command 'screen'. Take a look at post #3 in this [thread]("http://ubuntuforums.org/showthread.php?t=1988379").

Let us know how it goes.
Regards.

---

### Post by HiImTye on 2013-06-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
screen and tmux will continue to run it if it hasn't ended, however, if it is reporting 'Exit' then that means it quit. does it continue to run if you run it in the shell normally?

---

