---
title: "[HOW-TO] Easily remove all text on the terminal/command prompt"
date: 2010-10-04
forum: Programming Talk
---

### Post by Pyro.699 on 2010-10-04
Hey all,

I found something that might help a few people out. A quick and easy way to remove all of the text on your terminal. For sure all i know is that it works with python on Linux although im sure it will work in other languages.

All you need to do is print this text **\x1b[H\x1b[2J**, ill also paste the source for a quick 'timer' program that i was using this for:

[php]
#!/usr/bin/python
import threading, datetime, time, sys, random

class Timer(threading.Thread):
    def __init__(self, itemName, doneTime):
        threading.Thread.__init__(self)
        self.name = itemName
        self.time = doneTime
        self.str = ""
        
        self.daemon = True


    def run(self):
        while True:
            now = datetime.datetime.now()
            self.str = "%s: %s"%(self.name, self.time-now)
            time.sleep(0.1)

taskList = []

taskList.append( Timer("       Portal 2        ", datetime.datetime(2011, 2, 9, 00, 00, 00, 00)) )
taskList.append( Timer("Call of Duty: Black Ops", datetime.datetime(2010, 11, 9, 00, 00, 00, 00)) )

for task in taskList:
    task.start()

while True:
    sys.stdout.write( '\x1b[H\x1b[2J' )
    
    out = ""
    for task in taskList:
        out += "%s\n"%task.str
    sys.stdout.write( out )

    time.sleep(0.2)
[/php]

Enjoy
~Cody

---

### Post by worksofcraft on 2010-10-04
That is indeed a handy escape sequence to know :)
Also useful is the command "clear" when there is too much clutter in your console terminal window.

---

### Post by spjackson on 2010-10-05
> **Pyro.699 said:**
> 
I found something that might help a few people out. A quick and easy way to remove all of the text on your terminal. For sure all i know is that it works with python on Linux although im sure it will work in other languages.

All you need to do is print this text **\x1b[H\x1b[2J**,

The escape sequence required may vary depending on the terminal type being used. That is precisely what the terminfo database is for (and formerly termcap). ncurses based programs such as "clear" and "less" use the terminfo database.

---

### Post by luvshines on 2010-10-05
As worksofcraft said "clear" OR ctrl+l, the default shortcut shud be the simplest :)

---

### Post by nvteighen on 2010-10-05
Hm... ncurses is there for a reason: portability. Ok, it's a horrible outdated library that uses a somehow old-fashioned design, but nobody replaced it so we still use it... maybe because it just works nevertheless. For the usual situations a "normal" program needs, I'd always recommend to use that library rather than to perform this by an escape sequence... I'd use that sequence only if ncurses isn't available for some reason (very unlikely to be absent from any UNIX/Unix-like OS) or really strict requirements force me to do so.

---

