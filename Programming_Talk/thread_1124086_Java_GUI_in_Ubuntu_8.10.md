---
title: "Java GUI in Ubuntu 8.10"
date: 2009-04-13
forum: Programming Talk
---

### Post by eman245 on 2009-04-13
I'm trying to create a simple java GUI application using eclipse, and I'm working on the newest Ubuntu and Java 6. For some reason, every time I run the application, the main JFrame doesn't respond to anything. I dumbed down the code so much, and I still can't figure out whats going on. Most of the time, it displays like it should, but just doesn't respond when I click the close button. Eventually, a dialogue comes up saying the program is not responding, at this point, I just terminate it from eclise.

I've read around a little bit and heard that Compiz can mess up the Java GUI. I'm using Compiz, but I tried the app without it (by going to appearance, and selecting Visual Effects -> None), and it still didn't work. 

Here is my code, it's pretty much straight from one of Sun's examples, so I think it should work... Any suggestions would be very appreciated!

class MyClass{
private static void createAndShowGUI() {
        //Create and set up the window.
        JFrame frame = new JFrame("FrameDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JLabel emptyLabel = new JLabel("");
        emptyLabel.setPreferredSize(new Dimension(175, 100));
        frame.getContentPane().add(emptyLabel, BorderLayout.CENTER);

        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        //Schedule a job for the event-dispatching thread:
        //creating and showing this application's GUI.
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }
        });
    }
}

---

### Post by PaulM1985 on 2009-04-13
Provided you have got the correct import statements at the top:

```

import javax.swing.*;
import java.awt.*;
```

and you have changed

```
JFrame.EXIT_ON_CLOS E
```

to 

```
JFrame.EXIT_ON_CLOSE
```

Then I don't have any problems running from terminal.  (I have got Ubuntu 8.10).

Paul

---

