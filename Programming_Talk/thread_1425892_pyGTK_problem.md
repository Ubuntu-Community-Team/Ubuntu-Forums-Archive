---
title: "pyGTK problem"
date: 2010-03-09
forum: Programming Talk
---

### Post by armen_shlang on 2010-03-09
Hi Everyone,
I have a python program which uses pyGTK for the GUI.

setup:
One button goes into a while loop and I'd like it to stop when i press another button. 

problem:
But when i get into the while loop, the program halts until the task for that function call is finished. how can i send the while loop in the background so my GUI can respond when i press the stop button to stop the while loop?

Thank you,
-Armen

---

### Post by OgreProgrammer on 2010-03-09
A while loop assumes full control. Nothing outside of that loop(at least in the program) has any chance of acting. 

So you need to simulate a while loop. Generally you set a variable saying that a condition is true, then you use an if to repeatedly do an action.

---

### Post by armen_shlang on 2010-03-09
I didn't quite understand what you exactly mean.
let me show you a sudo-code of what i have:

button start handler:
 while( t_check == 1)
   receive_data = from bluetooth
   send_to_wifi(receive_data)


button stop handler:
 global receive_data
 receive_Data = 0

how can i use if I'm consistently receiving and sending the data?

---

### Post by spupy on 2010-03-09
You can have a run flag. The looping functions checks the flag each iteration - if it is True, go on; otherwise break the loop. That is in the handler of the first button.
The handler of the second button (the stop button), sets the flag to False. The loop will then break next time.

Here is a simple pseudocode:
```
start button handler:
while run_flag:
do_whatever_you_do_in_the_loop

stop button handler:
run_flag = False
```

---

### Post by armen_shlang on 2010-03-09
Oh, I posted my code wrong, damn, im so sorry. the stop button makes t_check = 0 .
so spupy, the code you have is what i implemented, but it would still not allow me to push the stop button. is there a way so to make it run in the background as a thread? and stop the thread using the stop button?
-Armen

---

### Post by spupy on 2010-03-09
> **armen_shlang said:**
> Oh, I posted my code wrong, damn, im so sorry. the stop button makes t_check = 0 .
so spupy, the code you have is what i implemented, but it would still not allow me to push the stop button. is there a way so to make it run in the background as a thread? and stop the thread using the stop button?
-Armen

Yes, it is possible. I myself am relatively new to python, so I haven't worked with threads. Look into the documentation, or some examples.
You basically do, "start this method in a separate thread". Then you can use the run_flag and stop the thread (with some stop() method of the thread object, I guess).

As far as I know, the gui has its own thread, it is taking care of this thread by itself. It seems your loop is making this thread busy. Running that loop in another thread should solve the problem.

---

### Post by __init__ on 2010-03-10
> **armen_shlang said:**
> Oh, I posted my code wrong, damn, im so sorry. the stop button makes t_check = 0 .
so spupy, the code you have is what i implemented, but it would still not allow me to push the stop button. is there a way so to make it run in the background as a thread? and stop the thread using the stop button?
-Armen

Working with threads in python is simple.
```

from threading import Thread

stop = False

def perform():
    while not stop:
        # do something

def start_button_clicked(...):
    stop = False
    thread = Thread(target=perform, name='Thread')
    thread.setDaemon(True)
    thread.start()

def stop_button_clicked(...):
    stop = True

```

---

### Post by nvteighen on 2010-03-10
And why not take advantage from the gtk main loop?

You set the flag at the button's "clicked" handler and for the second button assign a function for "clicked" that reads from bluetooth only if the flag is True...?

In PyGtk, you're relying on the GLib thread and signals system... use it!

---

### Post by SledgeHammer_999 on 2010-03-10
Or if you don't want to use threads then you could every eg 500 iterations of your loop do the equivalent of [g_main_iteration()](http://library.gnome.org/devel/glib/stable/glib-The-Main-Event-Loop.html#g-main-iteration) until [g_main_context_pending()](http://library.gnome.org/devel/glib/stable/glib-The-Main-Event-Loop.html#g-main-context-pending) returns false. But you must be careful of code re-entrance.

---

### Post by Left hand of Gaia on 2010-03-20
Similar (yet different) to the originators issue, I'm trying to run a loop only while a button is pressed.

Specifically I'm trying to have a seek button that updates a progressbar (HScale won't work here) by a fixed amount while the button is pressed, and calling an update function when the button is released.  

The issue is in my understanding of how to run a iteration loop (increment, sleep a tenth of a second, repeat) ONLY while the button is pressed.

Suggestions?

As for the originator, I'd suggest threading, specifically something like what is found [here]("http://g-off.net/software/a-python-repeatable-threadingtimer-class")

---

### Post by Tony Flury on 2010-03-20
You don't need threads.

What you need to do is every time round your while loop - you need to process the gtk input queue as suggested by SledgeHammer_999

---

### Post by SledgeHammer_999 on 2010-03-20
Here's a suggestion that will be fine if you don't need REALLY accurate timing.

1. connect to the "pressed" signal of the button.
2. in the "pressed" signal handler create a timer that will call every 100ms a specific function in your code(that function will update the progressbar each time it's called)
3. connect to the "released" signal of the button
4. in the "released" signal handler disconnect the timer you made earlier.

---

