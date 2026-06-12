---
title: "Viewing your aliases (the easy way)"
date: 2009-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by DemiReticent on 2009-05-20
I'm new to Ubuntu (coming from XP) but I'm already finding a lot of things I really like about the operating system.

I'm the kind of person that loves to type before using the mouse. Having an intuitive GUI is nice, too, but I'm spending almost all my time in the terminal. I asked about how to make it faster for me to launch a program from the command line, and now I know about aliases.

I already know I'm going to be using a lot of them; I'm going to lose track.

So I created the following alias:
```
alias alist='grep ^alias ~/.bashrc'
```Now every time I want to know which aliases I'm using it will display any uncommented alias lines for me and I can see my options. (Actually this is inspired by the help command in the Windows shell where you get a brief listing of common commands and what they do.)

Other useful aliases for quick editing of aliases:
```
alias aledit='gedit ~/.bashrc' #edit aliases
alias alrl='source ~/.bashrc' #reload aliases
```Aside from just being shorter, the advantages of these aliases is that no matter where I am in the filesystem I have the commands right there to use.

---

