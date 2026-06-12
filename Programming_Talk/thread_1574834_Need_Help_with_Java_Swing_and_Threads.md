---
title: "Need Help with Java Swing and Threads"
date: 2010-09-14
forum: Programming Talk
---

### Post by BlackSwordD2 on 2010-09-14
I'm doing a project for class that needs to implement the swing class. But i want to add an animation frame.

as it stands at the moment, i have a working GUI and a working animation thread that extends JFrame. However when i add this frame to by GUI's frame it covers all that was originally there.

I want to have this animation frame centered (using BorderLayout) with several other JPanels surrounding it

could anyone help point me in the right direction?

---

### Post by BlackSwordD2 on 2010-09-14
i see my problem is trying to add a window to a container... how can i do something similar but avoid this?

---

### Post by PaulM1985 on 2010-09-15
It sounds like you have two things.

1) Your application window, which is to contain things like panels, including an animation.
2) An animation which extends JFrame

You want to add your animation frame to your application window and you can't do this since your animation is a JFrame.

(I hope I have understood your problem so far.)

If this is the case, all you should need to do is change your application to extend JPanel rather than JFrame, which means that it is a type of panel, which can then be added to an application window.

If you have other issues, you may want to start printing out to command line the sizes of all the other panels on your window.  It might be that these have shrunk to allow for your animation.  

Paul

---

