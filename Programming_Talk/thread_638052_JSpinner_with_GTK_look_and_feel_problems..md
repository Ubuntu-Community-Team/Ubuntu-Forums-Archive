---
title: "JSpinner with GTK look and feel problems."
date: 2007-12-11
forum: Programming Talk
---

### Post by Hospadar on 2007-12-11
I'm writing some stuff with swing, using the gtk look and feel, as set by ```
javax.swing.UIManager.setLookAndFeel(javax.swing.UIManager.getSystemLookAndFeelClassName());
```in the constructor for the frame.

My problem is that the JSpinners arn't drawing properly when I use the gtk look and feel.  the buttons that open up the drop down menu arn't being drawn, although they do work.

The first picture (screenshot,jpg) shows what the problem is, and the other picture (java-swing.png) shows what (I believe) the spinners should look like.

In the screenshot I have, the spinners are in a JFileChooser, but even spinners in the main frame do the same thing.

---

### Post by clemente on 2008-06-05
Hi Hospadar, 
did you have found a solution for this problem? 
Greets, 
Clemente

---

### Post by xlinuks on 2008-06-05
This is a Java bug, I have the same issue. If theme changed to something radically different then the JSpinner is drawn almost fine.
Since this is not a critical bug I'm skeptical it will be fixed any time soon. People cannot print from Sun's Java for a year or so and the bug is still there (openJDK is not usable yet), this one could stay on Sun's bug shelves even longer (unless you fix it yourself and provide them the patch and convince them to apply it in the next update).
Sun is almost totally conserned about Java on windows, they don't quite care about Java on the Linux desktop (on Linux the Java system tray doesn't even support transparent images, on windows it does, and so on).
As I watch the trend, which is all about the Java update 10 release, it's still "windows centric" and important GUI features are implemented "windows only", claiming that on Linux it's impossible.

---

