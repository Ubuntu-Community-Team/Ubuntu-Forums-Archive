---
title: "How to run Java in eclipse"
date: 2007-05-16
forum: Programming Talk
---

### Post by Ameliorate on 2007-05-16
I am just making a simple program to test Java on Ubuntu. 
this is the program:

package test;
import javax.swing.*;

public class PaneTester {
	public static void main(String args[])
	{
		JOptionPane.showMessageDialog(null, "Test", "this is a test",
				JOptionPane.INFORMATION_MESSAGE);
	}//end main method

}//end class PaneTester


However,
Every time I try to run a Java application in Eclipse (Ubuntu Feisty Fawn) I get this error:



Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.70)
   at javax.swing.JOptionPane.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at test.PaneTester.main(PaneTester.java:7)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...9 more




Any Help here?

---

### Post by wiebers10 on 2007-05-16
How did you install it?  What version of the JRE did you also install?  And In Eclipse if you go to Window - Prefrences then Java and installed JRE's what does it say there also?

---

### Post by Ameliorate on 2007-05-16
it says java-1.4.2-gcj-4.1-1.4.2.0

I just tried the same thing in emacs and it worked. I might just do that, but i really like IDE's as compared to text-based interfaces.

---

