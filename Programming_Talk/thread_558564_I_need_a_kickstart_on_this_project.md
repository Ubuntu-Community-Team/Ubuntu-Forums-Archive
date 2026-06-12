---
title: "I need a kickstart on this project"
date: 2007-09-24
forum: Programming Talk
---

### Post by spaceboy909 on 2007-09-24
Hey all.

I'm still learning c++ (currently learning classes), and am new to Linux, but I would like to at least be able to take a look at a 'simple' project, to use as motivation, and hopefully tackle it once I'm up to par.

The Ubuntu development sites/pages seem to be slapped together somewhat chaotically, but I managed to find the 'bitesize' list.

I found this bug: [https://bugs.launchpad.net/ubuntu/+source/xmms-status-plugin/+bug/90529](https://bugs.launchpad.net/ubuntu/+source/xmms-status-plugin/+bug/90529)

It apparently revolves around this package: xmms-status-plugin

I just need help finding the source files that I need to look into this issue.  Are they already installed with my basic Fawn installation, or do I need to download them somewhere?

And is there a list somewhere that shows what language each package is coded in?  I'm seeing Python pop up a lot around here.  Not sure I'm up for learning two languages at once..... :)

Thanks for any help.

---

### Post by Compyx on 2007-09-24
First off, I'm not sure you should start debugging packages when you're still learning a language, but anyway..

To get the source of that package you can do:
```

mkdir xmms-status-plugin && cd xmms-status-plugin
apt-get source xmms-status-plugin

```

It looks like that particular package is written in C, not C++. It also heavily uses Gtk+ so you'd have to learn about that too.

Good luck ;)

---

### Post by pmasiar on 2007-09-24
Start with simple projects. Wiki in my sig has some ideas of command-line programs good as training task for beginners. It is for python, and you can solve them also in C++. You will have to work 10 times as hard as in Python, but C++ was your choice, not mine :-)

---

### Post by spaceboy909 on 2007-09-25
**EDIT: (Problem fixed!  See next post)**  Thanks for the tips guys.  Did a little reading on Python.....looks like I'll be adding that to my to-do list.... :)

Anyway, I'm getting an error:

apt-get source xmms-status-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xmms-status-plugin

Does this mean the download location doesn't contain the file?

---

### Post by spaceboy909 on 2007-09-25
Had to do a few more things, which solved it.

(For reference)

Checked the 'source code' box in sources.list located in /etc/apt

Directed by apt-get to install dpkg-dev

---

