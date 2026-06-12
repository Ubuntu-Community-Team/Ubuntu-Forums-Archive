---
title: "extends JFrame and extends JPanel Together?"
date: 2009-05-03
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-03
I need to find a way to get the following code to function the same way when the class extends JPanel instead of JFrame.

This is a demo i put together but i have some more code which i am trying to get the same functionality out of. However that code extends JPanel instead of JFrame and i dont think changing it is the best approach. 

The other code gives me the following error when i click the JLabel, and i have narrowed it down to being caused by the line that adds the mouselistener to the JLabel if that helps.

I dont really understand fully what extending does.

```
import java.io.*;
import java.awt.*;
import java.util.*;
import javax.swing.*;
import java.awt.event.*;
import java.lang.Object.*;

public class LabelEvent extends JFrame implements MouseListener, ActionListener
{
	private JLabel label = new JLabel("   [ON]    ");
	private JButton button = new JButton("Open");
	
	private JFrame testFrame = new JFrame("Test Frame");
	private JPanel testFramePane = new JPanel();
	
	LabelEvent()
	{
	    button.addActionListener(this);
	    add(button);
	}
	
	public void actionPerformed(ActionEvent ae)
	{
		if(ae.getSource() == button)
		{
			newFrame();
		}
	}
	public void mouseClicked(MouseEvent me) {}
	public void mouseEntered(MouseEvent me) {}
	public void mouseExited(MouseEvent me) {}
	public void mousePressed(MouseEvent me)
	{
		if(me.getSource() == label)
		{			
			Color curr = label.getForeground();
			if(curr == Color.red)
			{
				label.setForeground(Color.gray);
			}
			else
			{
				label.setForeground(Color.red);
			}			
		}
	}
	public void mouseReleased(MouseEvent me) {}
	
	private void newFrame()
	{
		label.addMouseListener(this);
		label.setForeground(Color.gray);
		testFramePane.add(label);
		
		testFrame.setSize(100,100);
		testFrame.getContentPane().add(testFramePane);
		testFrame.setVisible(true);
	}
	
	public static void main(String[] args) 
    {
		LabelEvent le = new LabelEvent();
		le.setBounds(0, 0, 200, 100);
		le.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		le.setVisible(true);
	}
}
```


error from other code when i click the JLabel:

```
Exception in thread "AWT-EventQueue-0" java.lang.NumberFormatException: For input string: "  [ON]  "

        at java.lang.NumberFormatException.forInputString(Unknown Source)
        at java.lang.Integer.parseInt(Unknown Source)
        at java.lang.Integer.valueOf(Unknown Source)
        at HomeController.mousePressed(HomeController.java:333)
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
        at java.awt.EventDispatchThread.run(Unknown Source)
```

---

### Post by CptPicard on 2009-05-03
> **mikemcleanuk said:**
> I need to find a way to get the following code to function the same way when the class extends JPanel instead of JFrame.

Well, JPanels and JFrames are two different things. Is there something in your code that specifically relies on the class being a JFrame?

The error itself seems like it's not caused by that kind of a distinction.

> I dont really understand fully what extending does.

[http://en.wikipedia.org/wiki/Inheritance_(computer_science](http://en.wikipedia.org/wiki/Inheritance_(computer_science))

---

