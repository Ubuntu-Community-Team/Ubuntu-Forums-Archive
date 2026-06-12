---
title: "has anyone tried to develop programs for psp using ubuntu?"
date: 2009-11-03
forum: Programming Talk
---

### Post by henryfranz2005 on 2009-11-03
I would like to ask if anyone here tried to develop programs using ubuntu? :)

---

### Post by Can+~ on 2009-11-03
PSP as in Python Server Pages, or PSP as the Playstation Portable?

Assuming the later, if you want to develop programs that run on the PSP, you're out of luck, try on other sites, like psphacks and the like, but you could probably code them on linux. 

If you want to develop apps that run on ubuntu, and handle PSP, it's plain easy to work as any other pluggable device (for example, something that will handle ISOs, pictures, music, etc).

---

### Post by Thesuperchang on 2009-11-03
I don't have a PSP, but I have developed some software for the PS2 in Ubuntu. The link below will lead you to a forum where all the PSP development goes down.
[http://forums.ps2dev.org/viewforum.php?f=14&sid=b31f3ce380c4315dddc57aade4a7335b](http://forums.ps2dev.org/viewforum.php?f=14&sid=b31f3ce380c4315dddc57aade4a7335b)

From previous experience, windows is a troublesome environment to develop PS2 software in.

---

### Post by henryfranz2005 on 2009-11-03
Yes, developing on Windows is so lame. On linux you could just use the command line yet you could develop faster.

---

### Post by Can+~ on 2009-11-03
> **henryfranz2005 said:**
> Yes, developing on Windows is so lame. On linux you could just use the command line yet you could develop faster.

I agree. When I'm on windows, I usually get desperate when using the command line there.

If you are developing on C, the usual choice is:

gcc/makefile + gedit: For small files.
geany: For small files (and having click&run buttons).
Big project: Eclipse/Netbeans with C plugin (auto-generated makefile)
gcc/makefile + vim/emacs: Also nice.

---

### Post by henryfranz2005 on 2009-11-03
> **Thesuperchang said:**
> I don't have a PSP, but I have developed some software for the PS2 in Ubuntu. The link below will lead you to a forum where all the PSP development goes down.
[http://forums.ps2dev.org/viewforum.php?f=14&sid=b31f3ce380c4315dddc57aade4a7335b](http://forums.ps2dev.org/viewforum.php?f=14&sid=b31f3ce380c4315dddc57aade4a7335b)

From previous experience, windows is a troublesome environment to develop PS2 software in.

> **Can+~ said:**
> I agree. When I'm on windows, I usually get desperate when using the command line there.

If you are developing on C, the usual choice is:

gcc/makefile + gedit: For small files.
geany: For small files (and having click&run buttons).
Big project: Eclipse/Netbeans with C plugin (auto-generated makefile)
gcc/makefile + vim/emacs: Also nice.

of course sir, on windows you must first google the needed packages, install cygwin, and hell I don't know how to add packages on cygwin. On Linux specifically ubuntu I just typed the needed package sudo apt-get install <package name> and then your finished. Run the toolchain, add to path then yeah. You now have the environment. Windows sucks on developing applications. That's true.

---

