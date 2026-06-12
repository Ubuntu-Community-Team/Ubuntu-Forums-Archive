---
title: "Writing Java Code"
date: 2010-06-27
forum: Programming Talk
---

### Post by Kirkland14 on 2010-06-27
So I'm new to linux and have started playing around writing code.  I was using the standard gedit text editor to make the Hello World program.  So I made the class and see it listed in the directory I made as a .class file.  But I thought their would be a way i could see it in a more graphical way.  When I went to the file through the GUI and clicked on the .class file to open it I was told there isn't a application to open it up.  Is there something I need to do so that I can see the finished project outside of the terminal?  Thanks

Kevin

---

### Post by GregBrannon on 2010-06-27
It's not clear if you have the Java Development Kit (JDK) installed.  That will give you the Java compiler, javac, if  you don't already have it.  If it's not installed, install it.  Since I'm not sure which Linux distro you're using, start with this guide, and ask questions in the Programming Talk section if you need more help:

[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

Then, I'm not 100% sure what you mean by seeing "it in a more graphical way," but I'm going to assume you mean as in an integrated development environment, or IDE.  There are several excellent Java IDEs, Geany, JavaBeans, and Eclipse to name a few, and there are also several discussions in the programming forums on which are "better.

If I've completely missed the mark, read the stickies in the Programming Talk section AND review the discussions that have occurred there on these topics, then ask for more help there.

Good luck!

---

### Post by jediborger on 2010-06-27
Well since you were able to compile the program and make the .class file you already have java which lets you run the file. I will presume you know how to run the file from the terminal which is just running java followed by the name of the class file without the .class extension. 

Now if you want to run the program simply by clicking on it, find your class file, right click it and select "Open with Other Application" then towards the bottom of the window expand "Use a Custom command" and type in java. Make sure the bottom box is checked to save this command for all .class files and click Open. Now all your java classes should just open when you double click them.

---

### Post by stderr on 2010-06-27
If you meant that you expected a custom Java window to appear with the text Hello World, then no, not yet. Java apps, like most languages, are entirely console-based until you explicitly start including GUI libraries, manually creating windows, adding layout containers and items to them, etc.

---

### Post by simeon87 on 2010-06-27
> **jediborger said:**
> Now if you want to run the program simply by clicking on it, find your class file, right click it and select "Open with Other Application" then towards the bottom of the window expand "Use a Custom command" and type in java. Make sure the bottom box is checked to save this command for all .class files and click Open. Now all your java classes should just open when you double click them.

However, most classes won't do anything. Only those that have a ```
public static void main(String[] args) {}
``` in them can actually be run.

---

### Post by lykeion on 2010-06-27
I'm also not really clear on what exactly you're asking for, but if it's any help here are some simple examples of graphical Hello world:

First the simplest possible example:
[PHP]import javax.swing.*;

public class SimpleHello extends JFrame {

    public SimpleHello() {
        this.add( new JLabel("Hello World!") );
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        this.setSize(100, 100);
        this.setVisible(true);
    }

    public static void main(String[] args) {
        new SimpleHello();    
    }
}[/PHP]

Secondly a more extendable example:
[PHP]import javax.swing.*;

public class ExtendedHello extends JPanel {

    JLabel textLabel;

    public ExtendedHello() {
        textLabel = new JLabel("Hello World!");
        add(textLabel);
    }

    private static void createAndShowGUI() {

        //Create and set up the window.
        JFrame frame = new JFrame("LabelDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //Add content to the window.
        frame.add( new ExtendedHello() );

        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {

        //Schedule a job for the event dispatch thread:
        //  creating and showing this application's GUI.
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }

        });
   }
}[/PHP]

---

### Post by Kirkland14 on 2010-06-27
> **stderr said:**
> If you meant that you expected a custom Java window to appear with the text Hello World, then no, not yet. Java apps, like most languages, are entirely console-based until you explicitly start including GUI libraries, manually creating windows, adding layout containers and items to them, etc. 


That's pretty much what I expected to happen, ya.  So then how does it become an active program.  Like say I was to write a basic bounce code,  how would I play it?  Is it a string I would write somewhere in the program?  I just started messing around with this the other day but am a pretty quick learner.  Thanks for everyones help

Kevin

---

### Post by Kirkland14 on 2010-06-27
> **lykeion said:**
> I'm also not really clear on what exactly you're asking for, but if it's any help here are some simple examples of graphical Hello world:

First the simplest possible example:
[PHP]import javax.swing.*;

public class SimpleHello extends JFrame {

    public SimpleHello() {
        this.add( new JLabel("Hello World!") );
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        this.setSize(100, 100);
        this.setVisible(true);
    }

    public static void main(String[] args) {
        new SimpleHello();    
    }
}[/PHP]Secondly a more extendable example:
[PHP]import javax.swing.*;

public class ExtendedHello extends JPanel {

    JLabel textLabel;

    public ExtendedHello() {
        textLabel = new JLabel("Hello World!");
        add(textLabel);
    }

    private static void createAndShowGUI() {

        //Create and set up the window.
        JFrame frame = new JFrame("LabelDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //Add content to the window.
        frame.add( new ExtendedHello() );

        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {

        //Schedule a job for the event dispatch thread:
        //  creating and showing this application's GUI.
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }

        });
   }
}[/PHP]

So your second example is exactly what I was looking for.  Apparently I have to learn how to write a little more code in to make a whole new window.  I'm cool with that.  Thanks for the help.  

Kevin

---

