---
title: "HOW-TO: Install FrostWire P2P Client"
date: 2005-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by cstudent on 2005-12-17
[B]This How-To will explain how to install the P2P client called FrostWire, which is a free substitute to LimeWire.
[/B]
Enter code via the terminal (Applications>>Accessories>>Terminal). This how-to assumes you are using Ubuntu with the Gnome desktop.

[B]New deb file available from FrostWire.
[/B]
FrostWire now has a deb file available for download. It seems to work pretty well. To install FrostWire using this deb file you'll first need to download it from the FrostWire download page. [Click here]("http://www.frostwire.com/index.php?title=FrostWire:Download") to go to that page.

Once you have to deb file downloaded you need to open a terminal window and navigate to the directory where you downloaded the file. Then just enter the command below to install FrostWire.

```


sudo dpkg -i FrostWire-4.10.9-1-i586.deb


```

The file listed above was current at the time this was written. You'll want to change the file name to the one you downloaded if yours is different.

[B]Original How-To Instructions:
[/B]
For those who like a more hands-on approach to installing software can use the original how-to instructions below. Except for having to remove the sinqle quotes in the first example, you should be able to copy and paste each line in the terminal. 

First start by getting the zip file for FrostWire. (Remove the single quotes at each end. I had to use them to get the full path to show up.)

```


**'wget http://voxel.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.9-1-AnyOS.zip'**


```

If you get an error that the file can not be found to download, there may be a new version available. [Click here]("http://www.frostwire.com/index.php?title=FrostWire:Download") to go to the FrostWire download page and download the current version listed as AnyOS.zip.

Next extract the zip file to the /opt directory and change permissions. You will be prompted for your password.

```


[B]sudo unzip -u FrostWire-4.10.9-1-AnyOS.zip -d /opt/
sudo chown -R root:root /opt/FrostWire/[/B]


```

Now add a little script in the /usr/bin/ directory. First open our scipt file in the text editor.

```


**sudo gedit /usr/bin/runFrostWire.sh**


```

Now enter the script code into the text editor that opened.

```


cd /opt/FrostWire/
java -jar FrostWire.jar


```

Save and close the text editor.

Now let's make it executable for everyone.

```


**sudo chmod +x /usr/bin/runFrostWire.sh**


```

Now we need to add a menu item to our applications menu. Again we are going to use the text editor to write a script.

```


**sudo gedit /usr/share/applications/FrostWire.desktop**


```

Now we enter our code in the text editor.

```


[Desktop Entry]
Name=FrostWire
GenericName=Free P2P Gnutella client
Comment=Search and share all kinds of files on the Gnutella network
Exec=/usr/bin/runFrostWire.sh
Icon=/opt/FrostWire/FrostWire.ico
Terminal=false
Type=Application
Categories=Application;Network;


```

Save and close the file.

That should be it. Go to your Applications menu and look under Internet. You should see an entry for FrostWire. Click on it and fire it up!

Hope this is of use to some people. Thanks to Arnieboy and the old Unofficial 5.04 Guide for showing me how to do this. If any errors are found please let me know so that I can correct them.

Thanks to ykpaiha for the chmod +x suggestion.

cstudent

Edit: Updated download file to newest version of FrostWire.

---

### Post by Aeon17x on 2005-12-22
For the lazy, here's something a bit shorter - 

1.) If you haven't installed Java, do it now [[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=java]("http://www.ubuntuforums.org/showthread.php?t=76702&highlight=java")]. FrostWire needs it to operate.
2.) Go to the FrostWire [download page]("http://www.frostwire.com/") website and download the Debian/Ubuntu package. Alternatively, you can enter this in the terminal - 
```
wget -c http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
```
3.) Now go to the folder where you downloaded the .deb, and use dpkg to install it directly.
```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```
4.) If you did it right, you should see FrostWire at Applications > Internet.

That's it. Frostwire is based on the LimeWire code; it does everything LimeWire Pro does, except FrostWire is totally free and wouldn't be restricted in the future. 8)

---

### Post by joshuapurcell on 2005-12-26
I've installed Frostwire but the systemtray icon is not working. In the application options, the icon is set to visible and the default shutdown behavior is "Minimize to System Tray.' Should this option work? I'm using version 4.9.37.

---

### Post by cstudent on 2005-12-28
Updated the download link to the newest version of FrostWire that was released 12-27-05.

---

### Post by meborc on 2005-12-29
i believe automatix also supports frostwire installation... or was i just h*gh when i got it installed ;)

---

### Post by cstudent on 2005-12-29
[QUOTE=meborc]i believe automatix also supports frostwire installation... or was i just h*gh when i got it installed ;)[/QUOTE]

Yes, Automatix does support FrostWire installation. I don't know if Arnieboy has updated his package to include the newer version. This How-To also serves the purpose of showing those new to Linux a way to install software outside the repositories. And there are those that do not wish to use Automatix, although I'm not one of them. I think Automatix is a great tool. I realize there are a number of ways to install software packages. You are free to install FrostWire any way you like.

---

### Post by akniss on 2006-01-15
what's the CLI command to run frostwire after I get it installed?  I'm running XFCE and would like to start it up from the command line.

---

### Post by Dr Von Bon Bon on 2006-01-15
While we're talking about Frostwire,


I installed it through automatix yet nothing happens when I try to open it.


Does anyone know what to do please so I can get it working?

Thanks

---

### Post by cstudent on 2006-01-15
[QUOTE=akniss]what's the CLI command to run frostwire after I get it installed?  I'm running XFCE and would like to start it up from the command line.[/QUOTE]

From the directory in which Frostwire is installed:

```


java -jar FrostWire.jar


```

Otherwise, insert the path to Frostwire if you start it from another directory. In the case of my installation:

```


java -jar /opt/FrostWire/FrostWire.jar


```

---

### Post by cstudent on 2006-01-15
[QUOTE=Dr Von Bon Bon]While we're talking about Frostwire,


I installed it through automatix yet nothing happens when I try to open it.


Does anyone know what to do please so I can get it working?

Thanks[/QUOTE]


If it starts and hangs during the splash screen, it is usually an indication that you do not have the version of Java it wants. Do you have Sun's jre1.5 installed? That is the one it wants. Automatix can install that for you too.

---

### Post by akniss on 2006-01-15
[QUOTE=cstudent]
 ...insert the path to Frostwire if you start it from another directory. In the case of my installation:

```


java -jar /opt/FrostWire/FrostWire.jar


```[/QUOTE]


I tried using the above code as the command for a launcher and got an error about not all files being present, probably due to a bad installation.  

So I tried having the launcher run the script your howto made me create with the following:
```
/opt/bin/runFrostWire.sh
```
and it works great!

Thanks!

---

### Post by hen3rz on 2006-01-15
> Yes, Automatix does support FrostWire installation. I don't know if Arnieboy has updated his package to include the newer version. This How-To also serves the purpose of showing those new to Linux a way to install software outside the repositories. And there are those that do not wish to use Automatix, although I'm not one of them. I think Automatix is a great tool. I realize there are a number of ways to install software packages. You are free to install FrostWire any way you like.

I like installing stuff manually as it allows me to learn, cause any fool can tick a box and click apply..

Great Tutorial! Keep up the great work.

---

### Post by Dr Von Bon Bon on 2006-01-16
No, it just doesn't start up.


I click on the icon and nothing comes up, not even the spash screen.

---

### Post by gabhla on 2006-01-16
Howdy!  Thanks...this is great.  Copy & Paste...worked like a champ.

---

### Post by wickwire on 2006-01-17
I found this thread just now, was about to follow the guide but I accessed the website to download the rpm, found out they have a deb package as well, new.

I installed with the deb using "sudo dpkg -i" and it's working, no problem.

---

### Post by TheSource on 2006-01-21
derek?

---

### Post by Anti-Establishment on 2006-01-23
I used the Automatix to install FrostWire first, but thats an older version and started freezing almost as soon as it opened, i might be lucky to click 2 buttons and it totally freezes.

Then I try the Second method here, newer version of FrostWire, same thing, totally freezes (won't even close)

Then, I try option 1 in this thread, seems to go ok, SAME THING!

What is wrong with my FrostWire? ](*,)

---

### Post by cstudent on 2006-01-23
[QUOTE=Anti-Establishment]I used the Automatix to install FrostWire first, but thats an older version and started freezing almost as soon as it opened, i might be lucky to click 2 buttons and it totally freezes.

Then I try the Second method here, newer version of FrostWire, same thing, totally freezes (won't even close)

Then, I try option 1 in this thread, seems to go ok, SAME THING!

What is wrong with my FrostWire? ](*,)[/QUOTE]


Which version of Java are you using?

---

### Post by cstudent on 2006-01-23
[QUOTE=wickwire]I found this thread just now, was about to follow the guide but I accessed the website to download the rpm, found out they have a deb package as well, new.

I installed with the deb using "sudo dpkg -i" and it's working, no problem.[/QUOTE]


Excellent. Thanks for letting us know.

If you install the .deb from Frostwire you'll want to uninstall the version from this how-to. The FrostWire deb will install FrostWire in /usr/lib instead of /opt. The Gnome panel applet also works with the .deb file.

To remove the how-to version:

```


sudo rm -rf /opt/FrostWire
sudo rm /usr/bin/runFrostWire.sh
sudo rm /usr/share/applications/FrostWire.desktop


```

---

### Post by cstudent on 2006-01-23
It appears that there may be issues with FrostWire itself. I opened FrostWire in a terminal this evening after getting home and received pretty much the same dialog that you posted earlier Anti-Establisment. My usual use of FrostWire and/or Limewire has been just searching for a file and downloading it. I never did much with the menu options, but did mess around with them this evening. I was able to get it to give me freeze problems, but for now can not give reasons for it. Maybe someone more familiar with Java can give some insight, but for what it's worth, I have not had any problems with just my usual search and download use of the software.

---

### Post by Anti-Establishment on 2006-01-23
[QUOTE=cstudent]Which version of Java are you using?[/QUOTE]

My Synaptic Package Manager says j2re and j2sdk are both installed :confused:

What should I be using?

---

### Post by shiellb on 2006-01-23
A very big thank you to CSTUDENT.  I followed your instructions for frostwire and it works.:)

---

### Post by cstudent on 2006-01-23
[QUOTE=Anti-Establishment]My Synaptic Package Manager says j2re and j2sdk are both installed :confused:

What should I be using?[/QUOTE]


Sounds like you have to right version installed. Check to see if it is set as the default version.

```


sudo update-alternatives --config java


```

Select j2re1.5-sun as the version you want to use.

---

### Post by Anti-Establishment on 2006-01-23
set j2re as the default, but it still freezes. It's completely motionless.

---

### Post by cstudent on 2006-01-23
[QUOTE=Anti-Establishment]set j2re as the default, but it still freezes. It's completely motionless.[/QUOTE]

OK. Plan B. Try running it from terminal and see if you get any error messages.

To run the version from my how-to enter:

```


cd /opt/FrostWire
java -jar FrostWire.jar


```

You may have to add sudo in front of java -jar FrostWire.jar if it complains.

If you installed the new .deb from FrostWire all you need to enter at the command line is frostwire. 

Copy any messages you get here and I'll see if I can help you figure out what the problem is.

---

### Post by Anti-Establishment on 2006-01-23
> If you installed the new .deb from FrostWire all you need to enter at the command line is frostwire.

Nope I used your how-to.

When I started from the terminal not much changed, i was able to click on the library and moniter buttons, but as soon as I go near File, View, Tools etc it froze up again.

---

### Post by cstudent on 2006-01-23
[QUOTE=Dr Von Bon Bon]No, it just doesn't start up.


I click on the icon and nothing comes up, not even the spash screen.[/QUOTE]


You might try the same things Dr. Von Bon Bon. Check your java default version and if that doesn't work, try running from the terminal and see if it spits anything useful back at you. Sorry I didn't respond sooner. I have this thread subscribed to, but I didn't get an email for your post.

---

### Post by cstudent on 2006-01-23
[QUOTE=Anti-Establishment]Nope I used your how-to.

When I started from the terminal not much changed, i was able to click on the library and moniter buttons, but as soon as I go near File, View, Tools etc it froze up again.[/QUOTE]


There wasn't any error messages in the terminal?

---

### Post by Anti-Establishment on 2006-01-23
pc4-blfs1-6-0-cust107:~$ cd /opt/FrostWire
connor@cpc4-blfs1-6-0-cust107:/opt/FrostWire$ java -jar FrostWire.jar
log4j:ERROR setFile(null,true) call failed.
java.io.FileNotFoundException: log.txt (Permission denied)
        at java.io.FileOutputStream.openAppend(Native Method)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at java.io.FileOutputStream.<init>(Unknown Source)
        at org.apache.log4j.FileAppender.setFile(FileAppender.java:272)
        at org.apache.log4j.RollingFileAppender.setFile(RollingFileAppender.java:156)
        at org.apache.log4j.FileAppender.activateOptions(FileAppender.java:151)
        at org.apache.log4j.config.PropertySetter.activate(PropertySetter.java:247)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:123)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:87)
        at org.apache.log4j.PropertyConfigurator.parseAppender(PropertyConfigurator.java:645)
        at org.apache.log4j.PropertyConfigurator.parseCategory(PropertyConfigurator.java:603)
        at org.apache.log4j.PropertyConfigurator.configureRootCategory(PropertyConfigurator.java:500)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:406)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:432)
        at org.apache.log4j.helpers.OptionConverter.selectAndConfigure(OptionConverter.java:460)
        at org.apache.log4j.LogManager.<clinit>(LogManager.java:113)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at com.limegroup.gnutella.util.CommonUtils.isLog4JAvailable(CommonUtils.java:549)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:85)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:41)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.limegroup.gnutella.gui.Main.main(Main.java:43)
/home/connor/.themes/Crystal dlb/gtk-2.0/gtkrc:9: Unable to find include file: "panel.rc"
/home/connor/.themes/Crystal dlb/gtk-2.0/gtkrc:10: Unable to find include file: "toolbar.rc"
/home/connor/.themes/Crystal dlb/gtk-2.0/gtkrc:32: Failed to parse property value " GTK_SHADOW_NONE " for `GtkStatusbar::shadow-type'

---

### Post by cstudent on 2006-01-23
I'm not sure why you're getting this problem Anti-Establishment. I can try out some things when I get home this evening. Currently I'm at work and don't have a Ubuntu box to tinker with. You might try installing the .deb file from FrostWire and see if that works for you. You can install it without removing the version from this how-to, you'll just have two versions installed. They shouldn't cause a problem with each other. You'll have two menu items for FrostWire, one from the  deb and from the how-to. You can use the menu editor to determine which icon is from the deb by looking at the properties. The deb laucher is just frostwire, the how-to would say /usr/bin/runFrostWire.sh, or you can just run it from the terminal by just typing frostwire. If the deb version works for you, just use the steps I mentioned earlier for removing the how-to version from your system. You can find the deb package at [http://www.frostwire.com/index.php?title=FrostWire:Download](http://www.frostwire.com/index.php?title=FrostWire:Download)

---

### Post by wickwire on 2006-01-24
As stated before, I'm using the deb package - tried to do the same on my laptop and the program won't run.

On this computer I have sun-j2sdk1.5 package installed, it was in the repositories, I installed via Synaptic, however when checking which version is being used:

```
akuma@Loki:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

```


So aparently I'm using nr2. Frostwire has started to use up most of the CPU these last few days, it's always at 100%, and I'm experiencing messed up windows, meaning if I open say a terminal on top of Frostwire's window and then drag it around, Frostwire gets all "erased kind", the areas I go through become grey and the buttons get deleted. The image doesn't refresh until I click on where some of the buttons are, getting the window back bit by bit.

As I'm typing I'll try switching to nr3 option and see what happens...

Hope some of this helps.

---

### Post by wickwire on 2006-01-24
uhmmm... nope, switching to Sun Java 1.5 didn't solve anything. There's still the "eraser effect" and CPU is at 97%...

I'm using an AMD AthlonXP 2000+ 512MB RAM DDR 400MHz

---

### Post by Anti-Establishment on 2006-01-24
[QUOTE=wickwire]

So aparently I'm using nr2. Frostwire has started to use up most of the CPU these last few days, it's always at 100%, and I'm experiencing messed up windows, meaning if I open say a terminal on top of Frostwire's window and then drag it around, Frostwire gets all "erased kind", the areas I go through become grey and the buttons get deleted. The image doesn't refresh until I click on where some of the buttons are, getting the window back bit by bit.[/QUOTE]

Same here

---

### Post by rikai on 2006-01-30
This is apparently a known issue over in their forums.
Its a bug caused by java htat hey're working to fix in the next release.

---

### Post by Strangerdave on 2006-02-05
This is a totally newbie question I know, but I keep getting this when I type:


```
sudo dpkg -i FrostWire-4.10.5-0-i586.deb
```

I changed the 3 to a 5 since the version has been updated and I was hoping that this version had the Java issue fixed.  i know that automatrix install this, but I think it is an older version.  Anyways, this is what I get:
```

dpkg: error processing FrostWire-4.10.5-0-i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 FrostWire-4.10.5-0-i586.deb
```

What does this mean?

-SD-

---

### Post by gammagoat on 2006-02-05
I had these same problems, untill I removed Frostwire through apt-get, deleted these files .FROSTWIRE, incomplete and shared, from my home dir. Downloaded the deb. pkg from the frostwire site to my desktop. Right click and choose install. Frostwire is working now.

---

### Post by cstudent on 2006-02-05
[QUOTE=Strangerdave]This is a totally newbie question I know, but I keep getting this when I type:


```
sudo dpkg -i FrostWire-4.10.5-0-i586.deb
```

I changed the 3 to a 5 since the version has been updated and I was hoping that this version had the Java issue fixed.  i know that automatrix install this, but I think it is an older version.  Anyways, this is what I get:
```

dpkg: error processing FrostWire-4.10.5-0-i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 FrostWire-4.10.5-0-i586.deb
```

What does this mean?

-SD-[/QUOTE]


Make sure you are in the same directory as the file. Also the file name is
FrostWire-4.10.5-0.i586.deb. You have a - where a . should be.

---

### Post by Strangerdave on 2006-02-06
Thanks a lot *blush* I guess I will read the file name a little closer rather than always cutting and pasting.  It seems to work great, I just hope it stays that way.

-SD-

---

### Post by cstudent on 2006-02-06
[QUOTE=Strangerdave]Thanks a lot *blush* I guess I will read the file name a little closer rather than always cutting and pasting.  It seems to work great, I just hope it stays that way.

-SD-[/QUOTE]

Version 4.10.3 had the - and . the other way around. FrostWire hasn't been real consistant with their file names.

---

### Post by Aeon17x on 2006-04-15
[http://www.frostwire.com/forum/viewtopic.php?t=4](http://www.frostwire.com/forum/viewtopic.php?t=4)

I suggest we link to the 4.10.5 beta for now, as 4.10.9 beta has a bug when installing on Linux.

---

### Post by cstudent on 2006-04-15
[QUOTE=Aeon17x][http://www.frostwire.com/forum/viewtopic.php?t=4](http://www.frostwire.com/forum/viewtopic.php?t=4)

I suggest we link to the 4.10.5 beta for now, as 4.10.9 beta has a bug when installing on Linux.[/QUOTE]


The bug is in the format of the runFrost.sh script. Someone posted a workaround on the [FrostWire How-to]("https://wiki.ubuntu.com/FrostWireHowTo") page of the Wiki site. My fix was to take the runFrost.sh script from version 4.10.5 and overwrite the 4.10.9 version. It worked. :rolleyes:

---

### Post by darkarchon on 2006-04-15
from FrostWire Community forum:
"And the same as a one liner:
su -c "sed -i 's/\r$//' /usr/lib/frostwire/runFrost.sh"

by yaloki :]

just execute this one line after installing .deb file, and its gonna work fine

---

### Post by gundumfx on 2007-07-24
> **cstudent said:**
> [B]This How-To will explain how to install the P2P client called FrostWire, which is a free substitute to LimeWire.
[/B]
Enter code via the terminal (Applications>>Accessories>>Terminal). This how-to assumes you are using Ubuntu with the Gnome desktop.

[B]New deb file available from FrostWire.
[/B]
FrostWire now has a deb file available for download. It seems to work pretty well. To install FrostWire using this deb file you'll first need to download it from the FrostWire download page. [Click here]("http://www.frostwire.com/index.php?title=FrostWire:Download") to go to that page.

Once you have to deb file downloaded you need to open a terminal window and navigate to the directory where you downloaded the file. Then just enter the command below to install FrostWire.

```


sudo dpkg -i FrostWire-4.10.9-1-i586.deb


```

The file listed above was current at the time this was written. You'll want to change the file name to the one you downloaded if yours is different.

[B]Original How-To Instructions:
[/B]
For those who like a more hands-on approach to installing software can use the original how-to instructions below. Except for having to remove the sinqle quotes in the first example, you should be able to copy and paste each line in the terminal. 

First start by getting the zip file for FrostWire. (Remove the single quotes at each end. I had to use them to get the full path to show up.)

```


**'wget http://voxel.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.9-1-AnyOS.zip'**


```

If you get an error that the file can not be found to download, there may be a new version available. [Click here]("http://www.frostwire.com/index.php?title=FrostWire:Download") to go to the FrostWire download page and download the current version listed as AnyOS.zip.

Next extract the zip file to the /opt directory and change permissions. You will be prompted for your password.

```


[B]sudo unzip -u FrostWire-4.10.9-1-AnyOS.zip -d /opt/
sudo chown -R root:root /opt/FrostWire/[/B]


```

Now add a little script in the /usr/bin/ directory. First open our scipt file in the text editor.

```


**sudo gedit /usr/bin/runFrostWire.sh**


```

Now enter the script code into the text editor that opened.

```


cd /opt/FrostWire/
java -jar FrostWire.jar


```

Save and close the text editor.

Now let's make it executable for everyone.

```


**sudo chmod +x /usr/bin/runFrostWire.sh**


```

Now we need to add a menu item to our applications menu. Again we are going to use the text editor to write a script.

```


**sudo gedit /usr/share/applications/FrostWire.desktop**


```

Now we enter our code in the text editor.

```


[Desktop Entry]
Name=FrostWire
GenericName=Free P2P Gnutella client
Comment=Search and share all kinds of files on the Gnutella network
Exec=/usr/bin/runFrostWire.sh
Icon=/opt/FrostWire/FrostWire.ico
Terminal=false
Type=Application
Categories=Application;Network;


```

Save and close the file.

That should be it. Go to your Applications menu and look under Internet. You should see an entry for FrostWire. Click on it and fire it up!

Hope this is of use to some people. Thanks to Arnieboy and the old Unofficial 5.04 Guide for showing me how to do this. If any errors are found please let me know so that I can correct them.

Thanks to ykpaiha for the chmod +x suggestion.

cstudent

Edit: Updated download file to newest version of FrostWire.

after i did what you said it gave me this in my terminal 

gundumfx@gundumfx-desktop:~$ sudo dpkg -i FrostWire-4.10.9-2.i586.deb
Password:
dpkg: status database area is locked by another process
gundumfx@gundumfx-desktop:~$ 
 
so i don't know what to do next so i am trying to download frostwire

---

### Post by cstudent on 2007-07-24
> **gundumfx said:**
> after i did what you said it gave me this in my terminal 

gundumfx@gundumfx-desktop:~$ sudo dpkg -i FrostWire-4.10.9-2.i586.deb
Password:
dpkg: status database area is locked by another process
gundumfx@gundumfx-desktop:~$ 
 
so i don't know what to do next so i am trying to download frostwire

Looks like you have synaptic open while trying to install from a command terminal. You can't do that. Close synaptic and try to install from terminal again.

---

### Post by rayburn on 2008-01-06
> Quote:
Originally Posted by Anti-Establishment
My Synaptic Package Manager says j2re and j2sdk are both installed

What should I be using?

Sounds like you have to right version installed. Check to see if it is set as the default version.

Code:

sudo update-alternatives --config java

Select j2re1.5-sun as the version you want to use.
__________________
Thanks Reply With Quote

**cstudent**

Many thanks for the above advice given to another user earlier in this thread. This solved it for me!

---

