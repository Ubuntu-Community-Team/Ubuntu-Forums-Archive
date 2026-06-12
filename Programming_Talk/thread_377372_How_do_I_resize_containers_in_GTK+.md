---
title: "How do I resize containers in GTK+?"
date: 2007-03-06
forum: Programming Talk
---

### Post by CrazyTn on 2007-03-06
Hi, I am having trouble trying to resize anything in GTK.

Object -> Widget -> Container -> Bin -> Frame

If I have a frame, how would I set its size?

---

### Post by lnostdal on 2007-03-06
the GtkFrame widget is resized by the widget which contains it .. if you think about it, this makes very much sense

if you want to add more widgets to a window (a window is a container that can only contain one sub-widget; a subclass of GtkBin) you should use a container-widget: [http://developer.gnome.org/doc/API/2.0/gtk/LayoutContainers.html](http://developer.gnome.org/doc/API/2.0/gtk/LayoutContainers.html)

edit:
experimenting with glade might give you some insight .. the GTK tutorial also talks about containers

---

### Post by CrazyTn on 2007-03-06
thx, I am trying not to mess with Glade right now so I can see what is going on exactly

---

### Post by lnostdal on 2007-03-06
well, what i meant with glade is for you to experiment with it by adding widgets to a window (edit: or more correctly; to a container-widget in a window then add widgets to that when you want to add more widgets than just one) then try resizing the window and see what happens

then you can create the gui using GTK+ (without glade) afterwards when you understand how the widgets react and relate to each other

---

### Post by CrazyTn on 2007-03-06
> **lnostdal said:**
> well, what i meant with glade is for you to experiment with it by adding widgets to a window (edit: or more correctly; to a container-widget in a window then add widgets to that when you want to add more widgets than just one) then try resizing the window and see what happens

then you can create the gui using GTK+ (without glade) afterwards when you understand how the widgets react and relate to each other

Yea, I was just messing with glade, now I know which attribute to mess with. Thx or the tip.

---

### Post by CrazyTn on 2007-03-06
I stubble across gtkmm website, and read its features. They seem pretty nice.

GTK seems to be messy and requiring you to type a lot of prefix

is gtkmm good and worth the switch?

---

### Post by lnostdal on 2007-03-06
gtkmm is C++ bindings to GTK+ (which is written in C) .. gtkmm is in no way less "messy" than GTK+ as you will need to understand the _exact_ same concepts to be able to use and understand gtkmm

yes, you will save some typing because C++ has namespaces, but the mess you're seeing is most likely a lack of understanding of how GTK+ and GUI-programming works in general so you'll end up struggling whether you use GTK+, gtkmm or PyGTK .. for instance the question you had originally in this thread of how to get widgets to resize is in no way solved by switching to gtkmm! you'll need to use and manipulate the exact same containers, widgets and properties to do this

i am no fan of C++(#1) and i consistently avoid it and use and recommend instead C for parts that require computer-performance, combined with another more high-level language when i require more abstraction and programmer-performance

if you want an increase in productivity and more abstraction i'd consider PyGTK(#2) .. edit: but again; you will still need to understand the _exact_ same concepts as when using GTK+ to use and understand PyGTK or gtkmm


#1: it has serious flaws in its promise of ability to abstract, leading, in the end - to more problems for a user wanting to work at a level above C

#2: not really worth mentioning yet as they are still very incomplete, but i'm working on some Lisp-bindings for GTK+ here: [http://nostdal.org/~lars/programming/lisp/swgtk/swgtk.html](http://nostdal.org/~lars/programming/lisp/swgtk/swgtk.html) .. a major update will be up in a couple of days :}

---

### Post by CrazyTn on 2007-03-06
aight I will  stick to GTK for now, to learn the basics of GUI programming.

I am not sure if I should use the DrawArea to show the Tetris game.

Seems to me like it would be easier to just put a butch of buttons onto a fixed container, and move them around.

Would it be better to use the DrawArea?

---

### Post by lnostdal on 2007-03-06
i wouldn't use button-widgets for this .. that would probably not look very nice :)

..and instead of using GtkFixed i'd use GtkTable -- that way things would look good even when the user resizes the game-window

..but i'd probably go for either Cairo (best) or the drawing-functions in GDK and not use GtkTable or GtkFixed at all

edit: see [http://nostdal.org/~lars/programming/c/cairo.c](http://nostdal.org/~lars/programming/c/cairo.c) for an example of gtk+ and cairo combined

---

### Post by CrazyTn on 2007-03-06
I don't know what Cairo is, but will look into it.

Doing this in GDK is so weird/new to me, I am used to object programming.

I am thinking of making a class call TShapes: which will hold all the properties all the shapes in Tetris.

Will prob. have something like draw(GdkDrawable * drawable, gint x , gint y)

All I got so far.

Is there a way to make a line into an object?
 gdk_draw_line 

Really confuse about GdkGc too 
I don't know what this line is doing.
widget->style->fg_gc[GTK_WIDGET_STATE (widget)] 

```
gboolean
expose_event_callback (GtkWidget *widget, GdkEventExpose *event, gpointer data)
{
  gdk_draw_arc (widget->window,
                widget->style->fg_gc[GTK_WIDGET_STATE (widget)],
                TRUE,
                0, 0, widget->allocation.width, widget->allocation.height,
                0, 64 * 360);
 
  return TRUE;
}
```

---

### Post by CrazyTn on 2007-03-07
Nm I know how GdkGC works

---

### Post by CrazyTn on 2007-03-07
hey lnostdal  could you help me install Cairo?

It's like a loop.

In order to use Cairo I need to get GTK 2.8+, I have download GTK 2.10.9

When I try to install GTK

```
 Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

Requested 'glib-2.0 >= 2.12.0' but version of GLib is 2.7.7

```

I installed glib 2.7.7 in order to install atk, but atk didn't like that either.  It says that 

```
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

Linux makes everything so hard lol. or I am just a noob.
Kinda tempted to go learn C#, but already started this gona stick to it.

---

### Post by lnostdal on 2007-03-07
what do you mean you have downloaded GTK to get cairo? .. why did you not just do:

```
sudo aptitude libcairo2-dev
```

..to get cairo? you're making stuff harder then they have to be

---

### Post by lnostdal on 2007-03-07
i mean .. you know that the software is named cairo, right .. so you can do:

```

sudo aptitude search cairo

```

...then you get numerous hits .. and you want the cairo "libraries for development" .. thus: "libcairo2-dev"

edit:
further, i talk about pkg-config in pt.3 in the guides in my signature .. after installing libcairo, you can use pkg-config just as with libgtk:

```

lars@ibmr52:~$ pkg-config --list-all | grep cairo
pangocairo            Pango Cairo - Cairo rendering support for Pango
cairo                 cairo - Multi-platform 2D graphics library
mono-cairo            Mono.Cairo - Cairo bindings for Mono
cairo-xlib            cairo-xlib - Xlib backend for cairo graphics library
cairo-png             cairo-png - PNG backend for cairo graphics library
cairo-pdf             cairo-pdf - PDF backend for cairo graphics library
cairo-svg             cairo-svg - SVG backend for cairo graphics library
cairo-ps              cairo-ps - PostScript backend for cairo graphics library
cairomm-1.0           cairomm - C++ wrapper for cairo
cairo-xlib-xrender    cairo-xlib_xrender - Xlib Xrender backend for cairo graphics library
cairo-ft              cairo-ft - FreeType font backend for cairo graphics library

lars@ibmr52:~$ pkg-config --cflags cairo
-I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12  

lars@ibmr52:~$ pkg-config --libs cairo
-lcairo  

```

---

### Post by ZDemon on 2007-03-07
Hi there CrazyTN

I had no problems compiling cairo.c, here is my makefile :
```

main: cairo.c
	gcc -o cairo cairo.c -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0`
```

Save the file above as a file called "Makefile". Then just type "make" to compile. I did not have to use apt-get to download cairo. Im using edgy. Seems like you don't have to include libcairo. It works fine.

I hope that helps.

Bump.

By the way Inotsdal, can i ask a quick question? Am i right by saying, if i use the cairo functions, i can draw on ANY GtkDraw widget? This is because im using Glade, i want to avoid writing everything from scratch. The cairo functions look great.

---

### Post by lnostdal on 2007-03-07
> **ZDemon said:**
> By the way Inotsdal, can i ask a quick question? Am i right by saying, if i use the cairo functions, i can draw on ANY GtkDraw widget? This is because im using Glade, i want to avoid writing everything from scratch. The cairo functions look great.

yup, you can draw on any GtkDrawable-widget .. even if it is loaded using libglade .. :)

edit:
the cairo & gtk+ example ZDemon is talking about below was mentioned in another thread i think .. here it is: [http://nostdal.org/~lars/programming/c/cairo.c](http://nostdal.org/~lars/programming/c/cairo.c)

i've added a comment at the top that shows how to compile it from the terminal using pkg-config .. and also how to compile it using scons .. and yes - it really is simple; isn't linux great? :)

---

### Post by ZDemon on 2007-03-07
Wow.

The code is clean and just awesome. I cant believe it is so simple. Ive been meddling around Devhelp and the net for WEEKS on how to draw on that pesky widget. Im gonna use cairo to draw my graphs. That should satisfy those pampered lecturers. 

Thanks Inostdal. Your work has helped me a lot, in just a span of a few days. You are my guru.

Once again, it is an excellent example. The source code speaks for itself, no tutorial was needed. :)

---

### Post by CrazyTn on 2007-03-07
Thx, Now I have to go back and reinstall everything from the guide.
My old GTK program won't compile anymore after I started install all this junk.
I started a Java GUI program also, but can't seem to compile it.

Will mess around with Java GUI first so I get a better understanding of GUI in general since I am more comfortable with Java atm.

```
javac JTShapes.java JTetris.java 
JTetris.java:15: cannot find symbol
symbol  : constructor JTShapes()
location: class JTetris.JTShapes
                JTShapes s = new JTShapes();
                             ^
Note: JTetris.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
1 error

```

```
package JTetris;
//import JTetris.JTShapes;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.geom.*;
import javax.swing.*;

public class JTetris extends JPanel{
	public void  paintComponent(Graphics g){
		super.paintComponent(g);
		Graphics2D g2d = (Graphics2D)g;
		JTShapes s = new JTShapes();
		g2d.fill(s);	
	}

public static void main(String[] args){
		//set up the Window
		JFrame frame = new JFrame();
		frame.setTitle("Java Tetris");
		frame.setSize(400, 675);
		frame.addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent e){
				System.exit(0);	
			}
		});

		Container contentPane = frame.getContentPane();
		contentPane.setLayout(new BorderLayout());		

		//Buttons
		btnPanel = new JPanel(new GridLayout(3,1));	
		newGameBtn = new JButton("New Game");
		pauseBtn =   new JButton("Pause");
		quitBtn =    new JButton("Quit");
		btnPanel.add(newGameBtn);
		btnPanel.add(pauseBtn);
		btnPanel.add(quitBtn);

		contentPane.add(btnPanel, BorderLayout.WEST);
		contentPane.add(new JTetris(), BorderLayout.CENTER);

		frame.show();
	}
//Private variables
	static private JPanel btnPanel;
	static private JPanel rPanel;
	static private JButton newGameBtn;
	static private JButton pauseBtn;
	static private JButton quitBtn;



	/*//note: JTetris is the frame since it is extending JFrame
	public JTetris(){
		//get the frame and set the layout manager	
		Container window = getContentPane();
		window.setLayout(new BorderLayout());

		//The Panel that holds the other widgets 
		panel = new JPanel(new BorderLayout());

		//add panel to the window
		window.add(panel, BorderLayout.CENTER);


	}*/

}


```

```
package JTetris;
import java.awt.*;
import java.awt.geom.*;
import javax.swing.*;


public class JTShapes extends Rectangle2D.Double{
	//constructor
	public JTShapes(int shape){
		super(10, 20, 100, 100);
	}

   private Rectangle2D.Double rect;		

}

```

---

### Post by lnostdal on 2007-03-07
you're doing ```
new JTShapes()
``` .. but you only have a constructor for the JTShapes-class  that accept an int

edit: you can try removing junk from /usr/local/* .. i think most stuff is put there by default when you do `make install'

---

### Post by CrazyTn on 2007-03-07
I am just horrible at this.
Now getting this when I run scons

Getting a big headache.
```
scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o main.o -c -Wall -g -std=c99 -I/usr/local/include/cairo -I/usr/local/include -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/libglade-2.0 -I/usr/include/libxml2 main.cpp
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: 'GInitiallyUnowned' does not name a type
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: 'GInitiallyUnownedClass' does not name a type
scons: *** [main.o] Error 1
scons: building terminated because of errors.

```

---

### Post by CrazyTn on 2007-03-07
> **lnostdal said:**
> you're doing ```
new JTShapes()
``` .. but you only have a constructor for the JTShapes-class  that accept an int

edit: you can try removing junk from /usr/local/* .. i think most stuff is put there by default when you do `make install'

Hahahah I am an idiot always miss lil details like that.

and just delete stuff from the local directory? eg. rm

---

### Post by lnostdal on 2007-03-07
hm .. be careful :}  .. you can use rm -r to delete whole directory trees .. there might be some directories in /usr/local you'd like to keep though

also see rm --help  ... and man 1 rm

---

### Post by CrazyTn on 2007-03-07
problem solved after clearing out my local dir.

THx

---

