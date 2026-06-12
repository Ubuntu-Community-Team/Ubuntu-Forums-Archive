---
title: "[Tutorial]: Installing Eclipse 3.4 in Hardy Heron (8.04)"
date: 2008-10-08
forum: Programming Talk
---

### Post by fballem on 2008-10-08
The following notes may be helpful in doing a basic installation of Eclipse. Please note that this does not include the 'tuning' (i.e. setting parameters) that is required to get the installation working correctly.

Eclipse

This is a general purpose IDE used for development. The current version is 3.4 (Ganymede). This must be installed directly from the website ([http://www.eclipse.org](http://www.eclipse.org)), since the version of eclipse in the repositories is not current.

The original source for these instructions is: [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html). The original instructions were applicable to Eclipse Europa and have been updated here to include Ganymede.

Overview
As the result of these installation instructions
1. the main eclipse application will be installed in /opt/eclipse.
2. there will be a command shell located in /usr/local/bin.
3. there will be an eclipse folder in /usr/local/share.
4. there will be a desktop launcher (eclipse.desktop) in /usr/share/applications.

Prior to starting this process, 
1. sun java jdk must be installed. This may be installed from the repository through synaptic or using a terminal. In the case of terminal, type:
```
sudo apt-get install sun-java6-jdk
```.
2. a suitable icon must be found and downloaded. When completed, the icon will be located in /opt/eclipse. A suitable icon is located at [http://blog.benjamin-cabe.com/wp-content/uploads/2008/05/ganymede.png](http://blog.benjamin-cabe.com/wp-content/uploads/2008/05/ganymede.png) and may be initially downloaded to the Desktop or to any other location where it can be easily located.

Installation Instructions
1. Verify that any previous installation has been completely removed. In particular, the following needs to be verified:
a. There is no eclipse folder under /opt. If there is, it must be deleted. Sudo access will be required to delete the folder.
b. There is no eclipse folder under /usr/local/share. If there is, it must be deleted. Sudo access will be required to delete the folder.
b. There is no entry for eclipse in either /usr/bin or /usr/local/bin. If there is, then the entry must be deleted.
c. There is no entry for eclipse.desktop in /usr/share/applications. If there is, then the entry must be deleted.
b. There is no configuration files for eclipse in the users' home folders. These are hidden directories. If there are any, these must be deleted.

2. Obtain the appropriate file from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/). Only one of the packages is required. The file should be saved to the Desktop.

3. When the download has been completed, open a Terminal and execute the following commands:
cd ~/Desktop
tar xzf eclipse-SDK-3.4-linux-gtk.tar.gz (note that the filename may differ, depending on what was downloaded in step 2)
sudo mv eclipse /opt/eclipse
sudo mv ganymede-logo.png /opt/eclipse (this will move the icon. The filename and location for the logo may differ - depending where it was saved)
cd /opt
sudo chown -R root:root eclipse
sudo chmod -R +r eclipse
cd /opt/eclipse
sudo chmod +x eclipse

4. Create an executable shell for eclipse. This is done through Terminal by executing the following commands:
sudo touch /usr/local/bin/eclipse (this assumes that /usr/local/bin is in the path)
sudo chmod 755 /usr/local/bin/eclipse
sudo nano /usr/bin/eclipse (this will open the nano editor)

5. When the eclipse shell file is open (in nano), the following contents need to be inserted and the file saved:
#!/bin/sh
export ECLIPSE_HOME="/opt/eclipse"
$ECLIPSE_HOME/eclipse $*

6. Create a GNOME menu item. This is done through Terminal by executing the following command:
sudo nano /usr/share/applications/eclipse.desktop

7. When the GNOME menu item is open (in nano), the following contents need to be inserted and the file saved:
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse Ganymede IDE
Exec=eclipse
Icon=/opt/eclipse/ganymede-logo.png
Terminal=false
Type=Application
Categories=GNOME;Application;Development
StartupNotify=True

8. Initialise eclipse by running the following command in Terminal: /opt/eclipse/eclipse --clean.

From this point forward, eclipse may be run from the Application menu.

Please let me know how these work for you, and if you need any additional help.

---

### Post by FrankieFrankie on 2008-10-08
Thanks for the tutorial. Could you fix the broken link to the logo image?

---

### Post by ger_macaco on 2008-10-08
Many Thanks for this tutorial!

Are there any dependencies that should be taken into account? (probably sun's java6 runtimes is one)

---

### Post by Shin_Gouki2501 on 2008-10-08
download eclipse unzip( assuming u have java installed, java sun not gjc) and it jsut runs...
for me :)

---

### Post by fballem on 2008-10-08
> **FrankieFrankie said:**
> Thanks for the tutorial. Could you fix the broken link to the logo image?

Thanks - link has been fixed. If you wouldn't mind testing, I would be most grateful.

---

### Post by fballem on 2008-10-08
> **ger_macaco said:**
> Many Thanks for this tutorial!

Are there any dependencies that should be taken into account? (probably sun's java6 runtimes is one)

Identified that sun java jdk needs to be installed. Is this sufficient for the dependency?

Thanks,

---

### Post by ger_macaco on 2008-10-08
So far, everything is working perfectly. I'm now installing some plugins.

Thanks again.

---

### Post by matmatician on 2008-10-17
ok, i did everything you said, but i cant run eclipse off my toolbar (applications/programming/eclipse). when i run it in terminal, i cant make new files because there is no source folder.  ive used jcreator for several years, but i cant figure this out for the life of me. any help would be appreciated. i want to get away from windows, but if i cant program my java in linux, im gonna be stuck forking my money over to Microsuck.

---

### Post by gregkarr on 2008-10-24
I followed these instructions and it seemed like everything worked fine in terms of getting Eclipse 3.4 installed on my system. However, when I tried to install Photran via Eclipse's "Software updates" (or something like that) menu option I just get the error message in the attached screenshot. Any ideas on how to fix these unsatisfied dependencies?

---

### Post by Vishal Vivek on 2008-11-26
Hello,
  I am relatively new to eclipse, I installed Eclipse SDK 3.4.1 as per the  instructions here but I had to suffice with gcj java compiler as I couldn't get teh full package of java-6-jre. Would this affect the performance of my Eclipse??? Also II cannot get eclipse start off from my main applications menu even though there is a short-cut for it there....

Please Help :confused:

---

### Post by Reiger on 2008-11-28
In steps 6 & 7 you created that 'shortcut'.
Yes: GCJ is (widely?) regarded to be inferior to Sun's own, if not because of the speed at least because of the fact it's incomplete. It isn't on par with Java 1.5 yet, which translates in way-too-outdated for people that want to use Swing or similarly 'new' Java concepts.

The SUN JDK 6 is obtained from (notice the bold part):
```

sudo aptitude install **sun**-java6-jdk

```

Substitute 6 with 5 if you'd like to use Java 1.5/Java 5 instead of Java 1.6/Java 6. There are Opend JDK equivalents as well.

Since you've saddled yourself with the GCJ it's time to issue the following command (after installing a more suitable Java JDK):
```

sudo update-alternatives --config java

```

Choose your Java of choice.

Clean up whatever traces left of your previous Eclipse installation (as outlined in the tutorial in post #1).

For me I had to substitute any reference to /usr/local/bin with /usr/bin: you can check if the same applies to your by cd-ing into either and see if these folders are 'populated'. For me: /usr/local/bin is 100% empty (you can check by issueing ls), /usr/bin is crowded. So the right choice was obvious there.

---

### Post by littlebrat_pal on 2008-11-28
THANKS . I had been trying to install eclipse 3.4 on Ubuntu 8.04 a couple of weeks ago but there were these annoying errors like the one below:-
 
CompilerOracle: exclude org/eclipse/core/internal/dtreeDataTreeNode.forwardDeltaWith

I tried a few fixes but finally gave up due to lack of time. This the time installation was just sooo smooth .

Thanks once again.

---

### Post by ender4 on 2009-01-27
I followed these instructions with a few modifications

1. Instead of created a shell script I created a symbolic link with the command
```

cd /usr/local/bin
sudo ln -s /opt/eclipse/eclipse

```

2. I used the graphical menu editor to create a launcher in the programming menu

it now works fine, thanks

---

### Post by DSL5 on 2009-02-05
Everything worked for me, except when I try to run Eclipse from the menu shortcut, I get a window that says:

     Could not launch menu item

     Failed to execute child process "/usr/bin/eclipse" (Permission denied)

How do I get permission??

---

### Post by jdoge13 on 2009-02-06
Everything works fine for me when I use the 
sudo /opt/eclipse/eclipse --clean command
However, when I try to run it from the applications menu it just gives me a pinwheel then quits.

---

### Post by akoblentz on 2009-02-09
> **DSL5 said:**
> Everything worked for me, except when I try to run Eclipse from the menu shortcut, I get a window that says:

     Could not launch menu item

     Failed to execute child process "/usr/bin/eclipse" (Permission denied)

How do I get permission??

If you use the symbolic link in the post above yours, it will work.
I had the same issue.

---

### Post by ai2068 on 2009-02-10
I get the same error message as gregkarr's.  Has anyone solved this problem?

---

### Post by cdaaawg on 2009-02-15
In step 4, 

sudo nano /usr/bin/eclipse (this will open the nano editor) 

should read: 

sudo nano /usr/local/bin/eclipse (this will open the nano editor)

Making this change should allow the launcher created in
Applications --> Programming --> Eclipse to work properly.

---

### Post by jamesgate on 2009-02-22
Two useful additions to the eclipse start command line:  I added -vm for java version, and memory parameters (at step 5).  The -vm will substitute Sun to GCJ, and the memory parameters will eliminate the periodic application exit.  See 
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/83779](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/83779)

[from /usr/local/bin/eclipse]
#!/bin/sh
export ECLIPSE_HOME="/opt/eclipse"
$ECLIPSE_HOME/eclipse -vm /usr/lib/jvm/java-6-sun-1.6.0.07/bin/java -Xms40m -Xmx512m -XX:PermSize=128M -XX:MaxPermSize=256M $*

---

### Post by Silvestro Fantacci on 2009-03-01
Looking at the [Ubuntu Documentation]("https://help.ubuntu.com/community/EclipseIDE") I have noticed that the shell file suggested there has an additional command:

export MOZILLA_FIVE_HOME="/usr/lib/mozilla/"

I wonder... what's the purpose of this command and/or can it be omitted?

---

### Post by JoulSauron on 2009-03-14
When 
```
/opt/eclipse/eclipse --clean.
```

I get a denied permission message: plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805

and a window shows: The Eclipse executable launcher was unable to locate its  companion shared library.

However, everything goes OK when I * [COLOR="Red"]sudo[/COLOR] /opt/eclipse/eclipse --clean.*, so I think it is a problem of permissions. How can I fix this so I can run eclipse from GNOME menu?

---

### Post by pfwd.tech on 2009-03-29
Thanks for a great guide.
After reading this I was able to set up eclipse 3.4 on Intrepid
Good work

---

### Post by yeehi on 2009-03-30
Regarding Item 5 and Item 7:

1) I open nano but there seems to be no way to save a file; all I can do is exit.

2) Under which names and in which directories should I save these files?

---

### Post by pfwd.tech on 2009-03-30
> **yeehi said:**
> Regarding Item 5 and Item 7:

1) I open nano but there seems to be no way to save a file; all I can do is exit.

2) Under which names and in which directories should I save these files?

To save a file using nano you press CTRL + X it will then ask you:
```
Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?                    
 Y Yes
 N No           ^C Cancel

```Press y for yes
It will then ask you for the file name
Once entered press enter to save the file

Hope that helps

Edit
Make sure you enter sudo before nano so that you have write permissions

---

### Post by pcjunkie on 2009-04-02
After following many tutorials on this, cleaning up and starting again I am still getting this...

> !ENTRY org.eclipse.osgi 4 0 2009-04-02 20:43:53.701
!MESSAGE Error reading configuration: /opt/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock (No such file or directory)
!STACK 0
java.io.FileNotFoundException: /opt/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock (No such file or directory)
	at java.io.RandomAccessFile.open(Native Method)
	at java.io.RandomAccessFile.<init>(RandomAccessFile.java:233)
	at org.eclipse.core.runtime.internal.adaptor.Locker_JavaNio.lock(Locker_JavaNio.java:32)
	at org.eclipse.osgi.storagemanager.StorageManager.lock(StorageManager.java:389)
	at org.eclipse.osgi.storagemanager.StorageManager.open(StorageManager.java:687)
	at org.eclipse.osgi.internal.baseadaptor.BaseStorage.initFileManager(BaseStorage.java:208)
	at org.eclipse.osgi.internal.baseadaptor.BaseStorage.initialize(BaseStorage.java:142)
	at org.eclipse.osgi.baseadaptor.BaseAdaptor.initializeStorage(BaseAdaptor.java:124)
	at org.eclipse.osgi.framework.internal.core.Framework.initialize(Framework.java:180)
	at org.eclipse.osgi.framework.internal.core.Framework.<init>(Framework.java:152)
	at org.eclipse.osgi.framework.internal.core.OSGi.createFramework(OSGi.java:90)
	at org.eclipse.osgi.framework.internal.core.OSGi.<init>(OSGi.java:31)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:286)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:175)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)



Eclipse seems to be the most time consuming program to install. Flex can only be used if Eclipse is in opt. Kinda annoying..

Java 6 SDK is installed. I have been using it with Console to write short nasty apps..

---

### Post by tamas305 on 2009-04-14
This is an alternate way, a way I believe is easier (this also works for installing the java plugin for firefox 3).

1) Boot up Ubuntu and open up a terminal (Applications --> Accessories -- > Terminal)

2) Type 

```
sudo su
```

3) Enter your password, you will not see what you enter (a security feature)

4) Type

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

5) Agree to the license agreement and let it install, restart firefox, eclipse or any other program that needs JAVA and it should work

-tamas

---

### Post by SynnerG on 2009-05-03
Could someone help me out? Ive followed this tutorial to the T but I keep getting this error. "org.eclipse.swt.SWTError: XPCOM error -2147467262"

Ive uninstalled everything and tried again but with the same result. Has anyone else experienced this? Any help would be appreciated. I am running ubuntu 64 bit. here is the complete error log.


!SESSION 2009-05-03 17:58:09.851 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2009-05-03 17:58:13.923
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:658)
	at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
	at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:443)
	at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:266)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(ViewIntroAdapterPart.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$1.propertyChanged(ViewIntroAdapterPart.java:55)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:374)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireZoomChange(WorkbenchPartReference.java:539)
	at org.eclipse.ui.internal.PartPane.setZoomed(PartPane.java:349)
	at org.eclipse.ui.internal.PartStack.setZoomed(PartStack.java:1526)
	at org.eclipse.ui.internal.PartSashContainer.zoomIn(PartSashContainer.java:884)
	at org.eclipse.ui.internal.PartSashContainer.childRequestZoomIn(PartSashContainer.java:905)
	at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
	at org.eclipse.ui.internal.PartStack.setState(PartStack.java:1501)
	at org.eclipse.ui.internal.WorkbenchPage.setState(WorkbenchPage.java:3872)
	at org.eclipse.ui.internal.WorkbenchPage.toggleZoom(WorkbenchPage.java:3944)
	at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(WorkbenchIntroManager.java:201)
	at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:136)
	at org.eclipse.ui.internal.WorkbenchWindow$20.runWithException(WorkbenchWindow.java:2182)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1363)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2295)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2200)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:495)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:490)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1212)

---

### Post by psaville on 2009-06-12
I posted an answer that uses apt-get to do the upgrade to eclipse 3.4.

See this posting:
[http://ubuntuforums.org/showpost.php?p=7442900&postcount=3]("http://ubuntuforums.org/showpost.php?p=7442900&postcount=3")

---

### Post by ksp1717 on 2009-06-24
Hi

After following the process described, i can run eclipse from the last command in the console. But I was not able to do the same from the programming menu. 
I did the following changes and i could.

1. I changed the /usr/bin/eclipse to /usr/local/bin/eclipse and then opened nano.
2. I changed the gnome desktop icon in /usr/share/applications/eclipse ....
   in the program that is entered in nano, i changed the 'exec = eclipse' to 'exec=/opt/eclipse/eclipse' and saved it.

Thats it everything is running smooth.

But I do have one query.... incase i want to install any plugins, if i do tht from synaptic manager, will the changes be effective??? or should i follow any other process.

---

### Post by DimCI on 2010-02-16
Many, many THANKS to **fballem**!:guitar:

I've spent about 2 days trying to install Eclipse but failed a few times... But by means of following your SUPER tutorial I have php ide at last! (_***eclipse-php-galileo-SR1-linux ***_package's been installed btw )  ;) At least it seems working ;) Thank u again!

---

### Post by ahmon_abilar on 2011-05-02
Great tutorial thanks... I'm running PHP Eclipse now...

---

