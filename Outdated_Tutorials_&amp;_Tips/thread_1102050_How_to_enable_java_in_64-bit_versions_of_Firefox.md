---
title: "How to enable java in 64-bit versions of Firefox"
date: 2009-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxed on 2009-03-21
As many of you have probably discovered the jre available from the Ubuntu repository does not contain a 64-bit java plugin for 64-bit browsers.  This means that you have to manually download, extract, and install the 64-bit plugin yourself if you want to be able to view java applets in 64-bit versions of Firefox.  While this is not necessarily a cumbersome task it *is* certainly an inconvenience so I eventually ended up creating a deb package to automate this task.  Unfortunately due to Sun's software license I can't redistribute the jre so making the deb package available for download isn't possible.  However I have posted the instructions below on how to create your own deb packge which makes for an incredibly easy installation of the 64-bit java plugin.

[color=red]**Important:**[/color] Make sure to install the sun-java6-bin package prior to installing the new jre package.  Since Sun requires users to accept their license agreement prior to installing the jre it may prevent the jre64 package installation from completing successfully if you haven't already accepted their agreement.

[list=1]
[*]Install sun's jre.
```

sudo apt-get install sun-java6-bin

```
[*]_[Download the latest 64-bit jre from Sun.](http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.bin)_  At the moment it's version 1.6.0.14.  Make sure to save the file to your desktop.
[*]Open a terminal window and change to your desktop directory.
```

cd /home/yourUserName/Desktop

```
[*]Type the following:
```

mkdir -p jre64/DEBIAN
mkdir -p jre64/usr/lib/jvm
mkdir -p jre64/usr/lib/firefox-addons/plugins

```
[*]Now we're going to create the control file with gedit.
```

gedit jre64/DEBIAN/control

```
[*]Copy ALL of the following and paste into gedit.  Add your name and email address to the Maintainer line.  Do not delete the < > characters.
```

Package: jre64
Version: 1.6.0_14
Architecture: amd64
Maintainer: YourName <yourname@yourname.com>
Installed-Size: 87869
Depends: dpkg, sun-java6-jre, sun-java6-bin, firefox (>= 3.0)
Conflicts: icedtea-gcjwebplugin, icedtea6-plugin
Section: net
Priority: extra
Homepage: http://www.ubuntuforums.org
Description: Sun java runtime with 64-bit browser plugin
 This package will provide the latest jre from Sun including
 a 64-bit java plugin designed to work in 64-bit browsers.
 This package will automatically install the plugin for Firefox.

```
[*]Click save and close gedit.
[*]We're going to create a post install file to set the jre we're installing as the default. Type the following:
```

gedit jre64/DEBIAN/postinst

```
[*]Copy ALL of the following and paste into gedit.
```

#!/bin/sh
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_14/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/jre1.6.0_14/bin/java
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jre1.6.0_14/bin/javaws" 1
sudo update-alternatives --set javaws /usr/lib/jvm/jre1.6.0_14/bin/javaws

```
[*]Click save and close gedit.
[*]Now we need to create a post remove file to restore the default jre in the event that this package is ever removed. Type the following:
```

gedit jre64/DEBIAN/postrm

```
[*]Copy ALL of the following and paste into gedit.
```

#!/bin/sh
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-6-sun/jre/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/java-6-sun/jre/bin/javaws" 1
sudo update-alternatives --set javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws

```
[*]Click save and close gedit.
[*]Now we need to set the files we just created as executable.  Type the following:
```

chmod +x jre64/DEBIAN/post*

```
[*]Now we're going to extract the jre we downloaded earlier.  Type the following:
```

chmod +x jre*.bin
./jre*.bin

```
[*]Press enter repeatedly to navigate to the end of Sun's license.  Then type "yes" to accept the license.  The jre will then be extracted to a folder on your desktop.  Type the following:
```

mv jre1.6.0_14 jre64/usr/lib/jvm

```
[*]Now we need to create a symlink to the 64-bit java plugin and save it to the Firefox plugins folder.  Type the following:
```

ln -s /usr/lib/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so jre64/usr/lib/firefox-addons/plugins/libnpjp2.so

```
[*]Now let's build the package.
```

dpkg-deb --build jre64

```
[*]And finally click on the newly created package on your desktop to install it.  I prefer to install packages using a gui since it allows you to easily view the details and file contents of the package, but you can also install it with "dpkg -i packageName".
[*]You may want to test the new version of java after installing this package.
```

java -version

```
Should display something similar to the following.
```

java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b12, mixed mode)

```
[*]Type the following to test the java web start version.
```

javaws

```
Should display the following.
```

Java(TM) Web Start 1.6.0_14-ea                            
Usage:  javaws [run-options] <jnlp-file>                  
        javaws [control-options]   

```
[*]You can test the java plugin in Firefox by typing the following in the address bar.
```

about:plugins

```
You should see the java plugin listed if the installation was successful.  Java.com also offers a simple java applet test.  Just click the 'Do I have java?' link.
[/list]

[color=red]**IMPORTANT NOTE:**[/color] There are a number of instances in the guide above where I've used the version "1.6.0_14" in a directory path.  If you end up downloading a newer version of the jre from Sun make sure to replace those instances with the newer version.  For example, replace all occurences of "1.6.0_14" with "1.6.0_15" or whatever the new version is.

**UNINSTALL**
To uninstall the package simply type the following:
```

sudo apt-get remove jre64

```

---

### Post by jmtdstoc on 2009-03-30
Thanks for this great work "linuxed".

I have tried it on my system and it works perfectly!!!

You have explained it very simply and thanks to you I have just created my first .deb package :) .

---

### Post by neela on 2009-04-15
linuxed, Thanks for your detailed post on how to enable java in a 64-bit version of Firefox. I stepped through your instructions carefully. After I finished, I tried to open a .jnlp file and failed. I am new to ubuntu (8.10; amd64), and have spent the better part of the day trying to set this up. Would appreciate any further help. Incidentally, this is the .jnlp that I am trying to access:                  [http://www.interactivebrokers.com/java/classes/tws.jnlp?counter=0.9656534328107323](http://www.interactivebrokers.com/java/classes/tws.jnlp?counter=0.9656534328107323)
Thanks.

---

### Post by tad1073 on 2009-04-15
Where do I get 64 bit firefox

---

### Post by Clancy_s on 2009-04-15
> **tad1073 said:**
> Where do I get 64 bit firefox

If you have 64 bit Ubuntu the default install of FF is also 64 bit.  If you have 32 bit Ubuntu 64 bit FF won't run.

---

### Post by linuxed on 2009-04-16
> **neela said:**
> linuxed, Thanks for your detailed post on how to enable java in a 64-bit version of Firefox. I stepped through your instructions carefully. After I finished, I tried to open a .jnlp file and failed. I am new to ubuntu (8.10; amd64), and have spent the better part of the day trying to set this up. Would appreciate any further help. Incidentally, this is the .jnlp that I am trying to access:                  [http://www.interactivebrokers.com/java/classes/tws.jnlp?counter=0.9656534328107323](http://www.interactivebrokers.com/java/classes/tws.jnlp?counter=0.9656534328107323)
Thanks.
Make sure the new jre has been set as the default.  Type "java -version".  It should list "1.6.0_14-ea" as the version.

If the version is correct then try running a simple java app from the command line.  For testing purposes try the [varsha app from sourceforge.net.](http://sourceforge.net/project/showfiles.php?group_id=102448&package_id=116953&release_id=308414)  Download it to your desktop and type the following.
```

cd /home/yourUserName/Desktop
java -jar varsha.jar

```
If it opens then you know the new jre has been installed successfully.  To test the Firefox java plugin [go to this link.](http://java.com/en/download/installed.jsp?detect=jre&try=1) If it displays "1.6.0_14-ea" as the version then the java plugin is working successfully.

---

### Post by EnSeNiX on 2009-04-21
Hi,i've have install everything with no errors.When typing
java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b12, mixed mode)

but when i click on your link to see if i have the latest java install it still said i have the ols 1.6.0.0 and ask me to upgrade?

---

### Post by linuxed on 2009-04-22
You may have more than one java plugin installed in Firefox.  Type the following into your browser and see which java plugin is installed.
```

about:plugins

```
Check each of your mozilla/firefox folders for an old java plugin and remove it if found.  The java package will install libnpjp2.so to your /usr/lib/firefox-addons/plugins folder.  If you find any other java plugins remove them.

libnpjp2.so -> /usr/lib/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so

You may not have all of the folders below installed on your system.
```

cd ~/.mozilla/plugins
ls -l

cd /usr/lib/mozilla/plugins
ls -l

cd /usr/lib/firefox/plugins
ls -l

cd /usr/lib/firefox-addons/plugins
ls -l

cd /usr/lib/firefox-3*/plugins
ls -l

```

---

### Post by EnSeNiX on 2009-04-22
i have all those folder except one cd ~/.mozilla/don't-have- plugins-folder
Should i create that folder plugins in ~/.mozilla?

thanks

---

### Post by linuxed on 2009-04-23
Post the contents of each of the folders listed above.  Don't worry about the .mozilla/plugins folder.  Just run the "ls -l" command in each folder and then copy the text (the directory contents) in your terminal and paste it here.  There's probably a conflict from another java plugin.

What version of Firefox are you using?  3.0.8?  And just in case you have the icedtea-gcjwebplugin package installed you might want to run the following.
```

sudo apt-get remove icedtea-gcjwebplugin

```

---

### Post by EnSeNiX on 2009-04-24
> **linuxed said:**
> Post the contents of each of the folders listed above.  Don't worry about the .mozilla/plugins folder.  Just run the "ls -l" command in each folder and then copy the text (the directory contents) in your terminal and paste it here.  There's probably a conflict from another java plugin.

What version of Firefox are you using?  3.0.8?  And just in case you have the icedtea-gcjwebplugin package installed you might want to run the following.
```

sudo apt-get remove icedtea-gcjwebplugin

```

Ok,i try removing icedtea-gcwebplugin and when i type "about:plugins in FF it's still there "IcedTea Java Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu7) executes Java applets."

As for the folder typing ls -l is
ensenix@JSX-desktop:~$ cd ~/.mozilla/plugins
bash: cd: /home/ensenix/.mozilla/plugins: No such file or directory "no plugins folder in $HOME .mozilla folder

ensenix@JSX-desktop:~$ cd /usr/lib/mozilla/plugins
ensenix@JSX-desktop:/usr/lib/mozilla/plugins$ ls -l
total 400
lrwxrwxrwx 1 root root    37 2009-04-24 13:40 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 81576 2009-02-09 15:23 gecko-mediaplayer-dvx.so
-rw-r--r-- 1 root root 81568 2009-02-09 15:23 gecko-mediaplayer-qt.so
-rw-r--r-- 1 root root 81568 2009-02-09 15:23 gecko-mediaplayer-rm.so
-rw-r--r-- 1 root root 81568 2009-02-09 15:23 gecko-mediaplayer.so
-rw-r--r-- 1 root root 81576 2009-02-09 15:23 gecko-mediaplayer-wmp.so


ensenix@JSX-desktop:~$ cd /usr/lib/firefox/plugins
ensenix@JSX-desktop:/usr/lib/firefox/plugins$ ls -l
total 0
lrwxrwxrwx 1 root root 37 2009-04-24 13:40 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 46 2009-04-24 13:43 gecko-mediaplayer-dvx.so -> ../../mozilla/plugins/gecko-mediaplayer-dvx.so
lrwxrwxrwx 1 root root 47 2009-04-24 13:43 gecko-mediaplayer-dvx.xpt -> ../../mozilla/plugins/gecko-mediaplayer-dvx.xpt
lrwxrwxrwx 1 root root 45 2009-04-24 13:43 gecko-mediaplayer-qt.so -> ../../mozilla/plugins/gecko-mediaplayer-qt.so
lrwxrwxrwx 1 root root 46 2009-04-24 13:43 gecko-mediaplayer-qt.xpt -> ../../mozilla/plugins/gecko-mediaplayer-qt.xpt
lrwxrwxrwx 1 root root 45 2009-04-24 13:43 gecko-mediaplayer-rm.so -> ../../mozilla/plugins/gecko-mediaplayer-rm.so
lrwxrwxrwx 1 root root 46 2009-04-24 13:43 gecko-mediaplayer-rm.xpt -> ../../mozilla/plugins/gecko-mediaplayer-rm.xpt
lrwxrwxrwx 1 root root 42 2009-04-24 13:43 gecko-mediaplayer.so -> ../../mozilla/plugins/gecko-mediaplayer.so
lrwxrwxrwx 1 root root 46 2009-04-24 13:43 gecko-mediaplayer-wmp.so -> ../../mozilla/plugins/gecko-mediaplayer-wmp.so
lrwxrwxrwx 1 root root 47 2009-04-24 13:43 gecko-mediaplayer-wmp.xpt -> ../../mozilla/plugins/gecko-mediaplayer-wmp.xpt
lrwxrwxrwx 1 root root 43 2009-04-24 13:43 gecko-mediaplayer.xpt -> ../../mozilla/plugins/gecko-mediaplayer.xpt

ensenix@JSX-desktop:~$ cd /usr/lib/firefox-addons/plugins
ensenix@JSX-desktop:/usr/lib/firefox-addons/plugins$ ls -l
total 0
lrwxrwxrwx 1 ensenix ensenix 46 2009-04-24 13:57 libnpjp2.so -> /usr/lib/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so
ensenix@JSX-desktop:/usr/lib/firefox-addons/plugins$ 

ensenix@JSX-desktop:~$ cd /usr/lib/firefox-3*/plugins
ensenix@JSX-desktop:/usr/lib/firefox-3.0.9/plugins$ ls -l
total 0
lrwxrwxrwx 1 ensenix ensenix 46 2009-04-24 13:57 libnpjp2.so -> /usr/lib/jvm/jre1.6.0_14/lib/amd64/libnpjp2.so
ensenix@JSX-desktop:/usr/lib/firefox-3.0.9/plugins$ 

thanks

---

### Post by EnSeNiX on 2009-04-24
I solve it..thanks alot for your help

---

### Post by linuxed on 2009-04-25
Apparently the icedtea plugin installs into the xulrunner plugins folder rather than one of the mozilla folders.  Just in case you run into any future problems you might double check each of your xulrunner plugins folders for the plugin and remove it if found.

/usr/lib/xulrunner/plugins
/usr/lib/xulrunner-1.9.0.9/plugins
/usr/lib/xulrunner-addons/plugins

Look for libjavaplugin.so or IcedTeaPlugin.so.

---

### Post by namd3r on 2009-05-13
Followed this guide step-by-step, and it worked beautifully!

Thanks!

---

### Post by JAwuku on 2009-06-06
Thank you very much, it works perfectly!

And when a new version comes out, I can just simply uninstall the jre64, and go though the procedure again.

Thanks again.

---

### Post by isatis8 on 2009-06-25
Thank you very much for explaining very simply how to enable java in 64-bit versions of Firefox.

Everything goes right and the installation has been successfully completed.

Unfortunately, the application which was asking for a java enabled browser doesn't work and I get the following message :

Orienteering results analysis
V2.1.3
Copyright D Ryder/R Balling 2003
 
Homepage:  [www.splitsbrowser.org.uk](www.splitsbrowser.org.uk)

Results are being read from file eventdata.php?eventId=3483
Error when reading file [http://www.splitsbrowser.org.uk/eventdata.php?eventId=3483](http://www.splitsbrowser.org.uk/eventdata.php?eventId=3483) in line 2

**Error: java.lang.NumberFormatException: For input string: "7.7"Error loading data. Applet terminated.**

Is it a bug of the [www.splitsbrowser.org.uk](www.splitsbrowser.org.uk) application and can I do something to go around ?

I have tested the application which works on Windows.

I'm on ubuntu 9.04 64 bits.

Thank you for your help.

---

### Post by linuxed on 2009-06-25
It's a website related bug.  The java applet seems to work fine for eventId 3484.  It's just eventId 3483 that produces an error.

[eventId 3483](http://www.splitsbrowser.org.uk/splitsgraph.php?eventId=3483) produces error

[eventId 3484](http://www.splitsbrowser.org.uk/splitsgraph.php?eventId=3484) works as expected

---

### Post by isatis8 on 2009-06-26
Thank you,
 
But it is strange that it works on Windows AND on Redhat 5.2 64 bits,
and not on Ubuntu 9.04 64 bits.

---

### Post by marseille on 2009-07-06
hello all...

i see i am a day late and a dollar short but the directions did work for me and i can access jar files from firefox 64-bit

> Java enabled 	Yes
Java supported 	Yes
Java version 	Yes - version 1.6.0 


about:plugins

> Java(TM) Plug-in 1.6.0_14

    File name: libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java™ Plug-in 		Yes
application/x-java-applet 	Java™ Plug-in Applet 		Yes
application/x-java-applet;version=1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.5 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.6 	Java™ Plug-in 		Yes
application/x-java-applet;jpi-version=1.6.0_14 	Java™ Plug-in 		Yes
application/x-java-bean 	Java™ Plug-in JavaBeans 		Yes
application/x-java-bean;version=1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.5 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.6 	Java™ Plug-in 		Yes
application/x-java-bean;jpi-version=1.6.0_14 	Java™ Plug-in


i just cant seem to get javaws -- java webstart -- to open up a jnlp file. i did see a _[bug filed]("https://bugs.launchpad.net/ubuntu/+bug/375194")_ -- and many more recommendations -- but decided to try this _[update]("http://ubuntuforums.org/showthread.php?t=992515")_ solution. it didnt work for me.

i dont seem to have any other versions of java installed based on the following output:

> $ java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b12, mixed mode)




> $ _[sudo update-alternatives --config java]("http://ubuntuforums.org/showpost.php?p=6408840&postcount=18")_

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/jre1.6.0_14/bin/java
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

(note:  i did not pick a different alternative)

i am not sure what else to do... any recommendation?  i read in a few spots folks were trying a 32bit firefox but i would rather pass it up.  plz suggest an alternative if one is available.  thx.

---

### Post by linuxed on 2009-07-07
Enter the following to update the javaws version.
```

sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jre1.6.0_14/bin/javaws" 1
sudo update-alternatives --set javaws /usr/lib/jvm/jre1.6.0_14/bin/javaws

```
I've updated the guide to include those commands in the post install file.

---

### Post by marseille on 2009-07-08
:KS it worked! thx very much :)

---

### Post by cobaltseeker on 2009-07-08
Marry Me O.O 

Thank you so much!!!!!!!!!

Lol i was avoiding ubuntu for a couple weeks because i couldn't figure out why my java was acting so damn funny... thank you SO SO SO much for this fix :)

---

