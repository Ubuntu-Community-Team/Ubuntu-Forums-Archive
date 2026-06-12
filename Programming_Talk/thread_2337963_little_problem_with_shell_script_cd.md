---
title: "little problem with shell script cd"
date: 2016-09-23
forum: Programming Talk
---

### Post by zagicien on 2016-09-23
Hello, I am a beginner on linux and I can't simplify my task with a small shell script.

Normally, I open a Terminal and I will write this:
$ cd Directory1/Directory2/directory3/Directory4/Directory5 /Directory6/Directory7/Directory8
$ ./start.sh

I would like that when I open the Terminal, I simply type "./test.sh" (or something)  (test.sh is in /home/xxx/)

The problem is that when I run the script. the  cd Directory1 ... doesn't work. As if I can't manage to browse folders.

I don't know really how I could do to resolve this.
Can you help me please to understand how I can solve this?

thank you,

---

### Post by steeldriver on 2016-09-23
Normally, commands inside a script run inside their own subshell and don't affect the parent shell from which they are called

To have a cd command inside a script change the working directory of the *parent *shell you would need to **source **the script, rather than run it

```

. ./start.sh

```

[URL="https://en.wikipedia.org/wiki/Source_(command)"]https://en.wikipedia.org/wiki/Source_(command)

[http://unix.stackexchange.com/questions/43882/what-is-the-difference-between-sourcing-or-source-and-executing-a-file-i](http://unix.stackexchange.com/questions/43882/what-is-the-difference-between-sourcing-or-source-and-executing-a-file-i)
[/URL]

---

### Post by zagicien on 2016-09-23
I solved my problem by adding "/home/xxx/" at the beginning of my cd and by doing this:

[I]vi -b test.sh
# we must remove all  ^M  at the end of each line
dos2unix test.sh[/I]

---

