---
title: "Problem with JFrame in  Java"
date: 2006-07-09
forum: Programming Talk
---

### Post by Mikael Gustafsson on 2006-07-09
I have a problem when i try to compile this program below:
```
import javax.swing.*;
public class GameWindow {
	public static void main(String[] args) {
		JFrame mainWindow = new JFrame("test");
		mainWindow.setSize(300, 200);
		mainWindow.setVisible(true);
	}
}
```

I get this error from eclips 3.2 when i try to run it.

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at GameWindow.main(GameWindow.java:8)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...5 more

I have installed sun-java5-bin and Installed the j2re1.4 package. And i have run the command 
sudo update-alternatives --config java
and updated this so it is to sun-java5.
But still i have the problem with the JFrame program. I can run hello world program with out problems.

Can anyone help me? 

/Mikael Gustafsson

---

### Post by Max Luebbe on 2006-07-09
Yeah - Swing isn't supported by GCJ if I recall.

I forget how to change the JRE in an existing project, but to make sure you're using the sun implementation, start a new java project, under jdk compliance click configure default, and there should be a button to show installed jre's.

It sounds like you got eclipse from the repos which has gcj all over the place as a default.

Let me know if this takes care of it.

---

### Post by gmclachl on 2006-07-09
First of all if you don't have it downlod the Sun Java SDK.

 Open up elcipse and go 
 **Window > Preferences**

 Click on the arrow beside [B}Java[/B] and a sub menu will appear. 
 
 Select **Installed JREs** and then press the **Add...** button 

 Another window will open up, give your additional JRE a unique name and browse to the folder where sun-java is kept.

George

---

### Post by Mikael Gustafsson on 2006-07-10
Thanks for all the help!
Your good and straigth forward explaning was superb gmclachi!! Now i can begin with my programming. :D 

Once again Thanke you!! 

/Mikael Gustafsson

---

