---
title: "Learning Python in Ubuntu"
date: 2007-01-23
forum: Programming Talk
---

### Post by Josh1 on 2007-01-23
Hi Guys,

I have decided to give programming a go, since I already study and know PHP (As well as the other "web" languages) and I decided to learn Python over everything else as it seems to be a good introduction to learning Programming for what I want to do (and it looks pretty popular as well!).

As I understand, Python comes by default with Ubuntu 6.10. I have been reading through [THIS]("http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/") guide, but it seems to be for Windows XP.

What is a good python application like this for Ubuntu, as I so far have no idea where to start, and I don't want to use Windows to learn it since I have been using Ubuntu for nearly a year now.

If anyone knows how to run IDLE in Ubuntu (natively) Iwill be grateful.

Thanks,
Josh

---

### Post by lnostdal on 2007-01-23
> **Josh1 said:**
> If anyone knows how to run IDLE in Ubuntu (natively) Iwill be grateful.

```
sudo aptitude search idle
...
sudo aptitude install idle
```
..or any of the more specific versions?

---

### Post by Josh1 on 2007-01-23
Ah I'm such a tool, tried:
```
sudo aptitude install idle
```
But didn't work for me first time since I didn't do search(?).

Cheers.

---

### Post by pmasiar on 2007-01-23
You have bunch of links in sticky for this forum, Python is [here ]("http://ubuntuforums.org/showpost.php?p=1984319&postcount=5")

"get the taste of Python" has 2 links to tutorial to IDLE. learn Python wiki has more links to good online books etc.

To run IDLE: Menu >> Applications >> Programming >> IDLE

Good choice - and good luck!

---

### Post by Josh1 on 2007-01-23
Yeah I read the stickies, that's where I got the guide from. :biggrin: 

Thanks,
Josh

---

### Post by pmasiar on 2007-01-23
I don't remember - I believe IDLE was installed on my Ubuntu by default. If not, I install everything via Synaptic  (Menu >> System >> Administration >> Synaptic) - it is just couple clicks away!

---

### Post by nick.inspiron6400 on 2007-01-23
You dont really need a IDE. 

Open a text editor, write your code. And i think you need to save it as .py

Then just go to a terminal and open up your work. e.g helloworld.py. (i think, i did try python a while ago)

---

### Post by pmasiar on 2007-01-23
> **nick.inspiron6400 said:**
> You dont really need a IDE. Open a text editor, write your code. And i think you need to save it as .py (..)

You need decent programmer's editor to handle tabs and spaces for you - like replace tab with 4 spaces. Remember in Python whitespace is significant, code needs be properly aligned, and if you will use just *any* random editor, it may go wrong (happened to me) newbie can get confused and frustrated. 

Nick is right, even gedit or any other simple editor will work - if editor is smart enough to recognize syntax (colorize), should handle tabs/spaces properly. But IDLE gives you syntax coloring even in the shell. Nice touch.

---

### Post by maddog39 on 2007-01-23
If you go to: Applications > Accessories > Text Editor

That serves as a programmers editor as well, because it supports syntax highlighting for several langauges as well as some other things and some basic programming tools/plugins. It should do just about everything as IDLE does, since IDLE isnt really a very in-depth IDE.

---

### Post by Tomosaur on 2007-01-23
I would recommend scite as a text editor, it's very lightweight and certainly does the job for me :) Also supports syntax highlighting and compilation (but you don't to compile Python programs)

---

### Post by Pobega on 2007-01-23
The way I practice Python is by opening a terminal and typing "python". It's quick and easy, just hit Ctrl+D to exit. Note though, that (I'm pretty sure) you cannot save the work you do in there. To be able to save your work you're better off using a text editor like SciTe, nano, or vim.

---

### Post by jblebrun on 2007-01-24
> **Pobega said:**
> The way I practice Python is by opening a terminal and typing "python". It's quick and easy, just hit Ctrl+D to exit. Note though, that (I'm pretty sure) you cannot save the work you do in there. To be able to save your work you're better off using a text editor like SciTe, nano, or vim.

You'll definitely like ipython. It's an enhanced verison of command-line Python. It supports lots of additional magic commands, tab-completion, better command history, and other cool stuff!

---

