---
title: "Sample java code not compiling"
date: 2007-05-09
forum: Programming Talk
---

### Post by Turk on 2007-05-09
I started with development in java, many examples don't compile standard:

----------
1. ERROR in example.java (at line 44)
        public class AWTExample extends Frame {
                     ^^^^^^^^^^
The public type AWTExample must be defined in its own file
----------
2. WARNING in example.java (at line 44)
        public class AWTExample extends Frame {
                     ^^^^^^^^^^
The serializable class AWTExample does not declare a static final serialVersionUID field of type long

Code from idevelopment.info:
```

// -----------------------------------------------------------------------------
// AWTExample.java
// -----------------------------------------------------------------------------

/*
 * =============================================================================
 * Copyright (c) 1998-2005 Jeffrey M. Hunter. All rights reserved.
 *
 * All source code and material located at the Internet address of
 * http://www.idevelopment.info is the copyright of Jeffrey M. Hunter, 2005 and
 * is protected under copyright laws of the United States. This source code may
 * not be hosted on any other site without my express, prior, written
 * permission. Application to host any of the material elsewhere can be made by
 * contacting me at jhunter@idevelopment.info.
 *
 * I have made every effort and taken great care in making sure that the source
 * code and other content included on my web site is technically accurate, but I
 * disclaim any and all responsibility for any loss, damage or destruction of
 * data or any other property which may arise from relying on it. I will in no
 * case be liable for any monetary damages arising from such loss, damage or
 * destruction.
 *
 * As with any code, ensure to test this code in a development environment
 * before attempting to run it in production.
 * =============================================================================
 */
 
import java.awt.*;
import java.awt.event.*;

/**
 * -----------------------------------------------------------------------------
 * This class provides an example of a simple AWT frame that contains an
 * example toolbar implementation made up of several AWT button objects.
 * This example will contain three buttons typically found in toolbar -
 * Copy, Cut, and Paste.
 *
 * @version 1.0
 * @author  Jeffrey M. Hunter  (jhunter@idevelopment.info)
 * @author  http://www.idevelopment.info
 * -----------------------------------------------------------------------------
 */

public class AWTExample extends Frame {

    // Object fields
    private Button copyButton;
    private Button cutButton;
    private Button pasteButton;
    private Button  exitButton;


    /**
     * Public no-arg constructor
     */
    public AWTExample() {

        super("Simple AWT Example");
        setSize(450, 250);

        addWindowListener(
                new WindowAdapter() {
                    public void windowClosing(WindowEvent e) {
                        System.exit(0);
                    }
                }
        );

        ActionListener buttonListener = new ActionListener() {
       
            public void actionPerformed(ActionEvent ae) {

                String action = ae.getActionCommand();
               
                if (action.equals("Exit")) {
                    dispose();
                    System.out.println("Exiting.");
                    System.exit(0);
                } else {
                    System.out.println(action);
                }
            }
           
        };


        // Toolbar Panel
        Panel toolbarPanel = new Panel();
        toolbarPanel.setLayout(new FlowLayout(FlowLayout.LEFT));

        copyButton = new Button("Copy");
        copyButton.addActionListener(buttonListener);
        toolbarPanel.add(copyButton);

        cutButton = new Button("Cut");
        cutButton.addActionListener(buttonListener);
        toolbarPanel.add(cutButton);

        pasteButton = new Button("Paste");
        pasteButton.addActionListener(buttonListener);
        toolbarPanel.add(pasteButton);

        add(toolbarPanel, BorderLayout.NORTH);

        // Bottom Panel
        Panel bottomPanel = new Panel();

        exitButton = new Button("Exit");
        exitButton.addActionListener(buttonListener);
        bottomPanel.add(exitButton);
       
        add(bottomPanel, BorderLayout.SOUTH);

    }




    /**
     * Sole entry point to the class and application.
     * @param args Array of String arguments.
     */
    public static void main(String[] args) {

        AWTExample mainFrame = new AWTExample();
        mainFrame.setVisible(true);

    }

}


```

Thanks.

---

### Post by vitku on 2007-05-09
```
mv example.java AWTExample.java
```
The file should be named after the public (main) class of the file.

Assuming "public class AWTExample" is not an inner class.

---

### Post by samjh on 2007-05-09
> **vitku said:**
> ```
mv example.java AWTExample.java
```
The file should be named after the public (main) class of the file.

Assuming "public class AWTExample" is not an inner class.

In other words, the file name should be the same as this bolded part:
```
public class **AWTExample** extends Frame {
```

ie. AWTExample.java

Java only allows a file to specify one class.  There are some occasions when it will accept more than one (if the additional classes are what are called "inner" classes, but you should learn that later).  So if your file specified a class called AWTExample, Java will expect that file to have AWTExample.java as its name.

By the way, welcome to programming in Java. :)

---

### Post by sloggerkhan on 2007-05-09
I've also noticed in feisty that the default java compiler is not sun's. You may have to make sun's java active manually or something.

---

### Post by Turk on 2007-05-09
Thanks,

Now, after changing the name to the class's name, I get this error:

```

1. WARNING in AWTExample.java (at line 21)
        public class AWTExample extends Frame {
                     ^^^^^^^^^^
The serializable class AWTExample does not declare a static final serialVersionUID field of type long

```

---

### Post by Blacktalon on 2007-05-11
Umm...Look very carefully and you can see a little problem.  Where and in what part of the 'internal' Java Library is there a "Frame" class or method?  I think it should be JFrame not frame and you probably need to import javax.swing.*;  or where ever JFrame is located, but I definately don't believe there is one called Frame.  The only case of this being true with Frame is if you are using an external library not the java one.

Give this a try, I think it will fix your problem.

Also don't forget to compile the file!

Good Luck!

---

### Post by samjh on 2007-05-11
> **Blacktalon said:**
> Umm...Look very carefully and you can see a little problem.  Where and in what part of the 'internal' Java Library is there a "Frame" class or method?  I think it should be JFrame not frame and you probably need to import javax.swing.*;  or where ever JFrame is located, but I definately don't believe there is one called Frame.  The only case of this being true with Frame is if you are using an external library not the java one.

Frame is part of AWT.  JFrame is as subclass of Frame for Swing.

[http://java.sun.com/javase/6/docs/api/java/awt/Frame.html](http://java.sun.com/javase/6/docs/api/java/awt/Frame.html)


> **Turk said:**
> Thanks,

Now, after changing the name to the class's name, I get this error:

```

1. WARNING in AWTExample.java (at line 21)
        public class AWTExample extends Frame {
                     ^^^^^^^^^^
The serializable class AWTExample does not declare a static final serialVersionUID field of type long

```

Are you using Eclipse?  That warning is an Eclipse-only quirk.  It actually doesn't matter, unless you are going to face situations where the user of the software is going to have multiple versions of AWTExample, which in your case is not an issue.

Ignore the warning.

But if you are interested in knowing what serialVersionUID field is, it is basically a constant that identifies what version your class is.  For example, you might call that version of AWTExample as 1, so you will declare in your class:
```
static final serialVersionUID = 1L;
```
It's used to identify different versions of the same class for the purposes of serialization.

For an explanation of serialization, take a read of this:
[http://en.wikipedia.org/wiki/Serialization](http://en.wikipedia.org/wiki/Serialization)

---

### Post by Turk on 2007-05-12
I just use the terminal.

Thanks for the replies.

However, when executing (java AWTExample.class), I get this error:

```

1 problem (1 warning)mustafa@mustafa-desktop:~/Desktop$ java AWTExample.class
Exception in thread "main" java.lang.NoClassDefFoundError: AWTExample.class
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: AWTExample.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

```

PS: I hav ethe sun-jdk installed:
* sun-java5-bin/jdk/jre/plugin

---

### Post by samjh on 2007-05-12
> **Turk said:**
> I just use the terminal.

Thanks for the replies.

However, when executing (java AWTExample.class), I get this error:

```

1 problem (1 warning)mustafa@mustafa-desktop:~/Desktop$ java AWTExample.class
Exception in thread "main" java.lang.NoClassDefFoundError: AWTExample.class
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: AWTExample.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

```

PS: I hav ethe sun-jdk installed:
* sun-java5-bin/jdk/jre/plugin

If you have it installed, then you don't have it enabled. :)

Look at the error.  It mentions libgcj.so, which means it is GCJ that is trying to run, not Sun Java.

To enable Sun Java, type:
```
sudo update-alternatives --config java
```and choose Sun Java, rather than GCJ.  Repeat the command, but substitute java with javac, to set the compiler to use Sun Java too.

---

### Post by sphinx on 2007-05-12
Ok, this should be your last hurdle. In Java land, you tell java to run the class, not the file. What does this mean?

It means you **don't** type this:
```
mustafa@mustafa-desktop:~/Desktop$ java AWTExample.class
```

But you **do** type this:
```
mustafa@mustafa-desktop:~/Desktop$ java AWTExample
```
Note the lack of .class at the end.

---

### Post by Turk on 2007-05-12
Thanks to everyone,

It works ;), I'm new in java (with C backend).

---

### Post by JT673 on 2007-05-12
Java only let's one PUBLIC class per file, so you can declare as much DEFAULT (no access modifiers) or PRIVATE classes as much as you want.

"public static final long serialVersionUID" is an interesting constant.  It's the only static variable allowed in an inner class.  If you don't declare one of your own, the compiler will automatically make get the class its own.  However, you only need to worry about it when you're serializing (making a deep copy of an object, or sometimes called marshalling).

---

