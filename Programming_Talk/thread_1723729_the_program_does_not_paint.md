---
title: "the program does not paint"
date: 2011-04-07
forum: Programming Talk
---

### Post by coshamak on 2011-04-07
```
public class Main 
{
	public static void main(String[] args) 
	{
		JFrame frame = new JFrame("2DGRAPHICS_EXAMPLE");
		Paintexample paint=new Paintexample();
		paint.init();
		frame.add(paint);
		frame.setResizable(false);
		frame.setSize(new Dimension(1024, 650));
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setVisible(true);
	}
}
```

this is the main and i call to paint.init().....
but the applet shotdown.
way?

this is the paint class:

```
public class   Paintexample extends JApplet
{
	private Graphics g;
	JPanel panel;
	public void init()
	{
		this.setLayout(new BorderLayout());
		this.panel=new JPanel();
		this.panel.setPreferredSize(new Dimension(1024,500));
		this.add(panel);
		g=this.panel.getGraphics();
		Paint(g);
	}
	public void Paint(Graphics g2)
	{
		g2=this.panel.getGraphics();
		g2.setColor(Color.black);
		g2.drawRect(50, 50, 400, 400);
	}
}
```


the eclipse write this messege:


Exception in thread "main" java.lang.NullPointerException
	at Paintexample.Paint(Paintexample.java:28)
	at Paintexample.init(Paintexample.java:23)
	at Main.main(Main.java:9)

---

### Post by simeon87 on 2011-04-07
The problem is that g2 is null. First of all, it's not a good idea to use getGraphics() as it's only needed in rare cirumstances. You want to use the normal paint method for Swing widgets, so use paint(Graphics g) instead of writing your own Paint method. You can then use the Graphics object that is provided (g).

The following should work:

```
public class   Paintexample extends JApplet
{
	private Graphics g;
	JPanel panel;
	public void init()
	{
		this.setLayout(new BorderLayout());
		this.panel=new JPanel();
		this.panel.setPreferredSize(new Dimension(1024,500));
		this.add(panel);
	}
	public void paint(Graphics g2)
	{
		g2.setColor(Color.black);
		g2.drawRect(50, 50, 400, 400);
	}
}
```

---

