---
title: "[wxPython] Properly Updating Panel Through Threads"
date: 2010-10-28
forum: Programming Talk
---

### Post by Pyro.699 on 2010-10-28
I wasnt too sure what to put as a title -.- Hopefully it made some sense to some people...

Now, ive done as much as i can to try and help isolate the problem and make a simple test for it... There are two files:

[LIST]
[*]newGrid.py - [http://pastebin.com/ArHHh9zc](http://pastebin.com/ArHHh9zc)
[*]test.py - [http://pastebin.com/06wvqRBh](http://pastebin.com/06wvqRBh)
[/LIST]


Everything should work...

As you can see when you add a new row with the normal method, it adds it properly... When you add a new row through a thread it doesn't add it, but the weird part is when you go to sort the columns (Click on one of the header labels) it adds them then (with no data).

newGrid.py is a bit messy and im sorry for that, im still learning how to do GUI's.

Thanks
~Cody

Also: The scrollbars don't appear unless you reseize the window...

---

### Post by Pyro.699 on 2010-10-29
Hey,

Ive been looking online for methods to refresh or repaint the panel... but none of that has helped... Anyone have any ideas?

---

### Post by spjackson on 2010-10-29
It's quite a long while since I used wxWidgets and I never tried updating the GUI from another thread. However, I know that Qt does not let you do this.

I have just had a quick look at the wxWidgets documents [http://docs.wxwidgets.org/trunk/group__group__funcmacro__thread.html](http://docs.wxwidgets.org/trunk/group__group__funcmacro__thread.html); they tell you to wrap your GUI code with wxMutexGuiEnter() and wxMutexGuiLeave(), but not all GUI operations work from a secondary thread on all platforms. Perhaps you just need to call those functions, but I'm not certain.

---

### Post by Pyro.699 on 2010-10-29
Thanks for the reply :)

Tried that and it didn't work ><

Any other ideas?

---

### Post by spjackson on 2010-10-29
> **Pyro.699 said:**
> Thanks for the reply :)

Tried that and it didn't work ><

Any other ideas?
Not really, since I haven't tried updating the gui from another thread, and it's a long time since I used wxWidgets. If I had this problem, I would first see whether the same code works when run from the main thread. Then I'd probably try the wx-users mailing list or possibly the wxPython-users list [http://www.wxpython.org/maillist.php](http://www.wxpython.org/maillist.php) , unless someone else here can help.

---

### Post by spjackson on 2010-10-29
> **Pyro.699 said:**
> 
Tried that and it didn't work ><

Any other ideas?
One further thought is that those functions might only work if the thread that you are updating from is a wxThread. You could try using wxThread instead of your python thread.

However, see this FAQ [http://wiki.wxpython.org/Frequently%20Asked%20Questions#How_do_I_use_multiple_threads.3F](http://wiki.wxpython.org/Frequently%20Asked%20Questions#How_do_I_use_multiple_threads.3F)  "All calls to methods of GUI objects and event  handlers need to happen on the main thread.  In wxPython the main thread  is the one that first imports the wxPython.wx module.  Other threads  can send events to the main thread using wxPostEvent as is done in the Threads sample in the wxPython demo. For more information and examples, please see [LongRunningTasks]("http://wiki.wxpython.org/LongRunningTasks")."

---

### Post by Pyro.699 on 2010-10-29
Thanks again :)

I have spent a great deal of time reading the [LongRunningTasks]("http://wiki.wxpython.org/LongRunningTasks") article and gotten quite a bit of information from it. In-fact I'm using the first example as a model for my real program (using their classes like *WorkerThread* and *ResultEvent*).

I have tried both of the examples that you have provided... It seems that no-matter how i do this it is difficult to update any part of the GUI using threads... I altered the code so that the "test" class was inside the *wx.Frame* class and was called via *win.test* and it still had the same results...

If anyone has a really good method for having long running tasks (without using the examples from the article) i would love to use them...

Thanks again for your help
~Cody

---

