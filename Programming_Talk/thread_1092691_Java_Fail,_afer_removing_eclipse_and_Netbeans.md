---
title: "Java Fail, afer removing eclipse and Netbeans"
date: 2009-03-10
forum: Programming Talk
---

### Post by vandorjw on 2009-03-10
Hey everyone.

I am not a very big fan of eclipse and Netbeans so I removed them.
But now when I want to compile a program I can't do it anymore because javac is missing.

I have jre and jdk installed in the following directory..

/usr/java

more specifically javac is located here /usr/java/jdk1.6.0_12/bin

So I know that jdk has javac but I don't know how to link to it.
What I am doing now is this.
```

/usr/java/jdk1.6.0_12/bin/javac main.java

```
Which is really annoying :( I want to be able to use my make file :)

I think it has to do with setting PATH in .bash_profile but I don't know the right stuff to put there.

I read the FAQ and 
```

"sudo aptitude install sun-java6-jdk" 

```is not what I want.
Cheers - CC7

---

### Post by vandorjw on 2009-03-10
Ok I figured it out.


I needed to add 
```

export PATH=$PATH:/usr/java/jdk1.6.0_12/bin

```

to .bash_profile

and then run source ~/.bash_profile

source:
[http://ubuntuforums.org/showthread.php?t=150354](http://ubuntuforums.org/showthread.php?t=150354)

I have another problem now however, it only works after I run the command

```

source ~/.bash_profile

```

[http://ubuntuforums.org/showthread.php?t=150354](http://ubuntuforums.org/showthread.php?t=150354)
> 
No, when you log in or open a new terminal, ~/.bash_profile is automatically sourced.
-- soce_32


I think this guy is wrong since I have to enter every time.

---

### Post by jespdj on 2009-03-11
You can put it into ~/.profile instead of ~/.bash_profile. Log out and back in again to make it work.

---

### Post by vandorjw on 2009-03-13
No, I read in the ~/.profile file that if ~/.bash_profile exist, it won't use ~/.profile.

> 
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.


So modifying this file won't do anything.

Cheers - CC7

---

