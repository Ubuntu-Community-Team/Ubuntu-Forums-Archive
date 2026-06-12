---
title: "java trouble... source /something gives errors"
date: 2006-10-16
forum: Programming Talk
---

### Post by red_Marvin on 2006-10-16
I'm taking a java class and have installed sun's jdk do be able to work on assignments at home, and in the beginning all worked well but not anymore.
We have a couple of standard classes to simplify certain parts, and to access those I have to enter

*source /somepath/to/something*

and normally I then get a message saying something along the lines of "Course packet installed"
But the last times I tried I instead got this error:

*bash: PK: command not found.*

The three chars after "PK" show up as empty squares.

What is wrong?

---

### Post by hod139 on 2006-10-16
How did you install Sun's java?  Did you use the official package in Dapper, and then make it the default? See this howto: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by red_Marvin on 2006-10-16
Hmm It doesn't seem to have to do with that, I partially posted the wrong error results. Sorry.

This is what I've done except installing suns jdk:

[LIST]
[*]Downloaded eda011.jar (the package) into /usr/local/java/packages
[*]Put [I]export PATH=/usr/local/java/jdk/bin:$PATH
export CLASSPATH=.:/usr/local/java/packages/eda011.jar[/I] in .bashrc
[/LIST]

And we are told to type *source /usr/local/cs/pt/initpt* But there's no such folder (and has never been afaik)
so I get a file or folder doesn't exist error

---

