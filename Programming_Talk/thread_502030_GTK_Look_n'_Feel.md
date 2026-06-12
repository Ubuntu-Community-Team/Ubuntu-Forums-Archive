---
title: "GTK Look n' Feel"
date: 2007-07-16
forum: Programming Talk
---

### Post by rem on 2007-07-16
Hello,

I was wondering if you guys might know of a good how-to regarding changing the default Java look n' feel. I'm working a lot with jEdit, which is a Java application and would like it more integrated with the Gnome desktop... Heard this is possible but couldn't find any accessible information for a non Java developer.

Thank you.

---

### Post by kknd on 2007-07-16
Yes, it is possible.

In the ~/java/lib dir, create / edit a file with name swing.proprierties:

Change the line:

swing.defaultlaf=com.sun.java.swing.plaf.CURRENTLOOKANDFEEL

to

swing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel

---

### Post by rem on 2007-07-16
I found a java folder inside the /usr/share directory, created the swing.properties files with the indicated line but it's not working ...

---

### Post by Occasionally Correct on 2007-07-16
You can set the look-and-feel programmatically using the [UIManager](http://java.sun.com/javase/6/docs/api/javax/swing/UIManager.html):

```
import javax.swing.UIManager;
...
try
{
	String laf = UIManager.getSystemLookAndFeelClassName();
	UIManager.setLookAndFeel(laf);
}
catch (Exception e) {}
...
```

You can find some more information about it (along with sample code) [here](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html#programmatic).

Hope that helps. :)

**Edit:** Oops, I thought you wanted to change the look-and-feel of your own applications. Sorry. :p

---

### Post by kknd on 2007-07-16
Some applications change the L&F programmatically, so its not possible to force one.

But, jEdit have a Look And Feel selector in its options. (When I used it, it had).

Other solution.:

Start the app with:

java --laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel -jar jedit.jar

or

java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel -jar jedit.jar

---

### Post by rem on 2007-07-16
The first command is giving me this error:

Unrecognized option: --laf
Could not create the Java virtual machine.

and the 2nd is starting jEdit but with the default look and feel.. no gtk :(

---

### Post by kknd on 2007-07-16
You can change the Look and Feel in jEdit, there is an **option** somewhere!

---

### Post by Eric Buist on 2012-03-24
Hi,

I am facing the exact same problem, but with the UIMA Document Analyzer tool which has no option to change the look and feel. It is very problematic, because each time I am searching for this, I find only posts describing how to change the look and feel programmatically. I tried the swing.properties editing, but it seems that the OpenJDK included with Ubuntu is lacking the GTK look and feel. If you call UIManager.getSystemLookAndFeelClass(), you will get the class name for the Metal LAF, not even the Nimbus one! I am now stuck with a growing wealth of unusable applications, including all Java/Swing ones. That is becoming a real show-stopper for me. Without a solution, I will be forced to give up on using a computer, or switch to a lower non-native resolution. This is very frustrating, I'm feeling I reached a dead end now.

---

