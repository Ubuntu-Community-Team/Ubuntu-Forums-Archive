---
title: "Ubuntu 11.10 Command Guide?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by hydroxph on 2011-11-03
Does anyone have this?

Most I know off my head is.

1. sudo su
2. shutdown -h now

---

### Post by Script Warlock on 2011-11-03
you mean [guide]("http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/")

---

### Post by vicshrike on 2011-11-03
Check this bash guide:

[http://www.linux-books.us/linux_general_0001.php](http://www.linux-books.us/linux_general_0001.php)

---

### Post by sisco311 on 2011-11-03
> **vicshrike said:**
> Check this bash guide:

[http://www.linux-books.us/linux_general_0001.php](http://www.linux-books.us/linux_general_0001.php)



I wouldn't recommend that guide.

First of all, it's outdated (2006). And here is an example from the guide (9.1.2.1):
```
[carol@octarine ~/articles] [color=red]ls *.xml > list[/color]
[carol@octarine ~/articles] for i in [color=red]`cat list`[/color]; do [color=red]cp "$i" "$i".bak[/color] ; done
```

There are 3 major errors in just 2 lines of code:
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
BashPitfalls 1 & 3 (link in my signature)

@OP

If you want to learn bash scripting, check out the guide from my signature, then [http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

You might also want to take a look at: [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Goldiescorpio on 2011-11-03
Hi there,

There are many guides to be found accross the net.
One who also has some basic commands concerning file editing, copy, update, etc is the [ubuntuguide]("http://ubuntuguide.org").

Happy learning!

Grtz

---

### Post by Goldiescorpio on 2011-11-03
sisco311,

There are some nice guides in ur sig. I thank you for that!

Grtz!

---

### Post by aeiah on 2011-11-03
once you get down to the command line, you might as well assume that ubuntu is the same as any other version of linux, so don't search for ubuntu specific commands, search for bash or linux commands.

there are a few files that are in different places on ubuntu, but that shouldnt stop much from working the same on ubuntu as other distros

---

