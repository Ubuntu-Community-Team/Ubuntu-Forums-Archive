---
title: "Java Listeners"
date: 2008-01-09
forum: Programming Talk
---

### Post by mike_g on 2008-01-09
Hi, I would like to add a listener to a JTextField, or the window its in, that triggers whenever a mouse button is clicked anywhere. 

I had a read about the event listeners on the Java tutorials site, but that mostly just confused me with beans and bounds and stuff I don't know. And MouseListener only seems to fire when the object its attached to is clicked on.

Could someone give me a short example of how to write a listener that fires whenever a mouse button is clicked regardless of position? It would be much appreciated by me :) 

Alternatively some indication of what methods I want to be using on what objects would also be a help. Cheers.

---

### Post by mike_g on 2008-01-09
Ok, well heres my best attempt so far at getting a mouse listener to work on  a frame:
```
    public void makeFrame()
    {
        frame = new JFrame("Pizza ****");
        JPanel content = (JPanel)frame.getContentPane();
        content.setLayout(new BorderLayout());
        content.setBorder(new EmptyBorder(10, 10, 10, 10));
        
        content.setBackground(new Color(BACKGRND_R, BACKGRND_G, BACKGRND_B));
        
        //Fill the contents of the window
        makeTitleBar(content);
        makeMenuList(content);
        makeOrderList(content);
        makeBaseSection(content);

        //Apply some window settings
        MouseListener listener = new MouseListener();
        frame.addMouseListener(listener);
        
        frame.setAlwaysOnTop(true);
        frame.setResizable(false);
    }   
```
I get an error tho saying that MouseListener is abstract and can't be Instantiated. Anyone know how i can whack a mouse listener in here? Sorry for the double post; I'm in a bit of a rush at the moment as this is for an assignment  due tommorow, and we never covered this stuff o_0 

Cheers.

---

### Post by popch on 2008-01-09
> **mike_g said:**
> I get an error tho saying that MouseListener is abstract and can't be Instantiated. Anyone know how i can whack a mouse listener in here? Sorry for the double post; I'm in a bit of a rush at the moment as this is for an assignment  due tommorow, and we never covered this stuff o_0 

Cheers.

In that case, MouseListener is either an interface (and not a class) or class which is defined in so general terms that it can not be put to immediate use.

If MouseListener is an interface, use a class which implements MouseListener.

If MouseListener is an abstract class, use a subclass which is not abstract.

---

### Post by bobrocks on 2008-01-09
Hello

MouseListener is an Interface not a class, this is like a contract you are saying you are going to comply with if you implement it.  You cannot instantiate it as it is not a class it doesn't have a constructor.  For example -

[PHP]
public class Test extends JFrame implements MouseListener {

	public Test() {
		
		super("Test");
		this.setSize(800,600);
		this.setVisible(true);
		
		this.addMouseListener(this);
	}
	
	public static void main(String args[]) {
		SwingUtilities.invokeLater(new Runnable(){
			
			public void run() {
				new Test();
			}
		});
	}

	public void mouseClicked(MouseEvent e) {
		System.out.println("flying bananas");
	}

	public void mouseEntered(MouseEvent e) {
	}

	public void mouseExited(MouseEvent e) {
	}

	public void mousePressed(MouseEvent e) {
	}

	public void mouseReleased(MouseEvent e) {
	}
}

[/PHP]

*Don't look at that for good design principles, I wrote it very quickly*

As you can see if you implement the interface MouseListener it forces you to create all those mouse methods to complete the contract.  In my opinion this is bad and I would recommend you look to extend the abstract class MouseInputAdapter only overriding the methods that you need to use.  But thats up to you.

---

### Post by harold4 on 2008-01-09
[java.sun.com]("http://java.sun.com/docs/books/tutorial/uiswing/events/actionlistener.html") has fantastic documentation.

Look into this.super

---

### Post by mlind on 2008-01-09
Attach a [MouseAdapter]("http://java.sun.com/j2se/1.4.2/docs/api/java/awt/event/MouseAdapter.html") to a component you wish to listen.

```

import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;

import javax.swing.*;


public class TestMouseListener extends JFrame {
	private static final long serialVersionUID = 1L;

	public TestMouseListener() {
		Container c = getContentPane();
		c.setLayout(new FlowLayout());
		
		JTextField field = new JTextField(10);	
		field.**addMouseListener(new MouseAdapter()** {
			@Override
			public void mouseClicked(MouseEvent e) {
				((JTextField)e.getSource()).setText("click");
			}
		});
		
		c.add(field);
	}

	private static void createAndDisplay() {
		JFrame.setDefaultLookAndFeelDecorated(true);
		JFrame frame = new TestMouseListener();
		frame.setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);
		frame.pack();
		frame.setLocationRelativeTo(null); //center of the screen
		frame.setVisible(true);
	}
	
	public static void main(String[] args) throws Exception {
		SwingUtilities.invokeAndWait(new Runnable() {
			public void run() {
				createAndDisplay();				
			}
		});
	}
}

```

---

### Post by mike_g on 2008-01-09
Thanks for the replies people. Just got home atm and I'm a little bit drunk , but I'll go through this all first thing in the morning and hopefully get me prog working; as its all I have left to do.

And yeah, harold: I have to say, the sun documentation is a loteasier to understand than MSDN (to  me anyway), but I'm not the sharpest tool in the box, and theres a lot to it all. Anyway I'm hoping to do more Java coding and get used to it all; from what I have seen so far I like the language :)

Cheers.

---

### Post by harold4 on 2008-01-09
Totally agree about java vs msdn documentation.  msdn may be a mess, but Visual Studio 2k5 and 2k8 are really nice.  

Currently hunting for auto completion for python.

---

