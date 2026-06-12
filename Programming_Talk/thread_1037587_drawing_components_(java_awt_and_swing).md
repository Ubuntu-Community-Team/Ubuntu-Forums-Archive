---
title: "drawing components (java awt and swing)"
date: 2009-01-11
forum: Programming Talk
---

### Post by zizzdude on 2009-01-11
hey, I have something similar to this
```

public class Ball
{
    private Canvas panel;  // where it should be drawn on

    public void draw(Graphics g)
    {
        Image image = .. // image file;
        g.drawImage(image, 10, 10, panel);
    }
}

public class Canvas
{
    private Ball ball;

    public void pantComponent(Graphics g)
    {
        g.setColor(Color.white);
        g.fillRect(0,0, this.getWidth(), this.getHeight());
        ball.draw(g);
    }
    
    public static void main(String[] args)
    {
        // made JFrame frame ...
        frame.add(new Canvas());
        frame.setVisible(true);
    }
}

```

For some reason, I cannot see the image. Any reasons why it shouldn't?

Thanks. :)

---

### Post by lordikyiky on 2009-01-11
Where are you initializing the Canvas variable named panel?

I can't tell if you've just left that line out of your posted code or if it is missing from the program

for that matter, did you initialize "ball"?

---

### Post by zizzdude on 2009-01-11
> **lordikyiky said:**
> Where are you initializing the Canvas variable named panel?

I can't tell if you've just left that line out of your posted code or if it is missing from the program

well, let's say all the variables there are initialized. One thing I left out was having Canvas inheriting JPanel. Really, I just wrote down the methods that I had issues with. No errors, just could not see the image.

---

### Post by lordikyiky on 2009-01-11
Replace the g.drawImage line with a g.drawOval (different color) or something to see if that line is the problem.

If it is, an ImageIcon might be more appropriate here.

---

### Post by zizzdude on 2009-01-11
ok, I wrote down a test, and it worked fine. maybe I should post my real code:

```


==== Projectile.java ====

package universal_launch.materials;

import universal_launch.extras.Position;
import java.awt.*;
import javax.swing.*;
import universal_launch.frontend.Visualizer;

public class Projectile extends JComponent
{
	private Position myCenter;
	private Planet myLocation;
	private Visualizer container;
	
	public Projectile(Position center, Planet location)
	{
		myCenter = center;
		myLocation = location;
	}
	
	public Position getCenter()
	{return myCenter;}
	
	public void moveTo(Position newCenter)
	{myCenter = newCenter;}
	
	public String toString()
	{
		return "coord: " + myCenter;
	}
	
	public void setVisual(Visualizer c)
	{container = c;}
	
	public void draw(Graphics g)
	{
		//System.out.println("Painting Projectile thing");
		int x = (int)(myCenter.getX());
		int y = (int)(container.getHeight() - myCenter.getY());
		g.setColor(Color.red);
		g.fillOval(x, y, 10,10);
		System.out.println("drawing Image");
		Image image = new ImageIcon("smiley.gif").getImage();
		g.drawImage(image,x, y+50, container);
	}
}


==== Visualizer.java ====
package universal_launch.frontend;

import java.awt.*;
import java.awt.event.*;
import java.util.ArrayList;
import universal_launch.materials.*;
import universal_launch.extras.*;
import javax.swing.*;

public class Visualizer extends JPanel
{
	private Planet myPlanet;
	//private Projectile myBall;
	private Launcher myCannon = new Launcher(40);
	private int height, width;
	private ArrayList<Position> coordinates;
	private boolean ready;
	private Timer animationTimer;
	
	public Visualizer(Planet planet, Launcher launcher)
	{
		super();
		//setLayout(null);
		myPlanet = planet;
		myCannon = launcher;
		myCannon.setVisual(this);
		//add(myCannon.getAmmo());
		//height = 480;
		//width = 640;
		coordinates = new ArrayList<Position>();
		//setSize(width,height);
		animationTimer = new Timer(5, new VisualAnimation());
	}
	
	public void paintComponent(Graphics g)
	{
		//System.out.println("Paint Visualizer");
		g.setColor(Color.white);
		g.fillRect(0,0,this.getWidth(), this.getHeight());
		
		//System.out.println("Painting Ball");
		myCannon.getAmmo().draw(g);
		//g.setColor(Color.black);
		//g.fillOval((int)(myCannon.getAmmo().getCenter().getX()), this.getHeight() - (int)(myCannon.getAmmo().getCenter().getY()), 10,10);
	}
	
	public void executeGraph()
	{
		//System.out.println("== ready for launch ==");
		myCannon.directAmmo(0);
		double maxY = 0;
		//coordinates.clear();
		for (double seconds = 0; myCannon.getAmmo().getCenter().getY() >= 0; seconds += .1)
		{
			//System.out.println("loading");
			myCannon.directAmmo(seconds);
			if (maxY < myCannon.getAmmo().getCenter().getY())
				maxY = myCannon.getAmmo().getCenter().getY();
			//System.out.println(myCannon.getAmmo().getCenter());
			coordinates.add(myCannon.getAmmo().getCenter());
		}
	}
	
	public void clearGraph()
	{
		coordinates.clear();
	}
	
	public void setReady(boolean thing)
	{
		//System.out.println("Ready for Take OFF");
		ready = thing;
	}
	
	public void getAnimationReady()
	{animationTimer.start();}
	
	public ArrayList<Position> getCoord()
	{return coordinates;}
	
	private class VisualAnimation implements ActionListener
	{
		private int index = 0;
		
		public void actionPerformed(ActionEvent e)
		{
			System.out.println("Starting Animation");
			//System.out.println(coordinates.get(index));
			if (index < coordinates.size() - 1)
			{
				myCannon.getAmmo().moveTo(coordinates.get(index));
				repaint();
				index++;
			}
			else
			{
				animationTimer.stop();
			}
		}
	}
}


```

cannon.getAmmo() is the projectile/ball btw. I drew the oval and it works, just not the image.

---

