---
title: "Java - press a button to close one GUI panel to open another"
date: 2014-05-08
forum: Programming Talk
---

### Post by Kuuga on 2014-05-08
So I am stuck where I am currently at and I was hoping someone here might have some insight. Currently I have three classes. One main class, the first panel, and the second panel. In the first panel, I have the ActionListener assigned to a button. When I press that button it opens the other panel. But I need that first panel to disappear. The main class is the class that holds the frame for the first panel and sets it to viable. The first panel holds those same methods to control the second panel. I am currently trying to use a boolean value and change it to true when I press the button. But either the boolean is not switching to true, or the value is getting trapped in the ActionListener. I'll show you what I have so far.

[B]Main Class:

[/B]```
JFrame frame = new JFrame("Apple Crazy Cola Cash (Apple IIC) Register");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        AppleRegisterPanel panel = new AppleRegisterPanel();
        frame.getContentPane().add(panel);
        
        frame.pack();
        frame.setVisible(true);
        //panel.setBoolean(true);
        
        if (panel.getBoolean() == true)
        {
            frame.setVisible(false);
        }
```

[B]First Panel Class:
[/B]```
private class TempListener implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            
            if (event.getSource() == button5)
            {
                JFrame frame2 = new JFrame("Apple Crazy Cola Cash (Apple IIC) Register");
                frame2.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                
                AppleRegisterPanel2 panel = new AppleRegisterPanel2();
                frame2.getContentPane().add(panel);
                
                frame2.pack();
                frame2.setVisible(true);
                
                setBoolean(true);
            }
        }
    }
```You'll see here that I am using a mutator to set the value to true. This is because I have a private boolean value set to false in my constructor. When I call the accessor in the if statement within the main class, it still reads it as being false. I've testing this theory too. When I change the if statement to is equal to false, the program executes how I want it to. Can anyone see if there is a work around? Or should I use an entirely new method all together?

---

### Post by ofnuts on 2014-05-09
Without seeing your whole code it's hard to tell... What I see in the code you provided is that you call a setBoolean() (what a lousy name!) in the TempListener (not that good a name either) and we don't even know how that method is implemented. Your other code calls getBoolean() on another class and we can't tell how these classes are related.

---

### Post by Kuuga on 2014-05-09
The main class calls the panel to be displayed. That's how they are related. But if you'd like the see the whole code, sorry in advanced that it is so long. 

**Main:**
```
import javax.swing.*;

public class AppleRegister {

    public static void main(String[] args) 
    {
        JFrame frame = new JFrame("Apple Crazy Cola Cash (Apple IIC) Register");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        AppleRegisterPanel panel = new AppleRegisterPanel();
        frame.getContentPane().add(panel);
        
        frame.pack();
        frame.setVisible(true);
        //panel.setBoolean(true);
        
        if (panel.getBoolean() == true)
        {
            frame.setVisible(false);
        }
    }

}
```

**First Panel:**
```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class AppleRegisterPanel extends JPanel
{
    private JButton button1, button2, button3, button4, button5, button6;
    private JLabel label1, label2, label3, label4, label5, label6, label7;
    private JTextField text, text1, text2, text3, text4, text5, text6, text7, text8, text9;
    private JPanel panel, panel2, panel3, panel4;
    private JFrame frame;
    private boolean trueFalse;
    private int counter;
    
    public AppleRegisterPanel()
    {
        trueFalse = false;
        
        setLayout(new BorderLayout());
        text = new JTextField(10);
        text1 = new JTextField(5);
        text2 = new JTextField(5);
        text3 = new JTextField(5);
        text4 = new JTextField(5);
        text5 = new JTextField(10);
        text6 = new JTextField(10);
        text7 = new JTextField(10);
        text8 = new JTextField(10);
        text9 = new JTextField(20);
        
        button1 = new JButton("Child");
        button2 = new JButton("Medium");
        button3 = new JButton("Large");
        button4 = new JButton("Ex Large");
        button5 = new JButton("Close Out Register");
        button6 = new JButton("Complete Transaction");
        
        panel = new JPanel();
        panel.setPreferredSize(new Dimension(240,250));
        panel.setBackground(Color.cyan);
        add(panel, BorderLayout.WEST);
        panel.add(button1);
        panel.add(text1);
        panel.add(Box.createRigidArea(new Dimension(0,20)));
        panel.add(button2);
        panel.add(text2);
        panel.add(Box.createRigidArea(new Dimension(0,20)));
        panel.add(button3);
        panel.add(text3);
        panel.add(Box.createRigidArea(new Dimension(0,20)));
        panel.add(button4);
        panel.add(text4);
        panel.setLayout(new BoxLayout(panel, BoxLayout.PAGE_AXIS));
        
        panel2 = new JPanel();
        label6 = new JLabel("Change");
        panel2.setPreferredSize(new Dimension(270,250));
        panel2.setBackground(Color.cyan);
        add(panel2, BorderLayout.EAST);
        panel2.add(button5);
        button5.addActionListener(new TempListener());
        panel2.add(label6);
        panel2.add(text9);
        panel2.add(button6);
        panel2.setLayout(new BoxLayout(panel2, BoxLayout.Y_AXIS));
        
        panel3 = new JPanel();
        panel3.setPreferredSize(new Dimension(50,50));
        panel3.setBackground(Color.cyan);
        add(panel3, BorderLayout.NORTH);
        label1 = new JLabel("Apple Crazy Cola Cash (Apple IIC) Register ");
        label7 = new JLabel(" By Robert Burns");
        panel3.add(label1);
        panel3.add(label7);
        
        panel4 = new JPanel();
        label1 = new JLabel("Sub-Total");
        label2 = new JLabel("Tax");
        label3 = new JLabel("Total");
        label4 = new JLabel("Payment");
        label5 = new JLabel("Change Owed");
        panel4.setPreferredSize(new Dimension(140,250));
        panel4.setBackground(Color.cyan);
        add(panel4, BorderLayout.CENTER);
        panel4.add(label1);
        panel4.add(text);
        panel4.add(label2);
        panel4.add(text5);
        panel4.add(label3);
        panel4.add(text6);
        panel4.add(label4);
        panel4.add(text7);
        panel4.add(label5);
        panel4.add(text8);
        
    }
    
    private class TempListener2 implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            if (event.getSource() == button1)
            {
                
            }
            if (event.getSource() == button2)
            {
                
            }
            if (event.getSource() == button3)
            {
                
            }
            if (event.getSource() == button4)
            {
                
            }
        }
    }
    
    private class TempListener implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            
            if (event.getSource() == button5)
            {
                JFrame frame2 = new JFrame("Apple Crazy Cola Cash (Apple IIC) Register");
                frame2.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                
                AppleRegisterPanel2 panel = new AppleRegisterPanel2();
                frame2.getContentPane().add(panel);
                
                frame2.pack();
                frame2.setVisible(true);
                
                setBoolean(true);
            }
        }
    }
    
    private class TempListener1 implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            
            if (event.getSource() == button6)
            {
                
            }
        }
    }
    
    // Mutators
    public void setBoolean(boolean close)
    {
        trueFalse = close;
    }
    
    // Accessors
    public boolean getBoolean()
    {
        return trueFalse;
    }
}


```

---

### Post by ofnuts on 2014-05-09
Plenty of problems. You are creating new instances of the Panel window (with tile bar and all), so you can wonder which instance had its truFalse variable set. Then the code that sets the visibility of the window acording to trueFalse only runs once when you start the app (in the main() of AppleRegister).

For what you want to do you should look at the CardLayout (which is used to replace a panel by another panel within the same window).

---

### Post by Kuuga on 2014-05-10
Thanks for the replies. I figured it out.

---

