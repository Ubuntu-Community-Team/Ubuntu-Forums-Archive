---
title: "Logic separate from GUI - Limits?"
date: 2010-11-01
forum: Programming Talk
---

### Post by kentonspr on 2010-11-01
I'm a fairly novice programmer. I've done some Pearl and Python scripting, but haven't really ventured into GUI programming too much. I've heard quite a bit about keeping the GUI and the logic portions of your program separated, but I'm curious about the limits of this.

For example, I'm currently working on an Android application. Its a basic IP subnet calculator. The GUI is going to take input from the user in the form of an IP address, and pass it on to the logic on the program in order to parse the data and generate the information needed. My question is about checking the validity of the data the user is entering in the class that builds the GUI.

Is this a no-no and should I have all of that kind of logic separated into some sort of checking class, or is that a valid type of logic to put into the "Activity", as its called in Android?

Kenton

---

### Post by Mach1723 on 2010-11-01
> **kentonspr said:**
> 
------------
Is this a no-no and should I have all of that kind of logic separated into some sort of checking class, or is that a valid type of logic to put into the "Activity", as its called in Android?

Kenton

I'm no expert :), but I would say input validity checks would make sense as part of the logic of the class, since if you were to ever use this class outside of a GUI you could send input in and not have to worry about checking validiity.

---

### Post by nvteighen on 2010-11-02
In my opinion, the way to think correctly about this would be the following:

The GUI is no different than any text interface or any interface of any sort... So, the GUI should be just a mean to do something, so nothing that's related to the particular feature you want to create should be part of the GUI (the "View"). The GUI class should only include what's particular to its working and the "glue" code that connects it to the "logic" (in Qt and GTK+ programming, these would be the callbacks)... Well, actually some people, like me, like to create a specific class that contains the "glue" code (the "Controller"), but that's not necessary.

In the case of your project, such a sanity check would be useful regardless of what user interface you create, so I'd place it in the "logic" (aka "Model") of your application. 

Sometimes it's useful to think of your code as a command line terminal, where the functions that constitute the "Model" or "logic" are "typed" in the correct order by a "user" that is the GUI code. Not sure if this metaphor works for you but it works a lot for me :)

---

### Post by kentonspr on 2010-11-02
Excellent replies, thanks. 

My goal was to take input in the form of an IP address, and make sure it was correct. It sounds like I should send the data that was input to the "logic" and have it throw an exception back if it is incorrect, at which point the GUI would tell the user to input data that isn't out of range or in the incorrect format.

Kenton

---

