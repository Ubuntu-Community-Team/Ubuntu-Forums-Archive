---
title: "GWT (GOOGLE WEB TOOLKIT) runtime error"
date: 2007-01-09
forum: Programming Talk
---

### Post by ekravche on 2007-01-09
After downloading gwt-linux-1.2.22  and following the instructions of how to use this framework here at [http://code.google.com/webtoolkit/gettingstarted.html](http://code.google.com/webtoolkit/gettingstarted.html) [Creating an Application from Scratch (with Eclipse) section] I'm getting the following error when running it through eclipse.
> 
Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.RuntimeException: Installation problem detected, please reinstall GWT
   at com.google.gwt.util.tools.Utility.computeInstallationPath(Utility.java:310)
   at com.google.gwt.util.tools.Utility.getInstallPath(Utility.java:214)
   at com.google.gwt.util.tools.ToolBase.<clinit>(ToolBase.java:276)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...1 more
Caused by: java.io.IOException: Cannot determine installation directory; apparently not running from a jar
   at com.google.gwt.util.tools.Utility.computeInstallationPath(Utility.java:294)
   ...4 more

I think it has something to do with the fact that I have java 5 running on my machine and this framework requires java 1.4.

Any thoughts?

Best regards.

---

### Post by ekravche on 2007-01-09
Changing the project's jre from gnu 1.42 to sun's 1.5 did the trick!

---

### Post by kickabear on 2007-08-30
Can you tell me where you made the change which fixed your problem?  I'm having the same trouble with one of the sample applications.

Thanks!

---

### Post by viktor.ilijasic on 2007-09-04
I use Eclipse 3.2.2 with Aptana 0.2.9.16696.

```

sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```

That did it for me.

But there is one more step to do in Eclipse for the thing to work...

This version of eclipse is configured to use gcj Java. You need to configure it to be aware of SUN Java and to ise it instead of gcj.

Import GWT project in Eclipse: **File -> Import...**, **General -> Existing Projects into Workspace**, **"Next >"**, **"Browse"**, select directory, **"Finish"**.

Go to **Run -> Debug...**, then choose **Java Application -> your_project_name**, click on **"JRE"** tab, select **"Alternate JRE"**, click on **"Installed JREs..."**, **"Add..."**, type **/usr/lib/jvm/java-6-sun** in **JRE home directory"** and click **OK** button. **OK** again. Make sure that **java-6-sun-1.6** is selected as an Alternate JRE. Then click **Debug** button in the bottom of the dialog, and it should work.

When I write it like this, it seems more complicated than it really is. :)

Actually, it's a quite intuitive procedure.

Viktor


[COLOR="Red"]edit:[/COLOR]

I still get


```
TimerThread.run() line: 468
Source not found.
```

when I run the project. It runs normal in GWT debugger, but eclipse suspends it some seconds after starting debug.

Anyone have any idea what sources to add to source path? Or any other way to solve this?

---

### Post by viktor.ilijasic on 2007-09-04
Ok, problem solved...

instead of **sun-java6-*** use either **j2re1.5** or **sun-java5-***. I'm not certain which provided java-1.5, but when you set

```
sudo update-java-alternatives -s java-1.5.0-sun
```

gwt works and gives no error. Neither in Eclipse, nor when run in shell.

To see which java flavors you have installed use

```
update-java-alternatives -l
```

Viktor

---

