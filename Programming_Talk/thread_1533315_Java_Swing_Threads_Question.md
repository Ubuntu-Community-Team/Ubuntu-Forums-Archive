---
title: "Java Swing Threads Question"
date: 2010-07-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-17
I have a Java application which instantiates two completely different objects.  Each object opens a new JFrame and performs rendering on the frame.  Again, the objects and JFrames are completely independent.  Is there a way to allocate more than 1 thread for the Swing Thread?  I know work can be done with Worker classes, but I'd actually like to render with two threads at the same time.  Seems like there should be a way because there is no interaction between the two objects or object frames.

---

### Post by PaulM1985 on 2010-07-17
To me these sound like two different programs and I wonder if it is right fo you to have different processes rather than different threads if the two things are completely independent. Which is clearly more of a design issue. Anyway as a general answer to your question, have two classes which are called start1 and start2 each implementing runnable.  In each create a run method which runs one of each of your frames. In you main function create two threads each taking an object of each of your two starter classes and call run on each of the threads.  Paul

---

### Post by SNYP40A1 on 2010-07-17
That would give me 2 separate threads with each object running on its own thread.  However, in Java, there is only one swing thread and all paintComponent() calls are run on this thread.  So anytime paintComponent() is called, it's running on the single Swing Thread.  In my situation where the painting is on two different JFrames and completely independent, could I simply spawn off a new thread in paintComponent each time and not use SwingUtilities.InvokeLater on the swing calls?  Would this work, or would I need to create different processes?  My understanding of Swing is a bit rusty, but based on this handout:

[http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf](http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf)

---

### Post by kahumba on 2010-07-18
> **SNYP40A1 said:**
> That would give me 2 separate threads with each object running on its own thread.  However, in Java, there is only one swing thread and all paintComponent() calls are run on this thread.  So anytime paintComponent() is called, it's running on the single Swing Thread.  In my situation where the painting is on two different JFrames and completely independent, could I simply spawn off a new thread in paintComponent each time and not use SwingUtilities.InvokeLater on the swing calls?  Would this work, or would I need to create different processes?  My understanding of Swing is a bit rusty, but based on this handout:

[http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf](http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf)

I think that only applies to one component and two threads, and doesn't apply to 2 windows each in a different thread.
That is, when you call repaint() on one window the other one won't be affected, otherwise it would be really silly.

---

### Post by KdotJ on 2010-07-18
> **kahumba said:**
> otherwise it would be really silly.

Indeed surely that only accounts a single component being accessed by two separate threads?
To the OP, have you tried the 2 thread method outlined by PaulM1985 above?

---

### Post by phrostbyte on 2010-07-20
You don't need to implement Runnable. You can create an anonymous class that initialises your windows. I think this is a better approach because you don't put thread specific code into your classes.

---

