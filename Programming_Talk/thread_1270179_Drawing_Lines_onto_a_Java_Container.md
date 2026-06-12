---
title: "Drawing Lines onto a Java Container"
date: 2009-09-19
forum: Programming Talk
---

### Post by JCoster on 2009-09-19
I'm new to Java programming and I'm attempting to finish off my first GUI by drawing lines between two coordinates.

I'm not too sure where to start... I've seen the public void paint(Graph g) method signature several times about but I don't understand how I could call that and add the output to an existing container.

Here is what I'm trying to do:

```
Container contentPane;

Graphics g = frame.getGraphics();
g.drawLine(12, 12, 400, 400);
g.setColor(Color.BLACK);
contentPane.paintComponents(g);
```

This is inside of a method which adds Labels and other awt objects to the container.

What happens it that when I run it, the container pops up and the line drawn flashes on for literally a split second and then disappears, but all other components stay in-tact and visible.

Any ideas?

Thanks in advance.

---

### Post by Reiger on 2009-09-19
You could do so by having an anonymous inner class overriding the paint() method of your frame; like this:
```

JFrame frame = new JFrame(/*constructor args here*/) {
  @Override
  public void paint(Graphics g) {
     super.paint(g); // paint a JFrame
     /* draw more stuff here */
  }
};

```
Alternatively you could define a class (public or private) which extends JFrame() and only redefines the paint method; the code is pretty much the same:
```

class MyFrame extends JFrame {
  @Override
  public void paint(Graphics g) {
     super.paint(g); // paint a JFrame
     /* draw more stuff here */
  }
}

```

And then instantiate the frame with frame = new MyFrame(/* constructor args here */). You just have to make sure your define all necessary constructors you want to use for instantiating the frame, because my code for instance will only work as new MyFrame() and not new MyFrame("title here"): for that you would have to define a constructor to invoke the corresponding super constructor.

---

### Post by JCoster on 2009-09-19
Thank you for your quick response.

Is there no way then of adding to an existing container by calling a method then?  Does the frame have to be redrawn every time?

The reason I ask is because what I want to do is to iterate through a set, and if a certain condition is met then to draw a line from (x1,y1) to (x2,y2) after already adding in labels etc. before I reach this iteration.

(I hope that makes sense.)

Also, would I be right in thinking that using @Override is bad practice in programming?

---

### Post by Reiger on 2009-09-19
What you are doing is explicitly requesting the frame to be redrawn. Mind you, on resizing/moving the frame or whenever the frame is covered by another window or uncovered from another window the redraw will happen as well.

I do not see why annotating your code is bad coding practice: @Override is merely an annotation to say "look I am overriding stuff here".


As for what you want... Well the easiest thing would probably be to define your own public class (file of its own etc.); which extends JFrame, overrides that paint() methods and adds other methods for adding/removing dots to an internal data structure which is used in the paint() method for plotting out those dots... You will however have to either use that frame like this:
```

/* construction */
MyFrame frame = new MyFrame();

/* ... call a specific method not part of the JFrame super class , i.e.: addDot() */
frame.addDot(x, y);

```

Or do a cast each time you want to use a MyFrame specific (not inherited method)
```

/* constuction */
JFrame frame = new MyFrame();
/* more stuff here ... */

/* ... we cast to call a specific method not part of the JFrame super class, i.e.: addDot() */
((MyFrame) frame).addDot(x, y);

```

---

### Post by JCoster on 2009-09-19
Ok, thank you for your explanation.
I will give this ago over the weekend and let you know how I get on!

---

### Post by JCoster on 2009-09-19
Ok so I'm giving this method a try:
```
/* construction */
MyFrame frame = new MyFrame();

/* ... call a specific method not part of the JFrame super class , i.e.: addDot() */
frame.addDot(x, y);
```

The frame is setVisible in the class "Draw" and appears when run.

It is defined as ```
frame = new MyFrame("Title of Frame")
```

The MyFrame class currently is:
```
import javax.swing.JFrame;
import java.awt.*;

public class MyFrame extends JFrame {

	public MyFrame(String title) {
		super(title);
	}

	public void add(Graphics g) {
		this.paintComponents(g);
	}
	
}
```

I am then attempting to call MyFrame.add(g), where (as an example):
```
Graphics g = frame.getGraphics();
g.drawLine(12, 12, 400, 400);
g.setColor(Color.BLACK);
frame.add(g);

```

And the same is happening..; the frame is drawn with all labels permanently and the line is drawn for a split second before it disappears. I'm sure it's a case of me doing it wrong rather than your instructions, but further help would be greatly appreciated!  

Thanks.

---

### Post by Reiger on 2009-09-19
>  Well the easiest thing would probably be to define your own public class (file of its own etc.); which extends JFrame, overrides that paint() methods and adds other methods for adding/removing dots to an internal data structure which is used in the paint() method for plotting out those dots... You will however have to either use that frame like this:

Check list:
[list="1"]
[*]Define your own public class [check]
[*]which extends JFrame [check]
[*]overrides that paint() method [fail] (I am not seeing an overriding paint method... ?)
[*]add other methods for adding/removing dots [fail](You are not adding dots anywhere, you are again calling a paintComponents() method -> *explicitly requesting the paint method to be invoked* -> *explicitly requesting your changes to be wiped*)
[*]to an internal data structure [fail] (I am not seeing an internal data structure to hold those dots, anywhere... ?)
[*]which is used in the paint() method [fail] (Much less seeing it used there...)
[/list]

So 3 guesses as to what my advice would be? :P

Hint: use an ArrayList<Point> dots for holding your dots and iterate over the dots like this:
```

@Override
public void paint(Graphics g) {  
  super(g);
  for(Point p: dots) {
    g.drawLine(p.x, p.y, p.x, p.y);
  }
}

```

---

### Post by JCoster on 2009-09-22
Brilliant; thank you so much for your help, i really appreciate it.

Here is what I ended up doing:

In the draw method, I placed:
```
ArrayList<line> lineList = new ArrayList<line>();
		
// Currently just static figures to test multiple lines
lineList.add(new line(122, 122, 500, 500));
lineList.add(new line(110, 300, 200, 50));

frame.add(lineList);
```

Where:
```


public class line {
	private int startx;
	private int starty;
	private int endx;
	private int endy;
	
	public line (int startx, int starty, int endx, int endy) {
		this.startx = startx;
		this.starty = starty;
		this.endx = endx;
		this.endy = endy;
	}
	
	public int getStartX() {
		return startx;
	}
	
	public int getStartY() {
		return starty;
	}
	
	public int getEndX() {
		return endx;
	}
	
	public int getEndY() {
		return endy;
	}
}
```

And then, in my 'MyFrame' class:
```
import javax.swing.JFrame;
import java.awt.*;
import java.util.ArrayList;

public class MyFrame extends JFrame {
	private ArrayList<line> lineList;
	
	public MyFrame(String title) {
		super(title);
		lineList = new ArrayList<line>();	
	}

	public void add(ArrayList<line> lineList) {
		this.lineList = lineList;		
	}
	
	@Override
	public void paint(Graphics g) {  
	  for(line l: lineList) {
	    g.drawLine(l.getStartX(), l.getStartY(), l.getEndX(), l.getEndY());
	  }
	}
	
}
```

And I have absolutely no problem.

Thank you once again, and I'll mark the thread as solved.

---

