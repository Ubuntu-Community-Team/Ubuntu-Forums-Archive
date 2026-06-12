---
title: "java Simple GUI Understanding"
date: 2009-05-02
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-02
Hey i just thought i would throw this out there, i am currently searching and testing alot. But i am finding it very hard to get my hear arround extending the JPanel and various layout managers working together.

What i basicly want is a template with the different ways you can play with this so i can see it working.

I am currently trying and failing to:


Have 1 Driver Code that starts a JFrame and then initiated the class from another class file e.g. (with border layout)

```

JFrame myWindow = new JFrame("Test UI");		
UIBuilder uib = new UIBuilder();
myWindow.getContentPane().add(uib,BorderLayout.CENTER);

```

Then in the UIBuilder i want to be able to create the different panes and again use a border layout to layout them how i want. Then when the driver code takes the GUI it will be displayed exactly how i want it to be.

For example a line of Buttons at NORTH a big text area CENTER, another line of buttons SOUTH.

Could someone if you have simple examples or the time just throw together a basic representation of this working so i can begin to understand the path through the code and how everything links together.

I have looked for tutorials but they are all either the very basic or go to advanced for me. I am still on a search but would apprechiate some simplistic code to work from.

This is some of the stuff im playing with at the moment:

```
import java.awt.*;
import javax.swing.*;

class UIBuilder extends JPanel
{
	private JButton testButton1 = new JButton("One"), testButton2 = new JButton("Two");
 	private JTextArea testArea1 = new JTextArea(200,200);
	private JPanel TopPanel = new JPanel();
	private JPanel CenPanel = new JPanel();
	private JPanel BotPanel = new JPanel();
		
	public UIBuilder()
	{
		JFrame jf = new JFrame();
		jf.add(TopPanel, BorderLayout.NORTH);
		jf.add(CenPanel, BorderLayout.CENTER);
		jf.add(BotPanel, BorderLayout.SOUTH);

		TopPanel.add(testButton1);
		CenPanel.add(testArea1);
		BotPanel.add(testButton2);
		add(jf);
	}
}
```

```
import java.awt.*;
import javax.swing.*;

class TestUI
{
	public static void main(String[] args) 
    {
		JFrame myWindow = new JFrame("Test UI");
		myWindow.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		myWindow.setSize(400,300);
		
		UIBuilder uib = new UIBuilder();
        myWindow.getContentPane().add(uib,BorderLayout.CENTER);

		myWindow.pack();
        myWindow.setVisible(true);
    }
}



```

```
C:\JPR\Lab18\GUI>java TestUI
Exception in thread "main" java.lang.IllegalArgumentException: adding a window to a container
        at java.awt.Container.checkNotAWindow(Unknown Source)
        at java.awt.Container.addImpl(Unknown Source)
        at java.awt.Container.add(Unknown Source)
        at UIBuilder.<init>(UIBuilder.java:27)
        at TestUI.main(TestUI.java:12)
```

Mike

---

### Post by mikemcleanuk on 2009-05-02
well i discovered where my major flaw was JFrame instead of JPanel but i am still not much closer than before :(

---

### Post by drubin on 2009-05-02
[PHP]JFrame jf = new JFrame();
		jf.add(TopPanel, BorderLayout.NORTH);
		jf.add(CenPanel, BorderLayout.CENTER);
		jf.add(BotPanel, BorderLayout.SOUTH);

		TopPanel.add(testButton1);
		CenPanel.add(testArea1);
		BotPanel.add(testButton2);
		add(jf);// <<<<< THIS one
[/PHP]

This line above seems to be causing the issue.  You can't add a window to a container. as in this line add refers to the JPanels method. So you are adding a JFrame to a JPanel(a container).

---

### Post by mikemcleanuk on 2009-05-02
> **drubin said:**
> [PHP]JFrame jf = new JFrame();
		jf.add(TopPanel, BorderLayout.NORTH);
		jf.add(CenPanel, BorderLayout.CENTER);
		jf.add(BotPanel, BorderLayout.SOUTH);

		TopPanel.add(testButton1);
		CenPanel.add(testArea1);
		BotPanel.add(testButton2);
		add(jf);// <<<<< THIS one
[/PHP]

This line above seems to be causing the issue.  You can't add a window to a container. as in this line add refers to the JPanels method. So you are adding a JFrame to a JPanel(a container).

thanks ive spotted that and changed the relevant code so its working with jpanels not jframes and the code compiles but doesnt display anything close to how i imagine it

---

### Post by PaulM1985 on 2009-05-02
What you may want to do in UIBuilder, is add all the components to your JPanels, ie:

```

	TopPanel.add(testButton1);
	CenPanel.add(testArea1);
	BotPanel.add(testButton2);

```

Then add the panels to your UIBuilder, which itself is a type of JPanel due to inheritance:

```

	add(TopPanel, BorderLayout.NORTH);
	add(CenPanel, BorderLayout.CENTER);
	add(BotPanel, BorderLayout.SOUTH);

```

So now all the components are on your panels, and each panel has now been added to your IUBuilder (the larger panel).

In TestUI, I think you can just use myWindow.add(uib);  and I don't know if the myWindow.pack() is needed.

I hope this helps.

Paul

PS: So your UIBuilder constructor would look something like this:

```

public UIBuilder()
	{

		// setting a BorderLayout
	this.setLayout(new BorderLayout());

		// adding buttons to panels
	TopPanel.add(testButton1);
	CenPanel.add(testArea1);
	BotPanel.add(testButton2);

		// adding panels to your UIBuilder object
	add(TopPanel, BorderLayout.NORTH);
	add(CenPanel, BorderLayout.CENTER);
	add(BotPanel, BorderLayout.SOUTH);

	}

```

---

