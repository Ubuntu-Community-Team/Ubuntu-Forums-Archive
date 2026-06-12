---
title: "Functions or seperate scripts?"
date: 2013-05-20
forum: Programming Talk
---

### Post by Bufeu on 2013-05-20
Hi!
I currently have a separate file with all my aliases and functions that I source via .bashrc. But would separate scripts be faster (in e.g. ~/bin)?
Functions are, as I understand, loaded into the RAM and because of that, functions are very fast. An other advantage is that functions is executed in the current shell, which can be handy in some cases. And on the other side, scripts are only loaded when you run them, but the computer have to read from the disk every time you call a new script. All functions are in the RAM from beginning, and the computer don't need to read from the disk. Scripts often starts with comments and #! to tell Bash what shell it should use. Functions in Bash always run in Bash, so there's no need to find out which shell the script want to use, nor start a new subshell to run the script in.
What do you prefer and what is the fastest and best way?

---

### Post by ofnuts on 2013-05-20
There is no fast rule. On any Unix system the file system is quite fast anyway, and the overhead of reading the script file is minimal. Functions could have a speed advantage is you use a lot of for loops at the console, but that would hold only if the functions are 100% bash with no calls to utilities (rare).

---

### Post by trent.josephsen on 2013-05-20
Another difference is that scripts can be invoked from shells different from what they were written in, or even from other programs. Consequently, there are things you can do with a script that you can't do with a function, like monitor it with `watch` or run it with `find -exec`.

---

### Post by Bufeu on 2013-05-21
> **trent.josephsen said:**
> Another difference is that scripts can be invoked from shells different from what they were written in, or even from other programs. Consequently, there are things you can do with a script that you can't do with a function, like monitor it with `watch` or run it with `find -exec`.
As far as I know, *watch* are using *sh* to run commands. And since *sh* doesn't support shell functions, *watch* doesn't work with shell functions, either.
But I asked what the fastest way was. I have quite much own-written code now, and I just wonder how to make it as fast as possible.

---

### Post by ofnuts on 2013-05-21
> **Bufeu said:**
> I have quite much own-written code now, and I just wonder how to make it as fast as possible.
Rewrite it in C...

---

### Post by Bufeu on 2013-05-26
So, both ways are equally fast in modern UNIX-systems?

---

### Post by ofnuts on 2013-05-26
> **Bufeu said:**
> So, both ways are equally fast in modern UNIX-systems?
I don't think you will ever notice the difference in real use, unless you are trying to execute them in a tight loop with very many iterations...

---

