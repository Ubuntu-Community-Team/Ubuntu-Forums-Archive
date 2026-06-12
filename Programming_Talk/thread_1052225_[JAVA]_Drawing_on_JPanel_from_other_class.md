---
title: "[JAVA] Drawing on JPanel from other class"
date: 2009-01-27
forum: Programming Talk
---

### Post by tashe on 2009-01-27
Hi
I am trying to make a visual representation of how frames are sent from a sender to a receiver in a network, with the Selective-Reject technique, using Java.
 
I have classes Sender and Receiver which should exchange frames and ACKs, and also draw lines on a JPanel, similar to the picture attached. These lines have to be drawn not at once, but every one after a short interval, lets say 0.5 sec. I thought about using the repaint() method, but I think it will erase the previous lines.

In previous programs, I did the drawing with the paint(Graphics g), but now I can't access "g". 

Since the deadline is tomorrow I have no time for experimenting, so I decided to post here.
Does anybody know how can I draw the lines from outside the JPanel class?
Thank you

---

### Post by Reiger on 2009-01-27
```

JPanel myPanel = new JPanel(); /* obtain the panel... (to be substituted with actual code... */
Graphics g = myPanel.getGraphics(); // get its graphics object
g.fillRect(15,15,15,15); // paint something

```

---

### Post by tashe on 2009-01-27
thank you :)
/closed

---

### Post by tashe on 2009-01-27
/re-open :)

I found another problem. 
When I draw more lines, most of the lines after short period of time (0.1 sec) disappear.
I declare Graphics g;
and in the constructor of the class A (which is a Sender class, and doesn't extend JPanel) I have this:
 
[PHP]g=panel.getGraphics();[/PHP]

and later, the program draws lines. But most of them disappear.
Also, when I minimize or switch to another window, the drawn lines disappear, except the ones drawn by the JPanel's  paint() method. 

I have no idea what the problem.
Does anybody has a thought about this?

---

### Post by Reiger on 2009-01-28
Yes. That's the fun with events. The simple solution is to store everything inside a buffered image and draw on top of that image. See also (need to scroll down a bit): [http://forums.sun.com/thread.jspa?forumID=57&threadID=591408](http://forums.sun.com/thread.jspa?forumID=57&threadID=591408)

---

