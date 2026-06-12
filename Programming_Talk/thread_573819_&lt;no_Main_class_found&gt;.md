---
title: "&lt;no Main class found&gt;"
date: 2007-10-12
forum: Programming Talk
---

### Post by Kahai on 2007-10-12
I would like to know what is wrong with my coding, "netbeans" finds no compile-time errors, however when i try to "run" it i receive: <no Main class found> error before run-time

i have jumped ahead a bit into my programming book, and i started up on GUI,  to see what it was like, and i copied the coding exactly from the book, (however i couldnt have the same file name and class name :( (shupid netbeans) 

(Note this is a VERY basic GUI code)
```
/*
 * Main.java
 *
 * Created on October 11, 2007, 11:24 PM
 *
 */

package first;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Main extends JPanel 
{
   private int count;
   private JButton push;
   private JLabel label;
   
   public Main () 
   {
      count = 0;
      
      push = new JButton("Push me!");
      push.addActionListener(new ButtonListener());
      
      label = new JLabel("Pushes: + count");
      
      add(push);
      add(label);
      
      setBackground(Color.CYAN);
      setPreferredSize(new Dimension(300, 40));
      
   }
   
   private class ButtonListener implements ActionListener 
   {
      
      public void actionPerformed (ActionEvent event)
      
      {
         count++;
         label.setText("Pushes: " + count);
         
      }
      
   }
   
}

```

i am receiving errors in terminal as well :( 

is this a netbeans error, i do believe that the coding is right... could it be from netbeans auto "main" creation? idk :confused:

---

### Post by pbrockway2 on 2007-10-12
Your Main class doesn't have a main method - when you run a java program by specifying a class it looks for a method declared like
```
public static void main(String[] args)
```

You can add one like this:
```
public static void main(String args[]) 
{
    SwingUtilities.invokeLater(new Runnable() 
    {
            // create the GUI on the event dispatch thread
        public void run() 
        {
            Main test = new Main();
            JFrame frame = new JFrame("Panel test");
            frame.add(test);
            frame.pack();
            frame.setVisible(true);
        }
    });
}
```

In Sun's tutorial:
[The main() method]("http://java.sun.com/docs/books/tutorial/getStarted/application/index.html#MAIN")
[Creating and interacting with the GUI on the event dispatch thread]("http://java.sun.com/docs/books/tutorial/uiswing/concurrency/initial.html")

---

