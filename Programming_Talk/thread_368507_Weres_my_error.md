---
title: "Weres my error?"
date: 2007-02-23
forum: Programming Talk
---

### Post by stealth75711 on 2007-02-23
```
import javax.swing.JApplet;
import java.awt.*;

Public class Snowman extends JApplet
{



	public void paint (Graphics page)
	{

		final int MID = 150;
		final int TOP = 50;

		setBackground (Color.cyan);

		page.setColor (Color.blue);
		page.fillRect (0, 175, 300, 50);  //ground

		page.setColor (Color.yellow);
		page.fillOval (-40, -40, 80, 80);  //sun

		page.setColor (Color.white);
		page.fillOval (MID-20, TOP, 40, 40);  //head
		page.fillOval (MID-35, TOP+35, 70, 50); //upper torso
		page.fillOval (MID-50, TOP+80, 100, 60); //lower torso

		page.setColor (Color.black);
		page.fillOval (MID-10, TOP+10, 5, 5); //left eye
		page.fillOval (MID+5, TOP+10, 5, 5); //right eye

		page.drawArc (MID-10, TOP+20, 20, 10, 190, 160); //smile

		page.drawLine (MID-25, TOP+60, MID-50, TOP+40); //left arm
		page.drawLine (MID+25, TOP+60, MID+55, TOP+60); //right arm

		page.drawLine (MID-20, TOP+5, MID+20, TOP+5); //brim of hat
		page.fillRect (MID-15, TOP-20, 30, 25);  //top of hat

	}
    }
```

//Then i tried to compile it with the command line


stealth@stealth-desktop:~$ javac Snowman.java
Snowman.java:4: class, interface, or enum expected
Public class Snowman extends JApplet
^
1 error


//How i fix?

---

### Post by lnostdal on 2007-02-23
capital P in `Public'

---

### Post by stealth75711 on 2007-02-23
stealth@stealth-desktop:~$ javac Snowman.java
stealth@stealth-desktop:~$ java Snowman
Exception in thread "main" java.lang.NoSuchMethodError: main


//It compiled, but i still get an error?

---

### Post by lnostdal on 2007-02-23
you can't run applets from the console

or in other words; applications requires an entrypoint in form of a method named `main' .. and you have not provided a method `main'

i believe you can provide a `main' that sets up a container where you can "embed" your applet (ie; outside a browser) .. i haven't done java in a longlong time though, and i'm too lazy to look stuff up to provide an example -- anyone else?


edit:
or maybe there exists a tool that does this "automatically" -- i mean run applets outside the browser? edit2: `appletviewer' might work .. i do not remember

---

### Post by Engnome on 2007-02-23
appletviewer is good. It needs the argument of a html file though, can't run applets without those as html specifies the size.

Can't attach html so here goes:

```

<html>
<head>Test</head>
<body>
<APPLET CODE="your.class" WIDTH="400" HEIGHT="400">
</APPLET>
</BODY>
</HTML>

```

---

### Post by stealth75711 on 2007-02-23
So how do i put this html code in my program?

---

### Post by Tomosaur on 2007-02-23
You don't, you create a webpage and load it in a browser.

---

### Post by g3k0 on 2007-02-23
your error is in your thread title.  It should be "Where is"

---

### Post by Engnome on 2007-02-23
> **stealth75711 said:**
> So how do i put this html code in my program?

Put in a applet.html file and start it with
```
appletviewer applet.html
```

---

### Post by stealth75711 on 2007-02-23
It works!!

---

