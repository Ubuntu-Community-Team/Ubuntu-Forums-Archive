---
title: "apt-get vs aptitude"
date: 2009-12-16
forum: Recurring Discussions
---

### Post by beloved88 on 2009-12-16
ok, i have a question
what's the difference between apt-get and aptitude?
is one better than the other?
which one does's jaunty's add/remove programs utilize? or is it totally different? and synaptic package manager?
It's seems like aptitude is better, it tells you how much space the install is going to require, and also, several times i've tried to install a certain program or package using the add/remove interface or apt-get, and the program won't work, so i'll uninstall it and install it using aptitude and it works great.  I specifically remember that problem with soundconverter.  Also. var/log/apt seems to be missing, would creating that directory fix the problem, or is the an underlying issue?

---

### Post by kyuubi777 on 2009-12-16
sometimes it's just faster for me to sudo apt-get install than to use the synaptic or anything idk
that's weird about apt-get command not injecting the packets correctly.. never had that happen to me

---

### Post by greg963 on 2009-12-16
One has Super Cow Powers the other does not.

---

### Post by beloved88 on 2009-12-16
> **greg963 said:**
> One has Super Cow Powers the other does not.

hey, i've gotten an error message before telling me that, but i can't remember which one it was.  what does that mean!?

---

### Post by beloved88 on 2009-12-16
oh, i see
```
user@Skipper:~$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
user@Skipper:~$ aptitude moo
There are no Easter Eggs in this program.

```

---

### Post by greg963 on 2009-12-16
Seems apt has always been a more mainstream tool (I used debian distros for years without ever knowing about aptitude) and it seems aptitude was always just assumed to be only a curses frontend to apt, but really it seems to be a much more complete all-in-one command line package management tool.  But apt is still a very good tool, it is just a little harder to remember the commands sometimes.

---

### Post by khelben1979 on 2009-12-16
apt-get works good for me.

---

### Post by Sef on 2009-12-16
Moved to recurring discussions.

---

### Post by mthei on 2009-12-16
> **beloved88 said:**
> oh, i see
```
user@Skipper:~$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
user@Skipper:~$ aptitude moo
There are no Easter Eggs in this program.

```

Of course there are:

---

