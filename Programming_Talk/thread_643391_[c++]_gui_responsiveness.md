---
title: "[c++] gui responsiveness"
date: 2007-12-17
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-12-17
The past several weeks I've been coding using wxwidgets in Gutsy. But I think my question/problem applies to [almost] every gui application.

Here's an example of gui [un]responsiveness:
Imagine you have a window which has a **listbox** and a **checkbox**. The listbox is populated with several items, let's say 700 items. When you click the checkbox a function is called which sorts alphabetically the items in the listbox. The problem starts here:
When this function is called the window is practically "frozen" for 1-2 full seconds.

I think I understand why this happens. And the only solution in my head to solve this, is to make the app multi-threaded and use one thread for code execution and another for gui stuff.

Is there another way? Will the "multithreading" aproach work? Is this more of a wxWidgets' problem rather than a general gui problem?

thank you for your time.

---

### Post by aks44 on 2007-12-17
You should read [this thread]("http://ubuntuforums.org/showthread.php?p=3612446") (and IMO specifically [this post]("http://ubuntuforums.org/showthread.php?p=3621110") where I explain how GUIs work under the hood).

Now when it comes to wxWidgets, I never used that so I can't really help. But wxWidgets *should* have an equivalent to Delphi's Application->ProcessMessages() and Qt's QApplication::processEvents() though.

If you choose the multithreading approach, be sure that you don't update the GUI from another thread than the main (message loop) one or you're pretty much screwed(*), since GUI libraries are usually not designed for concurrent programming.

(*) unless you want to send raw messages to the main thread, but in this case you'll have to give up the platform independence that wxWidgets gives you.


I hope the link I provided clarifies this matter, feel free to ask if anything isn't clear enough.

---

### Post by sonofusion82 on 2007-12-17
> **SledgeHammer_999 said:**
> 
Here's an example of gui [un]responsiveness:
Imagine you have a window which has a **listbox** and a **checkbox**. The listbox is populated with several items, let's say 700 items. When you click the checkbox a function is called which sorts alphabetically the items in the listbox. The problem starts here:
When this function is called the window is practically "frozen" for 1-2 full seconds.


well, multi-threading will be an easy way to solve the problem, but it might also give some problems of itself when it comes to sharing data between threads and also like what aks44 has said about GUI toolkits and thread safety.

anyway, for 700 items to take 1-2 secs to sort? hmm... you might want to reconsider the design of your program and the choice of algorithm to speed things up a bit. if the program can be optimized nicely, you might be able to get away without using multi-threading.

---

### Post by DavidBell on 2007-12-18
Sorting 700 items should only take, I dunno, maybe a few milliseconds. *But* if you use the list as your holding area for your sorting it could be very slow, if it refreshes the GUI view after each change (swap) in the list... So if that is the case it is better cache the values in a memory array, sort them there, then completely replace the list in one hit.

I don't suppose you can just create the Listbox with **wxLB_SORT** window style? I would have thought there would be a Sort method too, but can't find one.

DB

---

### Post by Majorix on 2007-12-18
I would reconsider the algorithm that sorts the list. Bubble sort is not always the best approach.

---

### Post by SledgeHammer_999 on 2007-12-18
@aks44
I understood your explanation very well. But I have a question that is risen from that. Let's say you have two buttons. you click the first button which calls a lenghty function. This function contains enough "processevents" commands that make the gui responsive again. But while this lengthy function still executes and while the gui is still responsive you click the second button. What happens then? Does it wait for the first function to finish or does it execute it's function. If it's starting to execute it's function before the other function finishes, doesn't this make my program multi-threaded?

@sonofusion82
well my program is very small and 'simple' so I won't do any multithreading.(plus I don't want to start another adventure understanding multithreading)

The sorting function might be faster than 1-2 seconds but freezing is really noticeable.

@DavidBell
Well yeah I am directly rearranging the items in the list. Your suggestion about using an array is pretty interesting. **wxLB_SORT** is out of the question I want to sort it on demand not on creation time.

---

### Post by aks44 on 2007-12-18
> **SledgeHammer_999 said:**
> Let's say you have two buttons. you click the first button which calls a lenghty function. This function contains enough "processevents" commands that make the gui responsive again. But while this lengthy function still executes and while the gui is still responsive you click the second button. What happens then? Does it wait for the first function to finish or does it execute it's function.

The second function will execute "inside" the processEvents, ie. while the first function is "paused in order to handle massages".


> **SledgeHammer_999 said:**
> If it's starting to execute it's function before the other function finishes, doesn't this make my program multi-threaded?

It doesn't launch another thread, all code executes in the main (message-handling) thread:
```
Main application loop
  Some lengthy event (in response to a user action)
    processEvents() inside the lengthy event
      Handle any event (possibly in response to user action)
    back to the original lengthy processing
    processEvents() inside the lengthy event
      ... and so on
```

This is why you really need to be careful when running a processEvents()-like function, as this allows the GUI library to execute *any* event, possibly the same you're already running. I can't but stress out that you should make sure that your code is fully re-entrant (which is almost impossible to achieve in GUIs, as they are *the* definition of "stateful" ;)) or that you disable conflicting controls ASAP so that when you re-enter the message loop you don't end up handling unwanted messages.


The "do something" / "cancel" button pair I used as an example in the other thread is a good example of that:
- originally, "do something" will be enabled and "cancel" will be disabled
- as soon as you enter the "do something" event you should disable the corresponding button, and enable the "cancel" button
- if the user clicks "cancel", next time you'll call processEvents() the corresponding function will be called (which should set a boolean flag somewhere, and disable the "cancel" button too)
- your "do something" function regularly checks that boolean flag, when it is true it aborts
- in all cases, when "do something" exists you may want to re-enable "do something" and make sure that "cancel" is disabled again

---

### Post by engla on 2007-12-18
Assuming you have your data model in an array, you sort that quickly. Then you could load the data into the list view lazily, i.e pieces at a time; some gui apis even have a callback for this, some don't.

So, to use your normal event loop, you could do:
* Sort the model
* Update the view with the first few entries (~20)
* register an idle callback in the event loop called feed_data

in feed_data:
* Load another chunk into the view
* If the model is fully loaded, unregister the idle callback

The process would need a context/state variable to keep track of how many items are loaded, but normally that can be passed as context to the idle callback. An idle callback is something that gets called in the normal event loop if no events are queued, and it is available for example in gtk from gobject, and there is probably something in wxwidgets too.

---

### Post by psusi on 2007-12-18
> **SledgeHammer_999 said:**
> @aks44
I understood your explanation very well. But I have a question that is risen from that. Let's say you have two buttons. you click the first button which calls a lenghty function. This function contains enough "processevents" commands that make the gui responsive again. But while this lengthy function still executes and while the gui is still responsive you click the second button. What happens then? Does it wait for the first function to finish or does it execute it's function. If it's starting to execute it's function before the other function finishes, doesn't this make my program multi-threaded?

It makes it reentrant, not multithreaded.  The difference is that function1() and function2() are not executing in parallel; function1() gets to a point in the middle of its execution, and then it ends up calling function2() ( via the process events function ), which does its thing, and then returns to function1().  

What you have to watch out for is that during the processing of events, function1() could be re entered if they click the button again, or some other function can be called.  You have to be very careful about what data function1 manipulates and be sure that while processing other events, no other code manipulates that same data, and changes it out from under function1.  Generally this can be done by setting a flag that indicates function1 is running, and the first thing function1 does is check that flag, and if it is set, just return immediately.  Other functions that share data with function1 need to check the flag to and avoid accessing that data.  This may be done by disabling any controls that could result in those functions being called whenever function1 is running.

> **SledgeHammer_999 said:**
> 
@DavidBell
Well yeah I am directly rearranging the items in the list. Your suggestion about using an array is pretty interesting. **wxLB_SORT** is out of the question I want to sort it on demand not on creation time.

Yea, you need to use qsort or something on the array of strings directly, then shove the new list into the control.  This will be MUCH faster and should allow you to avoid this problem entirely.  Using this method the ui should remain responsive even with a few thousand items in the list.  You also might see if the list widget already has its own internal sort method you could call.

---

### Post by [h2o] on 2007-12-18
I haven't touched wxWidgets, but for GTK I remember that it is recommended that for big updates to a list you should disconnect the model from the view, then do your transformations (sorting, in this case) and then reattach the model to the view again.
Maybe this approach works in wxWidgets as well?

---

### Post by DavidBell on 2007-12-18
> **SledgeHammer_999 said:**
> 
Well yeah I am directly rearranging the items in the list ..... 

Well the listbox *could* be getting a signal to refresh the view every time you move an item, that might be thousands of times to sort 700 items depending how you do it. These refreshes may all be done completely, or abandoned half way through when a new signal comes through, depends on how the listbox works - but keep in mind wx supports multiple widget sets, so often has to go for the lowest common denominator.

At any rate it's a lot of refreshing, and as that much more expensive than moving data/pointers around I reckon that's where you problem is.

DB

---

### Post by SledgeHammer_999 on 2007-12-18
At this point I have to say something: I thank you all for your precious information because it *REALLY* helped me to understand(to some degree) how gui-things work.

Now more questions:

@aks44
What happens if the second function has a processEvents()? Obviously it allows other functions to execute. But is there any chance that it will let the first function execute until the next(in 1st function) processevents() call?

Now regarding the avoidance of reentrance:
Well if you don't disable the button that is clicked in order to avoid reentrance then you are stupid. This isn't hard to figure out, provided that you really understand how the message loop works. But there is another reentrance-danger that it isn't often obvious. Let's say that while you sort the really large list the user adds a new item or presses the "Move Up"/" Move Down" buttons. Then you have a problem and you must be carefull and set/check flags all the time. For me an easy way to get around this(in my specific example), is just disable the whole window and enable it just before the function ends!!!

---

### Post by SledgeHammer_999 on 2007-12-18
For those interested I had a quick look in the wx's docs and I think I found it(I am not able to test this now):
> 
wxWindow::Update

virtual void Update()

Calling this method immediately repaints the invalidated area of the window and all of its children recursively while this would usually only happen when the flow of control returns to the event loop. Notice that this function doesn't invalidate any area of the window so nothing happens if nothing has been invalidated (i.e. marked as requiring a redraw). Use Refresh first if you want to immediately redraw the window unconditionally.

---

### Post by psusi on 2007-12-18
> **SledgeHammer_999 said:**
> 
What happens if the second function has a processEvents()? Obviously it allows other functions to execute. But is there any chance that it will let the first function execute until the next(in 1st function) processevents() call?

Then you can end up with a call stack that looks like this:

```

function1
  processevents
    function2
       processevents
         function1

```

That's what I meant by reentrancy.  The function can end up recursing into itself and start manipulating the same data that it was already in the middle of manipulating.  In other words, the thread of execution re enters a function it is already in.

> **SledgeHammer_999 said:**
> 
Now regarding the avoidance of reentrance:
Well if you don't disable the button that is clicked in order to avoid reentrance then you are stupid. This isn't hard to figure out, provided that you really understand how the message loop works. But there is another reentrance-danger that it isn't often obvious. Let's say that while you sort the really large list the user adds a new item or presses the "Move Up"/" Move Down" buttons. Then you have a problem and you must be carefull and set/check flags all the time. For me an easy way to get around this(in my specific example), is just disable the whole window and enable it just before the function ends!!!

Yes, you have to look very carefully at anything you touch while processing that message ( possibly in another function that calls the one that calls processevents() ) and make sure that none of the code can be messed up by being reentered.  Getting this right in all cases can be very difficult.  

In the example you gave of adding an item while the sort is going on, you could resolve that by checking to see if that happened just after the processevents() call, and if a new item was added, restart the sort from the beginning.  This is assuming that you switch the sort to be internal rather than in place in the list box, because that way you are sorting one set of data while the add function adds to the list box itself, so they do not interfere with each other.  After processevents() if you detect a new item was added, you can just stop the sort, throw out that data, and restart with the new contents of the list box.

---

### Post by aks44 on 2007-12-18
> **psusi said:**
> <snipped>Thanks psusi, you saved me quite a bit of typing... ;)


> **SledgeHammer_999 said:**
> For me an easy way to get around this(in my specific example), is just disable the whole window and enable it just before the function ends!!!
The easy way would indeed be to disable the whole window (erm, make it "*all the controls in the window*"...). However in complex GUIs you theoretically could disable only some parts, and leave other parts enabled. But I agree this case is probably quite rare, and most of the time you'll end up disabling the whole window (or setting a global(*) flag that you test in each and every event handler, which has the same result).

(*) "global" to the window object of course, not to the whole application.


> **SledgeHammer_999 said:**
> For those interested I had a quick look in the wx's docs and I think I found it
Don't confuse: the Update() member you mention behaves like your window received & handled *one* PAINT message. But it won't handle other messages.
Granted for your purpose this may fit well (although I'm not even sure of that... if XWindows has the same set of messages than MSWindows then your window will freeze anyway if you move/resize it during the lengthy operation) but technically this is not the same.



> **SledgeHammer_999 said:**
> Now regarding the avoidance of reentrance
Re-entrance is by far not as complex as concurrent (multithreaded) programming but they have many common issues. As already stated, correct mutual exclusion is one of them. The good part with "simple" re-entrance is that you can just use boolean flags, and you barely have to fear dead/live-locks. :)

---

### Post by engla on 2007-12-20
I still think the lazy loading idea might be interesting. You have any comment on that or any experience aks44? I've seen APIs where you would have to each such large-dataset view you would have a datasource object, and the datasource would provide the current length of the data and a method to get a piece of it ("slice" in python terminology). Now the list widget in such a "smart" api would self lazily load data from its assigned datasource, in such a way not to block the event loop. But this behavior is not at all hard to emulate even though you don't have the "smart" widget around, just add some state variables and wrap this up in some modern Object oriented logic.

---

### Post by aks44 on 2007-12-20
> **engla said:**
> I still think the lazy loading idea might be interesting. You have any comment on that or any experience aks44?

TBH I don't have much hands-on experience in GUIs (and absolutely NO experience when it comes to Linux GUIs), as I'm more of a server guy. I only know the theory... :)

But I know for a fact that the guys developing the GUI client at work use a Delphi control that only handles the nodes that are in the current viewport. This is quite similar to the "sliced list box" you mention, except that their control doesn't even lazy-load in the background, it fully works on-demand.

I'll ask them what's the actual name of this control, but I doubt Delphi code can easily be ported to Linux... :|


_EDIT_
here it is: [VirtualTreeView from Soft-Gems]("http://www.delphi-gems.com/index.php?option=com_content&task=view&id=12&Itemid=38") (LGPL'ed)

---

### Post by SledgeHammer_999 on 2007-12-20
I think I finally found it. From the wx's docs:
> wxApp::Yield

bool Yield(bool onlyIfNeeded = false)

Yields control to pending messages in the windowing system. This can be useful, for example, when a time-consuming process writes to a text window. Without an occasional yield, the text window will not be updated properly, and on systems with cooperative multitasking, such as Windows 3.1 other processes will not respond.

Caution should be exercised, however, since yielding may allow the user to perform actions which are not compatible with the current task. Disabling menu items or whole menus during processing can avoid unwanted reentrance of code: see ::wxSafeYield for a better function.

Note that Yield() will not flush the message logs. This is intentional as calling Yield() is usually done to quickly update the screen and popping up a message box dialog may be undesirable. If you do wish to flush the log messages immediately (otherwise it will be done during the next idle loop iteration), call wxLog::FlushActive.

Calling Yield() recursively is normally an error and an assert failure is raised in debug build if such situation is detected. However if the onlyIfNeeded parameter is true, the method will just silently return false instead.

---

### Post by engla on 2007-12-20
> **aks44 said:**
> TBH I don't have much hands-on experience in GUIs (and absolutely NO experience when it comes to Linux GUIs), as I'm more of a server guy. I only know the theory... :)

But I know for a fact that the guys developing the GUI client at work use a Delphi control that only handles the nodes that are in the current viewport. This is quite similar to the "sliced list box" you mention, except that their control doesn't even lazy-load in the background, it fully works on-demand.

I'll ask them what's the actual name of this control, but I doubt Delphi code can easily be ported to Linux... :|


_EDIT_
here it is: [VirtualTreeView from Soft-Gems]("http://www.delphi-gems.com/index.php?option=com_content&task=view&id=12&Itemid=38") (LGPL'ed)
Exactly something like that :)! Interestingly they refer to this as unique, but NSTableView from Apple's Cocoa does almost exactly the same things. This is more interesting since it is OpenSource, I don't think GNUStep has apple's modified NSTableView.

---

### Post by aks44 on 2007-12-20
> **SledgeHammer_999 said:**
> I think I finally found it. From the wx's docs:
Looks like you indeed found it. :) Although on Windows (Borland VCL) I don't remember there's any re-entrance limitation (but I may well be wrong).


> **engla said:**
> Interestingly they refer to this as unique, but NSTableView from Apple's Cocoa does almost exactly the same things.
Well, I'd guess it's a unique feature _*on Windows*_... :)

---

