---
title: "GCJ and libgnome-java"
date: 2006-11-25
forum: Programming Talk
---

### Post by bieber on 2006-11-25
So, I've been using Java for a while, and I'd like to move into GUI programming with it.  My plan is to use GCJ and libgnome-java to create native executables, my only problem is that I don't know how to use GCJ to compile Java applications (I've only used Sun's Java til now) and I don't know how to set it up with the appropriate libraries.  So, if someone doesn't mind answering such an awful noob question, say I take a simple hello world program like this
```

// First we import the libraries used by this example
import org.gnu.gnome.App;
import org.gnu.gnome.Program;
import org.gnu.gtk.Gtk;

public class First {

    public static void main(String[] args) {
        // Initialization
        Program.initGnomeUI("First", "0.1", args);

        App app = new App("First", "First App");
        app.show();

        Gtk.main();
    }
}

```
in a file called First.java.  What commands would I have to use to compile this, and then run the resulting program?

Thank you,
Robert Bieber

---

### Post by shining on 2006-11-26
Maybe you should try running it like with sun java first?
Just switch from sun java to gij/gcj with:
sudo update-java-alternatives java-gcj
(sudo update-java-alternatives -l gives you the available choices)

Then use java and javac like before. In your case, I believe you would need to put the path to gnome java bindings in the classpath (-cp option of java/javac), but I've 0 experience with this.

For compiling natively though, I found this page:
[http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/NativeBinaries](http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/NativeBinaries)

Hope it'll help.

---

### Post by bieber on 2006-11-26
I tried using the command on that native binary compiling page, with my library jars substituted in, and got these errors
```

bieber@bieber:~/projects/HelloWorld$ gcj -classpath /usr/share/java/gtk2.10.jar:/usr/share/java/gnome2.12.jar:usr/share/java/glib0.4.jar -lgtkjar2.10 -lgnomejar2.12  --main=First -o first First.java
First.java:0: error: cannot find file for class org.gnu.glib.Struct
First.java:0: error: cannot find file for class org.gnu.glib.GObject
org/gnu/gtk/GtkObject.java:0: error: cannot find file for class org.gnu.glib.GObject
org/gnu/gnome/Program.java:0: error: cannot find file for class org.gnu.glib.Struct
First.java: In class 'First':
First.java: In method 'First.main(java.lang.String[])':
First.java:10: error: cannot find file for class org.gnu.glib.Struct
First.java:12: error: cannot find file for class org.gnu.glib.Handle
First.java:13: error: cannot find file for class org.gnu.glib.GObject

```

It seems to not be including all the proper glib libraries, or some such thing.  Once that's taken care of, does anyone know of a way to have automake and autoconf find and substitute in the neccesary libraries automatically?  Hard-coding the build commands would seem to be a very bad practice if I eventually want to distribute something to someone who has the libraries in a different directory, or with different version numbers, or etc. etc...

---

### Post by shining on 2006-11-27
I don't know.
I would try to also put -lglibjar0.4 in the command, like the two others, but that's really just a wild guess based on nothing :)

---

