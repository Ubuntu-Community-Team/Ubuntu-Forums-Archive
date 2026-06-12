---
title: "[python] How can I run a DBus loop at the same time as my main loop"
date: 2011-04-13
forum: Programming Talk
---

### Post by Crazedpsyc on 2011-04-13
As the title says, I have a CLI app (a shell actually) that I want to communicate and be controlled over DBus. So I have a "while 1:" loop with a fancy raw_input inside, but if I call loop.run() (with loop being the dbus gobject.MainLoop()), it stops there (duh) and wont continue to my while loop.

I need my dbus handler to handle commands (passed to a function as strs), and I also need one or more getxxyyzz() functions that just return a variable.

btw, I am using code pulled out of examples given at today's DBus session in the ubuntu app developer week IRC school

---

### Post by Tony Flury on 2011-04-13
I don't know the specifics of DBUS, but GTK (which has a main loop concept) also has the ability for a program to pull an event of the queue and process it - you do that until the queue is empty - and then get on with your main program.

Has DBUS got something similar ?

---

### Post by SledgeHammer_999 on 2011-04-13
Why not just use only the dbus loop(I suppose it is a glib mainloop) and not your own? It will save you the trouble...

---

### Post by StephenF on 2011-04-14
Found on the web.
```

import fcntl

# make stdin a non-blocking file
fd = sys.stdin.fileno()
fl = fcntl.fcntl(fd, fcntl.F_GETFL)
fcntl.fcntl(fd, fcntl.F_SETFL, fl | os.O_NONBLOCK)

# user input handling thread
while mainThreadIsRunning:
      try: input = sys.stdin.readline()
      except: continue
      handleInput(input)

```

---

### Post by Crazedpsyc on 2011-04-18
Sorry, ive been busy and forgot I asked...
SledgeHammer, I guess I could somehow add whatever happens in the DBUS main loop to my main loop, but my loop has so many other things in it that make my shell a shell (like the raw_input) that I can't simply replace it
StephenF, I'm trying that right now, and I'll edit with the results.

EDIT: I'm afraid I still don't quite understand where i would put loop.run() in your code StephenF :(
EDIT 2: I am still using raw_input instead of sys.stdin.readline because the latter returns
```
Traceback (most recent call last):
  File "/home/mike/git/DOSPrompt/dosprompt.py", line 150, in <module>
    try: cmd = sys.stdin.readline()
IOError: [Errno 11] Resource temporarily unavailable

```
and I don't think it would work with readline anyway.

---

### Post by Crazedpsyc on 2011-04-22
bump

---

### Post by StephenF on 2011-04-22
Your program is already using D-Bus so why not just use the dbus-send command line program to do the console communication?

---

### Post by Crazedpsyc on 2011-04-29
Oh, I never really thought of that :D
Its not very "pythonic", but it'll do
Thanks!

EDIT: :( How do I use dbus-send?
I have the main loop running in my program with the DBus interface up.
I can access it and use its methods from d-feet, but dbus-send doesn't do anything when I run it.

My paths, ifaces, etc:
```
DBUS_BUSNAME = "org.dosprompt.DOSprompt"
DBUS_IFACE = 'org.dosprompt.DOSpromptInterface'
DBUS_PATH = '/org/dosprompt/DOSprompt/DOSprompt'
```
(the method is 'set_title' and it takes one string)

and the dbus-send command I am trying:
```
dbus-send --dest=org.dosprompt.DOSprompt /org/dosprompt/DOSprompt/DOSprompt org.dosprompt.DOSpromptInterface.set_title string:'title'
```

---

### Post by StephenF on 2011-04-30
> **Crazedpsyc said:**
> How do I use dbus-send?
Try it with the --print-reply option. It could yield some useful information.

---

### Post by Crazedpsyc on 2011-05-02
Actually, the --print-reply option makes it work! I tried it several times with and without --print-reply, and the method only worked when I used --print-reply!

---

### Post by SledgeHammer_999 on 2011-05-02
I have to offer a different approach.

Use the API to **not** set-up a glib-mainloop automatically. Instead call the equivalent dbus-poll() functions from your custom mainloop regularly to see if there are any new events that need processing...

---

