---
title: "Newbie to linux Bash scripting has questions"
date: 2010-11-16
forum: Programming Talk
---

### Post by argedion on 2010-11-16
I have a few questions I would like to get answers for.

1. Once I make my batch executable with chmod u+x scriptname how long does it stay executable? And if I tweak the code do I have to re-execute it?

2. Is there a resource available to help me learn Linux commands that are available to me?

3. Do I have to name all my script files with the .sh?

---

### Post by tacantara on 2010-11-16
I think I can handle your first two questions, as I've done a little bit of scripting with Bash.

1.  As far as I remember, once you've set up the file as an executable, it stays that way, even if you edit the script later.  I've never experienced anything to the contrary.

2.  Here's one place to look for more on scripting:  [http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)

I've used this site to get help with some of the scripting I've done, and it's pretty good.

---

### Post by C0derBear on 2010-11-16
> **argedion said:**
> 1. Once I make my batch executable with chmod u+x scriptname how long does it stay executable? And if I tweak the code do I have to re-execute it?

Permanently, no.

> **argedion said:**
> 2. Is there a resource available to help me learn Linux commands that are available to me?

Goolge? "ls /bin" - ;^) Seriously, this is such an open-ended question I don't know where to begin. OReilly "Linux in a Nutshell" maybe? There is also a fair amount of depth to the BASH script programming to be covered.

> **argedion said:**
>  3. Do I have to name all my script files with the .sh?

No, but it's good form to make sure the first line of the file is

> #!/bin/bash

That plus the executable bit being set will make things easier.

If you want to make it easy to run scripts in your current working directory then make sure to modify your PATH

> export PATH=$PATH:.

If you don't already have '.' in your PATH. You can check with

> echo $PATH

regards

---

### Post by Crusty Old Fart on 2010-11-16
Here's something I highly recommend that can really save your tail.
```

#!/bin/bash
**[COLOR=Red]set -e[/COLOR]**

```The line in **[COLOR=Red]red[/COLOR]** above will cause your script to abort on its first error. The best place to put it is directly beneath #!/bin/bash.

Sometimes, you can make a simple typo in a script and it can end up throwing all sorts of really wild commands at the shell that end up trying to be executed. God only knows how badly this can mess up a system. There's no UNDO in the shell. If it gets a tsunami of crap code thrown at it, you can't take anything back that it executes.

If someone were to ask me: What is the most important script command that every newbie should learn?...This one would be my answer.

Beyond that, I would recommend they learn as much as they can about grep, sed, awk, and regular expressions (regex).

Have fun.

---

### Post by Ruzbeh on 2010-11-16
> **argedion said:**
> 2. Is there a resource available to help me learn Linux commands that are available to me?
There most certainly is. I recommend getting a book. There's nothing more annoying than having to look up absolutely everything on the internet. There are a lot of books you could have on your shelf, making it more fun to learn new things. (That is not to say manpages are useless. But it's not always the most relaxed way of learning a new tool.) Start browsing at amazon.com. One book that I recently started reading and like is the Bash Cookbook. The style is very nice. But your first question is kinda weird so I would first suggest getting a book about linux in general, that teaches you the basics, e.g. the basics on files and file permissions.

---

### Post by argedion on 2010-11-16
> Start browsing at amazon.com. One book that I recently started reading and like is the Bash Cookbook. The style is very nice.
Does the Book have a Name?

Thanks for all the info. I see this is going to be a process but thats kewl cause I'm up for the challenge :P

---

### Post by Vox754 on 2010-11-16
> **argedion said:**
> I have a few questions I would like to get answers for.

1. Once I make my batch executable with chmod u+x scriptname how long does it stay executable? And if I tweak the code do I have to re-execute it?

2. Is there a resource available to help me learn Linux commands that are available to me?

3. Do I have to name all my script files with the .sh?

1. As you discovered, no. Think about it, it would be a pain in the behind. Also, many modern text editors are "intelligent" in the sense that when you add the shebang (#!/bin/interpreter), or name your file with the proper extension, the file will be saved as executable immediately. This works for many scripts, not just bash ones. (It may be actually nautilus, or the gnome virtual filesystem which does this, I'm not sure.)

2. Any basic guide will help you learn the most common commands. Off the top of my head, most of them deal with files and strings. Think about it, you need to know these, as they suppose you don't have a graphical interface: cp, mv, rm, file, ls, ln, dd, mkdir, rmdir, chown, chmod, gzip, gunzip, tar, cat, man, info, cut, tr, test, ln, grep, sed, rename, which, tail, head, less.

In general, I always say that "users don't need to learn Bash", they need to learn to use the terminal. Once you know basic commands, you can put them all together in a file, and instantly you have a "script", that is, a sequence of commands that are called, well, sequentially.

Only true Linux administrators need to comprehend all features that Bash provides. Bash is a complete programming language after all, it takes years to learn.

Most users just need to get comfortable using the terminal, and after a while they'll hack small scripts here and there to automate basic stuff. If you need more than that, then you can research solutions on the internet. For example, a backup script is an excellent exercise, because everyone has made one, and you can compare different ways people do things.

This is the best advice I could give you, don't "learn" Bash all at once. Just learn basic commands, learn what you need. If you feel you need to know more, read more, research more, dig more.

Here is a [Bash guide](http://mywiki.wooledge.org/BashGuide).

3. In Linux files don't need an extension at all. They are for the convenience of the user.

A script can be run in two ways:
```

# explicitly through its interpreter
bash my_script

# by itself, giving the full or relative path, if it already has the shebang
./my_script
/full/path/my_script

```

Do this
```

which firefox

file /usr/bin/firefox

```
As you see, "firefox" in the command line is not a binary, but actually a symbolic link to a shell script which sets up some variables, and then it calls the real binary. There are a bunch of such files in any Linux system, shell scripts which behind the scenes do things and then call other programs, but you never realize that because they have no extension.

---

### Post by ziekfiguur on 2010-11-17
> **Crusty Old Fart said:**
> Here's something I highly recommend that can really save your tail.
```

#!/bin/bash
**[COLOR=Red]set -e[/COLOR]**

```The line in **[COLOR=Red]red[/COLOR]** above will cause your script to abort on its first error. The best place to put it is directly beneath #!/bin/bash.
...
If someone were to ask me: What is the most important script command that every newbie should learn?...This one would be my answer.

I'm not new to bash, but I wish  I had known about that one, thanks.

2. [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
This might not be the best place to learn about bash, but it does have a lot of information you might need, use it as a reference.

---

### Post by Crusty Old Fart on 2010-11-17
> **ziekfiguur said:**
> I'm not new to bash, but I wish  I had known about that one, thanks.

You're mighty welcome. I, as well, wish I had discovered it years before I did.

You might like this one too. It's [COLOR=Red]**set -x**[/COLOR] a nice debugging tool that prints command traces to the screen before the commands execute.

To turn tracing on: [COLOR=Red][B]set -x
[/B][/COLOR]To turn tracing off: [COLOR=Red][B]set +x
[/B][/COLOR]
If you put [COLOR=Red]**set -x**[/COLOR] at the top of a script, and never turn it off with [COLOR=Red]**set +x**[/COLOR], the entire script will be traced.

You can also distribute as many of them as you want throughout a script to activate tracing for particular blocks of code. For example:
```

~~~ some code that won't be traced ~~~
[COLOR=Red]**set -x**[/COLOR]
**[COLOR=Green]~~~ some code that will be traced ~~~[/COLOR]**
[COLOR=Red]**set +x**[/COLOR]
~~~ some code that won't be traced ~~~
[COLOR=Red]**set -x**[/COLOR]
**[COLOR=Green]~~~ some code that will be traced ~~~[/COLOR]**
[COLOR=Red]**set +x**[/COLOR]
~~~ some code that won't be traced ~~~

```

---

### Post by cmcanulty on 2010-11-17
Wow what a great thread, I learned a lot, thanks

---

### Post by Crusty Old Fart on 2010-11-17
> **cmcanulty said:**
> Wow what a great thread, I learned a lot, thanks
In my opinon, credit for that goes to argedion because of how he titled it.
Perhaps there's a lesson in that too.

---

