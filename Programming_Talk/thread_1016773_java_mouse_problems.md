---
title: "java mouse problems"
date: 2008-12-20
forum: Programming Talk
---

### Post by sandyd on 2008-12-20
i'm currently trying to make the java applet draw circles at the place where the mouse is clicked. THe problem is that on the 5th line, java says that theirs a problem with the part "implements MouseListener ". can you help please?

---code---
import java.awt.*;
import java.awt.event.*;
import java.applet.*;

public class Intro extends Applet implements MouseListener {

  public void init() {
    addMouseListener(this);
  }



       
    
@Override
public void paint(Graphics g) {
setSize(1024,768);      

Image Img1 = getImage(getCodeBase(), "http://img210.imageshack.us/img210/6033/newyorkcityut0.jpg");


//g.drawImage(Img1, 1, 1, 1022, 766, this);

        Font f = new Font ("Serif", Font.BOLD, 30);
        FontMetrics fm = g.getFontMetrics();
        g.setFont(f);
        g.setColor(Color.red);//set font color
        int width;
        int height;
        width = (this.size().width); //find width of applet
        height = (this.size().height);//find height of applet
   
        g.drawString("Asteroid Attack in New York",((width/2)-260), (height/2));//center and print name of game
        g.drawString("By Gary Tang", ((width/2)-140), ((height/2)+70));//center and print name
         try
                    {
                        Thread.sleep(10000); // do nothing for 10000 miliseconds (10 seconda)
                    }
                        catch(InterruptedException q)
                    {
                        q.printStackTrace();
                    } 
        


        }

    
public void mousePressed(MouseEvent e) {
		Graphics g = getGraphics();
		int radius = 30;
		g.setColor(Color.red);
		g.fillOval(e.getX()-radius, e.getY()-radius, 2*radius, 2*radius);
	}   
     

}

---

### Post by bobrocks on 2008-12-20
Hello,

When you post code can you please post it inside code tags, or php tags, as it will then keep it's identation and people will be able to read it. 

Also post entire compile errors not just that java says there is a problem.  I would expect it to say something along the lines of Intro not implementing all methods from the interface MouseListener.  Or something equally informative.

In java if you implement an interface you must create an implementation of all methods on that interface unless you declare your class abstract.  You have only implemented one method, mousePressed, as far as I can see from this code hence the compiler will not let you continue.

---

### Post by achelis on 2008-12-20
What bobrocks says :)

You can find the documentation for MouseListener here:

[http://java.sun.com/j2se/1.5.0/docs/api/java/awt/event/MouseListener.html]("http://java.sun.com/j2se/1.5.0/docs/api/java/awt/event/MouseListener.html")

---

### Post by cl333r on 2008-12-20
You needed to implement all Mouse Listener methods not just the one you're interested into.
```

package testapplet;

import java.awt.*;
import java.awt.event.*;
import java.net.URL;
import javax.swing.JApplet;

public class Intro extends JApplet implements MouseListener, Runnable {
	Image image = null;
	private Thread th = null;
	private Point p = null;

	@Override
	public void init() {
		addMouseListener(this);
		if( th == null ) {
			th = new Thread( this );
			th.start();//calls the run() method
		}

		setSize(1024, 76);
	}

	public void run() {
		//load image in background so the applet stays responsible to clicks.
		System.out.println( "started loading image.." );
		image = getImage( "http://img210.imageshack.us/img210/6033/newyorkcityut0.jpg");
		System.out.println( "done, gotta repaint the applet to draw background image now." );
		repaint();
	}

	@Override
	public void paint(Graphics g) {
		if( image != null ) {
			g.drawImage(image, 1, 1, 1022, 766, this);
		}
		
		Font f = new Font("Serif", Font.BOLD, 30);
		g.setFont(f);
		g.setColor(Color.red);//set font color
		int width;
		int height;
		width = getWidth();
		height = getHeight();
		g.drawString("Asteroid Attack in New York", ((width / 2) - 260), (height / 2));//center and print name of game
		g.drawString("By Gary Tang", ((width / 2) - 140), ((height / 2) + 70));//center and print name

		if( p != null ) {
			int radius = 30;
			g.setColor(Color.red);
			g.fillOval((int)p.getX() - radius, (int)p.getY() - radius, 2 * radius, 2 * radius);
		}
	}

	public void mousePressed(MouseEvent e) {
		p = e.getPoint();
		repaint();
	}

	public void mouseClicked(MouseEvent arg0) {
	}

	public void mouseReleased(MouseEvent arg0) {
	}

	public void mouseEntered(MouseEvent arg0) {
	}

	public void mouseExited(MouseEvent arg0) {
	}

	private Image getImage(String string) {
		try {
			return javax.imageio.ImageIO.read( new URL( string ) );
		} catch( Exception exc ) {
			System.err.println( "Can't load image: " + exc );
			return null;
		}
	}
}

```

Also attached the NetBeans project.

---

### Post by cl333r on 2008-12-20
btw, don't use java.awt.Applet, but javax.swing.JApplet instead, because the former has been deprecated long ago and the latter is designed to work fine with Swing and Java 2D.

---

### Post by sandyd on 2008-12-20
thanks!
that solved my problem

---

