---
title: "Can't activate python"
date: 2015-06-23
forum: New to Ubuntu
---

### Post by jola on 2015-06-23
Hello, i'm sorry if this is a dumb or repeated question, but here it is anyway. 
I have python 3.4 & 2.7 installed, but i can't seem to access or open it for use. I want to place it in a more accessible folder, such as "Education".
It seems to be here: /usr/bin  
But the problem is there are so many pythons i don't know which one to open. There is a python3 with a gear icon, what is that? 
Can someone please help? 

Thank you very much, jola

Lubuntu 14.04, ThinkPad R51

---

### Post by branau on 2015-06-23
Hi Jola,

I'm not sure why you'd want to move Python to another folder, because you should be able to access it from the Terminal by just typing in
```
python
``` for Python 2.7 or ```
python3
``` if you want to use Python 3.4. Also, I don't recommend you move any of those python files to another directory because from what I've been told, some programs depend on them so you don't really want to mess with them. For the same reason, it's recommended that you use a virtual environment for Python, just to really make sure you don't mess up anything. I use Pyenv, for example.

---

### Post by oldfred on 2015-06-23
Do not move the standard versions of python. System relies on those to run. It used to be if you deleted python that was not even repairable as python was used for the Internet. Now it usually is repairable, but lots of effort.

What issue are you having. Python should just run and if you want python3 you just run that.

---

### Post by pissedoffdude on 2015-06-23
Probably best to focus on your end goal first.  Python in Ubuntu comes pre-installed, kinda like the way it does in mac, where it's just out of your way, because other programs use it.  If your plan is to learn python, you can create an entry for it in the 'education' category.  If you see multiple, it's probably because many programs use python2 and python3, which are incompatible.  They're installed for compatibility reasons, not for use in the 'education' category.  If that's an issue, just hide them.  Otherwise, just leave them both accessible.  Hehe, more power to the user anyway

---

