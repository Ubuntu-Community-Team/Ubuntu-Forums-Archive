---
title: "[Java] Swing and observers and threads"
date: 2011-07-09
forum: Programming Talk
---

### Post by SpinningAround on 2011-07-09
There is something wrong with a gui that I have created, the strange part is that some components simply disrepair. There is a JPanel (1*) that contains two JScrollPane, one contains a JPanel and the other contains a JEditorPane. The wired this is that 1*  display as it should but all components that this JPanel contains isn't displayed at all. The code isn't generating any exception that might explain it.

I started guessing what might be the cause of this and thought that it might be related to the observer pattern. Many of the components displayed is an observer and these might receive updates from different threads at the same time.

The observer pattern consists of about 10 different events and an observer can listen to one or more of these events. Also, one of the components display a countdown clock, this is done by using a thread.

My question is if this can be the cause of the problem, that swing simply can't handle multiple threads or might there be some other cause? More impotently is how to solve the problem?

---

### Post by dwhitney67 on 2011-07-09
> **SpinningAround said:**
> 
My question is if this can be the cause of the problem, that swing simply can't handle multiple threads or might there be some other cause?

One can use threads in a Java program that employs swing.  As for the cause for the issue in your program, I can only guess.  Concurrent access to data should be syncronized.

> **SpinningAround said:**
> 
More impotently is how to solve the problem?
Please deposit $0.25 into my crystal ball, and then I will get back to you with the solution.

---

### Post by SpinningAround on 2011-07-09
> **dwhitney67 said:**
> One can use threads in a Java program that employs swing.  As for the cause for the issue in your program, I can only guess.  Concurrent access to data should be syncronized.


Please deposit $0.25 into my crystal ball, and then I will get back to you with the solution.

Those this include the JFrame that contains the components, might it be caused by Component A, B, C all try to update at the same time?

There is a control unit that controls the gui, handle request to and from it. Would it do any difference if I only let this control unit receive all updates and then update each component first A then B then C.

I'm not asking anyone to write the code that solves it simply what I should do to solve it.

EDIT:
Since it might be bit tricky to debug the code that I have written, might it be easier if I learned how to write a proper gui. Would anyone recommend a guide regarding gui that include how to handle updates from different sources?

EDIT2:
Finally solved it but it wasn't related to threads, but there probably something since it don't update properly. So I will follow Reiger advice with EvenQueue. Thanks :)

---

### Post by Reiger on 2011-07-09
As a rule of thumb all Swing GUI operations should be done on the AWT Event Dispatch Thread (EDT). This implies that you must make all alterations to the GUI itself &#8220;cheap&#8221; so that the GUI doesn't block when you modify it, and that long running tasks should be delegate to worker threads or something similar. In particular you should not perform I/O on the EDT.

The typical way of ensuring that your GUI operations occur on the EDT --regardless from which thread the GUI update is requested-- is to schedule a new job in the AWT EventQueue:
```

java.awt.EventQueue.invokeLater(new Runnable() {
    @Override
    public void run() {
        // change text in myJLabel. Must be a JTextComponent, obviously.
        myJLabel.setText("hello world!");
    }
});

```

---

