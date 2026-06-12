---
title: "How to install Cron-O-meter in Ubuntu"
date: 2008-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by carlostenorio on 2008-04-20
Cron-O-meter is a free java program that allow us to keep track of our diet and watch calorie consumption. It is a must have for calorie restriction practitioners.

To install it, you need to download the machintosh version of the program from [http://downloads.sourceforge.net/cronometer/CRONoMeter-0.9.3.zip]("http://downloads.sourceforge.net/cronometer/CRONoMeter-0.9.3.zip") and unzip it in a desired location.

then you need to write a little script. In a console write:

```
$gedit cron-o-meter.sh
```

Now copy and paste the next lines:

```
#!/bin/bash
cd /pathtothefolderwhereyouunzippedtheprogram/CRONoMeter.app/Contents/Resources/Java
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.0.jar:cronometer.jar:usda_sr20.jar:crdb_003.jar:docs.jar ca.spaz.cron.CRONOMETER

```

Just make sure to replace /pathtothefolderwhereyouunzippedtheprogram with the path you are using.

Now save it and close gedit. You need to make this script executable.
Write in a terminal:

```
$chmod +x cron-o-meter.sh
```

Finally, to run the program just type in a terminal

```
$sh cron-o-meter.sh
```

And that's it, now you can restrict your calorie intake:popcorn: and hopefully outlive your grandchildren!

---

### Post by ASL4U on 2008-07-06
frustrated -
I do not know to make this work.
I have downloaded it , I have done everything you have directed - 
but it will not work. nothing happens
I re-installed OpenJava...Ubuntu
I dont know how to use it - but it is there.
I dont know how to know if it is running...
I dont know how to make it run a file
I dont know where to put this program - so I have created a Programs directory in my Documents folder... so the program is there- but I dont know how to start it.

I go back and retry what you have suggested - and nothing happens.
the last message I got is: 

asl4u@Zip:~$ $chmod +x cron-o-meter.sh
bash: +x: command not found

asl4u@Zip:~$ $sh cron-o-meter.sh
bash: cron-o-meter.sh: command not found

what do I have to do to make it run? and what will it look like when it does? (so I know that I've succeded)...

Thank you

---

### Post by ASL4U on 2008-07-06
got it!
Thank you!
couldn't have done it without you... and thats a fact!

---

### Post by ergonomicdesign on 2008-08-09
Hey, thanks, this was actually...EXACTLY what I was trying to find. I'm trying to switch over from Windows to linux...and always hit snags...like installing a programming that's supposedly cross-platform. 

Anyway, thanks again!

---

### Post by snikeris on 2008-08-19
Has anyone figured out how to run Cronometer from the panel?

---

### Post by snikeris on 2008-08-25
I figured it out...you just need to make sure the cd command in your cronometer.sh is using the full path.  For example:

cd "/home/username/.cronometer/CRONoMeter.app/Contents/Resources/Java/"

I was using the cronometer.sh that came with the program.  If you follow the instructions here, this shouldn't be an issue.

---

### Post by freedomtolearn on 2008-11-11
I still can't seem to make this work.  This is the message I get now.  (I know it's a lot to get through, but maybe someone can see what I need to do next?)

~$ sh cronometer.sh
Nov 11, 2008 11:50:14 AM com.sun.corba.se.impl.orb.ORBImpl getLocalHostName
WARNING: "IOP00710208: (INTERNAL) Unable to determine local hostname from InetAddress.getLocalHost().getHostName()"
org.omg.CORBA.INTERNAL:   vmcid: SUN  minor code: 208  completed: No
	at com.sun.corba.se.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:3815)
	at com.sun.corba.se.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:3833)
	at com.sun.corba.se.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1593)
	at com.sun.corba.se.impl.orb.ORBImpl.set_parameters(ORBImpl.java:557)
	at org.omg.CORBA.ORB.init(ORB.java:354)
	at org.GNOME.Accessibility.AccessUtil.getORB(AccessUtil.java:222)
	at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
	at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1058)
	at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:341)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:874)
	at javax.swing.UIManager.getSystemLookAndFeelClassName(UIManager.java:617)
	at ca.spaz.cron.CRONOMETER.main(CRONOMETER.java:563)
Caused by: java.net.UnknownHostException: xcompx: xcompx
	at java.net.InetAddress.getLocalHost(InetAddress.java:1425)
	at com.sun.corba.se.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1591)
	... 16 more
org.omg.CORBA.INTERNAL:   vmcid: SUN  minor code: 208  completed: No
	at com.sun.corba.se.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:3815)
	at com.sun.corba.se.impl.logging.ORBUtilSystemException.getLocalHostFailed(ORBUtilSystemException.java:3833)
	at com.sun.corba.se.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1593)
	at com.sun.corba.se.impl.orb.ORBImpl.set_parameters(ORBImpl.java:557)
	at org.omg.CORBA.ORB.init(ORB.java:354)
	at org.GNOME.Accessibility.AccessUtil.getORB(AccessUtil.java:222)
	at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
	at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1058)
	at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:341)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:874)
	at javax.swing.UIManager.getSystemLookAndFeelClassName(UIManager.java:617)
	at ca.spaz.cron.CRONOMETER.main(CRONOMETER.java:563)
Caused by: java.net.UnknownHostException: xcompx: xcompx
	at java.net.InetAddress.getLocalHost(InetAddress.java:1425)
	at com.sun.corba.se.impl.orb.ORBImpl.getLocalHostName(ORBImpl.java:1591)
	... 16 more
Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/swingx/JXBusyLabel
	at ca.spaz.cron.CRONOMETER.main(CRONOMETER.java:579)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.swingx.JXBusyLabel
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 1 more

---

### Post by Pegasus22 on 2009-04-17
> **ASL4U said:**
> got it!
Thank you!
couldn't have done it without you... and thats a fact!

What did you "got it" ? share the secret!!!!! I am still with " $gedit cron-o-meter.sh
bash: cron-o-meter.sh: command not found"

C'MOOOONNNN, PLEASEEEE

---

### Post by carlostenorio on 2009-04-20
Since Version 9.4, the cronometer.sh script is working.
The script should be located inside the same folder you unzipped the program bundle. This can be easily done from the GUI, so no comments here.

Now, open a terminal and go inside the folder:
$cd /path-to-the-folder/
$ls
You should see a list like this one:
CRONoMeter.app  cronometer.sh  __MACOSX
You need to be able to execute the script, so:
$chmod +x cronometer.sh
Now to open the program
$sh cronometer.sh

That should do it. Next time, you just need to open a terminal and type
$cd /path-to-the-folder/
$sh cronometer.sh

Best wishes

---

### Post by carlostenorio on 2009-04-20
Pegasus22, you should not copy the $ symbol. I just use it to indicate that line is to be input in the terminal. ;)

---

### Post by ekpyrotic on 2009-04-21
Crashes.

```
jordan@jordan-laptop:~/Desktop/Cronometer$ sh cronometer.sh
Header Chunk. Image width:100 height:100 depth:8 color type:6 compression type:0 filter type:0 interlace:0
Initializing settings file /home/jordan/.cronometer/Settings.xml
Loading index...
Loading index...
Loading Deprecated index...
Loaded 37 foods.
Loading index...
Loading Deprecated index...
Loaded 8095 foods.
Loading: /home/jordan/.cronometer/Default User/servings.xml
  --> file does not exist
Loading: /home/jordan/.cronometer/Default User/notes.xml
  --> file does not exist
Loading: /home/jordan/.cronometer/Default User/metrics.xml
  --> file does not exist
Killed

```

---

### Post by h_ryan503 on 2009-06-21
> **ekpyrotic said:**
> Crashes.

```
jordan@jordan-laptop:~/Desktop/Cronometer$ sh cronometer.sh
Header Chunk. Image width:100 height:100 depth:8 color type:6 compression type:0 filter type:0 interlace:0
Initializing settings file /home/jordan/.cronometer/Settings.xml
Loading index...
Loading index...
Loading Deprecated index...
Loaded 37 foods.
Loading index...
Loading Deprecated index...
Loaded 8095 foods.
Loading: /home/jordan/.cronometer/Default User/servings.xml
  --> file does not exist
Loading: /home/jordan/.cronometer/Default User/notes.xml
  --> file does not exist
Loading: /home/jordan/.cronometer/Default User/metrics.xml
  --> file does not exist
Killed

```

I get the same output when I run it. Sometimes I makes it to the next stage and a window pops up but goes Grey and I have to force quit the application.

---

### Post by seandiggity on 2010-01-12
```
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.0.jar:cronometer.jar:usda_sr20.jar:crdb_003.jar:docs.jar ca.spaz.cron.CRONOMETER

```

Users should be aware that this line in the shell script ^ will change in updated releases. For release 0.9.7, it's:
```

java -cpcronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.3.jar:cronometer.jar:usda_sr22.jar:crdb_004.jar:docs.jar ca.spaz.cron.CRONOMETER

```
...just make sure that the .jar files referred to in that line correspond to the files in the .zip package you download and extract.  You can also just copy the line from [http://spaz.ca/cronometer/cronometer.sh](http://spaz.ca/cronometer/cronometer.sh)

---

### Post by hortstu on 2010-01-25
Is there different code for getting this to work in hardy?

---

### Post by pwrcul on 2010-03-12
As seandiggity pointed out the easiest way now that the developers have updated their Linux script is to 

"just copy the line from [http://spaz.ca/cronometer/cronometer.sh](http://spaz.ca/cronometer/cronometer.sh) "

I came back to check to see if anyone had solved that issue.  I had figured out how to edit the--previously outdated--script on my own back in January but was too busy to provide feedback.  I am glad the fix has been published and even more that the developers have done the fix for all.  If you download their script now it should work.

---

### Post by uriol108 on 2010-03-17
It didnit run, when i try to execute the file it appears the following error

oriol@oriol-desktop:~/CRON-O-METER$ sh cron-o-meter.sh
Exception in thread "main" java.lang.NoClassDefFoundError: ca.spaz.cron.ui.SplashScreen
   at java.lang.Class.initializeClass(libgcj.so.90)
   at ca.spaz.cron.CRONOMETER.main(CRONOMETER.java:584)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.swingx.JXBusyLabel not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:cronometer.jar,file:jcommon-1.0.10.jar,file:jfreechart-1.0.6.jar,file:cronometer.jar,file:docs.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...1 more

---

### Post by pwrcul on 2010-03-17
I don't recall that Java error.  I will have to pass on it and hope someone else with Java in their blood has a clue.

---

