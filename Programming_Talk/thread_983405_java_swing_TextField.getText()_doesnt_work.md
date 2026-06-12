---
title: "java swing TextField.getText() doesnt work"
date: 2008-11-15
forum: Programming Talk
---

### Post by exhume on 2008-11-15
Hey guys,

I am trying to teach myself Java and I have run into a strange problem where every time I try to get the text from a swing textField using getText() a null pointer exception is thrown and the program stops working. My code is as follows:

```
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JButton;
import javax.swing.JTextField;
import javax.swing.JTextArea;
import javax.swing.JCheckBox;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import java.awt.FlowLayout;

public class rulecreator extends JFrame implements ActionListener
{
	public static final int WIDTH = 500;
	public static final int HEIGHT = 500;
	public static final int fieldlen = 5;
	public static final long serialVersionUID = 1;

	JTextField file;
	JLabel filelabel;
	JTextField name;
	JLabel namelabel;
	JTextArea summary;
	JTextField book;
	JLabel booklabel;
	JTextField page;
	JLabel pagelabel;
	JCheckBox optional;
	JLabel optionlabel;
	JButton create;
	JButton open;
	//rule rule;
	int i;

	public static void main(String[] args)
	{
		rulecreator ui = new rulecreator();
		ui.setVisible(true);
	}

	public rulecreator()
	{
		super();
		setTitle("Rule Creator");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setSize(WIDTH, HEIGHT);
		setLayout(new FlowLayout());
		JLabel filelabel = new JLabel("File:");
		add(filelabel);
		JTextField file = new JTextField(10);
		add(file);
		JLabel namelabel = new JLabel("Name:");
		add(namelabel);
		JTextField name = new JTextField(10);
		add(name);
		JTextArea summary = new JTextArea("Rule Summary", 10, 40);
		add(summary);
		JLabel booklabel = new JLabel("Book:");
		add(booklabel);
		JTextField book = new JTextField(10);
		add(book);
		JLabel pagelabel = new JLabel("          Page:");
		add(pagelabel);
		JTextField page = new JTextField(3);
		add(page);
		JLabel optionlabel = new JLabel("               Optional:");
		add(optionlabel);
		JCheckBox optional = new JCheckBox();
		add(optional);
		JButton create = new JButton("Create");
		create.addActionListener(this);
		add(create);
		JButton open = new JButton("Open");
		//open.addActionListener(this);
		add(open);
		
	}

	public void actionPerformed(ActionEvent e)
	{
		String buttonString = e.getActionCommand();
		if(buttonString.equals("Create"))
		{
			System.out.println(file.getText());
			//rule = new rule(name.getText(), optional.isSelected(), summary.getText(), book.getText(), Integer.parseInt(this.page.getText()));
			//rule.save(file.getText());
		}
		//else if(buttonString.equals("Open"))
			//open();
	}
	
}
```

This is the error I get when I click the "Create" Button:


```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at rulecreator.actionPerformed(Unknown Source)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6041)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5806)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4413)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4243)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2440)
        at java.awt.Component.dispatchEvent(Component.java:4243)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
```


 After some testing I figured out that it is the getText() method that is causing the exception. I can have it just print a random string I put in and I get no problem (but this is useless). Thanks for the help in advance!

---

### Post by dwhitney67 on 2008-11-15
You have declared member data handles in your class, but you are never allocated memory for them.

The objects that are allocated in the constructor, rulecreator(), are assigned to local variables within that method.  Just remove the declaration portion so that Java will interpret that you are attempting to allocate and assign to your class member data.  Does that make sense?

In summary, this is an example of the error:
```

public rulecreator()
{
  ...
  JLabel filelabel = new JLabel("File:");
  ...

```
It should be:
```

public rulecreator()
{
  ...
  filelabel = new JLabel("File:");
  ...

```

---

### Post by Ragazzo on 2008-11-15
When you write [PHP]JTextField name = new JTextField(10);
[/PHP] you declare a new local variable and instantiate it. Change it to 
[PHP]name = new JTextField(10);
//or to make sure:
this.name = new JTextField(10);
[/PHP] and it should work.

---

### Post by exhume on 2008-11-15
Thanks a lot guys! That fixed it. I thought it kindof odd that the book I was looking in was telling me to use the constructors that way. This isn't my first language and I knew that was not the usual convention. I just figured it was something weird about the way it was done in Java.

---

