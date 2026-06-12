---
title: "dealing with terminal prompts in gui programs that i am making"
date: 2012-08-19
forum: Programming Talk
---

### Post by rhlegion on 2012-08-19
I am making an application that has a gui to do my system updates [mainly just for programming practice (I'm still a noob)]  and i know that i can do gksudo to get a password prompt to come up in gui to solve the problem of running something in root privileges, but what do i do about the [Y/n] prompt? 
I'm using python 2.7.3
and Tkinter for my gui.

if this can be done purely in python (which i know it probably can but i mean in a simple way i could use, learn from, and implement later)  i would like to find out how.
also
if it can be done through a terminal command similar to gksudo that too would be helpful.

[RIGHT]Thanks
rhlegion
[/RIGHT]

---

### Post by 25tom on 2012-08-19
With apt-get terminal command there's the option "-y" which assumes yes to all queries...
Hope this helps

---

### Post by rhlegion on 2012-08-19
[LEFT]Thank you very much that will do it!
[/LEFT]
but i will leave this thread open a little longer just to see some other options, such as maybe how to completely do it in python. :) 
[RIGHT]


Thanks
rhlegion
[/RIGHT]

---

### Post by 25tom on 2012-08-19
Glad to have helped! Sorry, I don't know anything about Python, so hopefully someone who can do the Python equivalent of this will be give more info.
Have fun programming :)

---

### Post by sisco311 on 2012-08-19
Thread moved to **Programming Talk**.

---

### Post by rhlegion on 2012-08-19
well i guess that will do it for the ubuntu forums. I guess ill move over to the python documentation to figure out the rest.

---

### Post by steeldriver on 2012-08-19
I'm not exactly clear what you want to do - maybe some kind of expect-like functionality? there appears to be a pexpect module for python

[http://pypi.python.org/pypi/pexpect-u](http://pypi.python.org/pypi/pexpect-u)

---

