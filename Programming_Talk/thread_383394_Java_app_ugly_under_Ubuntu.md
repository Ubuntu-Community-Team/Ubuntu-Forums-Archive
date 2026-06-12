---
title: "Java app ugly under Ubuntu"
date: 2007-03-13
forum: Programming Talk
---

### Post by Ariod on 2007-03-13
Hey guys,

I'm playing with Swing components in Java. I noticed that my Java application (that is using system L&F according to [Sun's tutorials]("http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html")) doesn't look quite like other Java applications that I have installed (it's somewhat... ugly). For comparison, I've attached a screenshot comparing my Java app and Azureus.

Why is that so?

This is the code that I used for setting L&F:

```

		try {
			UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
		}
		catch (UnsupportedLookAndFeelException e) {
			
		}
		catch (ClassNotFoundException e) {
		
		}
		catch (InstantiationException e) {
			
		}
		catch (IllegalAccessException e) {
			
		}

```

---

### Post by rjfioravanti on 2007-03-13
Why do you think its ugly compared to the other one... you only have 2 menu items

So the only things I can compare is File and Help, and the only difference between yours and the other is that they have hotkeys for F and H, maybe if you put those in it will look the same

---

### Post by thesmartace on 2007-03-13
Azureus uses the [swt](http://www.eclipse.org/swt/) for its widgets whereas your one appears to just use the normal swing widgets. Swing, as far as I know, doesn't like gnome very much.

---

### Post by rjfioravanti on 2007-03-13
what are the pros and cons of using swt over swing?

I mean on all OS's, not just linux

---

### Post by trippinnik on 2007-03-13
Do you have jdk6?  this one makes apps look native in gnome.

---

### Post by Ramses de Norre on 2007-03-13
Install jdk6 and add this to your ~/.bashrc: ```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```

---

### Post by Rizado on 2007-03-13
> **Ramses de Norre said:**
> Install jdk6 and add this to your ~/.bashrc: ```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```HOWEVER!, GTKLaf is quite slow and buggy still. Alot better than the old ones but still not good enough. Also not all applications will like GTKlaf and might not work, that's why making it the default isn't too good.

---

### Post by Ariod on 2007-03-13
Thanks for the replies everyone, yes, I was using JDK 5.0. So in order to get the right looks, I'll have to update to 6.0 or switch to SWT.

---

