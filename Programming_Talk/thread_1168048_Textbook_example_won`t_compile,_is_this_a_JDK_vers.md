---
title: "Textbook example won`t compile, is this a JDK version problem?"
date: 2009-05-23
forum: Programming Talk
---

### Post by Rumtscho on 2009-05-23
I have to (re-)learn Java. I got Horstmann`s Core Java book, the 8. edition, which is based on Java 1.6. Installed JDK 1.6, set the classpath, and ran the simplest examples. Installed Eclipse using Synaptic, which installed version 3.2.2. 
Then I tried running a Swing example. Downloaded the source from the book author`s site, but it won't compile. 

```
2. ERROR in SizedFrameTest.java (at line 39)
	setLocationByPlatform(true);
	^^^^^^^^^^^^^^^^^^^^^
The method setLocationByPlatform(boolean) is undefined for the type SizedFrame
```

Looked into my Java version and found out that Eclipse has installed the 1.5 SDK and set it as default. Changed that, now it shows 
```
rumi@LinuxPC:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
```
But Eclipse still says it is using 1.5. 
 
In order to forego Eclipse, I downloaded the code into another directory and tried to compile from the terminal window. Received the same error, although I seem to be using the correct JDK version?! 

First question. Now I'd like to uninstall Eclipse and all JDK versions from my machine and manually install the newest JDK and the newest Eclipse. Trouble is, how do I remove all installed JDKs? In Synaptic, I found the 1.6, but not the 1.5. 


And second, will that solve my problem? The API documentation says setLocationByPlatform was introduced in 1.5, so it should have worked with either JDK version. 

Here the code of the example I used. Without the "setLocationByPlatform(true);" line, the programm compiles and runs. 

```


import java.awt.*;

import javax.swing.*;

/**
 * @version 1.32 2007-04-14
 * @author Cay Horstmann
 */
public class SizedFrameTest
{
   public static void main(String[] args)
   {
      EventQueue.invokeLater(new Runnable()
         {
            public void run()
            {
               SizedFrame frame = new SizedFrame();
               frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
               frame.setVisible(true);
            }
         });
   }
}

class SizedFrame extends JFrame
{
   public SizedFrame()
   {
      // get screen dimensions

      Toolkit kit = Toolkit.getDefaultToolkit();
      Dimension screenSize = kit.getScreenSize();
      int screenHeight = screenSize.height;
      int screenWidth = screenSize.width;

      // set frame width, height and let platform pick screen location

      setSize(screenWidth / 2, screenHeight / 2);
      setLocationByPlatform(true);

      // set frame icon and title

      Image img = kit.getImage("icon.gif");
      setIconImage(img);
      setTitle("SizedFrame");
   }
}

```

---

### Post by welshboy on 2009-05-23
In Eclipse when you create a new project, I think you can set which JRE to use.

I think you need to select Use Specific JRE.

You may also need to either install the newest JRE or search for it.

What happens when you run the program from the terminal window using the javac command?

You'll need to get to where the file is stored, and type javac classname

if it compiles, you should get an object file, if not it'll return a bunch of errors.

Then if you want to run it, you type in java className 

And see if it runs

I compiled your program and ran it with the command line stuff and it seemed to work fine.

Let me know how you get on :)

---

### Post by Rumtscho on 2009-05-23
Welshboy helped me solve a part of the problem. When I set the JRE in Eclipse to 1.6, I can compile and run the code from Eclipse. So it is a JRE version problem, as assumed. 

But I have to set that for each project separately. Eclipse always offers 1.5 as the standard JRE on my system, and when try to compile from command line as welshboy suggested, I get the error posted above. 

I want to remove Eclipse and all the JREs from my system and make a clean install of JRE 1.6 and Eclipse 3.4. I don't have much experience with Ubuntu, so I don't know how to find out the name of the JRE 1.5 installation used in Synaptic. Can you please help me with that?

---

### Post by bubuzzz on 2009-05-23
if you have ubuntu 9.04 on your computer, open Aministrator>Synaptic Package Manager, click search button and type jdk. Press Enter and find all the jdk 1.5 package, right click and choose "mark for removal" and then install jdk 1.6 packages (see my screenshot for more details)

Open Terminal, type 

```
sudo update-alternatives --config java
```

and choose java 1.6 

Eclipse 3.4 will automatically detect JRE when you execute it (in my case)

---

### Post by Rumtscho on 2009-05-24
I'm still running 8.10, saw no point in upgrading when the old version works fine. 

When search for jdk in Synaptic, I see sun-java5-jdk in the list, but it isn`t installed. Eclipse (still 3.2.2) says my workspace default JRE is called java-1.5.0-gcj-4.3-1.5.0.0, but Synaptic does not contain a package with that name. It shows results when I search for gcj, and some are installed on my system, but as I don`t know what they are, I`m afraid to uninstall them. 

I have chosen 1.6 as alternative, but the javac command seems to still be linked to the wrong jdk. Here is what happens: 

```
rumi@LinuxPC:~$ sudo update-alternatives --config java
[sudo] password for rumi: 

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 
rumi@LinuxPC:~$ java -version 
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
rumi@LinuxPC:~$ cd CoreJavaNoEclipse/v1ch07/SizedFrameTest
rumi@LinuxPC:~/CoreJavaNoEclipse/v1ch07/SizedFrameTest$ javac SizedFrameTest.java
----------
1. WARNING in SizedFrameTest.java (at line 25)
	class SizedFrame extends JFrame
	      ^^^^^^^^^^
The serializable class SizedFrame does not declare a static final serialVersionUID field of type long
----------
2. ERROR in SizedFrameTest.java (at line 39)
	setLocationByPlatform(true);
	^^^^^^^^^^^^^^^^^^^^^
The method setLocationByPlatform(boolean) is undefined for the type SizedFrame
----------
2 problems (1 error, 1 warning)rumi@LinuxPC:~/CoreJavaNoEclipse/v1ch07/SizedFramrumi@LinuxPC:~/CoreJavaNoEclipse/v1ch07/SizedFrameTest$ 

```

---

### Post by Ragazzo on 2009-05-24
I believe you're using GCJ as the compiler. The source code should compile fine in 1.5 too so try writing "javac -version" to see what the compiler version is.

---

### Post by Kimm on 2009-05-24
> **bubuzzz said:**
> if you have ubuntu 9.04 on your computer, open Aministrator>Synaptic Package Manager, click search button and type jdk. Press Enter and find all the jdk 1.5 package, right click and choose "mark for removal" and then install jdk 1.6 packages (see my screenshot for more details)

Open Terminal, type 

```
sudo update-alternatives --config java
```

and choose java 1.6 

Eclipse 3.4 will automatically detect JRE when you execute it (in my case)

I know this is off topic, but where did you get that theme??

---

### Post by Rumtscho on 2009-05-24
```
rumi@LinuxPC:~/CoreJavaNoEclipse/v1ch07/SizedFrameTest$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
```

Is there a way to set my javac command to use the normal sun java 1.6 compiler and Eclipse to use its own?

---

### Post by bubuzzz on 2009-05-24
to Rumtscho: your source code works fine on my computer. You can see from the screenshot that my jdk is the same like yours in the previous reply. Don't know why your jdk changes back to eclipse jdk? Did you set something else? 

To Kimm: mod-SlicknesS them with mod-Hydroxygen icon from gnome-look.org

---

