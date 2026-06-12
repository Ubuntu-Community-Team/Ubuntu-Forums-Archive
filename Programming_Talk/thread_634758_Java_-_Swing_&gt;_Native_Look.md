---
title: "Java - Swing &gt; Native Look?"
date: 2007-12-08
forum: Programming Talk
---

### Post by chris062689 on 2007-12-08
I just recently installed NetBeans and am learning Java.
I made a few Swing tutorials, but there in Swing's default API.

I hear there is a way for it to use the GTK rendering system (Or atleast LOOK like the GTK rendering system, to make it look more native)

Is this possible?

---

### Post by zadig on 2007-12-08
I'm not an expert either but I guess this is what you are looking for
[http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/index.html](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/index.html)

java.sun.com is The documentation for Java.

---

### Post by Elegorod on 2007-12-08
It's possible, and simple.
```

public static void main(String[] args)
{ try
  { UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
  }
  catch(Exception e) {}
  JFrame frame = new MyApplication();
  ...
}

```

---

### Post by NoBugs! on 2009-06-22
Works great, thanks!
Do you know if there's a way for Java apps to also use the native open/save dialogs?

---

### Post by Habbit on 2009-06-22
> **NoBugs! said:**
> Works great, thanks!
Do you know if there's a way for Java apps to also use the native open/save dialogs?

No, Swing simulates GTK+ open/save dialogs just as it simulates the Windows open/save dialogs. However, you can use GTK itself in Java: [GTK+ language bindings]("http://www.gtk.org/language-bindings.html") which points you to [java-gnome]("http://java-gnome.sourceforge.net/"). This may or may not be optimal, depending on whether you want your application to try to look native in other platforms as well: GTK is available (and has themes) for Windows too, but here I consider Swing superior. Besides, Swing comes with the JRE, while with GTK you'd have to ship the libraries with your application.

---

