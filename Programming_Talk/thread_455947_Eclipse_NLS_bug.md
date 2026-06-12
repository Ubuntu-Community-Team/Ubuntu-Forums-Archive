---
title: "Eclipse NLS bug"
date: 2007-05-27
forum: Programming Talk
---

### Post by slamdunk on 2007-05-27
Hi,

running a simple JFACE/SWT application I get this bug in eclipse:

Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/osgi/util/NLS
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.core.runtime.Status.<clinit>(Status.java:30)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:117)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.jface.action.MenuManager.update(MenuManager.java:662)
	at org.eclipse.jface.action.MenuManager.update(MenuManager.java:581)
	at org.eclipse.jface.action.MenuManager.fill(MenuManager.java:235)
	at org.eclipse.jface.action.MenuManager.update(MenuManager.java:662)
	at org.eclipse.jface.action.MenuManager.update(MenuManager.java:581)
	at org.eclipse.jface.action.MenuManager.createMenuBar(MenuManager.java:158)
	at org.eclipse.jface.window.ApplicationWindow.createTrimWidgets(ApplicationWindow.java:348)
	at org.eclipse.jface.window.ApplicationWindow.configureShell(ApplicationWindow.java:336)
	at org.eclipse.jface.window.Window.createShell(Window.java:497)
	at org.eclipse.jface.window.Window.create(Window.java:425)
	at org.eclipse.jface.window.Window.open(Window.java:785)
	at myapp.ui.MainWindow.main(MainWindow.java:51)


jface/swt libraries are imported normally, and reading on eclipse-bug-list it seems fixed:

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=145504](https://bugs.eclipse.org/bugs/show_bug.cgi?id=145504)

is there maybe some bug in ubuntu version of eclipse/libs?

Thanks,
Alex

---

