---
title: "java GUI setForeground on JLabel"
date: 2009-05-03
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-03
i am attempting to have a MouseListener assigned to a JLabel and when clicked the label will change colour.

the code compiles fine however when i click the label nothing happens and i get a error in command prompt.

the label is declared and instansiated at the top of the code.
the label is however displayed in another frame to the default one.
the label updates when code is called within the the scope of which the label is added to the panel
but when i try to update the label from the mouselistener interface i get the following error:

```
Exception in thread "AWT-EventQueue-0" java.lang.NumberFormatException: For input string: "  [ON]  "

        at java.lang.NumberFormatException.forInputString(Unknown Source)
        at java.lang.Integer.parseInt(Unknown Source)
        at java.lang.Integer.valueOf(Unknown Source)
        at HomeController.mousePressed(HomeController.java:279)
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

some code snipets are:

```
	private JLabel lblOff = new JLabel("  [OFF]  ");		
	private	JLabel lblOn = new JLabel("  [ON]  ");




public void mousePressed(MouseEvent me) 
{
	Object s = me.getSource();
	if(s == lblOff)
	{
		lblOff.setForeground(Color.red);
		lblOn.setForeground(Color.gray);
	}
	if(s == lblOn)
	{
		lblOff.setForeground(Color.gray);
		lblOn.setForeground(Color.green);
	}
}


// below code called within the same block scope and ive tested it updates the label fine, but the above code when called by the listener errors

EditFrameLampPanel.add(lblOn);
EditFrameLampPanel.add(lblOff);

lblOn.addMouseListener(this);
lblOff.addMouseListener(this);

		if(powerStatus)
		{
			lblOn.setForeground(Color.green);
			lblOff.setForeground(Color.gray);
		}
		else
		{
			lblOn.setForeground(Color.gray);
			lblOff.setForeground(Color.red);
		}


```

---

### Post by dwhitney67 on 2009-05-03
It really irks me when someone does not post a complete example.

Here's something I threw together in a few minutes; it works as expected.  You must be doing something else?  The only subtle difference I see between the code you posted and what I have, is that I use of an else-if in the mousePressed() event handler.  But that shouldn't make a difference, albeit my method is more efficient.

```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;


class MyFrame extends JFrame implements MouseListener
{
  private JLabel lblOff = new JLabel("  [OFF]  ");
  private JLabel lblOn  = new JLabel("  [ON]  ");

  public MyFrame()
  {
    super("MyFrame");

    Dimension size = getToolkit().getScreenSize();
    int       xLoc = size.width  / 4;
    int       yLoc = size.height / 3;

    setLocation(xLoc, yLoc);

    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JPanel panel = new JPanel();

    panel.add(lblOff);
    panel.add(lblOn);

    lblOff.addMouseListener(this);
    lblOn.addMouseListener(this);

    lblOff.setForeground(Color.red);
    lblOn.setForeground(Color.gray);

    getContentPane().setLayout(new BorderLayout());
    getContentPane().add(panel, BorderLayout.CENTER);
  }

  public void display()
  {
    pack();
    setVisible(true);
  }

  public void mousePressed(MouseEvent me)
  {
    Object s = me.getSource();

    if (s == lblOff)
    {
      lblOff.setForeground(Color.red);
      lblOn.setForeground(Color.gray);
    }
    else if (s == lblOn)
    {
      lblOff.setForeground(Color.gray);
      lblOn.setForeground(Color.green);
    }
  }

  public void mouseClicked(MouseEvent me) {}
  public void mouseReleased(MouseEvent me) {}
  public void mouseEntered(MouseEvent me) {}
  public void mouseExited(MouseEvent me) {}

  public static void main(String[] args)
  {
    MyFrame mf = new MyFrame();
    mf.display();
  }
}

```

---

### Post by codeit on 2009-05-03
mikemcleanuk,

Are you sure you post all the stuff inside your mousePressed(), which causes exceptions ?

---

