---
title: "Quick way to type current folder into command prompt?"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by chihwah_li on 2014-08-01
I was wondering what fast way there is to paste the current foldername quickly.
ls -n /opt/Gog games/tetrobot/Tetrobot.exe Tetrobot

How can I type : /opt/Gog games/tetrobot/Tetrobot.exe ... the fastest way? Use pwd somehow??

---

### Post by mcduck on 2014-08-01
by current folder you mean the directory where you are executing the command? In that case, *pwd* would work, if you run it inside backticks (bash substitutes a command inside backticks with the actual result of that command).

Rather useless example:
```
ls -l `pwd`
```

edit: Another way of doing same is "$(command)", but I'm just so used to backticks it always takes me a while to remember the new syntax even exists :D
```
ls -l $(pwd)
```

---

### Post by ajgreeny on 2014-08-01
If you are already in a directory why do you need to use a variable that gives you the full pathway of that directory for something simple like **ls -l** as that will always give you the list of the current directory.

If you just want to save typing of the long version of the pathway, just use pwd to print the pathway then highlight the output, type the new command (ls -l) plus a space and then middle click; the copy buffer will add that pathway to the end of the command.  Normally the prompt will already show the full pathway of a system folder that you are already in so you could simply highlight that prompt and use the middle click trick that way, but I still don't quite see the point.

---

### Post by dave131 on 2014-08-02
Besides what appears to be a basic lack of understanding of linux paths (don't get me wrong - if you are new to linux this is to be expected - and we can help), I think you have another larger problem.  I've searched the net, and it appears that Tetrobot.exe is a Windows program (the .exe normally indicates a DOS or Windows program).  You cannot directly run a Windows program in Linux.  There are tools available to try to provide an environment to TRY to run Windows programs - the main piece being a package called Wine, with supportive tools such as PlayOnLinux.  Even then there's no guarantee it will run.  In addition, if the running of that program requires access to USB devices (other than keyboard, mouse and possibly a printer) you won't be able to access that device from Wine.

So,let's back up a step and ask:  Is this a Windows program you want to run in Linux?

---

### Post by sudodus on 2014-08-02
> **dave131 said:**
> ...

So,let's back up a step and ask:  Is this a Windows program you want to run in Linux?

I'd like to back up a step too, because of the path in your opening post. It contains a space and wont work unless you put it within quotes or escape the space character with backslash.

```
"/opt/Gog games/tetrobot/Tetrobot.exe"
```
```
/opt/Gog\ games/tetrobot/Tetrobot.exe
```

---

### Post by Impavidus on 2014-08-02
The current directory is **.** too. So you can use **.** instead of **$(pwd)**, with one difference. If you store the output of **$(pwd)** and reuse is after changing directory, it will still refer the the old current directory, whilst **.** will refer the the new current directory. The same way, **..** always refers to the parent of the current directory.

You don't often need **.**. Usually it can be omitted or you can use relative paths, but sometimes you have to provide an argument and it can be useful in scripting. For example, copy a file to the current directory (**cp blah/blah/file .**, this happens quite often actually) or execute a program in the current directory (**./progname**).

---

### Post by chihwah_li on 2014-08-02
@everyone. Thanks for the replies.
I installed a game an was just wondering how to make a symbolic link that would work everywhere.

I am a novice with Linux, just dumbed windows 7 with a school licence off my computer, because I am no longer studying any longer. 
Thus my windows 7 licence is no longer legal. So I made the decision to use Ubuntu 14.04 LTS, because I tried version 10 before and I liked it.

And learning about Wine, Winetricks, PlayonLinux to use , play some windows games and software on my Linux OS.
Is great, been able to run E-sword with help of Wine very well. Space run (windows) game runs good under Linux.

Thanks again, will try out the suggestion in this post later. =)

---

