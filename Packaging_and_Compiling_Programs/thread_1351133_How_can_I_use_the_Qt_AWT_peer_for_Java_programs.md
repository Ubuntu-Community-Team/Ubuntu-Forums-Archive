---
title: "How can I use the Qt AWT peer for Java programs?"
date: 2009-12-10
forum: Packaging and Compiling Programs
---

### Post by miklcct on 2009-12-10
I want to use gcj to compile my Java applications and I've installed both classpath and classpath-qtpeer but whatever I do the application starts with GTK interface which I don't want. When I set the property awt.toolkit to gnu.java.awt.peer.qt.QtToolkit a ClassNotFoundException is thrown saying the program cannot find gnu.java.awt.peer.qt.QtToolkit but I've checked the zip files in classpath-common that the class file actually exists. I've already set the environment CLASSPATH to /usr/share/classpath.

michael@ubuntu:~$ cat Hello.java
// Hello.java (Java SE 5)
import java.awt.BorderLayout;
import javax.swing.*;

public class Hello extends JFrame {
    public Hello() {
        super("hello");
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        add(new JLabel("Hello, world!"));
        pack();
    }

    public static void main(String[] args) {
        new Hello().setVisible(true);
    }
}
michael@ubuntu:~$ CLASSPATH=/usr/share/classpath gcj --main=Hello Hello.java -o Hello -Dawt.toolkit=gnu.java.awt.peer.qt.QtToolkit
Hello.java:5: warning: The serializable class Hello does not declare a static final serialVersionUID field of type long
        public class Hello extends JFrame {
                     ^^^^^
1 problem (1 warning)
michael@ubuntu:~$ ./Hello
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.qt.QtToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.10)
   at java.awt.Window.<init>(libgcj.so.10)
   at java.awt.Frame.<init>(libgcj.so.10)
   at javax.swing.JFrame.<init>(libgcj.so.10)
   at Hello.<init>(Hello)
   at Hello.main(Hello)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.qt.QtToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...6 more
michael@ubuntu:~$ unzip -t /usr/share/classpath/glibj.zip gnu/java/awt/peer/qt/QtToolkit.class
Archive:  /usr/share/classpath/glibj.zip
    testing: gnu/java/awt/peer/qt/QtToolkit.class   OK
No errors detected in /usr/share/classpath/glibj.zip for the 1 file tested.
michael@ubuntu:~$

---

