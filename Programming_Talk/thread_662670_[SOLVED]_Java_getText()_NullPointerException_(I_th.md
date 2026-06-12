---
title: "[SOLVED] Java getText() NullPointerException (I think)"
date: 2008-01-09
forum: Programming Talk
---

### Post by mike_g on 2008-01-09
Hi, I'm having a bit of a problem with Java. Basically I have a JFrame with several text fields in it. When the user hits a button the text field contents need to be validated.

I get errors in my prog when I call the JTextField getText() function. In the Javadocs it says that the getText() function will give a null pointer exception if the underlying document is null. 

Whats a document? Would a JFrame do? Thats what I am using. Anyway heres my code with relevant bits highlighted:
```
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;
import javax.swing.border.*;
import java.util.ArrayList;

public class UserInterface 
{
    private Menu menu;
    private Order order;    
    private JFrame frame;
    
    private JTextField total;
[COLOR="Red"]    private JTextField address_a;
    private JTextField address_b;
    private JTextField address_c;[/COLOR]
    private JButton submit;
    
    //These constants represent colour values for different fields of the UI
    //They can be altered to modify the display colour scheme
    private static final int HEAD_BACK_R=150, HEAD_BACK_G=150, HEAD_BACK_B=200;
    private static final int HEAD_FORE_R=000, HEAD_FORE_G=000, HEAD_FORE_B=000;
    private static final int LIST_BACK_R=200, LIST_BACK_G=200, LIST_BACK_B=220;
    private static final int LIST_FORE_R=050, LIST_FORE_G=050, LIST_FORE_B=060;
    private static final int BACKGRND_R=100, BACKGRND_G=100, BACKGRND_B=150;
    
    
    public UserInterface(Menu theMenu)
    {
        menu = theMenu;
        makeFrame();
        frame.setVisible(true);
    }
    
    public void makeFrame()
    {
        frame = new JFrame("Pizza ****");
        JPanel content = (JPanel)frame.getContentPane();
        content.setLayout(new BorderLayout());
        content.setBorder(new EmptyBorder(10, 10, 10, 10));
        
        content.setBackground(new Color(BACKGRND_R, BACKGRND_G, BACKGRND_B));
        
        //Fill the contents of the window
        makeTitleBar(content);
        makeMenuList(content);
        makeOrderList(content);
        makeBaseSection(content);

        //Apply some window settings
        frame.setAlwaysOnTop(true);
        frame.setResizable(false);
    }   
    
    private void makeTitleBar(JPanel content)
    {
        JLabel title = new JLabel("Name                 Price"+
                       "                           Quantity");
        title.setBorder(new EmptyBorder( 6, 10, 6, 10)); 
        title.setOpaque(true);
        title.setBackground(new Color(HEAD_BACK_R, HEAD_BACK_G, HEAD_BACK_B));
        title.setForeground(new Color(HEAD_FORE_R, HEAD_FORE_G, HEAD_FORE_B));
        content.add(title, BorderLayout.NORTH);
        frame.pack();        
    }    
    
    private void makeMenuList(JPanel content)
    {
        JPanel menuPanel = new JPanel(new GridLayout(menu.getMenuItems().size()-1, 2));
        menuPanel.setOpaque(true);
        menuPanel.setBackground(new Color(LIST_BACK_R, LIST_BACK_G, LIST_BACK_B));
               
        for(int i=1; i<menu.getMenuItems().size(); i++)
        {
            menuPanel.add(menu.getMenuItem(i).getNameLabel());
            menuPanel.add(menu.getMenuItem(i).getPriceLabel());
        }
 
        content.add(menuPanel, BorderLayout.WEST);
        frame.pack();       
    }  
    
    private void makeOrderList(JPanel content)
    {
        JPanel buttonPanel = new JPanel(new GridLayout(menu.getMenuItems().size()-1, 3));
        buttonPanel.setOpaque(true);
        buttonPanel.setBackground(new Color(LIST_BACK_R, LIST_BACK_G, LIST_BACK_B));
        
        for(int i=1; i<menu.getMenuItems().size(); i++)
        {
            buttonPanel.add(menu.getMenuItem(i).getMinusButton());
            buttonPanel.add(menu.getMenuItem(i).getQuantityField());
            buttonPanel.add(menu.getMenuItem(i).getPlusButton());
        }        
        content.add(buttonPanel, BorderLayout.EAST);
        frame.pack();        
    }
    
    private void makeBaseSection(JPanel content)
    {
        GridLayout grid = new GridLayout(5, 2);
        grid.setHgap(36);
        JPanel basePanel = new JPanel(grid);
        basePanel.setBackground(new Color(HEAD_BACK_R, HEAD_BACK_G, HEAD_BACK_B));
        basePanel.setOpaque(true);
        
        JLabel tot = new JLabel("   Total Order Cost: "); 
        tot.setForeground(new Color(HEAD_FORE_R, HEAD_FORE_G, HEAD_FORE_B));
        basePanel.add(tot);
        total = new JTextField();
        total.setText("0.00");
        total.setEditable(false);
        basePanel.add(total);
       
        addAddressField(basePanel, "   House Name/No:", address_a);
        addAddressField(basePanel, "   Street/Road:", address_b);
        addAddressField(basePanel, "   Town/City:", address_c);
        
        JLabel blank = new JLabel("");
        basePanel.add(blank);
        
        submit = new JButton("Submit");
        submit.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent e)
            {
                String message = validateOrder();
                Popup result = new Popup(message);
            }
        });
        basePanel.add(submit);
        
        content.add(basePanel, BorderLayout.SOUTH);
        frame.pack();
    }    
    
    private void addAddressField(JPanel content, String txt, JTextField field)
    {
        JLabel label = new JLabel(txt);
        label.setForeground(new Color(HEAD_FORE_R, HEAD_FORE_G, HEAD_FORE_B));
        content.add(label);
        field = new JTextField("");
        content.add(field);       
    }    
    
[COLOR="Red"]    private String validateOrder()
    {
        String a = address_a.getText();
        //if(address_a.getText().equals("")) return "Incomplete Address";   
        //if(address_b.getText().equals("")) return "Incomplete Address";
        //if(address_c.getText().equals("")) return "Incomplete Address";

        return "Order Successfully Placed";
    }    [/COLOR]

}
```

And this is the huge list of error stuff my compiler produced:
```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at UserInterface.validateOrder(UserInterface.java:148)
	at UserInterface.access$000(UserInterface.java:7)
	at UserInterface$1.actionPerformed(UserInterface.java:127)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
	at java.awt.Component.processMouseEvent(Component.java:6038)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5803)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4410)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Window.dispatchEventImpl(Window.java:2429)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at UserInterface.validateOrder(UserInterface.java:148)
	at UserInterface.access$000(UserInterface.java:7)
	at UserInterface$1.actionPerformed(UserInterface.java:127)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
	at java.awt.Component.processMouseEvent(Component.java:6038)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5803)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4410)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Window.dispatchEventImpl(Window.java:2429)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at UserInterface.validateOrder(UserInterface.java:148)
	at UserInterface.access$000(UserInterface.java:7)
	at UserInterface$1.actionPerformed(UserInterface.java:127)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
	at java.awt.Component.processMouseEvent(Component.java:6038)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5803)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4410)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Window.dispatchEventImpl(Window.java:2429)
	at java.awt.Component.dispatchEvent(Component.java:4240)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

```

Can someone please explain how I can fix this. Thanks.

---

### Post by harold4 on 2008-01-09
Where do you instantiate the following?
```

private JTextField address_a;
private JTextField address_b;
private JTextField address_c;

```

---

### Post by mike_g on 2008-01-09
Oh yeah, sorry. I forgot to highlight that bit.

I initialize the address fields In the makeBaseSection() function:
```
       
        addAddressField(basePanel, "   House Name/No:", address_a);
        addAddressField(basePanel, "   Street/Road:", address_b);
        addAddressField(basePanel, "   Town/City:", address_c);

```

And heres my addAddressField function:
```
    private void addAddressField(JPanel content, String txt, JTextField field)
    {
        JLabel label = new JLabel(txt);
        label.setForeground(new Color(HEAD_FORE_R, HEAD_FORE_G, HEAD_FORE_B));
        content.add(label);
        field = new JTextField("");
        content.add(field);       
    } 
```

---

### Post by Elegorod on 2008-01-09
Don't worry about document.
address_a is null. Change the code:
[code]
address_a = new JTextField();
addAddressField(basePanel, "   House Name/No:", address_a);
...

private void addAddressField(JPanel content, String txt, JTextField field)
{ ...
  field = new JTextField("");// remove this 
}

---

### Post by jviscosi on 2008-01-09
```

    private void addAddressField(JPanel content, String txt, JTextField field)
    {
        JLabel label = new JLabel(txt);
        label.setForeground(new Color(HEAD_FORE_R, HEAD_FORE_G, HEAD_FORE_B));
        content.add(label);
        field = new JTextField("");
        content.add(field);       
    }

```You can't pass your instance variables to *addAddressField* and then instantiate them there; this is just instantiating the local variable **field**.  You could instantiate the instance variable first, pass it to addAddress, and add it to content (without doing **field = new JTextField("")** first), or you could eliminate the JTextField parameter of *addAddressField* and instead return the local variable **field** and assign your instance variable to that.  There are other ways to handle it too but those are the two simplest ones.

---

### Post by Elegorod on 2008-01-09
> **mike_g said:**
> I initialize the address fields In the makeBaseSection() function[/code]

This doesn't work. At start of addAddressField field variable points to address_a. After 
```

field = new JTextField("");

```
field points to new JTextField and address_a remains null.

---

### Post by harold4 on 2008-01-09
I was trying to get him to look into the bogus instantiation, so he'd learn something. :)

---

### Post by mike_g on 2008-01-09
Thanks for the explanation, its all working now. :)

---

### Post by Elegorod on 2008-01-09
At start of stack trace is the line:
```

at UserInterface.validateOrder(UserInterface.java:148)

```
JTextField getText() function haven't been called! So, it doesn't matter, what exceptions the function can throw

---

### Post by Elegorod on 2008-01-09
So, Thread tools - Mark this thread as solved

---

### Post by mike_g on 2008-01-09
Yeah I kinda saw that huge list and my brain just turned off. I'm pretty new to Java, but I guess I should practice learning what the error messages mean.

---

### Post by harold4 on 2008-01-09
Knowing how to follow the debugger output helps tremendously.  You should also take a look into walking through your application with the debugger.  This way you can see line by line what is actually happening.

---

