---
title: "help on java-gnome setup"
date: 2006-10-16
forum: Programming Talk
---

### Post by rakis on 2006-10-16
Hi all, I was just wondering if:
1) Anybody has java-gnome setup and working on their box
2) is running java-gnome using sun's java

I know this isn't the standard practice, and I'm not sure if it will even work... I'm just hoping it will so I won't have to hop between jvms. 

I have managed to get everything installed correctly and am importing the glade/gtk libraries fine in eclipse.  

however I'm receiving errors when running a simple test program:

java code (.glade file has 2 buttons inside a window, very simple):

> 
import java.io.FileNotFoundException;
import java.io.IOException;

import org.gnu.glade.GladeXMLException;
import org.gnu.glade.LibGlade;
import org.gnu.gtk.Gtk;

public class MainGUI {
	
	LibGlade glade;
	public MainGUI() throws GladeXMLException, FileNotFoundException, IOException{
		glade = new LibGlade("glade/gui.glade",this);		
	}
	
	public static void main(String[] args) {
		MainGUI maingui;
		Gtk.init(args);
		try{
			maingui=new MainGUI();
		}
		catch(Exception e){
			e.printStackTrace();
		}
		Gtk.main();
	}
}


Error I'm getting:

> 
Exception in thread "main" java.lang.UnsatisfiedLinkError: no gtkjni-2.8 in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:992)
	at org.gnu.gtk.Gtk.<clinit>(Gtk.java:214)
	at project.MainGUI.main(MainGUI.java:23)


I then tried to run one of the tests on the java-gnome website and I get:


> Arrakis:/usr/share/doc/libgnome-java/examples$ ./runExample.sh testgnome/TestGNOME
Java-Gnome Example Application Launcher

Package gtk2-java was not found in the pkg-config search path.
Perhaps you should add the directory containing 'gtk2-java.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk2-java' found
Arrakis:/usr/share/doc/libgnome-java/examples$



Of course this was all done after running:
sudo aptitude install libgtk-java libgnome-java libglade-java libgconf-java

Apparently when you are running programs in eclipse, you must also add a library path to access the static libraries that the jar's above require.  Check this site:

[http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/EclipseDevelopment](http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/EclipseDevelopment)

---

### Post by nereid on 2006-10-16
Why don't you use SWING with the GTK look and feel?

---

### Post by rakis on 2006-10-16
Eventually, I need to have this program run natively.  Aside from having to learn GTK, I was opting to use a language I already knew extensively.  

Any ideas from people that have gotten java-gnome setup/working it would be a great help if you could post how you did it!! Thanks!!

---

### Post by kathe on 2007-04-29
hello

open this link thn u find the gnome java applications


[http://linuxera.com/content/view/182/2/](http://linuxera.com/content/view/182/2/)


kathe :)

---

### Post by Swege on 2007-05-17
Hey rakis,

How did you add that library path? The link is broken, since the java-gnome pages no longer have stuff about Eclipse on there.

---

### Post by yatt on 2007-05-17
> **rakis said:**
> -snip OP-

I've spent a good half hour trying to figure out the gtkjni-2.8 thing. I ended up getting nowhere. Maybe your link will help somewhat.
> **nereid said:**
> Why don't you use SWING with the GTK look and feel?
That's what I am doing, but you can still tell it is Swing.

---

