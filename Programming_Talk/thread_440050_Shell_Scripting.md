---
title: "Shell Scripting"
date: 2007-05-11
forum: Programming Talk
---

### Post by gantww on 2007-05-11
Hello all,
As I continue converting over to Linux, I've begun finding that some of my skills are not yet up to par. In particular, I would like to improve my lack of skills in shell scripting. Does anyone know of any good tutorials or books on the subject?

Thanks,
Will

---

### Post by johnnymac on 2007-05-11
Here's one...

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by Stephen Howard on 2007-05-11
Try the [advanced bash scripting guide]("http://tldp.org/LDP/abs/html/").  There's also a couple of useful sites like [Shelldorado]("http://www.shelldorado.com/") (click on the tutorial link for a bunch of options) and the [Unix Grymoire]("http://www.grymoire.com/Unix/index.html").

---

### Post by Stephen Howard on 2007-05-11
Also try [Bash by Example]("http://www-128.ibm.com/developerworks/library/l-bash.html") by Daniel Robbins (of IBM and Gentoo fame).

---

### Post by yaaarrrgg on 2007-05-11
Part of shell scripting is just knowing what commands are available on your system.    a short list is at:

    [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

Any list of commands is a shell script.  grep, cut, sed and awk are text manipulation tools that are fairly handy.  Also, embedding one command in another with backticks `` or $() is extremely useful at times.  Another handy trick: you can pipe output from one command to another with |.

You can do more advanced scripting (with if-then-else conditionals, for example).  Here's a couple pages I liked:

    [http://www.esscc.uq.edu.au/~ksteube/Bshell/](http://www.esscc.uq.edu.au/~ksteube/Bshell/)
    [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s1](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#s1)

... but if the script starts to feel like an application or starts getting complex, I'd recommend just switching to another programming language like Perl, Python, Ruby, for example.  Trying to do complex tasks in Bash is painful.  Bash scripts should be simple, so not knowing much about shell scripting isn't necesarilly a bad thing. :)

---

### Post by Stephen Howard on 2007-05-12
Also have a look at the boot scripts is /etc/rc.d to see some examples.  They offer the advantage of showing the programming choices of different script authors.

---

### Post by FuturePast on 2007-05-12
And if you really want to get stuck in try the O'Reilly book "Classic Shell Scripting".

---

