---
title: "Window Management Through Terminal"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by theoreo25 on 2011-09-26
So I've been using Ubuntu for just over a year now and I figured it was about time that I learned how to use the terminal. I learned some things but they're not that useful,I want to learn how to use the terminal like a windows manager. So if programs freeze and are unresponsive I can close them, or if the mouse stops working properly I can hot key the terminal open and solve the issue without restarting my computer. 
Thank You

---

### Post by haqking on 2011-09-26
> **theoreo25 said:**
> So I've been using Ubuntu for just over a year now and I figured it was about time that I learned how to use the terminal. I learned some things but they're not that useful,I want to learn how to use the terminal like a windows manager. So if programs freeze and are unresponsive I can close them, or if the mouse stops working properly I can hot key the terminal open and solve the issue without restarting my computer. 
Thank You

[RAISING ELEPHANTS]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device")

and top, ps, kill

you can man them or --help them or info them

---

### Post by MG&amp;TL on 2011-09-26
One to start with is a lot of fun:

run 

```
xkill
``` in a terminal.

Your mouse will turn into a cross. Click on a window titlebar(preferably an unimportant one) Boom! Window gone.

Run:

```
top
```And see what's using up what. You can then kill programs by pressing 'k' and choosing the pid of the process.

You can swap window managers in terminal:

```
<window manager here> --replace.
```Have a look at linuxcommand.org for extra stuff. Coding in BASH is a lot of fun. Particularly ones that crash your computer :D

Also, learn a few good text editors, if you're into command-line fun-it will save you time long term:

-*nano* Very simple, very fast.
-*gedit *If you can't bear a command-line
and the big daddy:
-*vi(m) *Which is incredibly fast, but takes a bit of investment to learn.

---

### Post by MG&amp;TL on 2011-09-26
Errr...but most of the time it's faster to just click and drag, etc.

---

### Post by sisco311 on 2011-09-26
It doesn't hurt if you understand the basics of process management: [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

And htop so much cooler than top.   :P

---

### Post by MG&amp;TL on 2011-09-26
just installed htop. ;) Agree, but the colours are a bit garish.

You might also want to know a little about how Desktop environments, X window system, and window managers all play together nicely. If you can, have a little play with compiz settings manager (any excuse!) and see if you can work out what it's doing.

---

### Post by haqking on 2011-09-26
ha i didnt even see the file management part, i only saw kill frozen apps.

yeah +1 to all the above.

Bash scripting

[https://help.ubuntu.com/community/Be.../BashScripting](https://help.ubuntu.com/community/Be.../BashScripting)


learning the terminal

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by sisco311 on 2011-09-26
> **haqking said:**
> 
Bash scripting

[https://help.ubuntu.com/community/Be.../BashScripting](https://help.ubuntu.com/community/Be.../BashScripting)



Unfortunately, our community documentation about Bash scripting, like most of the published books and on-line tutorials, is relatively poor.

For beginners, I can only recommend Greg's Wiki (links in my sig) and [http://wiki.bash-hackers.org/](http://wiki.bash-hackers.org/)

---

### Post by MG&amp;TL on 2011-09-26
Although to be fair, once you know control structures, *grep, sed, *and *awk*, you probably know enough to make a fearsome BASH script. You just string basic commands together. If you want something more specialised, look up the command for it and add it.

---

### Post by haqking on 2011-09-26
> **sisco311 said:**
> Unfortunately, our community documentation about Bash scripting, like most of the published books and on-line tutorials, is relatively poor.

For beginners, I can only recommend Greg's Wiki (links in my sig) and [http://wiki.bash-hackers.org/](http://wiki.bash-hackers.org/)

ahh yeah it is pretty poor i guess.

nice link, i will have a nice read of that, cheers

---

### Post by MG&amp;TL on 2011-09-26
I have time to edit that. ):P

Can I /Should I /Could I? I can sign in and get the editing interface. I have read the wiki FAQ, I just wondered whether that  page was reserved for BASH gurus, or any old squirt like me could help with it.

I think the OP got more than they bargained for!

---

### Post by BEEDO on 2011-09-26
I am a pretty raw beginner in Terminal. There might be some links of interest in my current thread: 

 [http://ubuntuforums.org/showthread.php?t=1848730](http://ubuntuforums.org/showthread.php?t=1848730)
  

And some more links that may be of interest:

 [http://www.debianadmin.com/manpages/nanomanpage.txt](http://www.debianadmin.com/manpages/nanomanpage.txt)
   
  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
   
  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
   
  [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
  

Hope this was helpful!

---

### Post by theoreo25 on 2011-09-26
thank you htop is just what i hwanted. you wouldn't happen to know the command for restarting the mouse driver?

---

### Post by MG&amp;TL on 2011-09-27
No, but you can restart the entire GUI with:

Ctrl-Alt-F1, then Ctrl-Alt-F7

---

