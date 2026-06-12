---
title: "How to install Adobe Flex Builder on Ubuntu 8.04 [64-bit]"
date: 2008-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxed on 2008-10-14
[color=red]**UPDATED:**[/color] *20/02/10*
This guide has been updated for Ubuntu 9.10 (karmic).  Please note that this guide is only for 64-bit users.  If you are running a 32-bit operating system then you won't need quite a few of the steps listed here.

Adobe's website lists some basic instructions for installing Flex Builder on a 64-bit system but it's a long way from being a complete guide.  If you're new to Linux or don't have the patience for a complex installation my advice is to walk away now.  This is not a simple installation and will take quite a bit of time to complete.

One of the main difficulties involved in the installation is that it requires the installation of a few 32-bit applications.  If your system is set up like mine you probably already have a 64-bit version of Firefox, Eclipse and Sun's JRE installed.  You also most likely have other applications that depend on those 64-bit versions so removing the 64-bit versions and replacing them with 32-bit versions isn't an option. The alternative is to install both 32 and 64-bit versions of those applications on the same system, but getting them to coexist creates an entirely new set of problems.

The following guide will walk you through installing the 32-bit versions of Firefox, Eclipse and Sun's JRE in a way that will also allow you to keep your existing 64-bit versions.  Before proceeding you'll need to download the following files.  Make sure to download them to your desktop as the steps below assume that these files can be found in your desktop folder.


[list=]
[*][_Adobe Flex Builder_](http://labs.adobe.com/downloads/flexbuilder_linux.html)
[*][_Eclipse 3.3.2 32-bit_](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/europa/winter/eclipse-java-europa-winter-linux-gtk.tar.gz) - The current version of Flex Builder will only work with Eclipse v3.3.x (europa).  You can install Flex Builder in v3.4 but the mxml editor will not function properly.
[*][_Firefox 3.6 32-bit_](ftp://ftp.mozilla.org/pub/firefox/releases/latest-3.6/linux-i686/en-US/)
[/list]


Since this guide is geared towards installing Flex Builder for Air application development I'd highly recommend installing the Air runtime before proceeding.  [Visit this link for a complete guide on how to install Air on 64-bit systems.](http://ubuntuforums.org/showthread.php?t=941093)


[list=1]
[*]Step one, put on a big pot of coffee because this is going to take a while. :)
[*]Install the following packages if they're not already installed.
```

sudo apt-get install ia32-libs ia32-sun-java6-bin

```
[*]We need to temporarily change the default JRE to the 32-bit version.  First let's find out where your java symlink points to.
```

readlink -e /usr/bin/java

```
The command above will display something like the following:
```

/usr/lib/jvm/java-6-sun/jre/bin/java

```
Write down the path that's displayed in your terminal.  If it's already set to the ia32-java-6-sun path then you can just skip the next step.


[*]Now set your 32-bit version of java as the default jre.
```

sudo update-alternatives --set java /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

```
[*]Now we need to extract the 32-bit versions of Eclipse and Firefox.  For this guide we'll use ~/Flex as our default installation directory.
```

mkdir ~/Flex
tar -xf ~/Desktop/firefox*.bz2 -C ~/Flex
tar -xf ~/Desktop/eclipse*.gz -C ~/Flex

```
[*]Let's make sure that we have the 32-bit versions of firefox and eclipse installed. This may sound like a pointless step but accidentally clicking on the wrong link can lead to a ton of wasted time and frustration. :)
```

file ~/Flex/firefox/firefox-bin
file ~/Flex/eclipse/eclipse

```
[*]If they're both listed as "ELF 32-bit LSB executable" then continue to the next step.  Otherwise you probably downloaded the wrong version which means it's time to start over...and possibly another pot of coffee.
[*]Run firefox and make sure it opens successfully.
```

~/Flex/firefox/firefox

```
[*]Run eclipse and make sure it opens successfully.
```

~/Flex/eclipse/eclipse

```
[*]The first time you run eclipse you will be asked to select a workspace path.  Enter the following path when prompted (replacing YourUserName with your own).
```

/home/YourUserName/Flex/workspace

```
[*]Assuming no errors are displayed in the terminal you should now be able to install Flex Builder so make the bin file executable.
```

chmod +x ~/Desktop/flexbuilder*.bin

```
[*]And now start the installation.  Make sure that firefox, eclipse and all java apps are closed before proceeding.
```

~/Desktop/flexbuilder*.bin

```
[*]When you are prompted to select the Flex Builder installation directory enter the following (replacing YourUserName with your own).
```

/home/YourUserName/Flex/Flex_Builder

```
[*]When you are prompted to select the 32-bit eclipse directory enter the following (replacing YourUserName with your own).
```

/home/YourUserName/Flex/eclipse

```
[*]Follow the on-screen instructions to complete the installation.  The JSEclipse plugin is optional but I chose to install it anyway.
[*]Now we need to copy the **DEBUG** flash plugin to the 32-bit version of firefox.  This is different from the standard flash plugin.
```

cp ~/Flex/Flex_Builder/Player/linux/install_flash_player_9_linux/libflashplayer.so ~/Flex/firefox/plugins

```
[*]Edit the eclipse.ini file so that it always uses the 32-bit version of java.
```

gedit ~/Flex/eclipse/eclipse.ini

```
[*]Add the following commands to the ini file.  Make sure to enter them on the first line.  The instructions on Adobe's website will tell you to place it at the end of the file.  IGNORE THOSE INSTRUCTIONS.  If you place it at the end of the file it will have no effect.  You must also enter the commands on two separate lines.  If you enter it as one line it will have no effect either.
```

-vm
/usr/lib/jvm/ia32-java-6-sun/jre/bin/java

```
The resulting file would look something like this:
```

-vm
/usr/lib/jvm/ia32-java-6-sun/jre/bin/java
-showsplash
org.eclipse.platform
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m

```
[*]Click save and close gedit.
[*]Change back to your default jre using the path you wrote down earlier.  You should probably update javaws as well just to be safe.
```

sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
sudo update-alternatives --set javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws

```
[*]Now we're going to create an application launcher for Flex Builder on your development menu.
```

sudo gedit /usr/share/applications/flexbuilder.desktop

```
[*]Copy ALL of the following and paste it into gedit (replace YourUserName with your own).
```

[Desktop Entry]
Name=Adobe Flex Builder
Comment=Flex Builder plugin for Eclipse IDE
Exec=/home/YourUserName/Flex/eclipse/eclipse
Icon=/home/YourUserName/Flex/eclipse/plugins/org.eclipse.platform_3.3.3.r33x_r20080129/eclipse48.png
Terminal=false
Type=Application
Categories=Development;
StartupNotify=true

```
[*]Click save and close gedit.
[*]I would highly recommend restarting your pc at this point just to be safe.
[*]Now if everything went well you should be able to open Flex Builder from your Applications menu.  Click on your Applications menu, select Development, and click Adobe Flex Builder.
[*]If it opens then you have one more step.  We need to set the default browser to the 32-bit version of Firefox that you installed.  Click on Window then click Preferences.  Expand the General menu.  Click on Web Browser.  Check the box labeled 'Use external Web browser'.  Click New.  Enter the following information.
```

Name: Firefox
Location: /home/YourUserName/Flex/firefox/firefox
Parameters: %URL%

```
[*]Click OK.  Check the box next to Firefox and click OK.
[/list]


**Update Flex and Air sdk**
The following steps will walk you through the process of installing the latest versions of the Flex and Air sdk and how to enable them in Eclipse.  Make sure to download both files to your Desktop folder.
[list=1]
[*]Download the latest Flex sdk from the nightly section.
[list=]
[*][Flex 3](http://opensource.adobe.com/wiki/display/flexsdk/Download+Flex+3)
[*][Flex 4](http://opensource.adobe.com/wiki/display/flexsdk/Download+Flex+4)
[/list]
[*]Download the latest AIR sdk.
[list=]
[*][Air 1.5](http://www.adobe.com/products/air/tools/sdk/)
[*][Air 2](http://labs.adobe.com/downloads/air2.html)
[/list]
[*]Extract the flex sdk.
```

mkdir ~/Flex/latest_flex_sdk
unzip -o -q ~/Desktop/flex_sdk*.zip -d ~/Flex/latest_flex_sdk

```
[*]Extract the air sdk.
```

tar --overwrite -xf ~/Desktop/AdobeAIRSDK*.tbz2 -C ~/Flex/latest_flex_sdk

```
[*]Try to remove the adl_lin and adt_lin files if they exist.  It's possible that they may not be present in that folder so don't worry if the commands below display any errors.
```

rm ~/Flex/latest_flex_sdk/bin/adl_lin
rm ~/Flex/latest_flex_sdk/bin/adt_lin

```
[*]Create the new adl_lin and adt_lin files.
```

rename s/adl/adl_lin/ ~/Flex/latest_flex_sdk/bin/adl
rename s/adt/adt_lin/ ~/Flex/latest_flex_sdk/bin/adt

```
[*]Create a symlink for the linux directory.
```

ln -s ~/Flex/latest_flex_sdk/runtimes/air/linux ~/Flex/latest_flex_sdk/runtimes/air/Linux

```
[*]Open Eclipse
[*]Click Window > Preferences
[*]Expand the Flex folder
[*]Click Installed Flex SDKs
[*]Click Add
[*]Enter /home/YourUserName/Flex/latest_flex_sdk as the location
[*]Enter Nightly as the name (if you don't plan on updating very often then just keep the auto-generated name)
[*]Click OK
[*]Check the box next to Nightly to use this version by default, then click Apply.
[/list]


[**HELLO WORLD Air Application**](http://livedocs.adobe.com/flex/3/html/FBHelloWord_1.html)
[list=1]
[*]To create a new flex project click on File > New > Project...
[*]Click Flex Builder > Flex Project > Next
[*]Type a project name and then select Desktop Application.
[*]Click Finish.
[*]Click Yes if you are prompted to "Switch to Flex Development Perspective?"
[*]In the "Flex Navigator" pane, expand the src folder, right click on both files (.mxml and .xml) and select "Open with > Text Editor".
[*]Paste the following into the .mxml file replacing all of the existing content.
```

<?xml version="1.0" encoding="utf-8"?>
<mx:WindowedApplication xmlns:mx="http://www.adobe.com/2006/mxml" layout="absolute" title="Hello World">
    <mx:Style>
        WindowedApplication
        {
            background-color:"0x999999";
            background-alpha:"0.5";
        }
    </mx:Style>
    <mx:Label text="Hello World" horizontalCenter="0" verticalCenter="0"/>
</mx:WindowedApplication>

```
[*]In the .xml file select the code beginning with <title> and ending with </transparent>. Paste the following over the selected code.
```

		<title>Hello World</title>
		<systemChrome>none</systemChrome>
		<transparent>true</transparent>

```
[*]Click save then click debug (or press F11).  A new window should appear with Hello World in the title bar and centered in the body of the window.
[/list]


**Notes**
If you discover that your mouse has a problem clicking on some of the Next and Finish buttons in Eclipse then simply click on the button to select it and then press enter.  Not sure if I'm the only one experiencing this issue but if you do encounter this problem it's fairly easy to work around it.

---

### Post by andyrue304 on 2008-10-18
Thanks for this. I was planning on attempting this now, but it's 12:50 am atm and I think I'll need some sleep first!

---

### Post by Karlabuzer on 2008-10-26
Very good HowTo, thank you! But... 

-> 33. If it opens ...

It doesnt :( Everything was good till the p.33.

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xf3c9fc69, pid=6684, tid=4157987728
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b23 mixed mode, sharing linux-x86)
# Problematic frame:
# C  [libxul.so+0x948c69]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---

### Post by linuxed on 2008-10-26
The 32-bit version of eclipse may not be using the correct version of java.  Type the following:
```

/usr/lib/jvm/ia32-java-6-sun-1.6.0.07/jre/bin/java -version

```
It should output the following:
```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```
If you can confirm that your 32-bit version of java is the same as above then double check the eclipse.ini file.
```

gedit /usr/lib32/eclipse/eclipse.ini

```
It needs to look exactly like the following.
```

-vm
/usr/lib/jvm/ia32-java-6-sun-1.6.0.07/jre/bin/java
-startup
plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vmargs
-Xms40m
-Xmx256m

```
Make sure that the -vm is the first line in the file and that the path to your 32-bit java appears on the second line.  If you still can't launch Flex Builder from your Development menu try opening the 32-bit eclipse as root.  The problem may be related to a permissions issue.
```

sudo /usr/lib32/eclipse/eclipse

```

---

### Post by Karlabuzer on 2008-10-27
thanks a lot for your answer!

I checked version and eclipse.ini - everething the same as you wrote.

```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```
-------------
```

-vm
/usr/lib/jvm/ia32-java-6-sun-1.6.0.07/jre/bin/java
-startup
plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vmargs
-Xms40m
-Xmx256m

```

Trying to start as root returns following

```

xxx@xxx:~$ sudo /usr/lib32/eclipse/eclipse
[sudo] password for xxx:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xf3c16c69, pid=6027, tid=4158475152
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b23 mixed mode, sharing linux-x86)
# Problematic frame:
# C  [libxul.so+0x948c69]
#
# An error report file with more information is saved as:
# /home/vit/hs_err_pid6027.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

:(

---

### Post by linuxed on 2008-10-27
It looks like there is a problem with one of the libraries you extracted to your lib32 folder.  Enter the following commands:
```

sudo -s
rm /usr/lib32/libjemalloc.so
rm /usr/lib32/libmozjs.so
rm /usr/lib32/libsqlite3.so
rm /usr/lib32/libsqlite3.so.0
rm /usr/lib32/libxpcom.so
rm /usr/lib32/libxul.so
rm /usr/lib32/libnssckbi.so
rm /usr/lib32/libpyxpcom.so
file-roller ./xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb

```
Then try re-extracting the following files from the xulrunner package into your /usr/lib32 folder.  Make sure you are using the 1.9 version of xulrunner.  You might try extracting the libnssckbi and libpyxpcom files from the xulrunner package as well.  
```

/usr/lib/xulrunner-1.9b5/libjemalloc.so
/usr/lib/xulrunner-1.9b5/libmozjs.so
/usr/lib/xulrunner-1.9b5/libnssckbi.so
/usr/lib/xulrunner-1.9b5/libpyxpcom.so
/usr/lib/xulrunner-1.9b5/libsqlite3.so
/usr/lib/xulrunner-1.9b5/libsqlite3.so.0
/usr/lib/xulrunner-1.9b5/libxpcom.so
/usr/lib/xulrunner-1.9b5/libxul.so

```

---

### Post by Karlabuzer on 2008-10-27
There wasnt libpyxpcom.so ...

I re-extracted all but nothing changed :(

I tried to start after removing files and eclipse was started, but when I extrated files back to /usr/lib32 it cant start again with the same error.

```

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xf407bc69, pid=9841, tid=4158708624
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b23 mixed mode, sharing linux-x86)
# Problematic frame:
# C  [libxul.so+0x948c69]
#
# An error report file with more information is saved as:
# /home/vit/all/hs_err_pid9841.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

Btw i have a little another url in xulrunner package

```

/usr/lib/xulrunner-1.9.0.3/libjemalloc.so
/usr/lib/xulrunner-1.9.0.3/libmozjs.so
/usr/lib/xulrunner-1.9.0.3/libnssckbi.so
/usr/lib/xulrunner-1.9.0.3/libpyxpcom.so
/usr/lib/xulrunner-1.9.0.3/libsqlite3.so
/usr/lib/xulrunner-1.9.0.3/libsqlite3.so.0
/usr/lib/xulrunner-1.9.0.3/libxpcom.so
/usr/lib/xulrunner-1.9.0.3/libxul.so

```

---

### Post by linuxed on 2008-10-27
Sorry, I posted the wrong xulrunner path.  The one you posted (/usr/lib/xulrunner-1.9.0.3/) is correct.  The files from the xulrunner package are used by the 32-bit version of firefox.  You may want to try removing the xulrunner related files from your lib32 folder and then check whether firefox still has access to all of it's required libraries.
```

ldd /usr/lib32/firefox/firefox-bin

```
More than likely it's going to say not found for a few libraries.  Either way you can still run eclipse without the use of a 32-bit version of firefox.  I'm not too sure why those files would be causing that error to occur on your system, but the only other suggestion I have is to run eclipse without the xulrunner library files in your lib32 folder.

---

### Post by Karlabuzer on 2008-10-29
Thanks a lot! It works!

I've copied only 4 files from xulrunner package

```

        libjemalloc.so
        libxul.so
        libmozjs.so
        libxpcom.so

```

About MXML editor:

Window -> Preferences -> General -> Editors -> File Associations -> *.mxml

Add your preferred editor and make it Default. It's enough for me ;-)

Thank you again :)

---

### Post by peddy on 2008-11-03
Perfect! Thanks!

---

### Post by peddy on 2008-11-03
sorry, double post...

---

### Post by andresmh on 2008-11-03
you might want to rename this to 8.04 and 8.10 :-)

Following your instructions I was able to get it to work in Intrepid. I did run into the same problems the previous poster reported but it works well with Firefox 64-bit which now can run Flash. Maybe at the time of your post there wasn't a Flash plugin for FF 64-bit?

Thanks!

---

### Post by peddy on 2008-11-03
I also had the xulrunner error, and I had to change references of

/usr/lib/jvm/ia32-java-6-sun-1.6.0.07/jre/bin/java

to


/usr/lib/jvm/ia32-java-6-sun-1.6.0.10/jre/bin/java

Cheers :)

---

### Post by ItecKid on 2008-11-07
Do this work in 8.10?  If I make the file executable (with chmod +x) and then try to install, it returns:

```
bash: ./flexbuilder_linux_install_a4_081408.bin: /bin/sh: bad interpreter: Text file busy

```

And if I execute it from the shell with:

```
sh flexbuilder_linux_install_a4_081408.bin
```

It returns:

```
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

```

Thoughts?

---

### Post by linuxed on 2008-11-07
> **andresmh said:**
> Following your instructions I was able to get it to work in Intrepid. I did run into the same problems the previous poster reported but it works well with Firefox 64-bit which now can run Flash. Maybe at the time of your post there wasn't a Flash plugin for FF 64-bit?

Flex Builder requires the flash debug plugin for FF.  As far as I know there isn't a 64-bit version of the debug plugin.  The standard flash plugin comes in a 64-bit version but the last time I checked the debug plugin only came in a 32-bit version.

---

### Post by linuxed on 2008-11-07
> 
I also had the xulrunner error, and I had to change references of

/usr/lib/jvm/ia32-java-6-sun-1.6.0.07/jre/bin/java

to

/usr/lib/jvm/ia32-java-6-sun-1.6.0.10/jre/bin/java

I think I may have overlooked one of the ia32 java folders.  Apparently there is an ia32 java folder that's included in the package that links to the folder with the version number it's name.  If that folder is used instead then it should eliminate the need to change the 32-bit java path each time a new version of the package is released.  I'll edit the instructions to use this path instead.  You may want to edit your eclipse.ini file to the use the following path.

/usr/lib/jvm/ia32-java-6-sun/jre/bin/java

---

### Post by linuxed on 2008-11-07
> **ItecKid said:**
> 
```
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

```
Thoughts?
It sounds like it can't find your 32-bit version of java.  Try changing the java paths to the following.
```

sudo rm /usr/bin/java
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/bin/java /usr/bin/java
sudo gedit /usr/lib32/eclipse/eclipse.ini

-vm
/usr/lib/jvm/ia32-java-6-sun/jre/bin/java

sudo chmod +x ./flexbuilder_linux_install_a4_081408.bin
sudo ./flexbuilder_linux_install_a4_081408.bin

```

---

### Post by ItecKid on 2008-12-01
The link above to get xulrunner is no longer working, where to download it now?

---

### Post by linuxed on 2008-12-01
Here's a list of download locations:

[http://packages.ubuntu.com/hardy-updates/i386/xulrunner-1.9/download](http://packages.ubuntu.com/hardy-updates/i386/xulrunner-1.9/download)

---

### Post by krange on 2009-01-03
This is great tutorial,. thanks so much! Got everything setup in 8.10 as well. The only issue I'm having when I go to change my Firefox version in Window - Preferences - General - Web Browser, Eclipse crashes.

Any ideas?

---

### Post by linuxed on 2009-01-03
Make sure that your 32-bit version of Firefox has all of it's required libraries.  Run "ldd /usr/lib32/firefox/firefox-bin" and make sure that none of the libraries say 'not found'.  Then try opening the 32-bit Firefox from the command line and see if it displays any errors "/usr/lib32/firefox/firefox-bin".  You might try running eclipse from the command line as well and see if it throws any errors when it crashes.

---

### Post by linuxed on 2009-01-03
Ignore my post above.  I was able to reproduce the crash you described.  As it turns out the problem is related to the libxul.so file.  To fix this issue simply download the latest xulrunner-1.9 package and extract the libxul.so file into your /usr/lib32 folder.  Make sure to overwrite the existing file.  [**Here's a list of download locations.**](http://packages.ubuntu.com/intrepid-updates/i386/xulrunner-1.9/download)

---

### Post by krange on 2009-01-03
awesome - that fixed it. thanks much

---

### Post by gurtnamona on 2009-01-11
Awesome HowTo but I have one issue:

Everything appears to have installed correctly but when I start a new Flex project, I get an "Failed to open editor: Assertion Failed" error when attempting to view the mxml file. The only departure I made from the instructions was with respect to the libxul.so file. What can I check to solve this? Should I be using a older version of Eclipse?

Many thanks,

Colin

---

### Post by linuxed on 2009-01-11
For some reason the mxml editor doesn't seem to work in Flex Builder so you'll have to use the text editor instead.
> 
There is one additional step that may be required before you can develop any Adobe Air applications. For some reason on my system the editor threw an error the first time I tried to use the MXML editor. As a workaround you can always use the text editor instead. First close the .mxml file's tab. Then in the 'Flex Navigator' tab right click on the .mxml file entry, select open with, then select 'text editor'.


---

### Post by JoelJohnson on 2009-02-01
Didn't have a single problem installing. I have a pretty much fresh install of Ubuntu 8.10, I pretty much only had Adobe Air installed when I began installing Flex Builder.

When I try to run Eclipse I have a problem...
The splash screen came up, prompted me for where I wanted my workspace to be, after I chose a location Eclipse closed.

I ran it from a terminal to find the error:

```
joel@laptop:~$ /usr/lib32/eclipse/eclipse
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xd163637d, pid=4887, tid=4158684048
#
# Java VM: Java HotSpot(TM) Server VM (11.0-b15 mixed mode linux-x86)
# Problematic frame:
# C  [libxul.so+0x94a37d]
#
# An error report file with more information is saved as:
# /home/joel/hs_err_pid4887.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

Any suggestions of what I can do to make this work?

I've gone through all the posts in this thread, and none of the suggestions worked.
I even downloaded the *.3 version of XulRunner (rather than the latest *.5) and dropped all the *.so files in the lib32 folder. Still no luck.

---

### Post by linuxed on 2009-02-02
> **linuxed said:**
> As it turns out the problem is related to the libxul.so file.  To fix this issue simply download the latest xulrunner-1.9 package and extract the libxul.so file into your /usr/lib32 folder.  Make sure to overwrite the existing file.  [**Here's a list of download locations.**](http://packages.ubuntu.com/intrepid-updates/i386/xulrunner-1.9/download)

The instructions above should fix the problem.  Make sure to download the latest version of xulrunner-1.9.  If that still doesn't fix it you can always try the libxul.so file that's included in firefox.  Try copying libxul.so from /usr/lib32/firefox to /usr/lib32.

---

### Post by vaibhav.nirma on 2009-02-24
Voila , it worked perfectly dude..........
I have to just removed the 'ia32' during the installation though.
When i did without removing the same it siad that Java VM not found in path.
I went to the directory, checked, and changed accordingly....
Installation was carried out perfectly......
Thanks a lot Bro.
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by vaibhav.nirma on 2009-02-24
Also xulrunner is not available on the link you have mentioned, it can be downloaded from here,
[http://mirror.unmul.ac.id/ubuntu/pool/main/x/xulrunner-1.9/](http://mirror.unmul.ac.id/ubuntu/pool/main/x/xulrunner-1.9/)

---

### Post by linuxed on 2009-03-26
**UPDATE**
The guide has now been updated for Ubuntu 8.10 [64-bit].  I've also created a 32-bit libs package to help simplify the installation which is attached to the first post.

**Note to Moderator**
If a moderator happens to see this post please update the title of this thread to read 8.10 instead of 8.04.  Thanks in advance.

---

### Post by gurtnamona on 2009-04-08
This HowTo worked great for 8.10. One thing that I may be missing: I have seen in tutorials for Adobe Flex a "Data" menu when in the Flex Perspective. This Data menu is on the top menu bar between the Project and Run menus. For my installation however, I have no Data menu. Is this something that should be available or am I missing something?

I know that this is probably outside the scope of this HowTo but any assistance would be greatly appreciated.

Thanks.

---

### Post by linuxed on 2009-04-08
The Data menu may only be available in Eclipse v3.4.  Currently the Flex plugin for Linux will only work in Eclipse v3.3.  I've previously installed it in v3.4 but the mxml editor doesn't work so you're basically limited to typing in a standard text editor.  The tutorials you saw might have been referring to Flex Builder on a Windows platform.

---

### Post by OmegaWarrior on 2009-09-13
Does anyone know why java needs to be installed for flex?  the whole reason I wanted to learn flex was to get AWAY from java.

---

### Post by linuxed on 2009-09-14
You need java in order to run Eclipse which is written mainly in java.  Flex Builder on Linux is simply a plugin for Eclipse.

---

### Post by OmegaWarrior on 2009-09-14
so if I use a different IDE to make flex apps, then I don't need it?  It seems like that could simplify this process quite a bit.

---

### Post by jap1968 on 2009-09-17
I have some blog entries about preparing a Flash development framework on Linux.

The setup is based on Eclipse 3.5 and AXDT as well as on the open source Flex SDK provided by Adobe.

You can have a look at the blog entries here:
[LIST]
[*]Setup [Eclipse + AXDT on Linux]("http://netpatia.blogspot.com/2009/09/flash-development-on-linux.html")
[*]Compile [your first Flash program on Linux]("http://netpatia.blogspot.com/2009/09/flash-development-on-linux-ii.html")
[/LIST]

---

### Post by mhuggins on 2009-12-06
Huge thanks!  Your effort is much appreciated, Linuxed.  I didn't need the ia32-flex-libs.deb package, but otherwise the step-by-step was perfect on Ubuntu 9.10 64-bit. :)

---

### Post by andxlr on 2010-02-15
Hi , first at all , Thanks a lot for the tutorial.
 I did it exactly with your points , and the Flex Builder is working but there is still a problem.
 I get every time Eclipse crash when I open some java Code in Java Perspective,
 then I go to Flex Perspective and try to open Flex Code.
 Did any one of you have this before ? ...google didn't say any thing :(
 This is my part ~/workspace/.matadata/.log :
Thanx a lot for any help ! 
In the attachment you can find  log file, here just a part :

```
!SESSION 2010-02-15 14:32:49.729 -----------------------------------------------
eclipse.buildId=M20080221-1800
java.version=1.6.0_15
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=de_DE
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2010-02-15 14:32:58.319
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.ui 2 0 2010-02-15 14:32:59.433
!MESSAGE Warnings while parsing the key bindings from the 'org.eclipse.ui.commands' extension point
!SUBENTRY 1 org.eclipse.ui 2 0 2010-02-15 14:32:59.440
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.actionscript', id='com.adobe.flexbuilder.editors.actionscript.rename.element'
!SUBENTRY 1 org.eclipse.ui 2 0 2010-02-15 14:32:59.441
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.ZoomIn'
!SUBENTRY 1 org.eclipse.ui 2 0 2010-02-15 14:32:59.441
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.ZoomOut'
!SUBENTRY 1 org.eclipse.ui 2 0 2010-02-15 14:32:59.441
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.Magnify100'

!ENTRY org.eclipse.jface 4 0 2010-02-15 14:33:43.315
!MESSAGE Undefined context while filtering dialog/window contexts
!STACK 0
org.eclipse.core.commands.common.NotDefinedException: Cannot get the parent identifier from an undefined context. com.adobe.flexbuilder.editors.common.flexEditorScope.design.mxml
    at org.eclipse.core.commands.contexts.Context.getParentId(Context.java:201)
    at org.eclipse.jface.bindings.BindingManager.createFilteredContextTreeFor(BindingManager.java:825)
    at org.eclipse.jface.bindings.BindingManager.recomputeBindings(BindingManager.java:1720)
    at org.eclipse.jface.bindings.BindingManager.contextManagerChanged(BindingManager.java:689)
    at org.eclipse.core.commands.contexts.ContextManager.fireContextManagerChanged(ContextManager.java:152)
    at org.eclipse.core.commands.contexts.ContextManager.addActiveContext(ContextManager.java:96)
    at org.eclipse.ui.internal.contexts.ContextAuthority.updateContext(ContextAuthority.java:765)
    at org.eclipse.ui.internal.contexts.ContextAuthority.activateContext(ContextAuthority.java:179)
    at org.eclipse.ui.internal.contexts.ContextService.activateContext(ContextService.java:88)
    at org.eclipse.ui.internal.contexts.ContextService.activateContext(ContextService.java:75)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.activateEditorContext(CodeAndDesignEditor.java:705)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.activateDesignEditorContext(CodeAndDesignEditor.java:714)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.pageChange(CodeAndDesignEditor.java:538)
    at com.adobe.flexbuilder.editors.mxml.MXMLEditor.pageChange(MXMLEditor.java:422)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.setActivePage(CodeAndDesignEditor.java:648)
    at com.adobe.flexbuilder.editors.mxml.MXMLEditor.setActivePage(MXMLEditor.java:487)
    at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.createPartControl(FlexMultiPageEditorPart.java:235)
    at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.createPartControl(CodeAndDesignEditor.java:162)

```

---

