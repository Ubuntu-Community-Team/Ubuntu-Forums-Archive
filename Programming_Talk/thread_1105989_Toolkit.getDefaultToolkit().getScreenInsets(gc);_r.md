---
title: "Toolkit.getDefaultToolkit().getScreenInsets(gc); returns 0,0,0,0 on ubuntu8"
date: 2009-03-25
forum: Programming Talk
---

### Post by singhkanhaiya on 2009-03-25
My aim is to capture the screen except taskbar and panel (Which have Applications, Places, System, they are defult from ubuntu 8.04) of ubuntu 8.04 system. Below code is giving correct insects on window os but giving 0,0,0,0 on ubutu 8.04. Can any one help in this regard?



import javax.swing.*;
import java.awt.*;
 
public class Test {
	
	public static void main(String args[])
	{
		int resoltuion = Toolkit.getDefaultToolkit().getScreenResolution();
		
		//System.out.println("Resolution::" + resoltuion);
		
		Dimension dim = Toolkit.getDefaultToolkit().getScreenSize();
		
		//System.out.println("Dimension::" + dim);
		
		GraphicsConfiguration gc = new Frame().getGraphicsConfiguration();
		
		Insets insects = Toolkit.getDefaultToolkit().getScreenInsets(gc);
		
		System.out.println("insects:::"+insects);
		
	}
 
}

---

### Post by Zugzwang on 2009-03-25
Read here:

[http://java.sun.com/javase/6/docs/api/java/awt/GraphicsConfiguration.html](http://java.sun.com/javase/6/docs/api/java/awt/GraphicsConfiguration.html)

See the comments on the X11 windowing system.

---

### Post by singhkanhaiya on 2009-03-26
Thanks for quick reply.

I read that link. I used the code whatever suggested in that. But I could not able to find the location, height of GNOPE panel present on ubuntu desktop. Can you please help in that regrard.

Thanks

---

### Post by Zugzwang on 2009-03-26
> **singhkanhaiya said:**
> I read that link. I used the code whatever suggested in that. But I could not able to find the location, height of GNOPE panel present on ubuntu desktop. Can you please help in that regrard.


I might be wrong but it seems as if you are unable to do that using Java as this function is not supported due to the underlying architecture in Java. How should Java know what the task bar is? The answer depends on the window manager. Even "native" applications are sometimes unable to take the location of the task bar into account (and thus restore their position incorrectly at the next start of the respective program as it seems that at least under QT, when using the "move" functions of a window, the task-bar position is added whereas "pos" returns the absolute position).

---

### Post by singhkanhaiya on 2009-03-30
The above suggested methods are well working on Windows OS but not working on Ubuntu system. Can you suggest any other way to find the location and height of Gnome Panel.

Thanks

---

### Post by Zugzwang on 2009-03-30
> **singhkanhaiya said:**
> The above suggested methods are well working on Windows OS but not working on Ubuntu system. Can you suggest any other way to find the location and height of Gnome Panel.

Thanks

Yes, but not in Java. Write a program that gets the process id of the "gnome-panel" process. Then use XLib to get the size of its window. However, that won't work under KDE, as there, there is no gnome-panel.

To summarize it up: The operation you requested cannot be implemented in a truly portable way in Linux. Try to work around it.

---

### Post by singhkanhaiya on 2009-04-01
Can you please suggest how to write that?
Thanks ...

---

