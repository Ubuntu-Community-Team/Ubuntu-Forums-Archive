---
title: "HOWTO: Install Aptana IDE"
date: 2006-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2006-12-09
I've had some difficulty installing [Aptana]("http://www.aptana.com") on Edgy, and when searching the forums for help I saw a few unresolved threads where others seem to have had a hard time with installing it, so I thought a short guide that puts together the installation steps would be useful. I've tested this on Edgy only and would like feedback from Dapper users as well, so that I can add any possible extra installation steps.

**1)** Download the installer from [http://www.aptana.com/](http://www.aptana.com/)

**2)** Install the dependencies ```
sudo apt-get install libswt3.1-gtk-java mozilla
```

**3)** Navigate to the directory where you downloaded the installer in the terminal and do the following```

cp Aptana_IDE_Setup.bin Aptana_IDE_Setup.bin.bak 

cat Aptana_IDE_Setup.bin.bak | \ sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > \ Aptana_IDE_Setup.bin 
```This will help with the "Unable to find shared library" errors. The first line creates a backup file named Aptana_IDE_Setup.bin.bak which you can later delete.

**4)** Launch the installer ```
./Aptana_IDE_Setup.bin
```and follow the instructions

**5)** Use the following script to launch Aptana. This is assuming you've installed it to your ~/Aptana folder.
```

#! /bin/bash
export MOZILLA_FIVE_HOME=/usr/lib/mozilla
~/Aptana/aptana 
```

---

### Post by els on 2006-12-12
**Edit: [http://www.aptana.com/forums/viewtopic.php?t=520&postdays=0&postorder=asc&start=0]("http://www.aptana.com/forums/viewtopic.php?t=520&postdays=0&postorder=asc&start=0")  solved my problems.  On page 3 there's a .deb that takes care of everything.**


I still get an error saying that the sed command can't be found when I try to do step #3.

By taking out the space between the "\" and "sed" I was able to avoid that particular error, but still ran into this one when I tried to install:

```
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.11946/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

Any ideas?

Thanks

---

### Post by tbfr on 2007-02-12
If Aptana constantly crashes check the maximum allowed number of opened files by typing this into the console:

ulimit -n

The value is propably set to 1024. It can be increased by adding your user to /etc/security/limits.conf like this:

yourusername hard nofile 32768

Log out and in again for the changes to become effective. Aptana is running stable for me since then. The output of lsof | wc -l always shows around 6000 opened files when running it.

---

### Post by eivindgl on 2007-02-19
Hi, thanks for the guide!
I still have some problems, when I try to run Aptana a message dialog pops up and tells me that > "An error has occurred. See the log file /home/eivind/aptana/workspace/.metadata/.log."

I'm guessing this error has to to with the mozilla engine, so I tried to edit the startup-script to point to /usr/lib/mozilla-firefox which resulted in the same message dialog.

The error log is long, and pretty repeating, so I'll only post the beginning 
> !SESSION 2007-02-19 13:43:48.936 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.4.2_09
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  #VM Runtime Configuration File
Command-line arguments:  -os linux -ws gtk -arch x86 #VM Runtime Configuration File

!ENTRY com.aptana.ide.rcp.main 1 0 2007-02-19 13:43:51.827
!MESSAGE (Build 0.2.7.13425) Bound to port 9980

!ENTRY com.aptana.ide.core.ui 1 0 2007-02-19 13:43:58.769
!MESSAGE (Build 0.2.7.13425) Connected to database aptanaDB 

!ENTRY org.eclipse.ui.workbench 4 0 2007-02-19 13:44:00.679
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
        at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
        at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
        at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
        at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
        at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)


The whole log can be found [here.]("http://heim.ifi.uio.no/eivindgl/aptana_errorlog.txt").
Why is this program so hard to install? :p 
Thanks to all of you who post solutions at the forum and in the wiki, it has really helped me a lot.

---

### Post by tbfr on 2007-02-20
@eivindgl: not sure about this one, but the logfile says that libxpcom.so is missing.

did you install mozilla?

how do you start aptana? like this?

[I]export MOZILLA_FIVE_HOME=/usr/lib/mozilla
/your/path/aptana[/I]

---

### Post by eivindgl on 2007-02-21
Hi 
Looks like I just just copied the instructions without paying any attention to the response. Sorry! No, I haven't installed Mozilla. It can't even find it in the repositories.
```
eivind@elap:~/www$ sudo apt-get install mozilla
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla has no installation candidate
```

I'm using the feisty fawn beta since my wireless card is unstable in edgy, I couldn't find a Mozilla installer at [www.mozilla.org](www.mozilla.org) either. Is Seamonkey equivalent to Mozilla?

---

### Post by tbfr on 2007-02-22
Mozilla has been removed from Feisty. Seamonkey is equivalent to the Mozilla Suite but you currently won't find it in Feisty either.

I just tried what happens if I remove Mozilla and set MOZILLA_FIVE_HOME to Firefox (also using Feisty, Aptana is 0.2.8.13501). Works fine for me, this is my start up script:

#! /bin/bash
cd /opt/aptana/
export MOZILLA_FIVE_HOME=/usr/lib/firefox/
./aptana -vm /etc/alternatives/java


More tips can be found here: [http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux]("http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux")

---

### Post by muncrief on 2007-03-02
OK everyone, after trying a lot of different things I was able to get the latest stable Aptana (0.2.7.13425 at the time of this writing) running beautifully (at least for the last hour or so) on Ubuntu Edgy AMD64. It turns out that it needs a particular version of mozilla, and has to use its own Java runtime to remain stable. This and a few other quirks made it quite a headache to install, but its easy once you know the "secret" steps! :) 

I haven't seen everything I had to do to make it work in one place so I'm posting it here in the hopes that it will save some of you time. As I said though, I went through many different installation techniques before hitting on one that worked, so I hope I haven't left out any dependencies or steps. I can't (and don't want to) restore my system to a pristine state so if I have left anything thing out please let me know and I'll update this howto.

OK, here's what worked for me folks:

1. Type "sudo apt-get install libswt3.1-gtk-java mozilla". I'm not sure we need this mozilla but it doesn't hurt, and I haven't tried installing without it. We actually have to use a different mozilla, so if someone wants to try to install without this mozilla and report the results it would be useful.

2. Download the Mozilla 1.7.8 GTK2 build from [http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.8/contrib/mozilla-i686-pc-linux-gnu-1.7.8-gtk2+xft.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.8/contrib/mozilla-i686-pc-linux-gnu-1.7.8-gtk2+xft.tar.gz) to /usr/local.

3. Open a terminal and type "cd /usr/local".

4. Type "sudo tar xvf mozilla-i686-pc-linux-gnu-1.7.8-gtk2+xft.tar.gz" (untars files to /usr/local/mozilla).

5. Type "export MOZILLA_FIVE_HOME=/usr/local/mozilla".

6. Type "sudo /usr/local/mozilla/mozilla" (just run mozilla once as root and then exit the browser).

7. Type "cd ~/".

8. Type "sudo chown -R <your username> .mozilla". This will restore your ownership to your local mozilla.

9. Download the "Current Release" "BIN plus Java Runtime" version of Aptana from [http://update.aptana.com/download_all.php#linux](http://update.aptana.com/download_all.php#linux) to your home directory (~/).

10. Type "mv Aptana_IDE_Setup.bin Aptana_IDE_Setup.bin.bak".

11. Type "sed 's/export LD_ASSUME_KERNEL=2.2.5/#xport LD_ASSUME_KERNEL=2.2.5/' Aptana_IDE_Setup.bin.bak > Aptana_IDE_Setup.bin". This is necessary to avoid terminal library dependency errors.

12. Type "sudo chmod a+x Aptana_IDE_Setup.bin".

13. Type "export XLOCALELIBDIR=/usr/lib32/X11/locale". This is required to avoid the "current locale is not supported in X11, locale is set to CX locale modifiers are not supported ..." compilation error for 32 bit java programs and 64 bit platforms.

14. Type "./Aptana_IDE_Setup.bin" to start the installer. Accept all default values. It will install in your home directory, which was the only way I could get it to work without dealing with a lot of permissions issues. If someone could figure out a multi-user installation I'm sure it would be useful, and shouldn't be to hard. It's just late and I'm to tired to mess with it now.

15. Since it needs its own special mozilla and Java you must launch Aptana with the following script:

#!/bin/bash
export MOZILLA_FIVE_HOME=/usr/local/mozilla
export PATH=$PATH:~/Aptana
export JAVA_BINDIR=/usr/lib32/jvm/java-gcj/bin
export JAVA_HOME=/usr/lib32/jvm/java-gcj
export JAVA_ROOT=/usr/lib32/jvm/java-gcj
exec ~/Aptana/aptana


And Enjoy!

I sure hope it works for you. I'm just trying it out now and so far it looks pretty cool!.

---

### Post by timmie on 2007-03-05
Hello,
I am wondering wheather one can use Aptana successfully in Linux as a plug-in for Eclipse itself.
I tried but don't get any tooltips nor HTML / CSS problems check...

Thanks,
Timmie

---

### Post by sk8dork on 2007-03-08
> **timmie said:**
> Hello,
I am wondering wheather one can use Aptana successfully in Linux as a plug-in for Eclipse itself.
I tried but don't get any tooltips nor HTML / CSS problems check...

Thanks,
Timmie

i was kinda miffed about all the hoops you have to jump through to install aptana standalone when it's based off of eclipse and it can be run as a plugin. so after getting the following error during installation of aptana standalone:
```
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.7589/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```
i decided to try to install eclipse from repos and install the aptana plugin (i read someone comment that you get all the aptana stuff and more). follow the instructions [here]("http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration") and you'll have it done relatively easily. i didn't run eclipse as root the first time, so i opened a root terminal and performed the steps that were listed in the terminal i ran eclipse from:
```
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
```
when you get the plugin installed you have to restart eclipse, go to window > open perspective > other, and pick aptana. now you're in.

---

### Post by bruceleo on 2007-03-10
muncrief, I think you forgot a comma or something on step 11. Does anyone know what the correct way to avoid the terminal library dependency error is? The original method is giving me the sed error.

---

### Post by bruceleo on 2007-03-10
Never mind. Here is what works:
   1. Download the install file at: [http://www.aptana.org/download_all.php#linux](http://www.aptana.org/download_all.php#linux)
   2. Open a terminal window and get the dependencies:

      sudo apt-get install mozilla

      sudo aptitude install libswt3.1-gtk-java

   3. Fix the installer issues:

      cp Aptana_IDE_Setup.bin Aptana_IDE_Setup.bin.bak

      cat Aptana_IDE_Setup.bin.orig | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Aptana_IDE_Setup.bin

   4. Make the bin executable:

      chmod +x Aptana_IDE_Setup.bin

   5. Run the installer:

      ./Aptana_IDE_Setup.bin

   6. Now we just make a little script to set an environment every time

      touch aptana

      sudo gedit aptana

   7. Now copy this

      #/usr/bin

      export MOZILLA_FIVE_HOME=/usr/lib/mozilla

      ~/Aptana/aptana

   8. save the file
   9. chmod it so it can be executed:

      chmod 755 aptana

  10. Now copy it to the /bin folder:

      sudo cp aptana /bin/

That's it.

---

### Post by johnficca on 2007-03-16
Hi I'm trying to get the installer to work on amd64 this is what I get :
any help at all would be great.


&^%^%$$^@^&*((**&^-desktop:~$ ./Aptana_IDE_Setup.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(Unknown Source)
        at sun.awt.motif.MFramePeer.<init>(Unknown Source)
        at sun.awt.motif.MToolkit.createFrame(Unknown Source)
        at java.awt.Frame.addNotify(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

---

### Post by johnficca on 2007-03-16
Ok I installed form apt-get and now it give me an error and tells me to check this and this is the .log
any help would be great.


```
!SESSION 2007-02-06 13:40:12.27 ------------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=es_CO
Framework arguments:  #VM Runtime Configuration File
Command-line arguments:  -os linux -ws gtk -arch x86 #VM Runtime Configuration File

!ENTRY com.aptana.ide.rcp.main 1 0 2007-02-06 13:40:17.28
!MESSAGE (Build 0.2.7.13425) Bound to port 9980

!ENTRY com.aptana.ide.core.ui 1 0 2007-02-06 13:40:28.247
!MESSAGE (Build 0.2.7.13425) Connected to database aptanaDB 

!ENTRY com.aptana.ide.scripting 1 0 2007-02-06 13:40:43.791
!MESSAGE (Build 0.2.7.13425) Scripting server started on port 9000

!ENTRY com.aptana.ide.core.ui 1 0 2007-02-06 13:40:43.944
!MESSAGE (Build 0.2.7.13425) current Aptana build number

!ENTRY com.aptana.ide.core.ui 1 0 2007-02-06 13:41:01.848
!MESSAGE (Build 0.2.7.13425) Database shut down normally 
!SESSION 2007-03-15 23:28:09.30 ------------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  #VM Runtime Configuration File
Command-line arguments:  -os linux -ws gtk -arch x86 #VM Runtime Configuration File

!ENTRY com.aptana.ide.rcp.main 1 0 2007-03-15 23:28:11.21
!MESSAGE (Build 0.2.7.13425) Bound to port 9980

!ENTRY org.eclipse.osgi 2007-03-15 23:28:11.103
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/johnficca/.eclipse/configuration/org.eclipse.osgi/bundles/46/1/.cp/libswt-pi-gtk-3139.so: /home/johnficca/.eclipse/configuration/org.eclipse.osgi/bundles/46/1/.cp/libswt-pi-gtk-3139.so: wrong ELF class: ELFCLASS32
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:381)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:155)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

```

---

### Post by muncrief on 2007-04-12
To everyone trying to install Aptana -

My original directions no longer seem to work anymore on either Edgy or Feisty, but post #10 by sk8dork above gives directions on how to install Eclipse, and then Aptana as a plugin under it.

Aptana works much better, and has many more capabilities (like realtime CVS version display), under Eclipse. It also doesn't have the high CPU usage that it does when compiled.

The only caveat is that you need to install Sun Java, and then change the Java version Eclipse uses to the Sun version after installing it.

Unfortunately, I have to reinstall Feisty now because I got a little to adventuresome with some 32 bit/64 bit compilations and have really screwed it up. However, when I reinstall I will create a step by step howto on installing the Java, Eclipse, and Aptana IDE for newbies, and to make it easier for all of us. I'll try to have it up by tomorrow.

However, if you're experienced, or a newbie looking for adventure, please try sk8dork's info and links. It's a little terse but I was able to follow it and get Aptana working great!.

---

### Post by rvanderblom on 2007-04-13
Maybe it would be a good idea to remove the first few posts and instead create a post which shows how to install eclipse (I've seen it also in the repositories) and then howto install Aptana as a plugin? 

I've got no experience with installing eclipse using the repository, but installing it directly after first installing java is no prob.

---

### Post by timmie on 2007-04-13
Thanks to all for keeping us updated.

My question for those who got it working now wheather the tooltips and HTML / CSS syntax check in the problems view works.

Keen to hear a statement on this.

---

### Post by muncrief on 2007-04-14
OK, here's the howto I promised. Sorry it took so long but the recent kernel problems took awhile to recover from.

As I said before, compiling Aptana doesn't work anymore, and even if it did running it under Eclipse is much more efficient and functional. Here are the steps I took to install it.


1. Install the version of Java you wish to use. In this example I use Sun Java 6:
[INDENT]**sudo apt-get install sun-java6-jdk**[/INDENT]

2. Now install eclipse:
[INDENT]**sudo apt-get install eclipse**[/INDENT]

3. Don't click on the Eclipse menu item yet!. We need to edit the menu entry for eclipse so it will use the desired Java. If you don't do this it will use Blackdown Java, no matter what "java -version" says. 
	[INDENT]1. Right click over your main gnome menu and Click on "Edit Menus" 
	2. In the left column of the box that pops up click on "Programming"
	3. Now in the right column double click "Eclipse".
	4. Put "/usr/bin/eclipse -vm /usr/lib/jvm/java-6-sun-1.6.0.00/bin/java" in the "Command:" line.
	5. Click "Close", and then "Close" again to exit the main menu editor.[/INDENT]

4. Now run "**eclipse -vm /usr/lib/jvm/java-6-sun-1.6.0.00/bin/java**" from the command line. If you get a message that says "Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root: ...". then just run the following commands after exiting Eclipse to fix things:

    [INDENT][B]sudo touch /usr/local/lib/eclipse/.eclipseextension
    sudo chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    sudo chown root:staff /usr/local/lib/eclipse/.eclipseextension[/B][/INDENT]

5. Now we can use the menu. Select "Programming->Eclipse" to start eclipse.

6. Next we need to set the Java that Eclipse will use for it's projects (Aptana is an Eclipse project). Otherwise it will only use Blackdown Java (regardless of java -version or the VM it is started with).
	[INDENT]1. From the "Window" menu in Eclipse select "Preferences".
	2. Click "Java" to open the java options list and click "Installed JRE's"
	3. Now you can enter as many JRE's as you want and select the default. We'll just enter Java 6, click on the "Add" button.
	4. Enter "/usr/lib/jvm/java-6-sun" in the "JRE home directory:" box and click the "OK" button. Everything else will fill in automatically.
	5. Click the check box by java-6-sun to set it as the default.
	6. Click "OK" to exit Preferences.[/INDENT]

7. From the Help menu in Eclipse, select Software Updates > Find and Install... to open an Install/Update pop-up window.

8. On the Install/Update pop-up window, choose the Search for new features to install option, and click the Next button.

9. Set up a new remote site to scan for updates.
      [INDENT]1. Click the New Remote Site... button to open a New Update Site pop-up window.
      2. On the New Update Site pop-up window, type "Aptana" in the site Name text box.
      3. In the URL text box, type the URL for the Aptana update site: [http://update.aptana.com/update/](http://update.aptana.com/update/) and click OK.
      4. Click the Finish button to open an Updates window. [/INDENT]

10. Now we'll install the Aptana plugin
      [INDENT]1. On the Updates window, check the Aptana box, and click the Next button.
      2. Choose the option to accept the terms of the license agreement, and click the Next button.
      3. Click the Finish button.
      4. Click the Install All button. 
      5. After Eclipse installs the Aptana plug-in, follow the prompts to shut down and re-start Eclipse.[/INDENT]

11. Finally we need to set the Ecplise Perspective to Apatana
	[INDENT]In the upper right hand corner of the Eclipse IDE there is a little window icon, this is used to select perspectives. Click it, and if you see "Aptana" just select it. Otherwise select "Other..." to open the Select Perspective pop-up window and select Aptana from there. That's it!.[/INDENT]


OK, hopefully you have a fully functional Eclipse/Aptana system now. Have fun!

---

### Post by Damiel on 2007-04-20
thank you, muncrief. trying to install aptana as a standalone app on feisty was getting me nowhere.

---

### Post by TheFuzzy0ne on 2007-04-23
Hi everyone. This is quite an interesting thread, so many thanks to all involved.

I have no had any problems installing Aptana as a standalone application. Well, until now... I seem to have an issue with Frostwire not being happy with running Java5. I think I need a method of telling Frostwire which version of Java it should be using, as I have both installed.

I have Eclipse, and I've used Aptana as a plugin. My personal preference is to use Aptana as a stand alone application. I believe it's quicker, and less bulky. Eclipse as an IDE is fantastic, but Aptana as a pure Web IDE, I think is even better. Also, Aptana as a standalone application, comes with some very useful references manuals for JavaScript, HTML, CSS and more, and all of the reference manuals have good examples in them. The plugin doesn't seem to have any of these integrated. If anyone can suggest an alternative, or find a way to port the reference manuals over from the standalone application, I'd be more than happy to make the switch.

Did you know you can install Aptana straight from the repositories? This is how I installed Aptana originally. Check out the forum thread by afterxleep: [http://www.aptana.com/forums/viewtopic.php?t=520](http://www.aptana.com/forums/viewtopic.php?t=520) . He's made a repository that takes most of the grunt out of installing Aptana manually, and it seems to work great, other than the problem I mentioned.

I'm open to suggestions as to what I should do, and I also just wanted to add another side to the debate. :)

I am not an experienced Linux user as such. I can achieve most simple things, but as for configuring things like Java, I'd be better off piloting a jumbo jet!

All the best.

Daz

---

### Post by smdepot on 2007-04-24
I was able to install Aptana with no issues on Feisty 7.04. I wrote a quick How to on the Aptana forums. Obviously as you all know in the new Feisty repositories the Mozilla and libswt3.1-gtk-java seem to be missing. This can be solved by simply grabbing them from the edgy repositories. It creates no conflicts and everything is seamless from there. Here's how I did it.

Edit /etc/apt/sources.list by issuing the following command 

```
sudo gedit /etc/apt/sources.list
```

insert the following

```
deb http://ubuntu.mylemontree.com/packages/ aptana-beta/
deb http://de.archive.ubuntu.com/ubuntu/ edgy universe
```

Then run update by issuing the following command 

```
sudo apt-get update
```

Now run

```
sudo apt-get install mozilla libswt3.1-gtk-java
```

Now you can install Aptana as the required dependencies will have been met 

```
sudo apt-get install aptana
```

[*orignal post]("http://www.aptana.com/forums/viewtopic.php?p=5092#5092")

---

### Post by barmazal on 2007-04-24
isn't that easier to install Aptana via Eclipse? Takes me 1 minute and no errors

---

### Post by smdepot on 2007-04-24
I'm not sure its all about speed. I tried the eclipse plugin and didn't see the ability to have a ftp / sftp session. I rely on it pretty heavily myself so I needed Aptana. Also, I simply like Aptana more. There are a few differences that I find important. (yes I know they look a lot alike).

The point though is to have the option of either or. Because, after all, isn't Linux all about the ability to customize your environment to your taste?

---

### Post by TheFuzzy0ne on 2007-04-30
Hi all.

Sorry for the dealy in my response. I had the page of my previous post bookmarked, and checked it daily. What I didn't realise, is that my post was the last post on the page, and any replies were added to page 3... I only found that out today. Man, do I feel dumb!(?)

I actually have both eclipse (with Aptana plugin), and Aptana standalone. As Aptana is aimed at Web development, it's very useful to me. However, I am starting to get into Java, so Eclipse is becoming quite useful to me also. I am still convinced that that standalone verion of Aptana is more lightweight, faster and less error prone than the plugin version. Also, as it contains reference manuals for JavaScript, CSS, HTML and the likes I can't complain. 

I know I can find these references online, but having them stored on your machine makes things a lot faster, especially when you're impatient like me. :lolflag: 

For Web developers who don't already know this, Adobe have made a nice plugin called JSEclipse. It's still in the Beta stage, but offers a few nice features that Aptana does not. You can find out more about JSEclipse [here]("http://www.interaktonline.com/Products/Eclipse/JSEclipse/Overview/"). You do need to sign up, but you won't get spam if you don't want it, JSEclipse works well with Eclipse, Eclipse with the Aptana plugin and Aptana standalone.

All the best.

Daz.

---

### Post by cisforcojo on 2007-05-03
It appears: deb [http://ubuntu.mylemontree.com/packages/](http://ubuntu.mylemontree.com/packages/) aptana-beta/
is no longer working:

```

Failed to fetch http://ubuntu.mylemontree.com/packages/aptana-beta/Packages.gz  
301 Moved Permanently


```

---

### Post by shoq on 2007-05-05
New to Linux, and having aptana drama. 

Installed Aptana with some shell script I cannot find again again. It may have been dated.  Anyway, everything worked fine, UNTIL I decided to make a new workspace outside the aptana folder. THEN I get that error telling me to see the metadata/log  file.

Can someone explain the steps clearly?  I have the Java 1.6 and the most recent firefox.  What now?

Sorry I am a newb.. but. well.. I'm a newb.  If you can clearly post this here, I would gladly post it in the aptana forum where this issue seems to be raging, as well.

Thanks

---

### Post by TheFuzzy0ne on 2007-05-08
> **cisforcojo said:**
> It appears: deb [http://ubuntu.mylemontree.com/packages/](http://ubuntu.mylemontree.com/packages/) aptana-beta/
is no longer working:

```

Failed to fetch http://ubuntu.mylemontree.com/packages/aptana-beta/Packages.gz  
301 Moved Permanently


```

Oh dear. I apologize for that. 

I spotted this article. [http://afterxleep.com/blog/2007/05/02/new-repository-change-your-sources/](http://afterxleep.com/blog/2007/05/02/new-repository-change-your-sources/) . Basically, it looks like he's registered a new domain name, so you'll need to read through the instructions and change your repository sources.

I looked a little more, and spotted this: [http://afterxleep.com/blog/2007/05/03/aptana-m8-is-almost-here/](http://afterxleep.com/blog/2007/05/03/aptana-m8-is-almost-here/)

It might be worth keeping an eye on :)

---

### Post by kroenecker on 2007-05-13
This will allow you to use Aptana:

1) sudo apt-get install sun-java6-jdk
2) Download the linux package from the Aptana website.
3) Unpack the package and run the executable using ./Aptana -vm /usr/lib/jvm/java-6-sun-1.6.0.00/bin/java

Done.

---

### Post by techie99 on 2007-07-02
[SIZE="4"]**Installing Aptana(Eclipse)+RDT+Radrails**[/SIZE]

[SIZE="4"][B]
If you wish to use either Eclipse or Aptana ***without*** ruby/rails support you can just install as per the 1000s of other posts on the matter, and you shouldn't have any issues.[/B][/SIZE]

For some reason the RDT/Rails Plugins don't like gij and although they appear to be installed, are not available from within the IDE.

Under normal circumstances **sudo update-alternatives --config java** should resolve any issues with multiple command choices. (i.e. 3 versions of java all executed with the synax **java**)

However, the command Eclipse is actually a shell script that looks for a environment variable called JAVA_HOME set to your preferred jvm.  In the event it isn't set it looks through the default jvm directory (/usr/lib/jvm) for the first jvm that is compatible, since gij is installed by default in *buntu, and G("gij-wrapper") comes before S ("sun-java") it is always chosen.  

This is how I got my Feisty/Aptana(Eclipse)/Rails Setup working.....

Run through the usual motions of installing  Eclipse or Aptana.  ([http://www.aptana.com](http://www.aptana.com))

I prefer installing Eclipse (via Synaptic or **sudo apt-get install eclipse**) due to the fact that it's available from a repository so I don't have to worry about where all of its bits and pieces are installed, but to each their own.

Now for the Magic!!!

First we install the Sun version of Java:
```
sudo apt-get install sun-java6-jdk
```

Finally we set our environment variable to the sun java so when Eclipse/Aptana start up, they use our preferred JVM:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
```


TADA!!!

I hope this was useful to someone, this is the first tutorial I've written.....
I apologize for the length of my post, however, posting the resolution without explanation does no one any good.  So this post is for all my peeps out in nooB-land!!!

---

### Post by 23meg on 2007-07-17
On Feisty with Sun JVM 1.6, Aptana Milestone 8 seems to work by just extracting the archive and running the executable. Sweet.

---

### Post by albertcito on 2007-12-05
The Aptana_IDE_Setup.bin is delete in all pages web!!!!!

:S


Where download Aptana_IDE_Setup.bin for installin???????????'


¿?¿?¿???

:(


Sorry, no se Ingles!!!!!!! 

:S

---

### Post by motin on 2008-02-15
I can't install the Subversive plug-in (I want to try it to see if it is not as buggy as subclipse). Where do I get the missing dependency "org.eclipse.ui" - anyone have an idea? It is not [http://update.eclipse.org/updates/3.2/](http://update.eclipse.org/updates/3.2/) ...

Thanks!

---

### Post by lmdavid on 2008-11-25
_Install Aptana IDE on Hardy AMD64_
Hi,

I installed Aptana using the plugin over Eclipse 2.2 (eclipse-gcj    3.2.2-5ubuntu2).
I was stuck on the following message:
org.eclipse.swt.SWTError: No more handles [NS_InitXPCOM3 /usr/lib/firefox]

After having tried different solutions (using mozilla-gtk, libxul, changing the MOZILLA_FIVE_HOME), I found out that:
* Even if you set MOZILLA_FIVE_HOME in the environment variable, it is then reset to another value in  /usr/bin/eclipse startup script (most likely to /usr/lib/firefox).
* if MOZILLA_FIVE_HOME=/usr/lib/xulrunner/ then it is working !

To make it work, I had to change slightly the /usr/bin/eclipse in order to point to the right folder ( /usr/lib/xulrunner/).

I hope this can help.

---

### Post by TANGO! on 2009-01-09
I got Aptana running with RadRails, ruby, gems and everything working perfectly on Intrepid Ibex.  To do this I followed the instructions on this thread to get the JRE working, then I downloaded the Linux file from the Aptana website, and then I used a root console to run the program (I also created an executable with chmod to make it easier).  

Only when I ran Aptana with a root console I was able to get the updates and plugins from their site, so now I have RadRails, the PHP plugin, the Iphone plugin, etc etc etc.

I have not been able to install the Aptana plugin in Eclipse, it gives me some odd error.  If anybody knows why is that happening, please let me know.

---

### Post by LaSlow on 2011-05-28
While searching for Aptana Studio 3 installation and configuraton, i found the following blog:
[http://thomas.deuling.org/tag/aptana-studio/]("http://thomas.deuling.org/tag/aptana-studio/")

Maybe it helps also other users :)

---

### Post by Wesley The First on 2011-07-04
> **LaSlow said:**
> While searching for Aptana Studio 3 installation and configuraton, i found the following blog:
[http://thomas.deuling.org/tag/aptana-studio/]("http://thomas.deuling.org/tag/aptana-studio/")

Maybe it helps also other users :)
That doesn't help much, has anyone been able to install Aptana Studio 3 on 11.04 64bit?

---

