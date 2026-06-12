---
title: "[SOLVED] Frostwire Problem!"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-06-26
Hello! I performed a fresh installation of Ubuntu, updated all my packages, etc etc... After that, I installed javajdk from Add/Remove and that was fine... Then I went to install Frostwire, and it sais it installed it correctly, but when I go to applications/internet and open "Frostwire" (By the way, the icon isn't the blue icon, it's a terminal icon) nothing happens! I don't know what to do! I have no clue how to "remove it", and it doesn't even work!!! Can someone please help me getting this thing to work!? Thanks so much:popcorn:
Johnathannn

---

### Post by WRDN on 2008-06-26
Type the application name in the terminal and post the output.
If the normal application name won't work, right click on the Applications/ Places/ System menu and select "Edit Menu". Then, find the application, right click on it and select Properties. The name will be listed at the end of the "Command" entry.

In the output, there will likely be an error if it wont open.

Its also worth trying to open the application with the "sudo" command to see if it makes a difference:

```
sudo [application_name]
```

---

### Post by robertchahine on 2008-06-26
usually frostwire doesn't work because you should configure java.

```

sudo update-alternatives --config java

```.
change it to the unused java version(jre java bin)

---

### Post by Johnathannn on 2008-06-26
I typed "FrostWire" in the terminal, and it just sais command not found lol... Hope that gave you some usefull info! :)
Johnathannn

---

### Post by Johnathannn on 2008-06-26
Robert, I typed in what you said, and I got this...
There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
What do I do now?
Johnathannn

---

### Post by Kreuger on 2008-06-26
You have to install **sun-java6-jre** and probably **sun-java6-bin** too. You should've used Synaptic to install it because it would've grabbed these for you. I would think the Add/Remove thing would too but apparently not.

---

### Post by WRDN on 2008-06-26
> **Johnathannn said:**
> I typed "FrostWire" in the terminal, and it just sais command not found lol... Hope that gave you some usefull info! :)
Johnathannn

So, the application that runs is not called FrostWire.

In that case find exactly what the application is called by:

- Right clicking on Applications
- Select Edit Menu's
- Select "Internet" from the Menus list
- Right click FrostWire and select Properties
- Type the word at the end of the "Command" line in the terminal

For example, if you right click "Chess" in the Games Menu and select Properties, the name of the application is "glchess", and if you type this in the terminal, the application will open properly.

---

### Post by Johnathannn on 2008-06-26
Thanks man, I just figured it out right before you posted lol... I typed in the command for frost wire (which is /usr/bin/frostwire) then I got /usr/bin/frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
:mad:Johnathannn

---

### Post by LuisGMarine on 2008-06-26
Hello,

I had this problem earlier.  First, fire up your Synaptic Package Manager.

[LIST]
[*]System > Admin > Synaptic Package Manager
[/LIST]

Then hit the "Search" button and type in each of these packages, and make sure that they are installed. In other words make sure they have a green box next to their names.  If not, download and install them.

[LIST]
[*]sun-java6-bin
[*]sun-java6-fonts
[*]sun-java6-jre
[*]sun-java6-plugin
[/LIST]


After that re-install Frostwire.  I just do that because I'm weird, but you can try to run Frostwire after all the necessary packages have been installed and see what happens.  If it doesn't work reinstall Frostwire and try again!

Hope this works!

-kill

---

### Post by Johnathannn on 2008-06-26
Thanks to all you guys, I learned some new stuff and you helped me a lot... Here's what I did... First I uninstalled JavaJDK (Because it mixed with Sun Java, and FrostWire gets cofused, therefore wont open)... Then I completely removed FrostWire (in the Synaptic Package Manager)...Then I installed Sun Java (the .bin files and everything in the Synaptic Package Manager)...Then I reinstalled FrostWire and VOILA! I got it to Work! One more thing though... The icon now is not the blue FrostWire icon, but its like a blank icon... How do I switch it to the blue FrostWire icon??? Thanks in advance and thanks again...
Johnathannn:):):):):)

---

