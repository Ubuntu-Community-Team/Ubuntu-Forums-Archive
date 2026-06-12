---
title: "Refreshing textEdit box"
date: 2007-10-23
forum: Programming Talk
---

### Post by NeillHog on 2007-10-23
As a Kubuntu newbie I quickly reached the stage of "what I need does not exist" so sat down to write it.
The code is written in Python. The GUI is created with Qt Designer 3.
In my GUI I have a text edit box - textEditInfo - that outouts info as the main function is running.
I have noticed that the box is not refreshed until the function is finished when all the text gets written to it in one go.
I actually wanted the text to appear as things happen.
Is there a way of forcing a refresh during the function.

As always - thanks! With all your help Ubuntu is actually getting to be fun :-)

Neill

---

### Post by aks44 on 2007-10-23
You may need to manually invoke the message-handling loop.

Not sure how Qt does that. I have very limited experience in GUIs, but in Delphi (on Windows) they use Application->ProcessMessages(); IIRC to "unfreeze" the GUI. I'd bet Qt has something quite similar.

Hope this helps (or at least that it can put you on the tracks).

---

### Post by NeillHog on 2007-10-24
OK! Thank you for that. Your answer seems to confirm that a "frozen" GUI is normal and offers me a hint of where to look for a solution. I will do some more sarching tonight.
Thanks - I appreciate all this help.

---

### Post by cwaldbieser on 2007-10-24
> **NeillHog said:**
> OK! Thank you for that. Your answer seems to confirm that a "frozen" GUI is normal and offers me a hint of where to look for a solution. I will do some more sarching tonight.
Thanks - I appreciate all this help.

Not sure what the Python bindings look like, but there is a QApplication::processevents(...) method in the C++ API.

---

### Post by aks44 on 2007-10-24
> **NeillHog said:**
> Your answer seems to confirm that a "frozen" GUI is normal and offers me a hint of where to look for a solution.

To give you a rough idea of what happens under the hood, I'll try to explain how the whole GUI thing works AFAIK.

Keep in mind that I have NO experience on Linux, and that the following applies to Windows. But I'm ready to bet that X / Qt / Gtk follow more or less the same principle, even if details are different.


Let's say your application is already running, and the user clicks a button, types some text or whatever. The windowing system must inform your application that this event occured, and it does so not by directly executing your code, but rather by placing a message in a queue.
It is the application's responsability to check that message queue and handle the messages correctly (in a loop).
Similarly, when your application updates a control (eg. changes the text of a box) it sends messages back to the application message queue indicating what must be done (change text, repaint box, ...).

So far so good: as long as your message-handling loop is running, the incoming messages are handled.

But now, as a consequence of a message (eg. a button has been clicked), your message loop launches a lenghty operation. *Until that operation finishes, no message is handled, so the GUI appears to freeze*.

The trick here to get a smooth ("responsive") GUI is to force the handling of incoming messages *inside* the lenghty operation.
According to cwaldbieser, Qt seems to do that thanks to QApplication :: ProcessEvents().

However there is a catch. Doing that allows your application to handle *any* message, so if the user clicks *again* on the same button the lengthy operation will be started again, even though it is already running. Same applies to other events.

eg. the user clicked "Download", you begin downloading and "unfreeze" the GUI from time to time, but if you didn't disable the button the user can launch the same download again (BAD). Or he could click on the "Cancel" button, which should set a flag somewhere that is checked by the download routine (GOOD).

IOW if you allow recursive message processing, you must ensure that your code is reentrant, and/or take the necessary steps to forbid possible reentrancy (disable controls, ...).



Oh well, I hope this was not too confusing. Feel free to ask for clarifications if you feel so. :)

---

### Post by NeillHog on 2007-10-24
Thank you!

Background information is always useful. I guessed this was how it worked as I (long ago) wrote a DOS program and had to program the whole main loop, event manager and so on myself (Yuk!)

Now it is too late but I will look in to processEvents at the weekend. The tip about disabling buttons is very good. 

Thank you!

---

### Post by NeillHog on 2007-10-27
processEvents works great thank you!

---

