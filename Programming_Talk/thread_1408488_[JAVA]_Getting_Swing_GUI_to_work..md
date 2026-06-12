---
title: "[JAVA] Getting Swing GUI to work."
date: 2010-02-16
forum: Programming Talk
---

### Post by Steveh15 on 2010-02-16
Hello

I'm learning Java for my Uni course and we've just started using swing and awt packages to create GUIs and create animations. They work fine on labs at the university but I can't get them to work on my PC.

I can compile the programs but Whenever I try to run them I get this error message.

```
steve@ubuntu:~/prog$ java sHelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: sHelloWorld
Caused by: java.lang.ClassNotFoundException: sHelloWorld
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: sHelloWorld.  Program will exit.
steve@ubuntu:~/prog$ 
```Here the simple program I'm trying to run

```

import java.awt.event.*;

import javax.swing.*;

class HelloPanel extends JPanel {

    // component to be added to the panel
    JLabel msg;

    // constructor
    public HelloPanel() {
        // initialise label
        msg = new JLabel("Hello World", JLabel.CENTER);

        // add label to the panel
        add(msg);
    }
}

class HelloGui extends JFrame {

    // constructor
    public HelloGui() {
        // Create panel
        HelloPanel contents = new HelloPanel();

        // Panel is not added directly to top-level container
        // Instead, it is added to the content pane
        getContentPane().add(contents);

        // this code enables you to close the window
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}

class SHelloWorld {

    public static void main(String[] args) {
        HelloGui testGui = new HelloGui();

        // set size of GUI
        testGui.setSize(200, 100);

        // and make it visible
        testGui.setVisible(true);
    }
}
```It's just a simple hello world program.

I don't know what to do to get this working, although I assume it's something simple. I get this error message if I run the program in Ubuntu, Sci LInux or Windows so the problem does seem to be me not doing it right.

It does work when i run it in NetBeans however, but I don't like that and just want to stick to emacs and the terminal for now.

What do I have to do to get these programs to run? Any help would be much appreciated. My grades would also appreciate the extra time put in at home as well :).

Thanks a lot
Steve

---

### Post by kahumba on 2010-02-16
I'd simplify things.

```

import java.awt.*;
import javax.swing.*;

public class HelloWorld extends JFrame {

    public static void main(String[] args) {
        new HelloWorld();
    }

    public HelloWorld() {
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        JPanel p = new JPanel(new BorderLayout());
        setContentPane(p);
        p.add(BorderLayout.CENTER, new JLabel("hello there", JLabel.CENTER));
        setSize(200, 200);
        setVisible(true);
    }
}

```

Now to the point: Java can't find your classes, google for "Java  classpath"

---

### Post by k@e on 2010-02-16
Actually, the problem is much simpler.

With the command from his first post, he is trying to run the class sHelloWorld, but there is none. There is however a class named **S**HelloWorld, which can be run.

In other words, you overlooked the case of your class name.

---

### Post by kahumba on 2010-02-16
Yeah, but even if he gets the name right, the code is so baroque.. he really needs a code cleanup imho

---

