---
title: "Run an app in a different workspace with the command line?"
date: 2008-11-25
forum: Programming Talk
---

### Post by souleestyles on 2008-11-25
Hi All,

All is in the title. Indeed, I would like to know what the command line is to run an application (eg firefox) in a different workspace.

ps: My project will be to do a script in order to run different apps on different workspaces. (Currently I use 4 workspaces).

thx in advance for your help,

---

### Post by mssever on 2008-11-25
> **souleestyles said:**
> Hi All,

All is in the title. Indeed, I would like to know what the command line is to run an application (eg firefox) in a different workspace.

ps: My project will be to do a script in order to run different apps on different workspaces. (Currently I use 4 workspaces).

thx in advance for your help,
This really is a question for a different section.

How you accomplish this depends on your window manager. I use Compiz, and the window rules plugin for ccsm allows you to configure things like that. I know that there are other methods as well, though I've never used any of them.

Basically, there's no pure command-line way to do what you want--at least not in a default install. Maybe someone's written something that you can install that'll interact with the window manager.

---

### Post by souleestyles on 2008-11-26
> **mssever said:**
> This really is a question for a different section

Which section? I though all stuff regarding shell and script were in programming talk section.:-k
Anyway my environment desktop is gnome and I use metacity as window manager.
(I'm running under Ubuntu 8.04.1, if that can help you).
I don't think what I ask is complicated. Only thing I want to know, it's how to run in a terminal (running on workspace 1 for example) an application in order to display on another workspace (different on workspace 1 for sure).

For example I tried this thing I found somewhere on Google. (don't remember where):
**export DISPLAY=:0.0 && kstart --desktop 2 firefox**

This command line works but kstart is more related to kde and not with gnome. Actually, I'd like the same way of this command line but for gnome.

---

### Post by mssever on 2008-11-26
> **souleestyles said:**
> For example I tried this thing I found somewhere on Google. (don't remember where):
**export DISPLAY=:0.0 && kstart --desktop 2 firefox**
Setting $DISPLAY won't change anything. I've heard of a program for metacity that allows control of such things, but I don't remember what it's called. At any rate, you'll need to install something metacity-specific.

---

### Post by unutbu on 2008-11-26
There is a package in the official repos that can give you control over initial window placement for all apps.
```

sudo apt-get install devilspie
```

It is a fairly small package; under 100KB.

Use System>Preferences>Sessions to run the command
```

devilspie
```

when you start up.

Make the directory ~/.devilspie
and put in it a file called config.ds with these lines as it content:

```
(if 
  (is (application_name) "firefox-bin") 
  (set_workspace 2)
)
```

For more information on devilspie:
[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by mssever on 2008-11-26
> **unutbu said:**
> There is a package in the official repos that can give you control over initial window placement for all apps.
```

sudo apt-get install devilspie
```
Thanks. That was the program I was trying to think of.

---

