---
title: "Help me as this applet java code is not responding to arrow movements..."
date: 2012-08-09
forum: Programming Talk
---

### Post by soham2013 on 2012-08-09
Help me as this applet java code is not responding to arrow movements...



import java.applet.*;
import java.awt.*;
import java.awt.event.*;

public class bhaja10 extends Applet implements KeyListener
{
	int x=200,y=200;
	String s;
	public void init()
	{
		s="Bradley Richards";
		addKeyListener(this);
    }
    public void keyPressed(KeyEvent k)
    {
		if(k.getKeyCode()==KeyEvent.VK_LEFT)
		  x=x-10;

		else if(k.getKeyCode()==KeyEvent.VK_RIGHT)
		  x=x+10;

		else if(k.getKeyCode()==KeyEvent.VK_UP)
		  y=y-10;

		else if(k.getKeyCode()==KeyEvent.VK_DOWN)
		  y=y+10;

		repaint();
    }
    public void paint(Graphics g)
	    {
		  g.drawString(s,x,y);
	    }

    public void keyTyped(KeyEvent k)
    {}
    public void keyReleased(KeyEvent k)
    {}

}

---

### Post by ofnuts on 2012-08-10
Looks OK... but you don't get keyboard events unless you have the focus, so you often have to click on the applet before using the keyboard.

---

