---
title: "Buttons do not work :("
date: 2009-12-09
forum: Programming Talk
---

### Post by gaarheidswafel on 2009-12-09
My Buttons do not work in the following code:

```
import java.awt.*;
import java.awt.event.*;
import java.applet.Applet;



public class Cirkel extends Applet implements ActionListener{
	Button b1;
	Button b2;
	int radius;
	
	public void init(){
	b1=new Button("Smaller");
	b2=new Button("Bigger");
	this.add(b1);
	this.add(b2);
	b1.addActionListener(this);
	b2.addActionListener(this);
	
	radius=100;
	}

	public void actionPerformed(ActionEvent e){
		if(e.getSource()=="Smaller" && radius>=10)
			radius-=10;
		if(e.getSource()=="Bigger" && radius<=200)
			radius+=10;
		
		this.repaint();
		
	}
	public void paint(Graphics g){
		g.setColor(Color.RED);
		g.fillOval(150-radius, 150-radius, 2*radius, 2*radius);
	}
}

```
Why don't my Buttons work ie: why does my circle not grow or shrink?

---

### Post by froggyswamp on 2009-12-09
About 8 years ago (maybe more) all java.awt.* gui classes like buttons, labels, panels have been deprecated.
In other words it looks like you are reading an old book.
You need to learn Swing.
[http://java.sun.com/docs/books/tutorial/ui/index.html](http://java.sun.com/docs/books/tutorial/ui/index.html)

edit: if you insist on continuing using java.awt - these components are not supported (but still ship in the default JRE for backwards compatibility, whether it's worth to try to be compatible with such old stuff is another question) any longer and you're supposed to run sooner or later into troubles.
And instead of java.awt.Applet use javax.swing.JApplet

---

### Post by sheep1 on 2009-12-09
I believe in the action listener e.getSource() == "Smaller" and e.getSource == "Bigger" should be e.getSource() == b1 and e.getSource() == b2

---

### Post by Zugzwang on 2009-12-09
> **sheep1 said:**
> I believe in the action listener e.getSource() == "Smaller" and e.getSource == "Bigger" should be e.getSource() == b1 and e.getSource() == b2

@OP: Even though this is likely to be the cause, note that you should never compare strings for equality using the "==" operator in Java. Always use the String.equals(...) function.

---

### Post by doas777 on 2009-12-09
> **Zugzwang said:**
> @OP: Even though this is likely to be the cause, note that you should never compare strings for equality using the "==" operator in Java. Always use the String.equals(...) function.

that there, is much of why I hate java...

op, swing or swt are much better options. also, be sure to define your listeners to point to a discrete method.

---

### Post by gaarheidswafel on 2009-12-13
> I believe in the action listener e.getSource() == "Smaller" and e.getSource == "Bigger" should be e.getSource() == b1 and e.getSource() == b2

Thanks, that was the right answer, sheep1.

PS: indeed: string **content** must be compared with equals, while string **variables** must be compared with ==.

---

### Post by Zugzwang on 2009-12-13
> **gaarheidswafel said:**
> PS: indeed: string **content** must be compared with equals, while string **variables** must be compared with ==.

What do you mean by comparing string variables? The variables "a" and "b" are never the same from a syntactic point of view (but their content might), so why bother with comparing them?

---

