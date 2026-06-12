---
title: "gui in java... bit of help"
date: 2007-10-18
forum: Programming Talk
---

### Post by Choad on 2007-10-18
following some tutorials for my uni course... they are written for J Developer but i am using eclipse because i like to be different.

anyway, all working fine so for for the cli stuff!

now i'm moving on to gui and it they are using a toolkit called "awt"

i have a class

public class MarksTestGui extends Frame {

and it doesnt know what Frame is, because i havent imported this stuff. i can't figure out how to import it either. to be honest, i dont think they will mind if i use a different toolkit...

so can someone give me the skinny on guis and java and ubuntu and eclipse! maybe a link to a nice tutorial or something?

---

### Post by LaRoza on 2007-10-18
> **Choad said:**
> 

so can someone give me the skinny on guis and java and ubuntu and eclipse! maybe a link to a nice tutorial or something?

See my wiki, Swing is easier to use by the way.

impor java.awt.*

[http://java.sun.com/javase/6/docs/api/java/awt/package-summary.html](http://java.sun.com/javase/6/docs/api/java/awt/package-summary.html)

---

### Post by jespdj on 2007-10-18
See Sun's [Java Tutorial](http://java.sun.com/docs/books/tutorial/). There is a trail on Swing there, which builds on top of AWT.

---

### Post by tenmillionmilesaway on 2007-10-18
If your gonna go with swing (which i recommend) then look at SwingSet2.  Its one of the demos that comes with the jdk, its a jar in the jdk demos folder, there is an online version here: java.sun.com/products/jfc/jws/SwingSet2.jnlp 

SwingSet2 shows all of the features available as standard for Java GUI programming and can give you a good idea what is available.

Now to answer your original question:

In eclipse ctrl-O is the organise imports command (its also available in one of the menus, source i think) this will import any classes that you haven't already imported for you.  All of the swing classes generally live in javax.swing. packages and awt ones live in java.awt. packages.  The Swing equivilent of an AWT component usually has the same name but with a J on the front eg AWT - Frame Swing - JFrame

The Frame is a top level component, like any other window, and you add things like panels, buttons etc into it.

On a side note the Netbeans IDE has a very good Graphical GUI designer (drag and drop building of GUI applications) but I doubt that you will get any marks for using it as it generates code for you, plus you wont learn as much as writing it yourself.

Richard

---

### Post by dismal_denizen on 2007-10-18
I also strongly recommend that you use NetBeans.  It makes making GUIs a breeze. I also recommend that you use Swing. It doesn't take up as much system resources as AWT.

---

### Post by Choad on 2007-10-20
thx for the replies guys. much apprieciated. i've gone with netbeans now with my new gutsy install. the autocomplete/hint was sooooo laggy in eclipse :(

i'll be bound to post more questions later :p:

---

