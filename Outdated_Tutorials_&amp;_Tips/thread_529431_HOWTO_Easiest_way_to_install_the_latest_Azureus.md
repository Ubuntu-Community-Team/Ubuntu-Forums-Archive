---
title: "HOWTO: Easiest way to install the latest Azureus"
date: 2007-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dr.koljan on 2007-08-19
Azureus version in the repositories is old and broken, but you can manually 'update' it to the latest and working version without having to manually create the shortcuts, configuring FireFox to work with it etc.

Here's how it can be done:

1) Install Azureus through Add/Remove Applications or through apt-get:

```
sudo apt-get install azureus
```

It will automatically install Java for you if you don't have it yet.

2) Download the latest Azureus 3.0 [here]("http://www.vuze.com/app"). (You can download the 2.5.0.4 version but it will force you to update to 3.0 anyway.)

3) Extract it to your home folder.

4) Open the terminal and type:

```
sudo cp ~/azureus/Azureus2.jar /usr/share/java/
```

This will overwrite the existing Azureus file with a new one.

5) The SWT library provided with the libswt3.2-gtk-java package is outdated which will prevent Azureus from updating itself so you will have to manually update SWT.

```
sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux*
```

6) Now try launching Azureus. If you get any errors while updating azureus, then exit Azureus and restart it using this command:

```
sudo azureus
```

After Azureus has updated, you may launch it normally.

7) If everything works all right, you may delete the azureus folder in your home folder. Have fun! :)

---

### Post by mahasmb on 2007-08-29
I keep on getting the following error

```
maha@maha-dlu:~$ sudo azureus
StartServer ERROR: unable to bind to 127.0.0.1:6880 listening for passed torrent info: Cannot assign requested address
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]
maha@maha-dlu:~$ 
```


I've tried uninstalling and re-installing Azureus but always keep on getting that error.

---

### Post by MateaMatt on 2007-08-29
I also get this error.

---

### Post by joris1977 on 2007-10-14
worked for me!

Even solved a problem i had with azureus when i installed it the non-repo way.

This part: sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux *

didn't work. 

I don't care cause i'm on Azureus 2.5 and don't want to upgrade since some trackers don't like this. I don't care about the plugins as well. ;) Before i always had check for updates disabled... It  gave permissions troubles as well...

I'm running Gutsy and maybe this part was feisty related?

On a side note: Azureus is one of the most popular open source programs on windows and mac. So it's a bit weird that this has never worked in ubuntu from the repos.  I guess that for a lot of newbie kids azureus will be one of the first programs they try. Doesn't really give a nice first impression you have to install the non-repo way or work arounds like this howto...

---

### Post by Titi on 2007-10-18
ok, i get a similar error:
> maarten@ubuntu2:~/Desktop/azureus$ ./azureus
Starting Azureus...
Passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]


searched the entire (!!!) internet and found nothing that could solve this...
i can't imagine any other java program is running or anything. i'm clueless...

---

### Post by C0n5ci3n53 on 2007-10-18
I've finally figured out what the problem is, it seems that azureus 3.0.* has shifted to Java 6.0 instead of 5.0, which is what is installed by default when installing azureus through apt-get. All you have to do is 

```
sudo apt-get install sun-java6-jre
```

---

### Post by vratnica on 2007-10-21
great job!

Thank you =D>

---

### Post by LoTech242 on 2007-10-21
Thank you C0n5ci3n53 !
That solved it for me.

---

### Post by bone0est on 2007-10-23
> **joris1977 said:**
> This part: sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux *

didn't work.Try removing the space from between linux and * at the end of the line ;)

---

### Post by ajeffreys on 2007-10-23
Thankyou for this guide, as I have now finally got azureus to work :)

---

### Post by taavi on 2007-10-24
> **bone0est said:**
> Try removing the space from between linux and * at the end of the line ;)

Please update the initial post... because this

```
This part: sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux *
```

is nonsense.

---

### Post by snerd on 2007-10-25
I was in the process of installing the java 6 but got interrupted somehow. Now I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I try that I get this:

dpkg: requested operation requires superuser privilege

So I'm a complete noob, how to proceed?

---

### Post by WedgeHG on 2007-10-25
> I was in the process of installing the java 6 but got interrupted somehow. Now I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I try that I get this:

dpkg: requested operation requires superuser privilege

So I'm a complete noob, how to proceed?

Put sudo in front of the command you were running:

```
sudo dpkg --configure -a
```

It will then prompt you for your password.

---

### Post by paynito on 2007-10-27
I get this error

The following packages have unmet dependencies:
  azureus: Depends: libgnucrypto-java but it is not installable
           Depends: libswt3.1-gtk-java but it is not going to be installed
           Depends: libgtk-java but it is not going to be installed
E: Broken packages

doesn't install through apt-get or through Add/Remove

---

### Post by dr.koljan on 2007-10-28
I have updated the how-to, now there shouldn't be any problems.

---

### Post by tomsa on 2007-11-07
Thanks for posting this!  Until now, I had not been able to get Azureus to work at all!  I guess there really is no need to fear the command line!  Now if I only understood how to use it better.......#-o

---

### Post by jasontan6 on 2007-11-07
Works with Gutsy. Thanks. :)

---

### Post by hobbes_ba on 2007-11-07
> **dr.koljan said:**
> I have updated the how-to, now there shouldn't be any problems.

I followed your tutorial, i got azureus updated to Vuze, but i only got Loading... Please Wait on the new interface, anyone else is having this issue?



Well, nevermind... i fixed.

If you're reading this  post looking for help, just type:

**sudo aptitude install xulrunner**

And it should  work now.

---

### Post by slyboots on 2007-11-10
i try to install it on my gutsy like you wrote, but after install of the version 3.0.3.4 or 2.5.0.0. too when i run under root and get to update  then crash azureus.


all what you wrote i make, when i will open something to download then come this error:
```

(gecko:8926): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/usr/bin/azureus: line 189:  8926 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" -Dazureus.script="$0" $JAVA_PROPS $START_CLASS "$@"
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.


```

i try to check it with v2.5.0.0 and when i run it like root:

```
(SWT:28053): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)

```


so i have installed sun-java the version 5 and 6 but not help. 
I try to change it on [B] sudo update-alternatives --config java
[/B] but it was the same.
It looks:
```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```I have many times reinstalled azureus and java and removed all config data from my home folder, but i don't now what i can do more?!

---

### Post by turezky on 2007-11-12
Any possibility of not running Azureus as root after installation. Otherwise it keeps giving errors being not able to save configs and etc...
Now i can run it only from console with **sudo**, and when I close the console window the prog closes too.. that totally sux :(

---

### Post by slyboots on 2007-11-12
Hi everybody. I solve the issue with this:

I install the latest package:

1. Make sure you have sun Java 1.5 or 1.6 installed and working. To see if what your Java version is set by default type: java -version in the terminal.

2. Download last Azureus 

3. Open up for the terminal:
go to location where is located the package:

```

sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
sudo chown -R <username>:<username> /opt/azureus/

```
4. Now we need a launcher from the Application tab, fire up the terminal again:

```

sudo nano /usr/share/applications/Azureus.desktop
```

add:
Quote:
```
[Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```
5. This is optional. If you want azureus to launch from a command in the terminal:

```

sudo nano /usr/bin/azureus
```

add:

Quote:
```
#!/bin/sh

/opt/azureus/azureus "$*"
```
save it and close it.
Now the last thing in the terminal:
Code:
```

sudo chmod +x /usr/bin/azureus
```

[B]
Now the most important command:[/B]
```
**sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so**
```
(same should work by java 1.5)

Then run azureus:

```
azureus
```

Now get the any updates and plugins you need.

---

### Post by Acksys on 2007-11-18
Thanks very much for this one. I've been unable to find another Torrent client as robust as Azureus, and have been unable to get the latter working. Until now.

---

### Post by azurepalm on 2007-12-19
hi there,

I have the previous Azureus version from Synaptic Package Manager. How do i upgrade that version instead?

I'm not sure where to put the latest Azureus installation files since I can't find the azureus executable under "/home/user123/.azureus/"

---

### Post by i M@N on 2007-12-21
Hello.

Here is the way i do (pretty similar and works great) ... you need Java installed (see the Ubuntu doc about this : [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) ).

1 create an azureus.sh file in your /home dir and copy/paste this in it :
```
#!/bin/bash
mkdir ~/azureus
cd ~/azureus
wget http://switch.dl.sourceforge.net/sourceforge/azureus/Azureus_3.0.4.0_linux.tar.bz2
wget http://azureus.sourceforge.net/cvs/commons-cli.jar
wget http://azureus.sourceforge.net/cvs/log4j.jar
wget http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.2.2-200702121330/swt-3.2.2-gtk-linux-x86.zip
tar jxvf Azureus_3.0.4.0_linux.tar.bz2
cp commons-cli.jar ./azureus/commons-cli.jar
cp log4j.jar ./azureus/log4j.jar
unzip swt-3.2.2-gtk-linux-x86.zip -d ./swt/
cd ~/azureus/swt/swt-M20070212-1330-gtk-linux-x86/
unzip swt.jar -d ~/azureus/azureus/
cd ~/azureus
sudo cp -r ./azureus/ /usr/local/share/azureus/
gconftool-2 -s -t bool /desktop/gnome/url-handlers/magnet/enabled true
gconftool-2 -s -t string /desktop/gnome/url-handlers/magnet/command '/usr/local/share/azureus/azureus "%s"'
cd
```
Save this file.

2 in a terminal type :
```
chmod +x azureus.sh
```

3 always in your terminal type :
```
./azureus.sh
```
type in the admin pass when asked and here you are, Azureus 3.0.4.0 is installed.

4 Launch it in your terminal :
```
java -Djava.library.path="/usr/local/share/azureus" -jar /usr/local/share/azureus/Azureus2.jar
```
Tip : create a launcher with this command.

5 if you want to encrypt your traffic : [http://torrentfreak.com/how-to-encrypt-BitTorrent-traffic/](http://torrentfreak.com/how-to-encrypt-BitTorrent-traffic/)

6 if you are behind a router don't forget to redirect UDP and TCP ports to your computer.

7 For the next version just change Azureus_3.0.4.0_linux.tar.bz2 by the new name in the script above.

Hope that help.

@+...

---

### Post by goofeyfoot on 2008-05-26
Well that last post didn't work for me.

I did the script thing like the man said.  But when I tried to run "Azureus" with the command:   java -Djava.library.path="/usr/local/share/azureus" -jar /usr/local/share/azureus/Azureus2.jar

Here is what I got for an error.

Unable to access jarfile /usr/local/share/azureus/Azureus2.jar

Does anyone know what went wrong.  And if you can't guess, I don't know much about this terminal stuff to begin with.

Thanks.

Michael

---

### Post by System_Restore on 2009-04-07
Thank you so much dr.koljan. everything worked perfectly for me. my headache is now gone

---

