---
title: "Jython Speed VS JAVA"
date: 2009-01-06
forum: Programming Talk
---

### Post by Kilon on 2009-01-06
I have created a small benchmark , to test the speed of Jython when calling swing components and JAVA2D methods. I was aiming to 5x times slower speed in JYTHON but JYTHON proved me very wrong. IT was only 3 times slower than JAVA.  

The benchmark was not only for speed reasons but also a way to learn Jython .

I share with you the code of both JAVA and Jython. You may run the test in your computer and share results. 

The app is building a window and draws 1 point lines and then displays a very large button   with the amount of nanoseconds it took to execute the program. 

I run the test in a ACER ASPIRE ONE with 1.GHz Pentium Atom Processor, 500 MB RAM, 8 GB SDD HD  and WINXP. 

JAVA CODE


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

Jython Code 

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

---

### Post by pmasiar on 2009-01-06
> **Kilon said:**
> test the speed of Jython when calling swing components and JAVA2D methods. I was aiming to 5x times slower speed in JYTHON but JYTHON proved me very wrong. IT was only 3 times slower than JAVA. 

Exactly. Jim Hugunin created Jython to show that JVM is badly designed for dynamic languages, and was surprised how fast Jython was. Sadly, Sun ignored Jython for 10 years, and now is catching up when MSFT hired Hugunin to create IronPython for .NET and C# is eating Java's lunch. In some benchmarks, IronPython is faster than CPython. But Jython was recently resurrected and not all is lost yet.

---

### Post by Kilon on 2009-01-07
> **pmasiar said:**
> Exactly. Jim Hugunin created Jython to show that JVM is badly designed for dynamic languages, and was surprised how fast Jython was. Sadly, Sun ignored Jython for 10 years, and now is catching up when MSFT hired Hugunin to create IronPython for .NET and C# is eating Java's lunch. In some benchmarks, IronPython is faster than CPython. But Jython was recently resurrected and not all is lost yet.

Well I was pleasantly surprised , 3X times slower with no optimization at all is very promising. I am sure there are ways to drop this to half. 

However both java and jtyhon version were crawling on my Pentium atom (1,6 GHZ).It took the jython version 18 seconds to finish (6 secs for the Java version)  

But when I tried to run the apps on my iMac (CORE 2 DUO 2,0 GHZ) 
... boom!!!! Both loaded in an instant. At least my jython version loaded immediately , this means at least 18 times faster than the Jython version in my Acer Aspire One (1,6 GHz Atom Pentium)!!!!  But for some strange reason it reported that it was running 1000x times slower than Java version!!!! The number it was showing was even bigger than the one it was showing in the Pentium Atom (ACER ASPIRE ONE). IMPOSSIBLE !!!

Running the tests in my pc pentium  3,20 Ghz (exactly double my ACER Aspire One) at work rendered expected results  with Jython version running 3X times slower than Java version (WINXP). 

In shorty I will have UBUNTU results as well.

---

### Post by Kilon on 2009-01-07
Again I have strange finding . The same Computer (Pentium 3,2 Ghz) which in Win XP gave me 3.5x times slowness in Jython , now in UBUNTU finds 7,7x times  slowness!!! 

And the thing is that it shows. The Java version executes much faster. 

Strange , strange , strange.... seems jython likes WinXP more.

Also the result are not always the same in each execution (in all OSs). They change up to 10% with the Java version  and up to 20% with Jython version. I do not know if this is is normal behavior.

---

