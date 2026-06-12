---
title: "Eclipse and Sun's Java"
date: 2006-09-24
forum: Programming Talk
---

### Post by HalNineThousand on 2006-09-24
I tried, when I first installed Dapper, to install Eclipse through apt-get.  I ran into problems with Java.  I need to use Sun's "official" Java, though I'd prefer to stay with 1.4.2 because I have to keep an eye on compatibility and I need Swing.  When I installed Eclipse, it installed gij and insisted on using an open source version of Java.

I love open source, but, for the reasons I mentioned, I have to stick with Sun's Java and it seems like no matter what I do, including usurping the current Java by deleting the files in /usr/bin and replacing them with Sun's Java files, Eclipse insists on using a non-Sun Java.

Right now I'm using Eclipse 3.2 that I installed from the standard Eclipse install.  I'm having problems with things that just don't work right, such as text being reformatted without me reformatting it and when I tell it to reformat, it won't do it according to my prefs.

I'd like to use Eclipse installed through apt-get.  Is there any way to easily deal with installing Eclipse and having it use Java 1.4.2?

Thanks!

---

### Post by Perfect Storm on 2006-09-24
```
sudo update-alternatives --config java
```

change it to:

3        /usr/lib/j2sdk1.5-sun/bin/java

---

### Post by hearnden on 2006-09-26
I don't know if Sun's 1.4.x JRE/SDK is in the repositories (version 5 is, but that's not what you want 1.4.2).  But if you manually install Sun's 1.4.2, then you can:

1. Install it in a way similar to the other Java installs:
1.1  Install in /usr/lib/jvm/java-1.4.2-minorversion
1.2  Symlink /usr/lib/jvm/java-1.4.2-sun to the dir from 1.1
1.3  Add /usr/lib/jvm/.java-1.4.2-sun.jinfo
     I'm not sure whether or not you can generate this file or not.  Check 
     out update-java-alternatives, that may tell you more.

2. Tell Eclipse to use your specific JVM
2.1  Use the Eclipse installation from the repositories (I think you've already done this)
2.2  Add /usr/lib/jvm-1.4.2-sun at the top of the list in /etc/eclipse/java_home

3. (Optional)  Tell everything else in your system to use your JVM.
Look at update-java-alternatives (man update-java-alternatives).

---

### Post by sarhento_lobo on 2006-09-26
> **HalNineThousand said:**
> I'd like to use Eclipse installed through apt-get.  Is there any way to easily deal with installing Eclipse and having it use Java 1.4.2?

Thanks!

By this do you mean:

1. Use a specific Java VM in development? This means that your project will use a specific Java VM. If so, you can configure this by adding a Java runtime library for Eclipse to use. Right-click on your project > Properties > Java Build Path > Add Library > JRE System Library, then point to the location of your Sun JDK. You will have to remove any preconfigured Java runtimes in the Libraries tab.

2. Run Eclipse using a speicific Java VM? If so, you'll need to execute the command for Eclipse with the "vm" option; i.e., /usr/bin/eclipse -vm /usr/lib/[path to JDK]. The easiest way to do this is to just edit the launcher properties.

---

### Post by hearnden on 2006-09-26
> **sarhento_lobo said:**
> By this do you mean:

2. Run Eclipse using a speicific Java VM? If so, you'll need to execute the command for Eclipse with the "vm" option; i.e., /usr/bin/eclipse -vm /usr/lib/[path to JDK]. The easiest way to do this is to just edit the launcher properties.

The eclipse setup that is installed through apt-get comes with a shell script to launch eclipse, and that shell script launches Eclipse using the first existing JVM found in /etc/eclipse/java_home.  It's a bit more organised than having your own script to add in the -vm switch.

---

### Post by sarhento_lobo on 2006-09-27
Right. You can generate an eclipserc file in ~/.eclipse and fill that with the JAVA_HOME variable pointing to your vm. That's just as easy as editing the launcher properties :)

---

