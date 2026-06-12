---
title: "Java help - Something wrong when trying to create a frame..?"
date: 2007-08-03
forum: Programming Talk
---

### Post by Fireblend on 2007-08-03
Hello. I'm a Computer Science student and I'm having a little trouble using ubuntu to work. I'm just starting to learn Java and when I was trying to create a simple frame using swing, I encountered some trouble.

This code, for example:

 > 1: import javax.swing.JFrame;
 2:
 3: public class SimpleFrame extends JFrame {
 4:     public SimpleFrame() {
 5:         super("Frame Title");
 6:         setSize(300, 100);
 7:         setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 8:         setVisible(true);
 9:     }
10:
11:     public static void main(String[] arguments) {
12:         SimpleFrame sf = new SimpleFrame();
13:     }
14: }

Is supposed to create a frame, but what seems to be creating for me is some kind of square that I have to force-quit because it lacks the close/minimize/etc bar. Why? In Windows apparently it does work, and since Java is multiplatform I though I wouldn't encounter this problem?

Please help, I really want to program in Ubuntu, but if it really is windows-dependable I might have to install Windows.

Also, I'm using Geany. And I can't use any easy-interface program like NetBeans or Eclipse since it was prohibited by my professor, so I have to make the interface like this.

Thanks in advance.

---

### Post by Yes on 2007-08-03
Java programming definitely does work in Ubuntu.

Try this:

```
import javax.swing.JFrame;
public class SimpleFrame {

public static void main(String args[]) {

JFrame simpleFrame = new JFrame("Title");
simpleFrame.setPosition(100,100);
simpleFrame.setSize(300, 100);
simpleFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
simpleFrame.setVisible(true);

}
}
```

---

### Post by Fireblend on 2007-08-03
Thanks, but that doesn't seem to build, it gives me an error on the line:

```
simpleFrame.setPosition(100,100);
```

Cannot find symbol.

Edit: I deleted the line and got the exact same output I posted above, an uncloseable, unminizable grey window.

Edit 2: Ahh, I found out what it was. For some reason it's Compiz Fusion's fault. Wonder why, but it does work using metacity. Well, it's better than nothing.

Edit 3: Rather, it was Compiz Fusion not recognizing a new window, I guess because it was opened "unnaturally". If I reload it after running the window, it does work. Thanks.

---

### Post by Yes on 2007-08-03
Sorry, it's been awhile since I used Java.  Change setPosition(); to setLocation(); .

---

### Post by kknd on 2007-08-03
```

import javax.swing.JFrame;
import java.awt.Dimension;

public class Test extends JFrame
{
	public Test()
	{
 		super("Frame Title");
 		setPreferredSize(new Dimension(300,100));
 		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 		pack();
 		setLocationRelativeTo(null);
 		setVisible(true);
 	}

	public static void main(String[] arguments)
	{
		Test sf = new Test();
	}
} 

```

You forgot to pack() it.

---

### Post by nitro_n2o on 2007-08-03
according to Java this is the right way to run a GUI for thread safety 
```
package start;

/*
 * HelloWorldSwing.java requires no other files. 
 */
import javax.swing.*;        

public class HelloWorldSwing {
    /**
     * Create the GUI and show it.  For thread safety,
     * this method should be invoked from the
     * event-dispatching thread.
     */
    private static void createAndShowGUI() {
        //Create and set up the window.
        JFrame frame = new JFrame("HelloWorldSwing");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //Add the ubiquitous "Hello World" label.
        JLabel label = new JLabel("Hello World");
        frame.getContentPane().add(label);

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
```
code from: [http://java.sun.com/docs/books/tutorial/uiswing/examples/start/HelloWorldSwingProject/src/start//HelloWorldSwing.java](http://java.sun.com/docs/books/tutorial/uiswing/examples/start/HelloWorldSwingProject/src/start//HelloWorldSwing.java)

---

### Post by kknd on 2007-08-03
Nitro is right. Always deal with Swing in the AWTEvent-Thread.

If you don't use multitreading, it isn't needed (By default it runs on the AWT Thread, but maybe i'm wrong).

---

