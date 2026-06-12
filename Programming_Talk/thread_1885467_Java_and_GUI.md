---
title: "Java and GUI"
date: 2011-11-23
forum: Programming Talk
---

### Post by Uchiha_Kori on 2011-11-23
Hello once again all.

I have returned yet again to seek your help. I am learning the Java Programming Language, and I have begun to really dive down into it. I'm watching a couple of videos on YouTube, and so far, I have only applied Java in command line interface programs (ex. Hello World). 

However, is Java good for Graphic User Interface? Please keep in mind people, I'm a noob and just started learning.

---

### Post by gateway67 on 2011-11-23
I've found that learning how to use Google is far more easier than learning any programming language.  You should consider refocusing your near-term efforts to learn Google.  For example, look at what I found by merely searching for the keywords "wiki" and "Java".

[http://en.wikipedia.org/wiki/Java_%28programming_language%29](http://en.wikipedia.org/wiki/Java_%28programming_language%29)

---

### Post by Uchiha_Kori on 2011-11-23
That reply was, in a sense, disrespectful. I am asking for help from experienced people who do this, of which does not include you.

---

### Post by gateway67 on 2011-11-23
> **Uchiha_Kori said:**
> That reply was, in a sense, disrespectful. I am asking for help from experienced people who do this, of which does not include you.
I am experienced.  Java is widely used... if you care for my opinion, it is a good language.  What else do you want to know?

---

### Post by Uchiha_Kori on 2011-11-23
I simply want to know if it a good language to use for GUI. Out of experience, can you tell me if it is or not?

---

### Post by gateway67 on 2011-11-23
Yes, it is good for GUI development.  It is widely used in the industry, and one of the main reasons for this is that it is supported on most major platforms (Windows, Unix, Mac, Linux).

If you want to procure a good book, I would recommend this one:
[http://www.amazon.com/Introduction-Java-Programming-Comprehensive-8th/dp/0132130807/ref=sr_1_1?s=books&ie=UTF8&qid=1322059527&sr=1-1](http://www.amazon.com/Introduction-Java-Programming-Comprehensive-8th/dp/0132130807/ref=sr_1_1?s=books&ie=UTF8&qid=1322059527&sr=1-1)

Here's an example from the book:

ButtonDemo.java
```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;


public class ButtonDemo extends JFrame
{
   // create panel for displaying message
   protected MessagePanel messagePanel = new MessagePanel("Welcome to Java");

   // declare two buttons to move the message left and right
   private JButton jbtLeft  = new JButton("<=");
   private JButton jbtRight = new JButton("=>");


   public static void main(String[] args)
   {
      ButtonDemo frame = new ButtonDemo();
      frame.setTitle("ButtonDemo");
      frame.setSize(250, 100);
      frame.setLocationRelativeTo(null);
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      frame.setVisible(true);
   }


   public ButtonDemo()
   {
      messagePanel.setBackground(Color.WHITE);

      JPanel jpButtons = new JPanel(new GridLayout(1, 2, 0, 10));
      jpButtons.add(jbtLeft);
      jpButtons.add(jbtRight);

      // set keyboard mnemonics
      jbtLeft.setMnemonic('L');
      jbtRight.setMnemonic('R');

      // set icons and remove text
      jbtLeft.setIcon(new ImageIcon("image/left.gif"));
      jbtRight.setIcon(new ImageIcon("image/right.gif"));
      jbtLeft.setText("Left");
      jbtRight.setText("Right");

      // set tool tip text on the buttons
      jbtLeft.setToolTipText("Move message to the left");
      jbtRight.setToolTipText("Move message to the right");

      // place panels in the frame
      setLayout(new BorderLayout());
      add(messagePanel, BorderLayout.CENTER);
      add(jpButtons, BorderLayout.SOUTH);

      // register listeners with the buttons
      jbtLeft.addActionListener(new ActionListener() {
                                    public void actionPerformed(ActionEvent e) {
                                       messagePanel.moveLeft();
                                    }
                               });
      jbtRight.addActionListener(new ActionListener() {
                                     public void actionPerformed(ActionEvent e) {
                                        messagePanel.moveRight();
                                     }
                                });
   }
}

```MessagePanel.java
```

import java.awt.FontMetrics;
import java.awt.Dimension;
import java.awt.Graphics;
import javax.swing.JPanel;


public class MessagePanel extends JPanel
{
   private String  message = "Welcome to Java";

   private int     xCoordinate = 20;   // x coordinate where message is displayed
   private int     yCoordinate = 20;   // y coordinate where message is displayed
   private boolean centered;           // indicate whether message is displayed in the center
   private int     interval = 10;      // interval for moving message left/right


   public MessagePanel()
   {
   }

   public MessagePanel(String message)
   {
      this.message = message;
   }

   public String getMessage()
   {
      return message;
   }

   public void setMessage(String message)
   {
      this.message = message;
      repaint();
   }

   public int getXCoordinate()
   {
      return xCoordinate;
   }

   public void setXCoordinate(int x)
   {
      xCoordinate = x;
   }

   public int getYCoordinate()
   {
      return yCoordinate;
   }

   public void setYCoordinate(int y)
   {
      yCoordinate = y;
   }

   public boolean isCentered()
   {
      return centered;
   }

   public void setCentered(boolean centered)
   {
      this.centered = centered;
      repaint();
   }

   public int getInterval()
   {
      return interval;
   }

   public void setInterval(int interval)
   {
      this.interval = interval;
      repaint();
   }

   protected void paintComponent(Graphics g)
   {
      super.paintComponent(g);

      if (centered)
      {
         FontMetrics fm = g.getFontMetrics();

         // find the center location to display
         int stringWidth  = fm.stringWidth(message);
         int stringAscent = fm.getAscent();

         // get the position of the leftmost character in the baseline
         xCoordinate = getWidth() / 2 - stringWidth / 2;
         yCoordinate = getHeight() / 2 - stringAscent / 2;
      }

      g.drawString(message, xCoordinate, yCoordinate);
   }

   public void moveLeft()
   {
      xCoordinate -= interval;
      repaint();
   }

   public void moveRight()
   {
      xCoordinate += interval;
      repaint();
   }

   public void moveUp()
   {
      yCoordinate -= interval;
      repaint();
   }

   public void moveDown()
   {
      yCoordinate += interval;
      repaint();
   }

   //@override
   public Dimension getPreferredSize()
   {
      return new Dimension(200, 30);
   }
}

```CheckBoxDemo.java
```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;


public class CheckBoxDemo extends ButtonDemo
{
   private JCheckBox jchkCentered = new JCheckBox("Centered");
   private JCheckBox jchkBold     = new JCheckBox("Bold");
   private JCheckBox jchkItalic   = new JCheckBox("Italic");


   public static void main(String[] args)
   {
      CheckBoxDemo frame = new CheckBoxDemo();
      frame.setTitle("CheckBoxDemo");
      frame.setSize(500, 200);
      frame.setLocationRelativeTo(null);
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      frame.setVisible(true);
   }


   public CheckBoxDemo()
   {
      // set mnemonic keys
      jchkCentered.setMnemonic('C');
      jchkBold.setMnemonic('B');
      jchkItalic.setMnemonic('I');

      // create a new panel to hold check boxes
      JPanel jpCheckBoxes = new JPanel();
      jpCheckBoxes.setLayout(new GridLayout(3, 1));
      jpCheckBoxes.add(jchkCentered);
      jpCheckBoxes.add(jchkBold);
      jpCheckBoxes.add(jchkItalic);
      add(jpCheckBoxes, BorderLayout.EAST);

      // register listeners with the check boxes
      jchkCentered.addActionListener(new ActionListener() {
                                     public void actionPerformed(ActionEvent e) {
                                         messagePanel.setCentered(jchkCentered.isSelected());
                                     }
                                    });

      jchkBold.addActionListener(new ActionListener() {
                                 public void actionPerformed(ActionEvent e) {
                                    setNewFont();
                                 }
                                });

      jchkItalic.addActionListener(new ActionListener() {
                                   public void actionPerformed(ActionEvent e) {
                                      setNewFont();
                                   }
                                  });
   }

   private void setNewFont()
   {
      // determine the font style
      int fontStyle = Font.PLAIN;
      fontStyle += (jchkBold.isSelected() ? Font.BOLD : Font.PLAIN);
      fontStyle += (jchkItalic.isSelected() ? Font.ITALIC : Font.PLAIN);

      // set font for the message
      Font font = messagePanel.getFont();
      messagePanel.setFont(new Font(font.getName(), fontStyle, font.getSize()));
   }
}

```RadioButtonDemo.java
```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;


public class RadioButtonDemo extends CheckBoxDemo
{
   // declare radio buttons
   private JRadioButton jrbRed   = new JRadioButton("Red");
   private JRadioButton jrbGreen = new JRadioButton("Green");
   private JRadioButton jrbBlue  = new JRadioButton("Blue");


   public static void main(String[] args)
   {
      RadioButtonDemo frame = new RadioButtonDemo();
      frame.setTitle("RadioButtonDemo");
      frame.setSize(500, 200);
      frame.setLocationRelativeTo(null);
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      frame.setVisible(true);
   }


   public RadioButtonDemo()
   {
      // create a new panel to hold radio buttons
      JPanel jpRadioButtons = new JPanel();
      jpRadioButtons.setLayout(new GridLayout(3, 1));
      jpRadioButtons.add(jrbRed);
      jpRadioButtons.add(jrbGreen);
      jpRadioButtons.add(jrbBlue);
      add(jpRadioButtons, BorderLayout.WEST);

      // create a radio-button group to group three buttons
      ButtonGroup group = new ButtonGroup();
      group.add(jrbRed);
      group.add(jrbGreen);
      group.add(jrbBlue);

      // set keyboard mnemonics
      jrbRed.setMnemonic('E');
      jrbGreen.setMnemonic('G');
      jrbBlue.setMnemonic('U');

      // register listeners for radio buttons
      jrbRed.addActionListener(new ActionListener() {
                                   public void actionPerformed(ActionEvent e) {
                                      messagePanel.setForeground(Color.RED);
                                   }
                              });

      jrbGreen.addActionListener(new ActionListener() {
                                     public void actionPerformed(ActionEvent e) {
                                        messagePanel.setForeground(Color.GREEN);
                                     }
                                });

      jrbBlue.addActionListener(new ActionListener() {
                                    public void actionPerformed(ActionEvent e) {
                                       messagePanel.setForeground(Color.BLUE);
                                    }
                               });

      // set initial message color to blue
      jrbBlue.setSelected(true);
      messagePanel.setForeground(Color.BLUE);
   }
}

```If you do not have JDK installed on your system, you will need it to compile the program above.  Now whether this be the OpenJDK or the Sun (Oracle) proprietary version, the choice is yours.  I personally use the latter, both at work and at home.

---

### Post by Uchiha_Kori on 2011-11-23
Thank you ^_^ That's what I was looking for.

---

### Post by PaulM1985 on 2011-11-23
I use Java alot for all my home projects and I have found that the user interface code does everything that I would want it to.  That being said, I am only doing straight forward dialogs and I am not wanting to create my own special custom controls.

I find it easy to use.  Remember that learning stuff like this will take time. You may find it difficult and awkward at first, but, like everything, once you get used to it it will seem straight forward.

I would try to focus on coding interfaces by hand at first so you know what is *really* happening, then move on to using the designers that are available in IDEs like Netbeans, so that you can create your interfaces alot quicker.

Paul

---

### Post by Uchiha_Kori on 2011-11-23
Thank you Paul.

---

### Post by ofnuts on 2011-11-23
The official Java Swing tuts are a good read. There are three things to know:

[LIST=1]
[*]basic principles, especially the event management and the MVC model. essential knowledge.
[*]a high-level view of what the various widgets do and what they are used for (buttons, panels, tables, sliders, layout managers...). The more you know the better, because you'll know what to use in your designs.
[*]the nitty-gritty details of the widgets. Apply the TL;DR rule and google the rest when you need it. You'll soon know by heart the stuff you use often anyway.
[/LIST]

---

