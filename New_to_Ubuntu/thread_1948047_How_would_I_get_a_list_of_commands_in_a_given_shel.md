---
title: "How would I get a list of commands in a given shell?"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-27
How would I get a list of commands stored in my bash profile? I tried to invoke "curl" to download a PDF, but it failed. I suspect I just don't have that command. 

Are man and info pages built in association with the list of commands in a user-specific shell, or are they "generic" (meaning "do they comprehensively list what commands exist in shells as a whole"?). 

Thanks for all the help. This forum is the first one where I LOOK FORWARD to talking to someone, because I've learned so much already, and it's a consistently good experience.

---

### Post by sidzen on 2012-03-27
[SIZE=3]A good place to start understanding of what you ask -- [***here***]("http://ubuntu-tutorials.com/tag/shell/")[/SIZE]

---

### Post by idoitprone on 2012-03-27
> **jps2012 said:**
> How would I get a list of commands stored in my bash profile? I tried to invoke "curl" to download a PDF, but it failed. I suspect I just don't have that command. 

Are man and info pages built in association with the list of commands in a user-specific shell, or are they "generic" (meaning "do they comprehensively list what commands exist in shells as a whole"?). 

Thanks for all the help. This forum is the first one where I LOOK FORWARD to talking to someone, because I've learned so much already, and it's a consistently good experience.

the bash shell has an some built commands but they are not stored in bash profile. Bash profile is just a script to edit your environment such as adding color coding to grep or and extra formatting to ls.

Here examples and some of bash build it [http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html)

Lot of commands are just extended since they are not needed for the most basic functionality

The which command should tell you which command you are using

```
which ls
```

Most of the shell commands should be in /bin

```
ls /bin | more
```

If not 
/usr/bin

But /usr/bin should not have shell commands since they should mostly be gui programs

---

### Post by lykwydchykyn on 2012-03-27
A "command", apart from a small set built into the shell itself, is nothing more than a program that is invoked from a shell.  Asking "what commands are available" is really just another way of asking "what programs do I have installed". 

You can list them all by hitting "TAB" twice in the terminal, but there would be thousands of them listed even on a default system.

If you want to know if you have a command installed, just run it.  If it's not installed, you'll be told that it isn't, and what package it's available from (if it is).

---

### Post by audiomick on 2012-03-27
Further to the previous post: man pages are associated with the programs. Generally, when you install a program, the man page comes with it and can be opened with 
```
man <program name>
```

---

### Post by jps2012 on 2012-03-27
All good info. Thanks, everyone. Sizden, I subscribed to the RSS for Ubuntu tutorials. 

I found the curl command in my usr/bin directory. I ran it and it worked this time (no idea what I might have done wrong the first time around). But the results are questionable. I'm posting a thread for "can't find file after curl command invoked."

---

### Post by yetiman64 on 2012-03-27
> **jps2012 said:**
> ... I'm posting a thread for "can't find file after curl command invoked."
If you did not specify where to save the file, my first instinct would be to look directly in your home folder, it is often used as the default save location. If not there then I would look into /home/<user>/Dowloads or /tmp. Though I really suspect it will be in your home folder.

---

### Post by jps2012 on 2012-03-27
Thanks for the suggestion, yetiman. I've looked in the following folders and haven't found it: Desktop, Temp, Downloads and my home folder.

---

