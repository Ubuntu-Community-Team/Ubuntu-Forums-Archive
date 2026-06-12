---
title: "ls --colour; i.e. ls for non-Americans"
date: 2008-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Darwin Award Winner on 2008-01-31
If you think the correct spelling of "color" is "colour," then here's a script to make the ls program agree with you:

```
#!/usr/bin/perl
foreach(0..$#ARGV) {
    last if $ARGV[$_] eq "--";
    $ARGV[$_] =~ s/^--colour/--color/;
}
exec("/bin/ls",@ARGV);
```

Put that in a text file called "ls", make it executable, and put it in your path somewhere before /bin (i.e. before the location of the *real* ls), and then start a new terminal to allow the path change to take effect.

Now, try ls --colour=yes

Enjoy!

Note: You could make a copy of this script for any other program that takes the --color option, such as grep. If there is demand for it, I will make a generalized script for any executable.

---

### Post by wavesound on 2008-02-03
Nice one
Bet you couldn't get bill gates to do that!!!

cheers
Bob

---

### Post by ~LoKe on 2008-02-03
That's a little excessive.  Just make an alias in your ~/.bashrc that reads:
```
alias ls --colour='ls --color=auto'
```

**EDIT**: Apparently you'd can't do that.  Dumb.

---

### Post by Darwin Award Winner on 2008-02-04
Even if that did work, it wouldn't cover something like 
```
ls -ld ~/Downloads --colour
```
Also, would anyone be interested in a more general implementation of this? This would mean support for more commands (e.g. grep --colour) and more options (can't think of any examples).

---

