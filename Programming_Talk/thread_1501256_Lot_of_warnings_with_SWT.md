---
title: "Lot of warnings with SWT"
date: 2010-06-04
forum: Programming Talk
---

### Post by lviggiani on 2010-06-04
Hi everybody,
I recently made a fresh installation of Lucid 64bit and eclipse.
I'm doing an Java / SWT based program which was running flawless on Karmic and it's now giving a lot of warning with Lucid.

Here is a simple code:

```
public class Main {
	public static void main(String[] args) {
		Display.setAppName("testswt");
		Display display = new Display();
		Shell shell = new Shell(display);
		shell.setText("test");
		
		
		Menu menuBar = new Menu(shell, SWT.BAR);
		
		shell.open();
		
		while (!shell.isDisposed()) {
	    	if (!display.readAndDispatch())
	    		display.sleep();
	    }
		display.dispose();
	}
}
```

and here are the warnings that I get when I try running it:

```
(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 75497513

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 75497513

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 75497513

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 75497513

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 4294967296

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 12884901888

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 75497513

(testswt:4678): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkproperty-x11.c:325 invalid X atom: 8589934592
```

But if I comment out the row... ```
Menu menuBar = new Menu(shell, SWT.BAR);
``` ...no warnings are displayed. So it seems to be related to menubar creation. In any case the program then runs without any further problem, however those warnings are really annoying.
I've already tried adding the environ variable "GDK_NATIVE_WINDOWS=true" to the run configuration but nothing changes.
Can someone help me please??
Thanks, Luca.

---

### Post by kahumba on 2010-06-04
A few side notes:
1) SWT is pretty much deprecated, the industry is gravitating towards Swing.
2) Eclipse is a dead bet, it shows no signs of serious progress in the recent years, buggy and non-smart as usually.
3) SWT is buggier than Swing so get used to artifacts.
Hence if you opt for using SWT you're asking for problems yourself.

---

### Post by lviggiani on 2010-06-04
> **kahumba said:**
> A few side notes:
1) SWT is pretty much deprecated, the industry is gravitating towards Swing.
2) Eclipse is a dead bet, it shows no signs of serious progress in the recent years, buggy and non-smart as usually.
3) SWT is buggier than Swing so get used to artifacts.
Hence if you opt for using SWT you're asking for problems yourself.

Thanks for your post but it doesn't really help... :( I'm using Eclipse as it does what I need and I use SWT as they provide better OS integration as they wraps native controls....

---

### Post by Reiger on 2010-06-04
Actually you get “better” visual integration from using Swing with the GTK look and feel than you get from SWT on Gnome, or in case you use KDE you get better visual integration from the plain Ocean look and feel.

---

### Post by kahumba on 2010-06-04
I don't know, but if I were you I'd also ask this question on the SWT forum, there must be some forum dedicated to SWT..
Also, try your app in different environments/OSes, might give you some clues whether it's a Java binding issue or a GTK issue and based on that ask in the corresponding forum (or report as a bug...).

---

### Post by lviggiani on 2010-06-05
@kahumba, Reiger:
Thank you both guys. The reason I'm using SWT is because I'm creating an app that must run cross platform (Linux, OSX, Win) and embed a web browser and I need the browser window javascript to be connected (call and be called) by the java app embedding it. Everything is already set up and work  flawless (with the exception of those warnings on Lucid) on the three os. So I cannot U turn now.
However I'll keep your suggestions into consideration for future projects.
Thanks, Luca.

---

### Post by lviggiani on 2010-06-07
Found what to blame:
Nothing to do with SWT actually. It's the global-menu panel applet.
Filed a bug here:
[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=610](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=610)

---

### Post by tonysonney on 2011-01-27
> **lviggiani said:**
> Found what to blame:
Nothing to do with SWT actually. It's the global-menu panel applet.
Filed a bug here:
[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=610](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=610)

Thank you lviggiani for the bug link. I went through the bug and it says it is fixed. But I cant see what the fix is. I have the same problem in ubuntu 10.10.

Thanks in advance,
Tony

---

