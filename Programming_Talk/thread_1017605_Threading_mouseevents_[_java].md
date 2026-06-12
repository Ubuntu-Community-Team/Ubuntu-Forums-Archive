---
title: "Threading mouseevents [ java]"
date: 2008-12-21
forum: Programming Talk
---

### Post by sandyd on 2008-12-21
I have a project for school and i would like to know how i would thread the mouseevents so it will paint the circles while the objects are still falling from the sky
```

import java.awt.*;
import java.awt.event.*;
import java.net.URL;
import javax.swing.JApplet;
import java.applet.*;





public class Intro extends JApplet implements MouseListener, Runnable {
	Image image = null;
        Image asteroid1 = null;
        Image asteroid2 = null;
	Image asteroid3 = null;
        Image asteroid4 = null;
        Image asteroid5 = null;
        Image asteroid6 = null;
        int asteroid1x;
        int asteroid1y;
        int asteroid2x;
        int asteroid2y;
        int asteroid3x;
        int asteroid3y;
        int asteroid4x;
        int asteroid4y;
        int asteroid5x;
        int asteroid5y;
        int asteroid6x;
        int asteroid6y;
        private Thread th = null;
	private Point p = null;
        private Thread rs = null;

	@Override
	public void init() {
       
		addMouseListener(this);
                rs = new Thread( this );
		if( th == null ) {
			th = new Thread( this );
			th.start();//calls the run() method
		}

		setSize(1024, 768);
	}

	public void run() {
		//load image in background so the applet stays responsible to clicks.
		System.out.println( "started loading images.." );
		image = getImage( "http://dl2.elyannanetworks.net/005/java/background.jpg");
		asteroid1 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid1.png");
                asteroid2 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid2.png");
                asteroid3 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid3.png");
                asteroid4 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid4.png");
                asteroid5 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid5.png");
                asteroid6 = getImage( "http://dl2.elyannanetworks.net/005/java/asteroid6.png");
                asteroid1y = 10;
                asteroid2y = 10;
                asteroid3y = 10;
                asteroid4y = 10;
                asteroid5y = 10;
                asteroid6y = 10;
               
                System.out.println( "done, gotta repaint the applet to draw background image now." );
		repaint();
	}

	@Override
	public void paint(Graphics g) {
		if( image != null ) {
			g.drawImage(image, 1, 1, 1022, 766, this);
                        image = null;
		}
		asteroid1x = (int)Math.floor(Math.random( ) * 600);
                asteroid2x = (int)Math.floor(Math.random( ) * 600);
                asteroid3x = (int)Math.floor(Math.random( ) * 600);
                asteroid4x = (int)Math.floor(Math.random( ) * 600);
                asteroid5x = (int)Math.floor(Math.random( ) * 600);
                asteroid6x = (int)Math.floor(Math.random( ) * 600);
                
                
                
		Font f = new Font("Serif", Font.BOLD, 30);
		g.setFont(f);
		g.setColor(Color.red);//set font color
		int width;
		int height;
		width = getWidth();
		height = getHeight();
		g.drawString("Paintball Shootout in New York", ((width / 2) - 260), (height / 2));//center and print name of game
		g.drawString("By Gary Tang", ((width / 2) - 140), ((height / 2) + 70));//center and print name
                 try
                    {
                        Thread.sleep(5000); // do nothing for 1000 miliseconds (1 second)
                    }
                        catch(InterruptedException e)
                    {
                        e.printStackTrace();
                 }
                for (int i = 10; i > 5; i++) {//keep it looping for eternity
                g.drawImage(asteroid1, asteroid1x, asteroid1y, 10, 20, this);
                asteroid1y = asteroid1y+1;
                 try
                    {
                        Thread.sleep(500); // do nothing for 1000 miliseconds (1 second)
                    }
                        catch(InterruptedException e)
                    {
                        e.printStackTrace();
                    }
                g.drawImage(image, 1, 1, 1022, 766, this);
                
                
		if( p != null ) {
			int radius = 10;
			g.setColor(Color.blue);
			g.fillOval((int)p.getX() - radius, (int)p.getY() - radius, 2 * radius, 2 * radius);
		}}
	
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
	}}


```

---

### Post by Phristen on 2008-12-21
What do you mean by "threading" mouse events?
I'm not sure I understand what you're trying to achieve here.

P.S. run() method is only called once... If you wanna repaint regularly, you should have some kind of loop inside...

---

### Post by sandyd on 2008-12-21
you see, the stuff thats painted with each click i make is supposed to stay there.
I want the mouseevent to work during the loop that causes my tiny asteroid to move.

---

### Post by Phristen on 2008-12-21
Define a collection of points, and add one every time you click a mouse... (if that's what you wanna do)
Then in paint method do something like this:
for (Point p : points)
g.drawOval(....);


And inside run() make a loop like this:
while (true) {
repaint();
Thread.sleep(100);
}


And make sure your mouse event is not adding to the list while another thread is looping over it... that will result in concurrent modification exception.

---

### Post by drubin on 2008-12-21
Ok Firstly some advice.
1) Use what Phristen about repainting the screen every X/ms.
2) Move your calculations out of your paint method. and into that seperate thread. (as the paint method may or may not be fired at reliable intervals)
3) Store the values from outside the paint method and use those in the paint method.

4) Java is an OO lang. make use of that istead of having asteroid1,asteroid4,asteroid3 | int1,int2. Create an Asteroid class and store the image, intx,inty in there an then have an Array of Asteroid objects.

5) Remove this code
>  ```

try{
      Thread.sleep(5000); // do nothing for 1000 miliseconds (1 second)
}catch(InterruptedException e){
      e.printStackTrace();
}
```

having thead.sleep in the paint method can call deadlocks errors and it not great coding style. Rather have a flag that is set out side the paint method and depending on the flag/screen var show the appropriate stuff.

Hope this  points you in the right directions.

---

### Post by cl333r on 2008-12-21
Here's a sample implementation.
The testapplet.zip is the NetBeans project which contains the source code and the images needed to compile.

btw, you should consider using Eclipse or NetBeans since according to the source code you paste - you ain't using any (modern) IDE. I'd recommend NetBeans since it's more user friendly.

ps: You should dig dipper into how to use animation with threads.

The Java executable (save and double click to launch):
[http://xlinuks.googlepages.com/testapplet.jar](http://xlinuks.googlepages.com/testapplet.jar)

---

### Post by drubin on 2008-12-21
> **cl333r said:**
> Here's a sample implementation.
The testapplet.zip is the NetBeans project which contains the source code and the images needed to compile.

btw, you should consider using Eclipse or NetBeans since according to the source code you paste - you ain't using any (modern) IDE. I'd recommend NetBeans since it's more user friendly.

ps: You should dig dipper into how to use animation with threads.

The Java executable (save and double click to launch):
[http://xlinuks.googlepages.com/testapplet.jar](http://xlinuks.googlepages.com/testapplet.jar)

This post instills all the values that I (maybe others) disagree with.

1) Posting complete answer. This post has even gone to the extent of including the images/projects. Including the *binary* (and I use the word lightly as java is not compiled) for the project.

Programmers need to work things out for them selves else they are never going to learn any thing. Programmers learn by doing and failing and then getting up again and trying again. not by being given.

2) There is no need to use an IDE to make you a good programmer infact it makes you a lazy bad one. (I my self use an IDE purely because it is convenent and makes my life easier for deadlines and work) but it does hide  all the things that happen in the background knowledge with you code that are *needed* to understand what is going on.

I have one question:
What learning is expected to be done from your example?

---

### Post by cl333r on 2008-12-21
Look at the source code and remember the answer you find right there. It answers many questions that would take that guy hours to find scattered across the net. Finding answers to questions is a blink is good regardless of the taste.
As to IDE's - I disagree. It doesn't make you lazy unless you're lazy. Since I started using NetBeans (I used jEdit) I got much more productive and started doing many things better because the IDE noted those things and suggested doing otherwise. So talkging about laziness should apply to yourself, not necessarily to the others.

---

### Post by drubin on 2008-12-21
> **cl333r said:**
> Look at the source code and remember the answer you find right there. It answers many questions that would take that guy hours to find scattered across the net. Finding answers to questions is a blink is good regardless of the taste.
Hours well spent learning.

> **cl333r said:**
> 
As to IDE's - I disagree. It doesn't make you lazy unless you're lazy. Since I started using NetBeans (I used jEdit) I got much more productive and started doing many things better because the IDE noted those things and suggested doing otherwise. So talkging about laziness should apply to yourself, not necessarily to the others.

I am not saying IDE's are bad (To clarify my previous point). I am saying starting off with IDE's is bad. You need to understand the fundamentals before letting the IDE do things for you.

Also Like I said I use an IDE because it makes me more productive but it doesn't mean I agree with learning to program with an IDE

**EDIT:**
This will be my last point on this "sub topic" as it has no relevance to the OP.

---

