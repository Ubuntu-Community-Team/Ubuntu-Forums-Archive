---
title: "JFrame does not work (Ubuntu 12.04)"
date: 2012-09-20
forum: Programming Talk
---

### Post by jamesallen4u on 2012-09-20
Hello,

I am running Ubuntu 12.04 with JDK 7 installed. My IDE is Geany. I am trying to run a simple JFrame window, nothing too complex. Here is my code for that:

```
// JFirstFrame.java

import javax.swing    .*;
import java.awt       .*;
import java.awt.event .*;

public class JFirstFrame extends JFrame
{
	public JFirstFrame()
	{
		int Row,Col;

		Toolkit MyKit = Toolkit.getDefaultToolkit ();

		Dimension XY  = MyKit.getScreenSize       ();

		Row           = XY.width ;
		Col           = XY.height;

		setSize    (3*Row/4,3*Col/4                );
		setLocation(Row/8  ,Col/8                  );

		Image MyImage = MyKit.getImage("square.gif"); // set your icon
		setIconImage(MyImage                       );
		setTitle("This is my first Frame!!!"       );

		MyPanel PanelA          = new MyPanel     ();
		Container ContentPanelA = getContentPane  ();

		ContentPanelA.add(PanelA                   );

				
	}

	private class MyPanel extends JPanel
	{
		public void paint(Graphics Draw)
		{
			int Row, Col, Ax, Ay, Bx, By;

			Dimension RowCol;

			RowCol = getSize();

			Row = RowCol.width ;
			Col = RowCol.height;

			Draw.setColor(Color.green);

			Draw.drawLine(     0 ,Col/2,Row,Col/2);
			Draw.drawLine(Row/2,0,Row/2,    Col  );
		}
	}
}


// JFrameCaller.java
import javax.swing.*;

public class JFrameCaller
{
	public static void main(String MeUp[])
	{
		JFirstFrame MyFrame = new JFirstFrame();

		MyFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		MyFrame.setVisible(true                              );
	}
}
```

When I try to run this program in Geany, I get the following errors:

```

// Errors in JFirstFrame.java

javac "JFirstFrame.java" (in directory: /home/jamesallen)
JFirstFrame.java:18: cannot find symbol
symbol  : method setSize(int,int)
location: class JFirstFrame
                setSize    (3*Row/4,3*Col/4                );
                ^
JFirstFrame.java:19: cannot find symbol
symbol  : method setLocation(int,int)
location: class JFirstFrame
                setLocation(Row/8  ,Col/8                  );
                ^
JFirstFrame.java:22: cannot find symbol
symbol  : method setIconImage(java.awt.Image)
location: class JFirstFrame
                setIconImage(MyImage                       );
                ^
JFirstFrame.java:23: cannot find symbol
symbol  : method setTitle(java.lang.String)
location: class JFirstFrame
                setTitle("This is my first Frame!!!"       );
                ^
JFirstFrame.java:26: cannot find symbol
symbol  : method getContentPane()
location: class JFirstFrame
                Container ContentPanelA = getContentPane  ();
                                          ^
5 errors
Compilation failed.


// Errors in JFrameCaller.java

javac "JFirstFrame.java" (in directory: /home/jamesallen)
JFirstFrame.java:18: cannot find symbol
symbol  : method setSize(int,int)
location: class JFirstFrame
                setSize    (3*Row/4,3*Col/4                );
                ^
JFirstFrame.java:19: cannot find symbol
symbol  : method setLocation(int,int)
location: class JFirstFrame
                setLocation(Row/8  ,Col/8                  );
                ^
JFirstFrame.java:22: cannot find symbol
symbol  : method setIconImage(java.awt.Image)
location: class JFirstFrame
                setIconImage(MyImage                       );
                ^
JFirstFrame.java:23: cannot find symbol
symbol  : method setTitle(java.lang.String)
location: class JFirstFrame
                setTitle("This is my first Frame!!!"       );
                ^
JFirstFrame.java:26: cannot find symbol
symbol  : method getContentPane()
location: class JFirstFrame
                Container ContentPanelA = getContentPane  ();
                                          ^
5 errors
Compilation failed.


```

I am stumped by these errors because the code is perfect. I can run applets just fine so I thought frames could also be accomplished. I even tried a complete re-install of java, and this problem still occurred. Please help me out guys. Thanks.

BTW I am new to this forum so sorry if I unknowingly violated any of your rules. :p

---

### Post by dwhitney67 on 2012-09-20
Your code compiles and runs fine using Java 1.6.0_26.  I'm sure it is fine with Java 1.7 too.

Why not try to build/run your project without the IDE?  Open a terminal and compile your .java files manually, and then run them.  Ad while your at it, verify the Java that your system has.

```

$ java -version

$ javac JFrameCaller.java JFirstFrame.java

$ java -cp . JFrameCaller

```

---

### Post by jamesallen4u on 2012-09-20
Hi dwhitney67,

Thanks for your reply. I tried the exact commands that you put in your post and I still got the same errors. Here are the screenshots of the terminal.

[IMG]http://i.imgur.com/tqpUE.png[/IMG]

[IMG]http://i.imgur.com/S7Oo7.png[/IMG]

---

### Post by spjackson on 2012-09-21
I can't replicate those errors with Java7 either using OpenJDK or Oracle's Java unless.... I have a file in the same directory like this:
```

$ cat JFrame.java 

class JFrame {
}

```With that, I get exactly the same errors as you do. Do you have a different implementation of JFrame either in the same directory or in your classpath?

---

### Post by jamesallen4u on 2012-09-21
> **spjackson said:**
> I can't replicate those errors with Java7 either using OpenJDK or Oracle's Java unless.... I have a file in the same directory like this:
```

$ cat JFrame.java 

class JFrame {
}

```With that, I get exactly the same errors as you do. Do you have a different implementation of JFrame either in the same directory or in your classpath?
What do you mean by different implementation? Sorry, I am a noob with JFrames so I don't know what you are talking about.

---

### Post by spjackson on 2012-09-21
> **jamesallen4u said:**
> What do you mean by different implementation? Sorry, I am a noob with JFrames so I don't know what you are talking about.
What I meant was something like I showed you - a file that defines the class JFrame that gets picked up in preference to the proper javax/swing/JFrame.class.

If you use the -verbose compiler flag, it should show you where it is finding JFrame.
```
javac -verbose JFirstFrame.java JFrameCaller.java
```When this succeeds, I get lots of output but importantly:
```

loading ZipFileIndexFileObject[/usr/lib/jvm/java-7-openjdk-amd64/lib/ct.sym(META-INF/sym/rt.jar/javax/swing/JFrame.class)]]

```However, if I put that empty class definition of JFrame that I showed you in the same directory as the java source that I am compiling, then the compilation fails and amongst the output I don't get the above line, but get instead
```

[loading RegularFileObject[./JFrame.java]]
[parsing started RegularFileObject[./JFrame.java]]

```

---

