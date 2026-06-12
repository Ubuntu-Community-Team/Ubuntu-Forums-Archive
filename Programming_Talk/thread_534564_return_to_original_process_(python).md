---
title: "return to original process (python)"
date: 2007-08-25
forum: Programming Talk
---

### Post by s1ightcrazed on 2007-08-25
Here's the dilema:

I'm working on a curses app written in python, and I've been trying to work on modularizing the app. The idea is that from within a parent curses window you can select an item off a menu, and that item will actually be a separate curses program itself. If you exit the spawned program you should return to the original parent app. 

What I've tried so far is an os.system call inside the parent:

os.system("python curses_app2.py")

and this works fine, spawning the 2nd program, although I do end up with 2 separate python processes. However, when I exit the second 'spawned' app, it does not return me to the original parent app. I just get dropped to a terminal - it's as if the first app never re-initializes. 

Just curious if anyone has ever done this before. I *could* just make everything into one big standalone app, but I'd prefer not to. I really like the idea of having each separate part of the app be a different file, for organization and maintenance, if for nothing else.

---

### Post by pmasiar on 2007-08-25
why you need second process be also curses? My gut feeling is that second process should do something and return. Do you need it be asynchronous?

---

### Post by s1ightcrazed on 2007-08-25
Let me explain better:

I have 2 applications, both curses/python. You launch App1, from app1 I want to be able to launch app2. When I close app2, I want it to return me to app1. App2 need not return anything to app1. For all intents and purposes it is a stand-alone app. I just want to be able to call it from within another curses app, and be able to return to the original app when the 2nd app is closed.

---

### Post by cwaldbieser on 2007-08-25
> **s1ightcrazed said:**
> Here's the dilema:

I'm working on a curses app written in python, and I've been trying to work on modularizing the app. The idea is that from within a parent curses window you can select an item off a menu, and that item will actually be a separate curses program itself. If you exit the spawned program you should return to the original parent app. 

What I've tried so far is an os.system call inside the parent:

os.system("python curses_app2.py")

and this works fine, spawning the 2nd program, although I do end up with 2 separate python processes. However, when I exit the second 'spawned' app, it does not return me to the original parent app. I just get dropped to a terminal - it's as if the first app never re-initializes. 

Just curious if anyone has ever done this before. I *could* just make everything into one big standalone app, but I'd prefer not to. I really like the idea of having each separate part of the app be a different file, for organization and maintenance, if for nothing else.

Do you have some sample code?

---

### Post by steve.horsley on 2007-08-25
What do you want app1 to be doing while app2 is active? Does app1 launch app2 and immediately exit, or does it sit there in the background behind app2?

If app1 exits after launching app2, then app2 is going to have to re-launch app1 before exiting.

---

### Post by slavik on 2007-08-26
what you are wanting to do is a basic shell routine, execp the stuff doesn't simply print to stdout (terminal) but prints to it using curses.

I do not know the exact way to do it in Python (my guess would be looking for the following methods of the os class)

fork, exec, wait if you search this forum, I am sure you will find a post I wrote long ago about the basic shell routine and also numerous other posts where I give a very cutdown C version of that routine

---

