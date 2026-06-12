---
title: "[Python] How to close the gtk window?"
date: 2009-10-21
forum: Programming Talk
---

### Post by baskar007 on 2009-10-21
i am new to python
i want to close the window when i call a function

#!/usr/bin/env python
import gtk,time

def caller(data=None,dat2=None):
    gtk.main_quit()
    print "will sleep"
    time.sleep(3)
    print "Over"
    
win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,None)
win.add(button)
button.show()
win.show()
gtk.main()

after i clicked the "start" button the window does not close until the time.sleep(3) process finish.

i want to close the window when i clicked the button
how can i do ?
is there is any wrong with code?

help me friends 
please.

---

### Post by Arndt on 2009-10-21
> **baskar007 said:**
> i am new to python
i want to close the window when i call a function

#!/usr/bin/env python
import gtk,time

def caller(data=None,dat2=None):
    gtk.main_quit()
    print "will sleep"
    time.sleep(3)
    print "Over"
    
win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,None)
win.add(button)
button.show()
win.show()
gtk.main()

after i clicked the "start" button the window does not close until the time.sleep(3) process finish.

i want to close the window when i clicked the button
how can i do ?
is there is any wrong with code?

help me friends 
please.

This seems to do what you want. If it's done the right way, I don't know - I don't know gtk.

```
import gtk,time

def caller(data=None,dat2=None):
    gtk.main_quit()
    dat2.destroy()
    print "Over"

win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,win)
win.add(button)
button.show()
win.show()
gtk.main()
print "will sleep"
time.sleep(3)
print "Over2"

```

---

### Post by baskar007 on 2009-10-21
thanks, 
my coding is right. the problem is

well i'll explain my question from your code:

```

import gtk,time

def caller(data=None,dat2=None):
    #closing window
    gtk.main_quit()
    dat2.destroy()
    # after window closed, do this job
    print "sleep will start"  #-------------add this code
    time.sleep(5)   #-----------------------add this code
    print "Over"

win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,win)
win.add(button)
button.show()
win.show()
gtk.main()
print "will sleep"
time.sleep(3)   #-----------------------unwanted
print "Over2"   #------------------------unwanted

```

i need
when i pressed the start button the window should close before printing 'print "sleep will start"  '
but in this code window does not close when
```

gtk.main_quit()
dat2.destroy()
```  
called, only closing after time.sleep(5) 


i just want to close my window when gtk.main_quit() called, without doing next line jobs.

---

### Post by Tony Flury on 2009-10-21
The reason that the window does not close is because GTK works on a queue, and the destroy window call puts a message on a queue, and that queue is only processed once your caller function completes.

If you want the destroy function to operate immediatley, you will have to process the queue :

```

while gtk.events_pending():
   gtk.main_iteration(False)

```

just after you do the destroy.

I would not do the main_quit before you do the destroy - do it after the code snippet above.

---

### Post by baskar007 on 2009-10-22
> **Tony Flury said:**
> The reason that the window does not close is because GTK works on a queue, and the destroy window call puts a message on a queue, and that queue is only processed once your caller function completes.

If you want the destroy function to operate immediatley, you will have to process the queue :

```

while gtk.events_pending():
   gtk.main_iteration(False)

```

just after you do the destroy.

I would not do the main_quit before you do the destroy - do it after the code snippet above.

thank you very much,
i did this
```

if gtk.events_pending() == True:
                gtk.main_quit()
                try:
                    #Do the job here 
                    load.dl_start(local,host,remote).start()
                except:print "ERROR !!! XXXXXXXXX!!!"
            else:
                print "'else' rule  running"
                load.dl_start(local,host,remote).start()

```

once again thank you.

---

### Post by Tony Flury on 2009-10-22
The problem with your solution is that you are making the assumption that there is only one event queued, whereas there could be several - including system generated events, and user generated ones - and you actually throw them all away - which might be "safe" now, but actually is probably not a good idea.

I would have expected your code to be something like : 

```

import gtk,time

def caller(data=None,dat2=None):
    #closing window
    dat2.destroy()
    # Consume all pending events - include the window destroy
    while gtk.events_pending():
        gtk.main_iteration(False)
    gtk.main_quit()
    # after window closed, do this job
    print "sleep will start"  #-------------add this code
    time.sleep(5)   #-----------------------add this code
    print "Over"

win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,win)
win.add(button)
button.show()
win.show()
gtk.main()
print "will sleep"
time.sleep(3)   #-----------------------unwanted
print "Over2"   #------------------------unwanted

```

Glad you were able to solve the problem - though.

---

### Post by baskar007 on 2009-10-24
> **Tony Flury said:**
> The problem with your solution is that you are making the assumption that there is only one event queued, whereas there could be several - including system generated events, and user generated ones - and you actually throw them all away - which might be "safe" now, but actually is probably not a good idea.

I would have expected your code to be something like : 

```

import gtk,time

def caller(data=None,dat2=None):
    #closing window
    dat2.destroy()
    # Consume all pending events - include the window destroy
    while gtk.events_pending():
        gtk.main_iteration(False)
    gtk.main_quit()
    # after window closed, do this job
    print "sleep will start"  #-------------add this code
    time.sleep(5)   #-----------------------add this code
    print "Over"

win=gtk.Window()
win.connect("destroy", lambda w: gtk.main_quit())
button=gtk.Button("start")
button.connect("clicked",caller,win)
win.add(button)
button.show()
win.show()
gtk.main()
print "will sleep"
time.sleep(3)   #-----------------------unwanted
print "Over2"   #------------------------unwanted

```

Glad you were able to solve the problem - though.
thanks

---

