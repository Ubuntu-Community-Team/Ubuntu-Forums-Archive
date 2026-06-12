---
title: "Getting a simple Swing Applet to display"
date: 2009-03-30
forum: Programming Talk
---

### Post by mike_g on 2009-03-30
I'm trying to make a simple applet using swing, but nothing gets displayed. Spent a while going through a load of useless stuff so now I'm bored and going to bed. Heres my code:
```
import java.applet.*;
import javax.swing.*;
import java.awt.*;

public class HelloWorld extends JApplet
{
	public void init()
	{
		Container content = getContentPane();
		content.add(new JLabel("Hello World"));
		content.setVisible(true);
		this.setVisible(true);
	}

	public void start(){}
	public void stop(){}
}
```
```
<html>
	<head>
		<title>Test</title>
	</head>

	<body>
		<applet code="HelloWorld.class" codebase="." align="baseline" width="600" height="600"></applet>
	</body>
</html>
```
Can someone tell me why nothing is being displayed? 

Cheers.

---

