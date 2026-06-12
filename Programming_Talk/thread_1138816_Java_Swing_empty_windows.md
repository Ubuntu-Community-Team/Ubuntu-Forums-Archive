---
title: "Java Swing empty windows"
date: 2009-04-26
forum: Programming Talk
---

### Post by sparks88 on 2009-04-26
Using Eclipse 3.2 and trying to write swing applications. When I try to run an application with a JFrame, it is drawn at the appropriate position and size, but has no contents.

I have tried adding AWT_TOOLKIT=”MToolkit” to my /etc/environment file.

I am using Sun Java 6 on Ubuntu 9.04.

---

### Post by MrStill on 2009-04-26
can you provide code?

---

### Post by jespdj on 2009-04-26
Are you sure that Sun Java 6 is the version of Java that's set as the default on your system? Maybe you are inadvertently using GNU Java. Try:
```
java -version
```
What does it return?

Try:
```
sudo update-java-alternatives -s java-6-sun
```
to make sure that Sun Java 6 is the default version of Java that's used on your system.

---

### Post by sparks88 on 2009-04-26
I've tried a number of different approaches, all yielding basically nothing. The following example actually shows up with content, but I can't close the window, and the okay button doesn't respond to hover or click.

```
public class JFrameTester {
  public static void main(String[] args) {
	  JOptionPane.showMessageDialog(new JFrame(), "Hello World!");
  }
}
```

```
$java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)

```

```
$sudo update-java-alternatives -s java-6-sun
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-1.9-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
Using '/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide 'HtmlConverter'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
Using '/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide 'java-rmi.cgi'.
Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.
Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.
Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.
Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.
Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.
Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.
Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.
Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.
Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.
Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.
Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-1.9-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
```

---

### Post by Zugzwang on 2009-04-27
You did try to run your program from the terminal, right? It should work then.

Eclipse has its own settings with regards to the JVM used. Find it and change it to one by Sun.

---

### Post by sparks88 on 2009-05-02
You were correct Zugzwang. I needed to change the setting in Eclipse too.

For some strange reason its in: Window > Preferences > Java > Installed JREs. From there all I did was change it from gcj to sun. 

Unfortunately I'm getting error messages about java not being able to find FontStructs. [This]("http://ubuntuforums.org/showthread.php?t=523604") user had the same issue, unfortunately changing the AWT toolkit variable doesn't make the error messages go away. Nor does changing my dekstop effects to none. At least now its just a nuisance, swing seems to work fine other than the warnings.

---

