---
title: "Prompt with long command line problem"
date: 2009-06-02
forum: Programming Talk
---

### Post by warpdesign on 2009-06-02
Hi,

I customized my prompt this way:

PS1=" \n\e[42;30m\d - \t \e[0m\e[1;37m \w >\e[0m "

It's working as expected, but there is a problem when I type a very long command after the prompt: instead of going to the next line to display the end of the command, it erases my prompt...

See the following screenshots:

1. Command-line doesn't exceed the window size: OK

[IMG]http://www.warpdesign.fr/tests/bash1.gif[/IMG]

2. This is what happens when the command-line exceeds the window size: it overwrites my prompt: WRONG

[IMG]http://www.warpdesign.fr/tests/bash2.gif[/IMG]

NOTE: with the default prompt it correctly goes to next line.

What can I do to make it go to the next line and no overwrite my prompt ?

---

### Post by Tibuda on 2009-06-02
I can't see the screenshots.

---

### Post by dwhitney67 on 2009-06-02
That's a good question; the short command line is a pet-peeve that I have had for a long time.  To counter the problem, I have merely relied on redefining the prompt so that my typing starts on the next line.

In my ~/.bashrc I have the following definition:
```

PS1='\u@\h:\[\033[01;34m\]\w\[\033[00m\]] \n> '

```

---

### Post by warpdesign on 2009-06-02
> **dwhitney67 said:**
> That's a good question; the short command line is a pet-peeve that I have had for a long time.  To counter the problem, I have merely relied on redefining the prompt so that my typing starts on the next line.

In my ~/.bashrc I have the following definition:
```

PS1='\u@\h:\[\033[01;34m\]\w\[\033[00m\]] \n> '

```
I'd rather not start at the next line... There must be a way since it works with the original prompt...

---

### Post by stroyan on 2009-06-02
You need to place marks around non-printing escape sequences to tell bash how to count the number of columns used by a prompt.
Use "\[" before and "\]" after each group of escape sequences.
Your example prompt would be fixed like this.
```

PS1=" \n\[\e[42;30m\]\d - \t \[\e[0m\e[1;37m\] \w >\[\e[0m\] "

```

---

