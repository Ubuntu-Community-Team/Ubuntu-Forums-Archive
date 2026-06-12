---
title: "Release objects [Java-Gnome]"
date: 2011-03-27
forum: Programming Talk
---

### Post by edan3250 on 2011-03-27
I'm supposed to release objects in Java Gnome?

When I'm creating object, and calling to Gtk.mainQuit() it's free all the objects automatic?

I see the function destroy() should I use that?
I means... If I made a class that extends from Window and I create a Label field, should I free the Label and than the Window?

```
public class A extends Window
{
    Label text = new Label();

    ctor()
    {
        ...
    }

    free_function()
    {
        this.text.destroy();
        this.destroy();
    }
}
```

I need to do like this?
Sorry for my bad english... and thanks :)

---

### Post by Reiger on 2011-03-27
I've no experience with Java-gnome but you can avoid the order problem by using finalizers. They will be called by the garbage collector, so order of finalisation should become irrelevant. (EDIT: and you can check the java-gnome source to see if the Java API does this for you, already.)

```

public class A {
  @Override
  protected void finalize() throws Throwable {
    // release resources here.
  }
}

```

---

### Post by edan3250 on 2011-03-27
> **Reiger said:**
> I've no experience with Java-gnome but you can avoid the order problem by using finalizers. They will be called by the garbage collector, so order of finalisation should become irrelevant. (EDIT: and you can check the java-gnome source to see if the Java API does this for you, already.)

```

public class A {
  @Override
  protected void finalize() throws Throwable {
    // release resources here.
  }
}

```
thanks for respone...

i want release before the garbage collector called.
and one more question...
look on my exemple, if i using only "this.destroy()" the field of label still will be allocate?

where can i see the source code of "Gtk.mainQuit()" and "destroy()" functions?

---

### Post by Reiger on 2011-03-27
You can use "apt-get source" command to download sources for packages in the archive. Or you can visit the project website and download from there?

---

### Post by Simian Man on 2011-03-27
This may not be helpful but...why on *Earth *would you use Java with Gnome?  C# is a better language, and is much better supported by the Gnome platform.

---

### Post by edan3250 on 2011-03-28
ok i download the source code, but its not helpful.

the Object.java class at gtk folder i see that:
```
    /**
     * Ask everything connected to this object to release its references. Use
     * this in preference to Container's {@link Container#remove(Widget)
     * remove()} if you don't need the Widget any more.
     * 
     * <p>
     * <i>We didn't expose this for a long time in java-gnome; after all,
     * memory management of both Java references and GObject Ref counts is
     * handled automatically by the diabolical cunning of this most excellent
     * library. It turns out, however, that this does not <code>free()</code>
     * the GtkObject's memory; it really only does what it says: ask other
     * GtkObjects to drop whatever Refs they may be holding to this object.
     * Thus if this GtkWidget is in a GtkContainer and you call</i>
     * <code>destroy()</code> <i>the GtkContainer will drop its Refs to this
     * GtkWidget thereby breaking its parent-child relationship.</i>
     * 
     * <p>
     * <i>Note that Java's references remain, so the object will <b>not</b>,
     * in fact, be eligable for finalizing until you drop all your references;
     * ie, the Java side Proxy Object goes out of scope. Nevertheless calling
     * this will speed up release of resources associated with a Widget, so
     * it's a good idea. Once you've done so,</i> <code>finalize()</code>
     * <i>will be traversed a short time later and the GObject will be
     * released.</i>
     * 
     * @since 4.0.18
     */
    public void destroy() {
        GtkObject.destroy(this);
    }
```
but i don't see the class called "GtkObject".

and on Object.java at glib i see:
```
    /**
     * Drop our reference count to the underlying GObject.
     * 
     * <p>
     * <i>This should, incidentally, cause this GObject to be disposed by GLib
     * of if we're the only one still holding a reference count to it. On the
     * other hand, if our Proxy just happens to be going out of scope, and the
     * GtkWidget (say) is [still] packed into some GtkContainer, then it will
     * continue to exist quite happily.</i>
     */
    protected final void release() {
        if (Debug.MEMORY_MANAGEMENT) {
            System.err.println("Object.release()\t\t" + this.toString());
            System.err.flush();
        }
        GObject.removeToggleRef(this);
    }
```
but i don't see the "Debug" class =/

---

### Post by r-senior on 2011-03-28
The idea of Java-Gnome is to let you write Gnome applications using Java. You don't need to worry about releasing objects. Let the API deal with that. 

If you want more control over when objects are released, you should consider a language that isn't based around garbage collection and hiding of pointers. People who fight with Java's garbage collector rarely win. ;)

---

### Post by edan3250 on 2011-03-28
> **r-senior said:**
> The idea of Java-Gnome is to let you write Gnome applications using Java. You don't need to worry about releasing objects. Let the API deal with that. 

If you want more control over when objects are released, you should consider a language that isn't based around garbage collection and hiding of pointers. People who fight with Java's garbage collector rarely win. ;)
umm you right, but if they give me using function called like "destroy" or "release" i guess it's my job to use them...

see at stack overflow, i post there now the same problem with better example:
[http://stackoverflow.com/questions/5465713/how-to-release-objects-java-gnome](http://stackoverflow.com/questions/5465713/how-to-release-objects-java-gnome)

---

### Post by r-senior on 2011-03-29
Have you looked at the examples here?

[http://java-gnome.sourceforge.net/4.0/doc/examples/START.html](http://java-gnome.sourceforge.net/4.0/doc/examples/START.html)

No release or destroy.

The mailing list for Java-Gnome is very good. Have you asked the question there?

---

### Post by edan3250 on 2011-03-31
> **r-senior said:**
> Have you looked at the examples here?

[http://java-gnome.sourceforge.net/4.0/doc/examples/START.html](http://java-gnome.sourceforge.net/4.0/doc/examples/START.html)

No release or destroy.

The mailing list for Java-Gnome is very good. Have you asked the question there?
ok thanks :)
i will keep the api release my objects...

at this website:
[http://zetcode.com/tutorials/javagnometutorial/dialogs/](http://zetcode.com/tutorials/javagnometutorial/dialogs/)

i see an examples for using java-gnome and they using the function "hide()".

---

