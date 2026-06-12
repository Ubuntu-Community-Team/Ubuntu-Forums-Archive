---
title: "How to run java GUI program"
date: 2009-08-26
forum: Programming Talk
---

### Post by shankhs on 2009-08-26
I am learning java using Head First Java.
In the GUI chapter its written 

```
import javax.swing.*;
import java.awt.*;

class MyDrawPanel extends JPanel
{
	public void paintComponent (Graphics g)
	{
		g.setColor(Color.orange);
		g.fillRect(20,50,100,100);
	}
}

```
and that the method calls itself.
What does this mean?
Its compiling fine but on runtime it says :

```
Exception in thread "main" java.lang.NoSuchMethodError: main
```

How do I run this?

---

### Post by Can+~ on 2009-08-26
Java requires a class with a method named main, to start. Probably your book says something about it, as I'm not sure how you're doing it.

---

### Post by shankhs on 2009-08-26
here is my code :

```

import javax.swing.*;
import java.awt.*;

class UseSimpleGraphics
{
	public static void main(String args[])
	{
		UseSimpleGraphics u=new UseSimpleGraphics();
		u.go();
	}
	public void go()
	{
		MyDrawPanel m=new MyDrawPanel();
		Graphics g;
		m.paintComponent(g);
	}
	class MyDrawPanel extends JPanel
	{
		public void paintComponent (Graphics g)
		{
			g.setColor(Color.orange);
			g.fillRect(20,50,100,100);
		}
	}
}

```

I have used inner class and trying to draw some graphics.
Graphics object can't be initialized as its abstract.
The paintComponent in JPanel takes Graphics object as argument!
Its not running as I want.
Any suggestions?

---

### Post by Reiger on 2009-08-27
Yes, you write "Graphics g" but that doesn't mean much. It declares something called "g" of type "Graphics" but that Graphics object is not yet initialized. Also you are toying with inner classes, perhaps (probably) inadvertently: Java is quite complex and inner classes are not what you would call beginner level.

What you probably wanted was retrieving the graphics object of your panel (inherited from JPanel) to use it for drawing your own stuff. Well, you can do that like this:

```

Graphics g = m.getGraphics();

```

Also: you didn't set your DrawPanel to a specified size which means there is no knowing whether or not it will actually be visible at all (could be 0 by 0 = invisible to the human eye).

However, you will "loose" your work when the panel is resized (e.g. the containing window is resized) because the component will repaint() itself. For "learning Java" it is probably better to lump your painting code in the method paint(Graphics g) of MyDrawPanel, thereby overriding the one of the super class JPanel:

```

public void paint (Graphics g)
{
  g.setColor(Color.orange);
  g.fillRect(20,50,100,100);
}

```

This has also the nice side effect that you basically "hook" up your DrawPanel into the frame work called Swing which means you no longer have to provide for the Graphics object.

Thus your code can be simplified to:
```

import javax.swing.*;
import java.awt.*;

class UseSimpleGraphics
{
	public static void main(String args[])
	{
		UseSimpleGraphics u=new UseSimpleGraphics();
		u.go();
	}
	public void go()
	{
		MyDrawPanel m=new MyDrawPanel();
                m.setSize(220, 250); // set this panel to a size so you can see what is drawn
                m.repaint(); // re-paint the Panel, this is a handy shortcut for m.paint(m.getGraphics());
                m.setVisible(true); // make the panel visible.
	}

}
	class MyDrawPanel extends JPanel
	{
		public void paint (Graphics g)
		{
			g.setColor(Color.orange);
			g.fillRect(20,50,100,100);
		}
	}

```

---

### Post by shankhs on 2009-08-27
Thanx Reiger

---

