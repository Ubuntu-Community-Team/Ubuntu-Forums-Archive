---
title: "can't start up eclipse,but with no error message"
date: 2008-07-07
forum: Programming Talk
---

### Post by careprad on 2008-07-07
hi,all.
I use ubuntu8.04 in vmware6.and download eclipse 3.4,extract it.set permissions.
when I run eclipse,It show the start image some seconds,then show a empty box with no text.I have check the error log,but can't find any.I have setup jdk1.5correctlly.the eclips ecan find it.The attachment is the screen shot.
plz help me ,tkx.

---

### Post by tinny on 2008-07-07
> **careprad said:**
> hi,all.
I use ubuntu8.04 in vmware6.and download eclipse 3.4,extract it.set permissions.
when I run eclipse,It show the start image some seconds,then show a empty box with no text.I have check the error log,but can't find any.I have setup jdk1.5correctlly.the eclips ecan find it.The attachment is the screen shot.
plz help me ,tkx.

There are two things you could try.

First run Eclipse from the command line like this

```

cd <path to eclipse>
./eclipse -debug

```

This will print debug info to the console. Post back the results.

The other thing you could do is install eclipse using the synaptic package manager. (This is what id recommend you do)

---

### Post by goerge on 2008-07-08
Exactly the same problem but with VMware® Player 2.0.2 build-59824.

Eclipse 3.4 Ganymede (even Europa) is not in Hardy repositories.

There is nothing wrong/suspicious in debug log.

There is some invisible text in that window - mouse cursor changes to I if you move it above window content. But you can't select it to make it visible :(.

Edit: I've just tried repository version of eclipse (3.2.2) and everything is OK

Edit 2: After I installed Eclipse 3.2.2 from Hardy repository and then run Eclipse 3.4 (downloaded manually). It starts up correctly. Not elegant solution, but it works. So I think there is some unresolved dependency.

---

### Post by tinny on 2008-07-08
> **goerge said:**
> Exactly the same problem but with VMware® Player 2.0.2 build-59824.

Eclipse 3.4 Ganymede (even Europa) is not in Hardy repositories.

There is nothing wrong/suspicious in debug log.

There is some invisible text in that window - mouse cursor changes to I if you move it above window content. But you can't select it to make it visible :(.

Edit: I've just tried repository version of eclipse (3.2.2) and everything is OK

Edit 2: After I installed Eclipse 3.2.2 from Hardy repository and then run Eclipse 3.4 (downloaded manually). It starts up correctly. Not elegant solution, but it works. So I think there is some unresolved dependency.

Are there significant differences between 3.2.2 and 3.4??? 

Id imagine not, so you should be fine with the version from the repositories.

BTW: This isnt a problem with VMware. I think this might be something to do with JRE 6, maybe. (I had this problem once)

What is the output of the following?

```

java -version

```

---

### Post by careprad on 2008-07-09
my eclispe can run now ,but I still do not know what is the very problem.
Waht I do is just update some soft ware remommanded by the update manager.

thank you:popcorn:

---

### Post by knolleary on 2008-07-10
I have hit this same issue.

Running Hardy, with eclipse 3.2.2-5ubuntu2 installed from the repositories, I have downloaded the eclipse 3.4 tar.gz and extracted it locally.

When I ran, I got the initial splash screen followed by the blank window as described by careprad.

I eventually found the problem to be that my user did not have write permissions in the eclipse/configuration directory. Once I fixed that, eclipse started up fine.

---

### Post by dpward on 2008-07-20
Finally! I believe I found the real problem here... when I extracted the Eclipse tar.gz file, the ownership of the files was all wrong.  I had to do this:

sudo chown -R root:root /opt/eclipse

(assuming /opt/eclipse is where you extracted the archive)


Additional note: if you receive an error that says "Could not initialize the application security component" on startup, then the permissions on ~/.mozilla/eclipse are wrong, possibly because you ran eclipse using sudo before running it with normal permissions.  I simply deleted this directory:

sudo rm -r ~/.mozilla/eclipse

---

### Post by Can+~ on 2008-07-20
> **dpward said:**
> Finally! I believe I found the real problem here... when I extracted the Eclipse tar.gz file, the ownership of the files was all wrong.  I had to do this:

sudo chown -R root:root /opt/eclipse

(assuming /opt/eclipse is where you extracted the archive)


Additional note: if you receive an error that says "Could not initialize the application security component" on startup, then the permissions on ~/.mozilla/eclipse are wrong, possibly because you ran eclipse using sudo before running it with normal permissions.  I simply deleted this directory:

sudo rm -r ~/.mozilla/eclipse

You should not use eclipse from the page, it is available on the repository.

[PHP]sudo apt-get install eclipse[/PHP]

And to circumvent the issue about Java 1.6, launch forcing with Java 1.5, first install Java 1.5:
[PHP]sudo apt-get install sun-java5-jre sun-java5-jdk[/PHP]
(Not sure if you need the jdk, but I installed it anyway)

Then add a launcher to the desktop with:
[PHP]/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/bin/java -cp /usr/lib/eclipse/startup.jar org.eclipse.core.launcher.Main[/PHP]
(Make sure JRE 1.5 is installed (also available in the repositories))

Optionally, install the Python plugin, or C/C++ plugin:
[PHP]sudo apt-get install eclipse-cdt eclipse-pydev[/PHP]

---

### Post by tinny on 2008-07-20
> **Can+~ said:**
> You should not use eclipse from the page, it is available on the repository.

[PHP]sudo apt-get install eclipse[/PHP]

And to circumvent the issue about Java 1.6, launch forcing with Java 1.5, first install Java 1.5:
[PHP]sudo apt-get install sun-java5-jre sun-java5-jdk[/PHP]
(Not sure if you need the jdk, but I installed it anyway)

Then add a launcher to the desktop with:
[PHP]/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/bin/java -cp /usr/lib/eclipse/startup.jar org.eclipse.core.launcher.Main[/PHP]
(Make sure JRE 1.5 is installed (also available in the repositories))

Optionally, install the Python plugin, or C/C++ plugin:
[PHP]sudo apt-get install eclipse-cdt eclipse-pydev[/PHP]

Yeah a repositories install should be the easiest path to getting this setup.

However if you would like to install the latest version from eclipse.org and have JDK 6 have a look at this thread (look for the last post by TonyGould)

[http://ubuntuforums.org/showthread.php?t=853632](http://ubuntuforums.org/showthread.php?t=853632)

---

### Post by mau84 on 2008-09-24
I have the same problem but I can't solve. Please help me. I extract the eclipse folder in my home dir and I use java 6...

---

### Post by tinny on 2008-09-24
> **mau84 said:**
> I have the same problem but I can't solve. Please help me. I extract the eclipse folder in my home dir and I use java 6...

Whats the output of...

```

java -version

```

---

### Post by marcellosales on 2008-12-28
Just add the following line to your ECLIPSE_UMPACKED_DIR/eclipse.ini. 

-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null

I found the error message just running 

./eclipse -consolelog 

Then, it took me direct to a problem related to firefox...

marcello@survival:~/development/ide/eclipse3.4$ xulrunner -v
Mozilla XULRunner 1.9b5 - 2008041514

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=213194](https://bugs.eclipse.org/bugs/show_bug.cgi?id=213194)
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=235020](https://bugs.eclipse.org/bugs/show_bug.cgi?id=235020)

I had spent around 2 hours to find the correct error message...

have fun!

---

### Post by rockballad on 2009-02-05
Hello, my Eclipse doesn't start too. 

I followed the instruction here: [http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/](http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/)
```

hailua@ubuntu-desktop:/data/app/eclipse$ ./eclipse -debug
Start VM: /usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-XX:MaxPermSize=256m
-jar /data/app/eclipse/plugins/org.eclipse.equinox.launcher_1.0.100.v20080509-1800.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /data/app/eclipse/eclipse
-name Eclipse
--launcher.library /data/app/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.100.v20080606/eclipse_1114b.so
-startup /data/app/eclipse/plugins/org.eclipse.equinox.launcher_1.0.100.v20080509-1800.jar
-exitdata 18000f
-framework plugins/org.eclipse.osgi_3.4.0.v20080605-1900.jar
-debug
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-XX:MaxPermSize=256m
-jar /data/app/eclipse/plugins/org.eclipse.equinox.launcher_1.0.100.v20080509-1800.jar 
Install location:
    file:/data/app/eclipse/
Configuration file:
    file:/data/app/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/hailua/.eclipse/org.eclipse.platform_3.4.0_485923933/configuration/
Configuration file:
    file:/home/hailua/.eclipse/org.eclipse.platform_3.4.0_485923933/configuration/config.ini loaded
Shared configuration location:
    file:/data/app/eclipse/configuration/
Framework located:
    file:/data/app/eclipse/plugins/org.eclipse.osgi_3.4.0.v20080605-1900.jar
Framework classpath:
    file:/data/app/eclipse/plugins/org.eclipse.osgi_3.4.0.v20080605-1900.jar
Splash location:
    /data/app/eclipse/plugins/org.eclipse.platform_3.3.100.v200806172000/splash.bmp
Debug options:
    file:/data/app/eclipse/.options not found
Time to load bundles: 15
Starting application: 3139

```


It just shows or runs nothing. If I don't pass "-debug" param, it stops quietly. Nothing happens.

I installed java:
```
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

```

Please help me to address the error. Thank you in advance!

---

### Post by regmee on 2009-02-11
Post number 12 solved my problem. 
I just added the line "-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null"
after the last line in the *.ini file

Thanks a lot.

---

### Post by rockballad on 2009-02-11
Thanks for your answer. I've just "solved" it. I realized that I'd been using the 32-bit version on my 64-bit Ubuntu LOL. A good advice is we should see the log file at the workspace for detail error.

Good day!

---

### Post by lol24h on 2009-03-30
OH !Now I think it's somelike connected with non-working java plugin in my firefox on ubuntu 9.04 . Java propably doesn't get the right path to xulrunner. I'll investigate it.

---

### Post by UbuDroid on 2009-04-03
Hi all

I am new to Ubuntu. I download eclipse3.4.2 ganymede IDE and extract it on Desktop.when I run eclipse,It show the start image some seconds,then show a empty box with no text.I have setup jdk1.6 and jre1.6 correctly.

Plz help me.
 thnx

---

### Post by rockballad on 2009-04-03
> **UbuDroid said:**
> Hi all

I am new to Ubuntu. I download eclipse3.4.2 ganymede IDE and extract it on Desktop.when I run eclipse,It show the start image some seconds,then show a empty box with no text.I have setup jdk1.6 and jre1.6 correctly.

Plz help me.
 thnx

A good advice is we should see the log file at the workspace for detail error.

Can you show it?

---

### Post by UbuDroid on 2009-04-03
In which folder we can find the log file.?

I searched but i dint get

I dont know :(

---

### Post by rockballad on 2009-04-03
Go to your Workspace folder (directory). Enable showing hidden files. Or you can gedit the log file here:
$ gedit /../../workspace/.metadata/.log

You may need to clear the log (select all - Delete) once, and restart Eclipse to get a new and clear log :-)

---

### Post by UbuDroid on 2009-04-03
!SESSION 2009-04-03 14:23:21.633 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.ui.workbench 4 0 2009-04-03 14:23:41.510
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)......
.
.
.
.
.
----------------------------------------

Its too large file unable to send it
It showing error as follows:
  "The following errors occurred with your submission:

   1. You have included 120 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator."

any other option plzz

---

### Post by brimbleshoes on 2009-06-03
Try this ... it worked for me:

```
cd /path/to/workspace/.metadata/.plugins
rm -rf org.eclipse.core.resources
```

You'll lose all of your workspace folders -- but you can just re-import them.  Better than losing it altogether.

I found it here:
[http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/]("http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/")

---

### Post by vishvesh on 2009-12-28
> **marcellosales said:**
> Just add the following line to your ECLIPSE_UMPACKED_DIR/eclipse.ini. 

-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null

I found the error message just running 

./eclipse -consolelog 

Then, it took me direct to a problem related to firefox...

marcello@survival:~/development/ide/eclipse3.4$ xulrunner -v
Mozilla XULRunner 1.9b5 - 2008041514

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=213194](https://bugs.eclipse.org/bugs/show_bug.cgi?id=213194)
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=235020](https://bugs.eclipse.org/bugs/show_bug.cgi?id=235020)

I had spent around 2 hours to find the correct error message...

have fun!

Hi marcellosales,

    I spent few hours trying to launch eclipse, but it didn't. Your suggestion worked well. Thank you very much.

---

### Post by MrPok on 2010-01-11
> **vishvesh said:**
> Hi marcellosales,

    I spent few hours trying to launch eclipse, but it didn't. Your suggestion worked well. Thank you very much.

I also confirm that this solves the problem. Tnx! :) 
Imho it is a better solution than having to re-import and setup your workspace(s).

I added the line
```
-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null
```..on the bottom of the file **eclipse.ini** (in directory **/opt/eclipse/** )
and when I started Eclipse everything was back to normal! :P


--not related to solution--
What I gathered from the various scattered bug reports and blogs on this issue it has something to do with having Firefox 3.5 (or more specific latest XUL libraries) in combination with (in my case) a deliberately downgraded (reverted configuration, since I couldn't get Eclipse to open an xml-file in the editor) of WST XML Core (3.0.4). But I'm no expert on these matters..so.. Same goes for the problems with buttons that do not work; a gtk issue that isn't solved at the moment. 
Anyway, I would think chances are that after some updates we don't need these workarounds.. Too bad that a great IDE like Eclipse suffers from these kind of problems.. <sigh>

---

### Post by ognum on 2010-05-03
> **brimbleshoes said:**
> Try this ... it worked for me:

```
cd /path/to/workspace/.metadata/.plugins
rm -rf org.eclipse.core.resources
```

You'll lose all of your workspace folders -- but you can just re-import them.  Better than losing it altogether.

I found it here:
[http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/]("http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/")

For me it was enough to remove the following file 
/path/to/workspace/.metadata/.plugins/org.eclipse.core.resources/.snap

/cheers

---

### Post by r2afa on 2011-04-01
> **brimbleshoes said:**
> Try this ... it worked for me:

```
cd /path/to/workspace/.metadata/.plugins
rm -rf org.eclipse.core.resources
```You'll lose all of your workspace folders -- but you can just re-import them.  Better than losing it altogether.

I found it here:
[http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/](http://letsgetdugg.com/2009/04/19/recovering-a-corrupt-eclipse-workspace/)

Thank you!!! :P

---

### Post by muktoshvruvro on 2011-04-01
i don't know how to find arm-elf-gcc path in ubuntu?? any idea???

---

### Post by o15977 on 2013-02-14
Worked solution for me:

delete /.metadata/ folder in the workspace you're trying to use.

---

