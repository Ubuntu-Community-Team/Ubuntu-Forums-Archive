---
title: "Switching Frames (Java)"
date: 2012-11-11
forum: Programming Talk
---

### Post by kevinharper on 2012-11-11
What is the correct way to switch from one frame to another?

I know that CardLayout can do this, but I don't think it's its intended purpose. I could set a big JPanel that took up 100% of the width and 100% of the height and just switch the panels when the user is ready to go to the next 'screen'/frame.

How do you guys do it?

---

### Post by Javacoder on 2012-11-11
if you mean an installation like wizard of next/previous buttons then your approach is correct, others would make a complete JDialog and use Hide/Show methods on clicking next/previous buttons

Actually card layout is intended for this purpose, switching between panels upon system (state transitions) from state to another which is your case i think.

---

### Post by kevinharper on 2012-11-11
Okay...

What about a program that has a welcome screen an the user can has a few options to click on. Each option has different content than the frame the user is viewing. Would I still be using CardLayout?

I'll have to read up on JDialog. Here's what I have to do:

An instructional support program that has a few frames that a student can access and others that an instructor can access.

A student clicks one of several possible instruction-sets and he/she is directed to a frame w/ the information for the instruction-set he/she selected. I'm looking for a way to navigate from frame to frame within a program. I hope I gave a clearer scenario.

---

### Post by Javacoder on 2012-11-11
this is called cascading style menu system, which mean you have a tree structure menu like this the one below, this can be implemented as a JTree structure with privileges that loads Teacher Tree or Student Tree according to UserID type (teacher or student)

Or

you can make the old VisualBasic-Like systems where after user login (teacher or student), you start a state transition JPanels using Card layout, that moves from Teacher main screen contains buttons for options, then after click button it goes to next state with option button and so on till reach target screen (state) that teacher shall input items in and same for students

These are the main menu-tree/control-panel styles of arranging system screens or states to collect user inputs

Menu Tree
Root:
---Teacher
   |
   --- Option 1 or State 1 or Frame 1
   --- Option 2 or State 2 or Frame 2
---Student
   |
   --- Option 1 or State 1 or Frame 1
   --- Option 2 or State 2 or Frame 2

---

### Post by kevinharper on 2012-11-11
Not JTree... I want the user to log into the system.

If user is student, he/she sees a screen (window/frame/gui) with a list of images or buttons. Each one corresponds to a different instruction module. When student clicks it, student simple goes to another frame (window/gui) w/ intro to the instruction module.

Same for instructor. When he/she logs in, he/she is directed to a frame that has several options (buttons or images). When he/she clicks on one of these buttons, a new frame is displayed with requested information.

Just like a wizard but without the unidirectional progress. Would CardLayout then be the appropriate way to navigate from from frame to frame?

---

### Post by kevinharper on 2012-11-11
I think I found a definitive answer... 

[http://www.dreamincode.net/code/snippet4460.htm](http://www.dreamincode.net/code/snippet4460.htm)

Basically set up the various JFrames and setVisible(false/true) depending on which one needs to be displayed. I now understand that's what you meant by:
> others would make a complete JDialog and use Hide/Show methods on clicking next/previous buttons

Thank you for your time!

---

