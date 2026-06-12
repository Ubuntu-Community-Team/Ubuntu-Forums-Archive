---
title: "Java Swing-Panels-BoxLayout"
date: 2011-09-09
forum: Programming Talk
---

### Post by raac on 2011-09-09
Hello I've got a question about java swing.
Let's say I have panels A, B, C, D

Panel A holds Panel B, C, and D
Panel A's layout is BoxLayout on the Y-Axis

By executing the code 
A.add(B);
A.add(C);
A.add(D);

The Panel A would look like this...

_____________
|   B                |
|-----------------
|   C                |             => The whole container is Panel A
|----------------|
|   D                |
|----------------|
|----------------|--------------> Unfortunately Panel A leaves a small space here
                                             How would I make Panel D occupies the rest of Panel A???

---

### Post by dwhitney67 on 2011-09-09
Have you read this short tutorial yet?
[http://java.sun.com/docs/books/tutorial/uiswing/layout/box.html](http://java.sun.com/docs/books/tutorial/uiswing/layout/box.html)


P.S.  Simple program... based specifically on the requirements you listed:
```

import javax.swing.*;
import java.awt.Color;

public class MyFrame extends JFrame
{
   public MyFrame()
   {
      JPanel panelA = new JPanel();
      JPanel panelB = new JPanel();
      JPanel panelC = new JPanel();
      JPanel panelD = new JPanel();

      panelA.setLayout(new BoxLayout(panelA, BoxLayout.Y_AXIS));

      panelB.setBackground(Color.RED);
      panelC.setBackground(Color.WHITE);
      panelD.setBackground(Color.BLUE);

      panelA.add(panelB);
      panelA.add(panelC);
      panelA.add(panelD);

      add(panelA);

      setSize(200, 200);
      setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
   }

   public static void main(String[] args)
   {
      SwingUtilities.invokeLater(
         new Runnable() {
            public void run() {
               JFrame frame = new MyFrame();
               frame.setVisible(true);
            }
         });
   }
}

```

---

### Post by raac on 2011-09-09
That's what I thought mine would look like, but there is an empty space between the last
panel and the frame. I tried to make the last panel bigger so it will cover eveything, but what it would do, it would shrink the rest of them(up ones) and it would still leave the empty space on the bottom. 

Now, that I'm actually talking about it, I may be adding another panel without knowing (because I'm doing all this in a for loop)

---

### Post by dwhitney67 on 2011-09-09
> **raac said:**
> That's what I thought mine would look like, but there is an empty space between the last
panel and the frame. I tried to make the last panel bigger so it will cover eveything, but what it would do, it would shrink the rest of them(up ones) and it would still leave the empty space on the bottom. 

Now, that I'm actually talking about it, I may be adding another panel without knowing (because I'm doing all this in a for loop)

Post the code where you are performing the loop.  Maybe you have a simple problem with iterating too much.  Alternatively, set each panel to a unique color so that you can actually see their respective areas.

---

### Post by raac on 2011-09-09
Nope I'm definitely adding the correct number of panels, what can I do to expand the last panel?

---

### Post by dwhitney67 on 2011-09-09
> **raac said:**
> Nope I'm definitely adding the correct number of panels, what can I do to expand the last panel?

Can you please show your code?  I provided a simple example earlier; does this also result in the same behavior that you describe?

---

### Post by raac on 2011-09-09
```
import javax.swing.*;
import java.awt.Color;

public class MyFrame extends JFrame
{
   public MyFrame()
   {
      JPanel panelA = new JPanel();
      panelA.setBackground(Color.yellow);
      JPanel panelB = new JPanel();
      JPanel panelC = new JPanel();
      JPanel panelD = new JPanel();
      
      JPanel mainPanel = new JPanel();
      mainPanel.setLayout(new BoxLayout(mainPanel, BoxLayout.X_AXIS));
      JPanel panel_2 = new JPanel();
      panel_2.setBackground(Color.yellow);
      
      JPanel panel_3 = new JPanel();
      panel_3.setBackground(Color.green);
      

      
      
      panelA.setLayout(new BoxLayout(panelA, BoxLayout.Y_AXIS));

      panelB.setBackground(Color.RED);
      panelC.setBackground(Color.WHITE);
      panelD.setBackground(Color.blue);

      panelA.add(panelB);
      panelA.add(panelC);
      panelA.add(panelD);
      
      mainPanel.add(panelA);
      mainPanel.add(panel_2);
      mainPanel.add(panel_3);

      add(mainPanel);

      setSize(900, 700);
      setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
   }

   public static void main(String[] args)
   {
      SwingUtilities.invokeLater(
         new Runnable() {
            public void run() {
               JFrame frame = new MyFrame();
               frame.setVisible(true);
            }
         });
   }
}
```

Note that there is a yellow line at the end

---

### Post by dwhitney67 on 2011-09-09
Attached is the visual output from running the program you posted.  Does your output look any different?

---

### Post by raac on 2011-09-09
You can see a small yellow line below the blue square

---

### Post by dwhitney67 on 2011-09-09
> **raac said:**
> You can see a small yellow line below the blue square

Barely, but yes, because of:
```

panelA.setBackground(Color.yellow);

```

---

### Post by raac on 2011-09-09
Exactly, is there a way to cover everything?

---

### Post by dwhitney67 on 2011-09-09
Try adjusting the mainPanel with the following:
```

mainPanel.setBorder(BorderFactory.createEmptyBorder(0, 1, 1, 1));

```
This will line up the bottom edges of the 3 panels (A, 2, and 3) that are sitting side-by-side within the mainPanel.

---

### Post by raac on 2011-09-09
Never thought about that though. Still, what it does is it will move everything up. I did this

```
 mainPanel.setBorder(BorderFactory.createEmptyBorder(0, 10, 10, 10));
```

A big border just so I can see what it is doing.

---

### Post by raac on 2011-09-09
I guess it is something that there is nothing to do about it

---

