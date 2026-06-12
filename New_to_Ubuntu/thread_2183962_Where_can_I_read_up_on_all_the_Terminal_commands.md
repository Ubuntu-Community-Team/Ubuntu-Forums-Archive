---
title: "Where can I read up on all the Terminal commands?"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by mithen2 on 2013-10-27
I was trying to find out the details of my Wi-Fi card on my laptop and since I couldn't find a Windows Device Manager alternative in Ubuntu I found out about the

 ```
sudo lshw
```

 and 

```
sudo lshw -short
```

commands in the Terminal. I think that is really cool! I would like to learn more commands in the Terminal!

---

### Post by Lars Noodén on 2013-10-27
For any program on your system, you should be able to call up the manual page and find out what it does and which options are available.

```

man lshw
man ls

```

That works for other systems too, such as BSD, OS X, Illumos (formerly Solaris), not just Linux.

---

### Post by TheFu on 2013-10-27
[LIST=1]
[/LIST]
Almost every ... 99.99% ... of the CLI commands will have a **man page** for the exact version of the command on your system.  Google will find man pages too, but it probably wont be for the same version on your box.  man is short for manual.

```
man man
man ls
man chroot
man lshw
man sudo
man .... 

```There is a specific organization to the manpages too.  Different sections for different purposes and users.  man pages that are primarily for root/administration are in section-8, for example.

**apropos** - seaches manpages.
**whatis** - provides a summary.

Of course, you could buy an OReilly book - there are many of them on CLI commands.  The UNIX Power Tools one isnt bad.  LPIC has training materials that cover system admin commands, but those are changing faster than the books can be published thanks to things like upstart.

So, basically Im tellnig your to RTFM! ;)  It is all there.

BTW, lots of GUI programs have manpages too.  **man firefox**, for example. Usually there are startup parameters to control stuff.

---

### Post by Lars Noodén on 2013-10-27
If you want to make a catalog of sorts for what you have on your machine, you can find every program in /bin, /sbin, /usr/bin, and /usr/sbin and take the title line from each man page and put them in a file, sorted alphabetically:

```

[s]for file in $(find /bin /sbin /usr/bin /usr/sbin -type f -printf "%f\n");
do man "$file" 2>/dev/null | grep -m 1 ' - ' | sed -e 's/^[[:space:]]*//';done | sort -u > files.txt[/s]

```

That puts the list of programs and their one-line descriptions in the file "file.txt" which can be viewed with [less](http://manpages.ubuntu.com/manpages/raring/en/man1/less.1.html)

```

less files.txt

```

It uses [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1posix.html), [man](http://manpages.ubuntu.com/manpages/raring/en/man1/man.1posix.html), [grep](http://manpages.ubuntu.com/manpages/raring/en/man1/grep.1.html), [sed](http://manpages.ubuntu.com/manpages/raring/en/man1/sed.1posix.html), and [sort](http://manpages.ubuntu.com/manpages/raring/en/man1/sort.1posix.html).  They are chained together so that the output from one becomes the input for the next.  That's done using a pipe | and the final result is redirected > into a file.  

Anyway, if you wanted a catalog of your programs, there it is.

EDIT:  I'm not sure why I always manage to forget some things, like [whatis](http://manpages.ubuntu.com/manpages/raring/en/man1/whatis.1.html)

```

 for file in $(find /bin /sbin /usr/bin /usr/sbin -type f -printf "%f\n");
do whatis "$file" 2>/dev/null ;done | sort -u > files.txt

```

---

### Post by mithen2 on 2013-10-27
That's pretty cool :D

What I really wanted to know is just like all the command keywords if you know what I mean? 

lshw = list hardware

There must be so many like that for the Terminal?

---

### Post by Lars Noodén on 2013-10-27
The options for any particular program will be in the manual page.  There might also be a quick summary if you run the program with the -h or --help option.

```

lshw -h
lshw --help

```

For nearly all programs, either or both should work.

---

### Post by Habitual on 2013-10-27
> **mithen2 said:**
> That's pretty cool :D

What I really wanted to know is just like all the command keywords if you know what I mean? 
```

man -k <keyword>

```

---

