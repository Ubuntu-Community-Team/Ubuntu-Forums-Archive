---
title: "Learning to use the Terminal"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by redandgreen on 2008-08-14
Hey all,

I'm a new ubuntu user and so far I'm loving it - I've had almost no problems, and am quickly becoming addicted to tetravex :P but everywhere I go, I keep hearing about how awesome and useful the terminal is. I've used it, a bit, but only in a copy-paste sort of way. Can you recommend any sites or guides that'll help me learn? What do you, personally, tend to use it for? 

redandgreen

---

### Post by Rolcol on 2008-08-14
The terminal is really great if you learn it.  I used this site:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Linuxcommand.org goes though some of the other unix stuff that you should know if you're using the terminal.  It explains what the most important folders in / are.

---

### Post by lordhaworth on 2008-08-14
I find the shell difficult to "learn", you kind of just use it as you find you need to do things. At first its a little slower but eventually it does work out faster than not using the terminal. as you get used to it
I've got quite a good (and cheap) book called the "linux phrasebook", its pretty small and allows you to look up commands for the terminal and a brief description/example of what they do when you actually come to need them - not everyones cup of tea but its the only thing I ever really need to use.

---

### Post by redandgreen on 2008-08-14
> **lordhaworth said:**
> I've got quite a good (and cheap) book called the "linux phrasebook", its pretty small and allows you to look up commands for the terminal and a brief description/example of what they do when you actually come to need them - not everyones cup of tea but its the only thing I ever really need to use.

And the commands are the same for every version of linux? I'm sure I've seen different commands for the same thing even within the different releases of ubuntu..

---

### Post by lordhaworth on 2008-08-14
I've not had anything not work,  yet..

---

### Post by hyper_ch on 2008-08-14
> **redandgreen said:**
> And the commands are the same for every version of linux? I'm sure I've seen different commands for the same thing even within the different releases of ubuntu..

some commands achieve the same thing..... to find a file you can use the slocate db with the locate command or use find....

---

### Post by starcannon on 2008-08-14
when you start using the terminal you find out theres a nearly infinite number of ways to skin your particular cat.

You'll develop your own style, and learn what is most efficient and accomplishes your tasks for you.

Like previously mentioned, one doesn't really study the terminal, one learns by using the terminal. I suppose it could be studied, but just digging in and getting the hands dirty approach is very good.

That said, having a primer guide available is excellent. If your unsure about a command then you can always man or --help it first.

Heres a couple to try out.

For example:
```

man --help
man man

```

or:
```

man glxinfo
glxinfo --help

```

Want to know if direct rendering is enabled?
```

glxinfo | grep direct

```

whats grep about?
```

man grep
grep --help

```

As you can see, one thing can lead or feed into another, you can learn as little or as much as you want/need. If you see a command in one of the threads around here, and are curious what it does, or how it works, just man or --help it.

GL and have fun!

P.S. while I normally don't say "google it" or "read the manual" I will note that on this vast subject, its often times the fastest way to get information, note you can man a command in google as well. Sometimes man or --help will tell you how to use a command but may not tell you why you'd ever use the command, google is your best bet in that case, or as always ask here on the forums as well.

---

### Post by redandgreen on 2008-08-14
Thanks, everyone :) I have more confidence now. Gonna go, read some guides, try things out. If it all goes horribly wrong, I'm sure you'll hear from me :P


redandgreen

---

