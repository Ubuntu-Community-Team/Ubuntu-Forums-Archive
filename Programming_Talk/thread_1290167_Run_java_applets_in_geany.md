---
title: "Run java applets in geany"
date: 2009-10-13
forum: Programming Talk
---

### Post by Flimm on 2009-10-13
For the beginner Java programmer, [Geany](http://www.geany.org/) is a nice and easy text editor. Creating, compiling and running Java applications is supported out of the box. Java applets, however, aren't. Here's how to do make Geany run both .java applications and applets.

First, download the attached file. Open it and extract run-java to your home folder. Then open a terminal and type these commands:```
sudo mv run-java /usr/bin/
sudo chmod 755 /usr/bin/run-java
```

Open geany and open a .java file. Click the menu Build, then Set includes and arguments. Under Execute, enter:```
run-java "%e"
```

Now all you have to do is click Compile, then Execute to run any Java applications or applets that you write.

NOTE: in order to detect whether a .java file is an Applet or not, the script run-java searches for "extends Applet" or "extends java.applet.Applet" and "class" in the same line. It's not clever enough to handle unusual whitespace so be warned.

Here's the contents of run-java:
[php]#!/bin/bash -e
# Created by David D. Lowe 2009
# released into the public domain

# expects #1 to be the name of the file to be run without an extension
# example: MyClass
if [ "$1" == "" ]; then
    echo "Please pass the filename of a .java file without the extension"
    echo "example: run-java MyClass"
    exit 2
fi

# check to see if file has been compiled:
if [ -e "$1".class ]; then

    # check to see if .java is an Applet
    if [ `cat $1.java | grep 'extends \(java.applet.\)\?Applet' | grep class > /dev/null; echo $?` == "0" ]; then
        # it's an Applet
        
        if [ `cat $1.java | grep setSize > /dev/null; echo $?` == "1" ]; then
            echo "TIP: remember to use the setSize method"
        fi
        
        # creates a .html file in the current directory with the same
        # name as the .java file
        echo "<applet code=\"$1.class\" width=\"20\" height=\"60\"></applet>" > "$1".html

        appletviewer "$1".html
        
        # if you don't want the .html to be saved, uncomment the following line:
        # rm "$1".html
    else
        # it's not an Applet
        java "$1"
    fi
else
    echo "cannot find $1.class, please compile $1.java"
    exit 1
fi[/php]

---

### Post by somebody100 on 2009-11-18
hey,

thanks for your entry, but it isnt working for me!

If followed exactly your description but i still cant run any applets with geany.

Do you maybe have an idea why?

greetz

---

### Post by trsmash on 2010-01-28
Thank you very much for the info! It worked for me quite easily and I'm very new to Ubuntu so I was very surprised. Thanks again.

---

### Post by ronrick on 2010-04-30
works well!! thanks a ton!!

---

### Post by Zumbaichichi on 2010-10-28
Awesome! Works smooth! Just be sure that the yourfilename.html has the exact name as the yourfilename.java file. Case sensitive!

---

### Post by MatthewMeredith on 2011-10-04
This is digging up a pretty old thread, but I just used it to fix my Geany for running applets with a _slight_ modification:

```
    if [ `cat $1.java | grep 'extends \(java.applet.\)\?Applet'
```

I had to add a "J" to "Applet" to make it \?JApplet' since my class line has the keyword JApplet in it, and not Applet.

Hope this helps anyone who's having trouble with it!

---

### Post by orttez on 2012-01-06
Unfortunately it did not work for me the way jGrasp does.
After compiling the Terminal window keeps asking for the main method.

In order to solve that, I am creating a frame for my applets in Java to include the main method. Then I make a class for the applet.

Here is a program example that draws a green rectangle:
[PHP]
import java.awt.*;
import javax.swing.*;

public class SampleApplet 
{	
	public static void main(String[] args) 
	{
		JFrame applet = new JFrame("Title");
		
		applet.getContentPane().add(new Rectangle());
		
		applet.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		applet.setSize(400,400);
		
		applet.setVisible(true);
	}
}
class Rectangle extends JApplet
{
	public void paint(Graphics g)
	{
		int x = 60;
		int y = 20;
		int length = 130;
		int width = 200;
		
		g.setColor(Color.green);
		
		g.fillRect(x, y, length, width);
	}
}
[/PHP]

---

### Post by suman garg on 2012-06-07
not working for meee
followed all ur instructions exactly but while extracting the file to home folder is showing following notification
You don't have the right permissions to extract archives in the folder "file:///home"

---

