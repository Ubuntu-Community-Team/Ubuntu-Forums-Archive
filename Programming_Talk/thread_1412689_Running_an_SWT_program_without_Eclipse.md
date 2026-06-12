---
title: "Running an SWT program without Eclipse"
date: 2010-02-21
forum: Programming Talk
---

### Post by coverslide on 2010-02-21
Hi folks, I can't seem to figure out a simple Hello World swt program. I can't do it through eclipse because I access my dev machine through a shell. I compiled it successfully with javac (i am using openjdk) like this:

```

javac HelloSWT.java -cp swt.jar

```

swt.jar I copied from /usr/lib/java/swt-gtk-3.5.jar to the same directory after installing the libswt-gtk-3.5-java package. I put HelloSWT.class and swt.jar in the same directory on my test machine, and also installed the packages  libswt-gtk-3.5-java and  libswt-gtk-3.5-jni.
Trying to run it I get this:

```

richard@rhmint ~/p/java/HelloSWT $ java HelloSWT
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Display
    at HelloSWT.main(HelloSWT.java:8)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Display
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 1 more

```

I've added "-cp swt.jar", and "-Djava.library.path=." and different combinations of both. I'm not sure what else I need to do to get it work.

I don't think it's relevant, but the source code to the hello world program is here:

```

import org.eclipse.swt.widgets.Display;
import org.eclipse.swt.widgets.Shell;

public class HelloSWT
{
  public static void main(String[] args)
  {
    Display display = new Display();
    Shell shell = new Shell(display);
    shell.setText("Hello World!");
    shell.open();
    while(!shell.isDisposed())
    {   
      if(!shell.isDisposed())
      {   
        display.sleep();
      }   
    }   
    display.dispose();
  }
}

```

---

### Post by falconindy on 2010-02-21
Arf, misread the OP... You could always just unpack the jar.

---

