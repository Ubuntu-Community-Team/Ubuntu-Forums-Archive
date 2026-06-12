---
title: "[ Java ] What's wrong with my ActionListener ( Unknown Source ) ?"
date: 2010-02-01
forum: Programming Talk
---

### Post by SemiBuz on 2010-02-01
[COLOR=Green]Sample.java[/COLOR]
```
import javax.swing.JFrame;

public class Sample {
    
    public static void main(String[] args) {
        
        GUI application = new GUI();
        
        application.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        application.setSize(600, 250);
        application.setVisible(true);
        
    }
    
}
```[COLOR=Green]GUI.java[/COLOR]
```
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;

public class GUI extends JFrame {

    JButton button1;
    
    public GUI() {
        
        super("Made by SemiBuz");
        setLayout(new FlowLayout());
        
        EventHandler eventHandler = new EventHandler();
        
        button1 = new JButton("Disabled");
        button1.addActionListener(eventHandler);
        
        add(button1);
    }
    
    private class EventHandler implements ActionListener {
        
        public void actionPerformed(ActionEvent event) {
            
            if (event.getSource() == button1) {
                button1.setText("Enabled");
                button1.setBackground(Color.GREEN);
            } else {
                button1.setText("Disabled");
                button1.setBackground(Color.RED);
            }
            
        }
        
    }
    
}
``````
[COLOR=Red]Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at GUI$EventHandler.actionPerformed(GUI.java:31)
    at javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
    at javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source)
    at javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
    at javax.swing.DefaultButtonModel.setPressed(Unknown Source)
    at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source)
    at java.awt.Component.processMouseEvent(Unknown Source)
    at javax.swing.JComponent.processMouseEvent(Unknown Source)
    at java.awt.Component.processEvent(Unknown Source)
    at java.awt.Container.processEvent(Unknown Source)
    at java.awt.Component.dispatchEventImpl(Unknown Source)
    at java.awt.Container.dispatchEventImpl(Unknown Source)
    at java.awt.Component.dispatchEvent(Unknown Source)
    at java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source)
    at java.awt.LightweightDispatcher.processMouseEvent(Unknown Source)
    at java.awt.LightweightDispatcher.dispatchEvent(Unknown Source)
    at java.awt.Container.dispatchEventImpl(Unknown Source)
    at java.awt.Window.dispatchEventImpl(Unknown Source)
    at java.awt.Component.dispatchEvent(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)[/COLOR]
```

---

### Post by denarced on 2010-02-01
I'm thinking it COULD be something like this:
You define a private class, and in the public class' constructor, you create a LOCAL variable of EventHandler. The object will be destroyed after you leave the constructor.

This might not work

---

### Post by SemiBuz on 2010-02-01
Thank you - moving the object ( eventHandler ) out of the constructor did the trick :)

---

