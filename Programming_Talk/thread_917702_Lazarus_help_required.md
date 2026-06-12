---
title: "Lazarus help required"
date: 2008-09-12
forum: Programming Talk
---

### Post by prshah on 2008-09-12
Hello,

I've recently installed "Lazarus" from the repositories.

However, I'm facing two problems:

a) When starting Lazarus, I get a message box:> The Free Pascal source directory was not found. Some code functions will not work. 
It is recommended that you install it and set the path
Environment->Environment Options->Files It then continues starting up after dismissing the message box. I've also installed "fpc" (free pascal) from the repositories.

b) When Lazarus has started up, the entire UI is devoid of text; the buttons, menus, tabs etc, have icons but no text. The property window and code window is fine.

I've looked around on Google but have not found anything suitable; (probably because I don't know what to search for, and "lazarus no text" is just lame.)

Any advice?

PS: I'm not sure if the choice of sub-forum is entirely appropriate, so please feel free to shuffle it around as appropriate.

---

### Post by pmasiar on 2008-09-12
Not sure why your goal is to learn obscure system like Lazarus for obsolete language like Pascal - you find out soon that community for it is minuscule and drying out. But you are free to waste your time in any way you prefer. 8-)

Also, "required" is little too strong word - read my FAQ about how to ask questions correctly.

---

### Post by prshah on 2008-09-12
> **pmasiar said:**
> Not sure why your goal is to learn obscure system like Lazarus for obsolete language like Pascal

I am a Delphi Gold Certified programmer, and Lazarus seems to be the point of least resistance (and hence quick accomplishment) for me.

I also have used and am accomplished in C, C++, Java, Visual Basic, Delphi and VBA (Office), but I have a lot to learn to use these languages on Linux (GTK, QT, etc), which could take a while. But it will be fun to learn something new, after a long break with these languages.

Aside from all this, do you have anything _useful_ to mention about my Lazarus _problem_?

---

### Post by cmay on 2008-09-12
here is a tread about this.
[http://ubuntuforums.org/showthread.php?t=730077&highlight=lazarus](http://ubuntuforums.org/showthread.php?t=730077&highlight=lazarus)

the lazarus IDE needs the sources for free pascal compiler to work.
you can download it as deb at the lazarus or free pascal compilers homepage.
i have link in my signature.

edit:
i download sources for free pascal from the debian package repo and place it home folder.for the sake of its easy.
for some reason the ubuntu repo forgot to add the source deb in the repo.

---

### Post by pmasiar on 2008-09-12
> **prshah said:**
> do you have anything _useful_ to mention about my Lazarus _problem_?

From your post it was not obvious why you decided to go for such obsolete systems - plenty of noobs  come along with strange ideas. 

It's not your case, I am sorry I wasted that little time i did, I'll make sure to ignore you from now on. Have fun!

---

### Post by PeterBBB on 2008-09-12
> the entire UI is devoid of text

It may be trying to use a font that is not installed on your system. Try

```
startlazarus
```

from a terminal, and see if you get any more meaningful error messages.

---

