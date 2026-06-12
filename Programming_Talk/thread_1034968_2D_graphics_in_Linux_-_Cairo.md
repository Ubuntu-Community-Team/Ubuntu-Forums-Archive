---
title: "2D graphics in Linux - Cairo?"
date: 2009-01-09
forum: Programming Talk
---

### Post by spupy on 2009-01-09
Hi fellow Linux users.
I'm interested in doing some simple 2D graphics programming. What I want is to be able to draw things directly on the screen (not in a window) or in full screen. Something looking like cairo/awn/whatever dock, desktop widgets, gnome-do, etc.

After reading for a while it seems that Cairo is a very good choice. Are there any other good options?
I'm a little familiar with Cairo since I used to tinker with two gtk engines that used it for drawing widgets.

Also, what language would be best? From the languages I know Java is out of the question (i know it best but not a huge fan); C looks perfect for this project. I see Cairo has bindings for python - I would like to try that as well since I started playing with python some time ago. Is there any speed penalty when using python instead of C? (C being the "native" language of Cairo)

P.S.: Since compositing is not obligatory for cairo-dock, I guess it isn't necessary for cairo at all?

---

### Post by Kilon on 2009-01-09
> **spupy said:**
> Hi fellow Linux users.
I'm interested in doing some simple 2D graphics programming. What I want is to be able to draw things directly on the screen (not in a window) or in full screen. Something looking like cairo/awn/whatever dock, desktop widgets, gnome-do, etc.

After reading for a while it seems that Cairo is a very good choice. Are there any other good options?
I'm a little familiar with Cairo since I used to tinker with two gtk engines that used it for drawing widgets.

Also, what language would be best? From the languages I know Java is out of the question (i know it best but not a huge fan); C looks perfect for this project. I see Cairo has bindings for python - I would like to try that as well since I started playing with python some time ago. Is there any speed penalty when using python instead of C? (C being the "native" language of Cairo)

P.S.: Since compositing is not obligatory for cairo-dock, I guess it isn't necessary for cairo at all?

Python has PyGame for fast and impressive 2d stuff. JAVA is out of the question but JAVA2dD is really powerful stuff. I guess it is out of the question cause you dont like the C++ syntax or the whole OBJECT ORIENTATED deal. 

If that is so then you still can use JAVA libraries with python syntax. 

I use Jython for exactly the same thing. Believe me when I say that is a piece of cake. Dead easy syntax combined with JAVA power. And also I managed yesterday to package my jython app in a JAR. All it takes to run is a double click, probably the easiest way to deploy application. No install required. Very simple and easy to build and execute.

Oh by the way , there is a voice inside me saying that you are going to love "Processing". What is "processing" I hear you say?

take a look here

[http://www.processing.org/](http://www.processing.org/)

---

### Post by spupy on 2009-01-09
> **Kilon said:**
> Python has PyGame for fast and impressive 2d stuff. JAVA is out of the question but JAVA2dD is really powerful stuff. I guess it is out of the question cause you dont like the C++ syntax or the whole OBJECT ORIENTATED deal. 

If that is so then you still can use JAVA libraries with python syntax. 

I use Jython for exactly the same thing. Believe me when I say that is a piece of cake. Dead easy syntax combined with JAVA power. And also I managed yesterday to package my jython app in a JAR. All it takes to run is a double click, probably the easiest way to deploy application. No install required. Very simple and easy to build and execute.

It's not that I don't like java, its syntax or OOP. For this project I need neither of these things. 

But why should I use jpython + java2d (if I understand you correctly) instead of python+cairo. Or even C+cairo? This is the answer that I'm looking for.

If it isn't closed source, can you please share that jpython app of yours, I would like to see the source and how the binary runs.

---

### Post by techmarks on 2009-01-09
.

---

### Post by Kilon on 2009-01-09
> **spupy said:**
> It's not that I don't like java, its syntax or OOP. For this project I need neither of these things. 

But why should I use jpython + java2d (if I understand you correctly) instead of python+cairo. Or even C+cairo? This is the answer that I'm looking for.

If it isn't closed source, can you please share that jpython app of yours, I would like to see the source and how the binary runs.


Ah choices ... choices ... choices.... is it not fun to have so many choices ?

Well jython has the same syntax as python , but instead of using python libraries it uses java libraries. Why I prefer java libraries ? well java is very well behaved in macos and widely supported. I fell that java is more cross platform than jython and of course there is so much java code out there that is so dead easy to convert to jython.  

Other than that , I will be happy when you will be happy.Cairo with C or python can be just as fine. I have no experience with Cairo.   

Oh by the way , take a look at processing . It really worths your time.  

Here is a compare between a java code and jython code. It is a programm I made to test the speed of Jython against Java.

Java --->


```
import javax.swing.JFrame;
import javax.swing.JButton;
import java.awt.color.*;
import java.awt.geom.Line2D;
import java.awt.*;
import java.util.Observable;
import javax.swing.JComponent;
import java.util.Observer;




public class Central {
	




	static JFrame aWindow = new JFrame("This is my window");
	
	
	public static void main(String[] args)
	{
		//Toolkit theKit = aWindow.getToolkit();
		//Dimension wndSize = theKit.getScreenSize();
		long StartTime = System.nanoTime();

		CentralView view; 
		view = new CentralView() ;
		
		aWindow.getContentPane().add(view, BorderLayout.CENTER);
		
		aWindow.setBounds(0,0,800,500);
		aWindow.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		aWindow.setCursor(Cursor.getPredefinedCursor(Cursor.CROSSHAIR_CURSOR));
		aWindow.getContentPane().setBackground(Color.PINK);
		aWindow.setVisible(true);
		long EndTime = System.nanoTime() ;
		long TimeExec= EndTime - StartTime;
		
		aWindow.getContentPane().add(new JButton("Time of Excution in nano seconds:"+TimeExec));
		
		
	}
	
}

class CentralView extends JComponent implements Observer {
	/**
	 * 
	 */
	private static final long serialVersionUID = 1L;

	public void paint(Graphics g){
		Graphics2D g2D = (Graphics2D)g;
		
		for (double x=0 ; x<801; x++){
			for(double y=0; y<501; y++){
				Line2D.Double l1 = new Line2D.Double(x,y,x,y);
				g2D.setPaint(Color.BLUE);
				g2D.draw(l1);
			}
		}
		
		g2D.setPaint(Color.RED);
		g2D.draw3DRect(50, 50, 100, 100, true);
		
		g2D.drawString("A Speed Test ", 60, 100);
		
	
	}

	@Override
	public void update(Observable arg0, Object arg1) {
		// TODO Auto-generated method stub
		
	}
}
```


Jython code

```

"""\
Equivalent to the ../awt/simple.py example but using swing components
instead of AWT ones.
"""

# This line will import the appropriate swing library for your system (jdk 1.1 or 1.2)
from javax import swing

from java import awt
from java import util
from java import lang

class CentralView(swing.JComponent, util.Observer):
    def paint(self,g):
        
        for x in range(0,800):
            for y in range(0,500):
                l1 = awt.geom.Line2D.Double(x,y,x,y)
                g.draw(l1)
                
        g.setPaint(awt.Color.RED)
        g.draw3DRect(50,50,100,100,1)
        g.drawString("a nice square", 60, 100)

StartTime = lang.System.nanoTime()
view = CentralView()

                       
aWindow = swing.JFrame('This is my window ')
aWindow.getContentPane().add(view, awt.BorderLayout.CENTER)
aWindow.setBounds(0,0,800,500)
aWindow.setDefaultCloseOperation(swing.JFrame.EXIT_ON_CLOSE)
aWindow.setCursor(awt.Cursor.getPredefinedCursor(awt.Cursor.CROSSHAIR_CURSOR))
aWindow.getContentPane().add(view,)
aWindow.setVisible(1)
EndTime = lang.System.nanoTime()
TimeExec = EndTime - StartTime
aWindow.getContentPane().add(swing.JButton("Time of Execution in nano seconds:"+str(TimeExec)))
```

as you can see Jython is 100% python using java libraries. And of course the code is alot less than Java and C.

---

### Post by alternatealias on 2009-01-09
If you are familiar and comfortable with C++, you might also look at AntiGrain:

[http://www.antigrain.com/](http://www.antigrain.com/)

As someone else has already pointed out in this thread, with cairo (and antigrain), you'll still need to create your own window. You can't just draw to the root window unless you get its context first (and I'm not yet proficient enough with Linux programming to figure out how to do that; I'm sadly a Windows programmer by day).

---

### Post by spupy on 2009-01-09
I looked at Cairo's API and some examples. I still can't figure out how to draw on the screen directly - not in a root window and not in a normal window. Strange :???:

EDIT: Let me shed some light on what I want my program to do. Take a screenshot of the whole screen or one window, and manipulate it. And move the (manipulated) image around to make some animations.

---

### Post by fabounet on 2009-01-09
draw on screen = draw on the root window
so you'll need to create a drawing context on this window.

Cairo is indeed a good choice for 2D, but be aware that you can't really do animations (it is not a very fast library, but this is counterparted by its powerful API)

---

### Post by Kilon on 2009-01-09
> **spupy said:**
> I looked at Cairo's API and some examples. I still can't figure out how to draw on the screen directly - not in a root window and not in a normal window. Strange :???:

EDIT: Let me shed some light on what I want my program to do. Take a screenshot of the whole screen or one window, and manipulate it. And move the (manipulated) image around to make some animations.

After 1 sec of googling

```
import java.util.Date;
import java.io.File;
import java.io.IOException;
import javax.imageio.ImageIO;

import java.awt.Toolkit;
import java.awt.Robot;
import java.awt.Dimension;
import java.awt.Rectangle;
import java.awt.AWTException;

import java.awt.image.BufferedImage;

public class ScreenShooter {

    public static String printScreen(String fileName) {
        try {
            Robot robot = new Robot();

            if (fileName == null)
                fileName = "C:\\" + new Date().getTime();

            Toolkit toolkit = Toolkit.getDefaultToolkit();
            Dimension screenSize = toolkit.getScreenSize();
            Rectangle screenRect = new Rectangle(screenSize);
            BufferedImage image = robot.createScreenCapture(screenRect);*

            fileName += ".png";

            try {
                ImageIO.write(image, "png", new File(fileName));
            } catch (IOException io) {}
            return fileName;
        } catch (AWTException e) {
            return null;
        }
    }
}
```

now replace this ugly Java with beautiful python code (quick and easy) and you have perfect jython start for your program.

---

