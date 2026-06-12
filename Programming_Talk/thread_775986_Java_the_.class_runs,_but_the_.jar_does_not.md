---
title: "Java: the .class runs, but the .jar does not"
date: 2008-04-30
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2008-04-30
Okay, I have a tangled JDK because of my AMD-'buntu.

1. Using NetBeans... I create a hierarchy which creates the package.unit line at the start of each source file:
```
fuelcost.db
fuelcost.gui
fuelcost.images
```

Works fine in NetBeans (and I copied the /images directory over into the build). My program will run from NetBeans IDE.

2. I Clean and Build Final which makes a /dist directory and inside is the .jar file. The .jar will not run. I get:
```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at fuelcosts.gui.BaseTable.<init>(BaseTable.java:35)
        at fuelcosts.gui.PanelEuro.<init>(PanelEuro.java:18)
        at fuelcosts.gui.DisplayCards.makeEuro(DisplayCards.java:97)
        at fuelcosts.gui.DisplayCards.<init>(DisplayCards.java:51)
```

3. From the Terminal, I can CD into the /build directory, but only to the /classes folder.
```
java fuelcosts.gui.Frame1 // instead of java Frame1
```
At first, this technique produced terrible GUI -- lack of Java's fonts. I remembered I installed the IcedTea JDK to get the 64-bit Firefox browser plug-in. Sure enough, the IcedTea jdk/lib has no /fonts. I changed the update-alternatives --config java back to sun-jdk-1.6.4. But I still have no run from.jar capabilities. The Manifest file inside the .jar:

```
Manifest-Version: 1.0
Ant-Version: Apache Ant 1.7.0
Created-By: 10.0-b19 (Sun Microsystems Inc.)
Main-Class: fuelcosts.gui.Frame1
[COLOR="Red"]Class-Path:[/COLOR] 
X-COMMENT: Main-Class will be added automatically by build
```

==========
Do I need classpath? Do I need to manually configure .jar? It is very tough to make code work and then the final .jar isn't trustworthy. What can I change on my Ubuntu so I get ./ for a classpath?

---

### Post by Zugzwang on 2008-05-01
That's the third time this problem occurs in a more or less similar form.  Note that in order to read images from a program located in a .jar file, you have to:
[LIST]
[*]Include the images in the .jar file itself - That's the intended to use of the .jar files. They are meant to contain all static data of your application. That's also the reason why ./ isn't in the classpath (on no platform). There's no need to if you use .jar files correctly.
[*]Load your image using **Class.getResource()**
[/LIST]

Note that the exception occurs in your own code, so we can only guess what went wrong. My guess would be that you try to read some data/image and throw away the Exceptions which leads to an NullPointerException later. See also [http://ubuntuforums.org/showthread.php?t=669277]("http://ubuntuforums.org/showthread.php?t=669277").

---

### Post by Unterseeboot_234 on 2008-05-02
I've done a bit of research since posting this question. NetBeans conception of valid application code -- that isn't monolithic -- means utilizing a Library to wrap classes. Which means I have to resharpen my pencil and go back to the drawing board. For this posted problem I was having, I do have my graphics in the same folder as .class. I have learned a .jar executes much faster than the IDE does. The .jar version considers I/O to the hard drive slow. Putting the call to an ImageObserver or a synchronized thread helps a little bit.

I have been advised on other forums to edit my shell bash, which I hate doing.

this hack almost works...

1. unpack the .jar
2. in the FOLDER called META-INF, edit your manifest.mf file by hand
and put in this folder.
3. add this hacked folder containing the file. It will replace the existing manifest.mf file with your recent one

```
<jar file="client.jar" update="true">
			<manifest>
				<attribute name="Class-Path" value="
					commons-logging.jar
					saaj.jar
					"/>
				<attribute name="Main-Class" value="com.sun.Test"/>
				<section name="Mapping Info">
					<attribute name="Built-By" value="${user.name}"/>
				</section>
			</manifest>
		</jar>
```

---

