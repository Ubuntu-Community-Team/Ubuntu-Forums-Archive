---
title: "Scribes + python debugger???"
date: 2007-05-25
forum: Programming Talk
---

### Post by cisforcojo on 2007-05-25
Hey guys,

I've just tried out Scribes and I love it! My question is is it possible to merge Scribes with a python debugger similar to IDLE? I hate having to save, then switch windows and then type python filename.py in a terminal.
Maybe I'm missing something really simple. I loved the simplicity of hitting 'F5' in IDLE but like Scribes format more. Any help?

---

### Post by ankursethi on 2007-05-25
Scribes is just a text editor. It doesn't support debugging and all that. I think you should wait for v0.4 which will support extensions. Somebody is bound to write an extension for debugging the programs you write.

---

### Post by cisforcojo on 2007-05-26
Ah hopin for that then. I'm having a LOT of problems with Scribes formatting the text file badly for Python.
It's gotta be a bug becaue I don't get it with any other app. This will cause python apps to run screwy when they LOOK correct in Scribes. I'll load the .py file up in another text file and see the formatting is off in some spots.

I really hope they fix this soon because it almost makes Scribes unuseable. I make enough error myself without having to figure out it's my text editor screwing me up!

---

### Post by ankursethi on 2007-05-26
I don't have such a problem, but I guess you should report this bug at the official website : scribes.sf.net

---

### Post by pmasiar on 2007-05-28
> **cisforcojo said:**
> I'm having a LOT of problems with Scribes formatting the text file badly for Python.
 python apps to run screwy when they LOOK correct in Scribes. I'll load the .py file up in another text file and see the formatting is off in some spots.

Looks like you are mixing tabs and spaces.

Set your editor to convert tabs to spaces. Good practices suggest to use 4 spaces as 1 level.

---

### Post by cisforcojo on 2007-05-28
Agreed, it does sound like that but I'm pretty sure I'm not.
Next time it happens I'll try converting tabs to spaces. What I currently do is go to the line in question, backspace it and retab, sometimes taking it back a line or so and then Enter + formatting. After a few tries that usually works.

---

### Post by kknd on 2007-05-28
Well, Scribes 0.4 will have several new features for python code editing.

I like it's philosophy, but there is a lot of things to be done! Maybe the plugin-manager thing will bring new plugins! (There are some Vim plugins written in python, maybe it will be easy to port to Scribes?)

---

### Post by DirtDawg on 2007-05-29
This may be obvious, but when coding Python, I use ALT+TAB to switch between editor/terminal. Speeds things up for me.

---

### Post by cisforcojo on 2007-05-29
Obvious but unrealized. Thanks!!!

Btw, how are you guys installing scribes? The .deb from GetDeb.net or the .tar.gz???

I personally HATE .tar.gz. I feel like after a month or so, I'll have no idea what's on my system and won't be able to get rid of anything to free up space!

---

### Post by ankursethi on 2007-05-29
As far as I can help it, I avoid manually compiling packages. You can generally find all you need on GetDeb or the official repos, or some far flung forum somewhere on the Internet.

---

