---
title: "PyQt4 equivilent to time.sleep?"
date: 2010-04-14
forum: Programming Talk
---

### Post by Stev0 on 2010-04-14
Is there an equivalent to timer.sleep in PyQt? I've an application that I've written in Python 3.1.1, using PyQt4. I originally wrote it for command line use, then decided to add the GUI stuff later on. In it's original form, I was using timer.sleep() to cause a small segment of code inside a try/except block to pause momentarily. Now that I've added the Qt GUI, I found that for some reason timer.sleep() was causing my application hang for some reason. 

It was suggested to me to use QTimer. I implemented that into my code, but the documentation for that particular class is kind of shoddy, and while I understand the basics of using it, putting it into my code, required me to change up alot of other things in order to meet the criteria for Qtimer.timeout.connect(), which tbh was severely interfering with what the loop was originally intended to do. So, how does one make applications pause whilst using PyQt? Again, I just really want to do something like time.sleep(), without having to worry about creating additional functions and signals. Any ideas?

---

### Post by Quikee on 2010-04-14
QThread.sleep() maybe...

---

### Post by Zugzwang on 2010-04-14
@OP: Unless I miss something important, you won't get around restructuring your program in the way you describe (or in a similar way, e.g., by using threads). The reasons is that "not having your application freezing during some operation" inherently induces parallelism in your application. For example what should happen in the user closes the window why you are waiting? In order to deal with this situation, your application must have some well-defined behaviour, and this requires restructuring your program to deal with parallelism.

Another way to accomplish what you want is to start a thread that executes the "sleep" command in its first line. You must however then take care of the situation that indeed some signal can occur while you are sleeping.

---

