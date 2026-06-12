---
title: "Eclipse Console Error libjava..."
date: 2006-02-21
forum: Programming Talk
---

### Post by crazygerad on 2006-02-21
I am using Breezy, so far its stable with the java console thing updated to 1.5 or v5. I am trying to do an exercise in a book and it works well when I use java and javac but looking for an easier time I got Eclipse through Synaptic (I might add it's a very useful tool). 


So I am using two classes, I checked them for errors and they are exactly like in the book and whenever I try to run it gives me this error:

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...

I did google about it, and all I could find is that people either weren't able to reproduce it, unanswered question or that I should update gcc 4.0 to 4.1 that will have that problem fixed but i checked the repositories and it doesn't exist.

Any help would be greatly appreciated since I have to learn this to build a program for a class. Sorry that the code isn't well written here, it seems I can't make it keep the original tabs and stuff.

so what I am trying to run is this:

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class TwoButtons {

	/**
	 * @param args
	 */
	JFrame frame;
	JLabel label;
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		TwoButtons gui = new TwoButtons();
		gui.go();

	}
	public void go() {
		frame = new JFrame();
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JButton labelButton = new JButton("Change Label");
		labelButton.addActionListener(new LabelListener());
		
		JButton colorButton = new JButton("Change Circle");
		colorButton.addActionListener(new ColorListener());
		
		label = new JLabel ("I'm a label");
		MyDrawPanel drawPanel = new MyDrawPanel();
		
		frame.getContentPane().add(BorderLayout.SOUTH, colorButton);
		frame.getContentPane().add(BorderLayout.CENTER, drawPanel);
		frame.getContentPane().add(BorderLayout.EAST, labelButton);
		frame.getContentPane().add(BorderLayout.WEST, label);
		
		frame.setSize(300,300);
		frame.setVisible(true);
		
	}

	class LabelListener implements ActionListener {
		public void actionPerformed(ActionEvent event) {
			label.setText("Ouch!");
		}
	}
	class ColorListener implements ActionListener {
		public void actionPerformed(ActionEvent event) {
			frame.repaint();
		}
	}
}

Other file:

import java.awt.*;
import javax.swing.*;

public class MyDrawPanel extends JPanel {
	public void paintComponent(Graphics g) {
		g.fillRect(0,0, this.getWidth(), this.getHeight());
		
		int red = (int) (Math.random() * 255);
		int green = (int) (Math.random() * 255);
		int blue = (int) (Math.random() * 255);	
		
		Color randomColor = new Color(red, green, blue);
		g.setColor(randomColor);
		g.fillOval(70,70,100,100);
	}
}

---

### Post by hod139 on 2006-02-21
I would suggest not using the GNU version of the Java SDK/JRE, but to instead use Sun's version.
**Step 1**.  Install Sun's SDK version 1.5

Add the [plf repositories]("http://doc.ubuntu-fr.org/doc/plf") to /etc/apt/sources.list 
```

 ## http 100mbit/s mirror provided thanks to OVH http://ovh.com
 deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
 deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
 
``` 
 then
 ```

 sudo apt-get update
 
``` 
 Lastly
 ```

 sudo apt-get install sun-j2sdk1.5
 
``` 

**Step 2**. Making Sun's JRE the system default
```
sudo update-alternatives --config java 
``` and select Sun's JRE.
 Next, edit /etc/jvm by adding /usr/lib/j2sdk1.5-sun/jre to the top of the file

**Step 3**.  Tell eclipse to use compile and run code using Sun's version of Java
Start eclipse and go to the Window->Preferences dialogue. 
Select "Installed JREs" on the left. Add and select the j2sdk1.5-sun JRE.
[B]
Optional. [/B]Expand the "Java" branch of the tree on the left and click "Compiler", then flip "Compiler compliance level" to 5.0.

---

### Post by crazygerad on 2006-02-22
Thanks a lot :), I also downloaded and used the newest eclipse version and it didn't gave me the problem. I will try to see if the one still on the menu thing will work or not.

---

