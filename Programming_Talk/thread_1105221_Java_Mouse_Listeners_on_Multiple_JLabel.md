---
title: "Java Mouse Listeners on Multiple JLabel"
date: 2009-03-24
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-03-24
Hey there im currently learning Java and am stuck on something. I need to find a efficent way of attaching the e.getSource() result to another function call such as:

setBackground(Color.BLACK)

i have several JLabel and i cant find a way to make the event action to do something based on which specific Label was clicked.

Here is my code so far:

```
import java.awt.*;
import java.awt.event.*;
import java.awt.Color;
import java.awt.Dimension;
import javax.swing.*;

class TilePanelA extends JPanel implements MouseListener
{
	JLabel jLabel1, jLabel2, jLabel3, jLabel4, jLabel5, jLabel6, jLabel7, jLabel8, jLabel9;
	
	public TilePanelA() 
	{	
		this.setLayout(new GridLayout(3,3));
		
		Dimension myLabelSize = new Dimension(200,200);

		jLabel1 = new JLabel();
		jLabel1.setOpaque(true);
		jLabel1.setBackground(Color.WHITE);
		jLabel1.setPreferredSize(myLabelSize);
		
		...
		
		jLabel9 = new JLabel();
		jLabel9.setOpaque(true);
		jLabel9.setBackground(Color.WHITE);
		jLabel9.setPreferredSize(myLabelSize);
			
		this.add(jLabel1);
		this.add(jLabel2);
		...
		this.add(jLabel9);
		
		jLabel1.addMouseListener(this);
		jLabel2.addMouseListener(this);
		...
		jLabel9.addMouseListener(this);
		
	}
	
	public void mouseEntered(MouseEvent me)
	{	
	}

	public void mouseExited(MouseEvent me)
	{	
	}

	public void mousePressed(MouseEvent me)
	{	
	}

	public void mouseReleased(MouseEvent me)
	{	
	}
	
	public void mouseClicked(MouseEvent me)
	{	
		Object event = me.getSource();
		JPanel temp = (JPanel)event;
		Color panelColor = temp.getBackground();
		if(panelColor == Color.WHITE)
		{
			temp.setBackground(Color.WHITE);
		}
		else
		{
			temp.setBackground(Color.BLACK);
		}
	}
	
}


```

The code compiles ok but when i run the program and click on one of the Labels the CMD window gives the following error:

> Exception in thread "AWT-EventQueue-0" java.lang.ClassCastException: javax.swing
.JLabel cannot be cast to javax.swing.JPanel
        at TilePanelA.mouseClicked(TilePanelA.java:108)
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

Any help would be apprechiated. I have searched ALOT and read multiple examples and many tutorial websites and documentation for Action and Mouse Listeners but none seem to have a solution for my specific problem.

Thanks
Mike

---

### Post by simeon87 on 2009-03-24
You're now casting the source of the event (a JLabel) to a JPanel, which is not possible. You could cast it to a JLabel and then just check which JLabel the user clicked on by doing:

```

JLabel label = (JLabel) event;
if (label == jLabel1) {
 // do something
}

```

---

### Post by mikemcleanuk on 2009-03-24
> **simeon87 said:**
> You're now casting the source of the event (a JLabel) to a JPanel, which is not possible. You could cast it to a JLabel and then just check which JLabel the user clicked on by doing:

```

JLabel label = (JLabel) event;
if (label == jLabel1) {
 // do something
}

```

Thanks alot that has fixed it but although i know this isnt the most efficent program overall is their not a more efficent way to do it without lots of if xy = xy then do this!

I know that its not possible to combine variables in java but is their any way to do something like this:


```

Object event = me.getSource();
event.setBackground(Color.BLACK);

OR

me.getSource().setBackground(Color.BLACK);

```

where me.getSource(); would be jPanel1 for example.

---

### Post by simeon87 on 2009-03-24
> **mikemcleanuk said:**
> Thanks alot that has fixed it but although i know this isnt the most efficent program overall is their not a more efficent way to do it without lots of if xy = xy then do this!

You're using the color of the JLabel to make a decision so you could use getBackground() on the JLabel to determine what to do.

> **mikemcleanuk said:**
> I know that its not possible to combine variables in java but is their any way to do something like this:


```

Object event = me.getSource();
event.setBackground(Color.BLACK);

OR

me.getSource().setBackground(Color.BLACK);

```

where me.getSource(); would be jPanel1 for example.

Well, you could do:

```

((JLabel) me.getSource()).setBackground(Color.BLACK);

```

but it's not pretty.

---

### Post by issih on 2009-03-24
You can also have multiple mouse listeners, which do different actions, and then attach the appropriate one to the labels depending on the desired behaviour.

Oh and look into mouseadapters, nice little wrapper classes that implement all the mouse listener interface methods as empty stubs. You then just declare them as an inner class and override the methods you want to use..it makes the code cleaner.

Hope that helps

---

### Post by mikemcleanuk on 2009-03-24
> **simeon87 said:**
> ```
((JLabel) me.getSource()).setBackground(Color.BLACK);

```

Does this method of joining variables and functions work in other areas such as being able to make a loop that creates 9 labels and does the settings etc...

something like:

```
	int count = 0;
	while(count != 9)
	{
		count++;
		redLabel((JLabel) count) = new JLabel();		
		redLabel((JLabel) count).setOpaque(true);
		
		....
	}
```

which would create redLabel1, 2, 3, 4 etc and make it Opaque and any other simular settings like Dimensions and Background Color?

Or if this doesnt work is their a way of avoiding repatidly typing the same thing out when setting up labels which all have simular settings and the only differance is the name which changes by 1 number each.

Mike

---

### Post by simeon87 on 2009-03-24
> **mikemcleanuk said:**
> Or if this doesnt work is their a way of avoiding repatidly typing the same thing out when setting up labels which all have simular settings and the only differance is the name which changes by 1 number each.

Mike

You could create an array of JLabels to store them:

```

JLabel[] jLabels = new JLabel[9];
for ( int i = 0; i < jLabels.length; i++ ) {
    jLabels[i] = new JLabel();
    jLabels[i].setOpaque(true);
}

```

---

### Post by issih on 2009-03-24
Your suggestion certainly won't work. What you are doing with the JLabel in brackets e.g.

```
((JLabel) me.getSource())
```

is telling the compiler that the object returned by me.getSource() is in fact a JLabel. This only works if that object actually is one.

In essence the return type of me.getSource() is Object, the very top of the hierarchy, so the Object returned could in fact be an instance of absilutely any class in the system. By putting that (JLabel) in front of it you are saying to the compiler, "trust me, this is actually a JLabel" and then it lets you access all the methods defined on JLabel, not just the ones on Object.

This falls in a big heap with a ClassCast exception if the object you try and cast to a JLabel is in fact NOT a JLabel. That is what happened when you were casting a JLabel as a JPanel. as JLabel doesn't inherit from JPanel that is invalid. You can only cast to something in the inheritance path of the actual object being cast.

Consequently your little example:

```
	int count = 0;
	while(count != 9)
	{
		count++;
		redLabel((JLabel) count) = new JLabel();		
		redLabel((JLabel) count).setOpaque(true);
		
		....
	}
```

is, I'm afraid, total gibberish, as you are trying to cast a primitive int to a JLabel, which is completely impossible. In addition you are trying to name a variable programatically, which you just can't do.

As already suggested you chould use an array, or a list to allow you to keep track of and easily loop over your JLabels.

Hope that helps

---

### Post by mikemcleanuk on 2009-03-24
> **issih said:**
> ...

thanks for the explination it helps me get a clearer picture of what is going on as if you understand whats happening it means your learning it not just copying code from countless previous programs every time to make a new one :P

Thanks to everyone whos contributed i think i managed to make my program alot more efficent im sure theirs still room for improvement but it is enough for me since its not actually going to be used for anything just during my learning.

Just incase anyone searches and finds this and is wondering what my final solution was here it is:

```
import java.awt.*;
import java.awt.event.*;
import java.awt.Color;
import java.awt.Dimension;
import javax.swing.*;

class TilePanelA extends JPanel implements MouseListener
{
	JLabel jLabel1, jLabel2, jLabel3, jLabel4, jLabel5, jLabel6, jLabel7, jLabel8, jLabel9;
	
	public TilePanelA() 
	{	
		this.setLayout(new GridLayout(3,3));
		Dimension myLabelSize = new Dimension(200,200);
		
		JLabel[] jLabels = new JLabel[9];
		for ( int i = 0; i < jLabels.length; i++ ) 
		{
			jLabels[i] = new JLabel();
			jLabels[i].setOpaque(true);
			jLabels[i].setBackground(Color.WHITE);
			jLabels[i].setPreferredSize(myLabelSize);
			this.add(jLabels[i]);
			jLabels[i].addMouseListener(this);
		}
	} // end of constructor
		
	// This method is called when the cursor enters the component
	public void mouseEntered(MouseEvent me){}
	// This method is called when the cursor leaves the component
	public void mouseExited(MouseEvent me){}
	// This method is called when a mouse button is pressed
	public void mousePressed(MouseEvent me)
	{
		Color bgColor = ((JLabel) me.getSource()).getBackground();
		if(bgColor == Color.WHITE)
		{
			((JLabel) me.getSource()).setBackground(Color.BLACK);
		}
		else
		{
			((JLabel) me.getSource()).setBackground(Color.WHITE);
		}
	}
	// This method is called when a mouse button is released
	public void mouseReleased(MouseEvent me){}
	// This method is called when a mouse button is pressed and released
	public void mouseClicked(MouseEvent me){}
} // end of class


```

---

### Post by HotCupOfJava on 2009-03-24
A simple solution would be to have a separate MouseListener, rather than trying to make the parent JPanel a MouseListener also, and attaching it with the "this" keyword. You would not have to use multiple MouseListeners, just the one would do.

[PHP]class TilePanel extends JPanel{
    jLabel1 = new JLabel();
    jLabel2 = new JLabel();
    jLabel3 = new JLabel();

    MyMouseListener ml = new MyMouseListener();

    jLabel1.addMouseListener(mL);
    jLabel2.addMouseListener(mL);
    // etc

}

class MyMouseListener extends MouseAdapter{
    public MyMouseListener(){
        super();
    }
    public void mouseClicked(MouseEvent evt){
        if(evt.getSource()==jLabel1){
            //Do whatever you want it to do
        }
        if(evt.getSource()==jLabel2){
            //You get the idea
        }
    }
} [/PHP]

Both classes can be stored in the same source file "TilePanel.java". If you are wanting to change something about the specific label that was clicked, you could even simplify by saying:

[PHP]public void mouseClicked(MouseEvent evt){
    evt.getSource().setBackground(Color.BLACK);
}[/PHP]

you will find the MouseAdapter class very useful. It prevents you from having to implement EVERY method of the MouseListener interface (it has already implemented it for you). Just extend it and override the method(s) you need.

---

