---
title: "Nothing will run"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by henry50 on 2015-08-30
I am new to Ubuntu and have no idea why I cant run any thing for exe's and linux exexutables it loads but nothing happens and for jar's no matter what I try it just takes me inside the file. Please help because I can barley do anything right now.

---

### Post by Petro Dawg on 2015-08-30
Executable files (ending in .exe) are for Windows only.  To run those types of files you will need Wine, which may or may not run whatever you are trying to install.  If you tell us what you are trying to run, we might be able to point you a suitable Linux alternative.  Typically Ubuntu programs will install using Debian formatted packages (ending in .deb).

---

### Post by mystics on 2015-08-30
I would advise you to start looking into the Ubuntu Software Center and Synaptic Package Manager as a way to install your programs. I know that those are different than the Windows way of searching for an Installer online, but each of them are much better than searching for Installers. I generally save searching for Installers as a last resort.

This, of course, is assuming that that option is available, but it often is for Linux programs. I just want to make sure you're aware of that option.

But a little more related to your questions themselves:

> **henry50 said:**
> I am new to Ubuntu and have no idea why I cant run any thing for exe's and linux exexutables

EXEs are Windows-specific and don't run on Linux without Wine, and even then they may not run perfectly. If you have one of these and want to use it, install [Wine]("https://www.winehq.org/download/ubuntu") or [PlayOnLinux]("https://www.playonlinux.com/en/download.html") to run it. (Note: Wine is still at the core of PlayOnLinux, but PlayOnLinux is relatively easier to use.)

If you go with Wine, go to the directory in a terminal and type:

```
wine <file>
```

Conversely, PlayOnLinux has a clear install button in its interface.

> for jar's no matter what I try it just takes me inside the file. Please help because I can barley do anything right now.

JAR files will behave more like archive files (think ZIP) than executables. If you want to run them, navigate to the directory in a terminal and type:

```
java -jar <file>
```

---

### Post by yetimon_64 on 2015-08-30
> **henry50 said:**
> ... and for jar's no matter what I try it just takes me inside the file....

To run a jar file you need to have a java runtime installed, you can do so by going to the Software Centre and searching for "openjdk-7-jre"; install it and you will have one if it is not already installed.

Once the java runtime environment is intalled you can run jar files from a terminal with a command like,
```
java -jar /path/to/jar/file/foo.jar
```
The keyboard combination "ctrl + alt + t" will give you a terminal in Unity.

An example of use: If you had a file called "foo.jar" on your desktop the terminal command would look like,
```
java -jar /home/$USER/Desktop/foo.jar 
```you could copy paste that last command and only need to change the filename, the "$USER" bit is a system variable that will automatically pick your user name in use.
Pressing "enter" once the filename is changed will run the jar file. 

If you don't want to use the terminal you can save the "java -jar" command into a desktop configuration file and save it in your home folder at /home/$USER/.local/share/applications. To do so open gedit,
```
gedit /home/$USER/.local/share/applications/jarfile.desktop
```
 then copy/paste the next quote/code box into the editor,
> ```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Run "Foo" Jarfile    # Change name to suit your file.
Icon=You can save icon image files, in /home/$USER/.icons and use just the name here    # Replace this line with just filename and extension eg "foo.png"
Exec=java -jar /home/$USER/Desktop/foo.jar    # Change the path here and filename to suit your jarfile's location/name etc.
Comment=Write some comment that describes the jar file etc.    # Replace this line with what you want to show in any tooltips etc.
NoDisplay=true     # This setting will hide your entry from any system menus when set "true".
```

Change all lines from "Name=" to the end of the file, from between the = sign and the # sign, to suit your jar file and its system use.

The comments after the # are for your instructions for the set up and can be either left for future reference or deleted.
When completed with changing the above details save the file and exit gedit.

Open your home folder and press "ctrl + h" to show hidden files, then open the folder /home/$USER/.local/share/applications.

You can then copy or link the file "jarfile.desktop" to your desktop or drag it onto the Unity sidebar. **Edit:** right clicking and selecting "Properties" and then setting the config file as executable [**Edit 2**: at the bottom on the "Permissions" tab after selecting "Properties"] enables any icon you created in your /home/.icons folder to show.
 
Double clicking the desktop config file in your home folder or from the desktop copy or the Unity side bar will run the jar file. 

Cheers, yeti. **Edit 3** ... :lol:, I just noted your join date, Welcome to the forums. :-)

---

### Post by monkeybrain20122 on 2015-08-30
> **yetimon_64 said:**
> To run a jar file you need to have a java runtime installed, you can do so by going to the Software Centre and searching for "openjdk-7-jre"; install it and you will have one if it is not already installed.

Once the java runtime environment is intalled you can run jar files from a terminal with a command like,
```
java -jar /path/to/jar/file/foo.jar
```
..

Or you can just right click the jar file, in Properties choose "Permission" and check "allow to execute", and then from "Open With" choose OpenJDK Java x runtime as default, then you can run the jar file by just clicking it in the future.

---

### Post by yetimon_64 on 2015-08-31
> ...then from "Open With" choose OpenJDK Java x runtime...Is that available with the openjdk-7-jre package ?
I don't seem to have that option listed here at all in the "Properties" > "Open With" choices.

---

### Post by monkeybrain20122 on 2015-08-31
> **yetimon_64 said:**
> Is that available with the openjdk-7-jre package ?
I don't seem to have that option listed here at all in the "Properties" > "Open With" choices.

Yes. But now you mention it I remember vaguely at some point there was a bug so installing openjdk7 did not automatically install a .desktop file so that option was missing and I had to make a .desktop file for it. But that seem to be a long time ago and I thought it was fixed after some updates. In  any case I have switched java default to openjdk8 for all my Ubuntu installs (Trusty and Vivid) so I no longer have an openjdk-7 option (openjdk-8 appears in the "open with" menu just as expected)

P.S. I always install the jdk package instead of just  jre since I need it for compiling certain things. Not sure if that is relevant.

---

### Post by yetimon_64 on 2015-08-31
> But now you mention it I remember vaguely at some point there was a bug  so installing openjdk7 did not automatically install a .desktop file ...That is something I may need to check further into on this install then. It does sound like that may be the case here.

> I always install the jdk package instead of just  jre... That crossed my mind yesterday after seeing your first post here. I installed the jdk package to see if it would make any difference ... it made no difference at all. I'll just have to keep my eyes open for any related bugs by the looks of it. Cheers, yeti.

---

### Post by monkeybrain20122 on 2015-08-31
> **yetimon_64 said:**
> That is something I may need to check further into on this install then. It does sound like that may be the case here.

That crossed my mind yesterday after seeing your first post here. I installed the jdk package to see if it would make any difference ... it made no difference at all. I'll just have to keep my eyes open for any related bugs by the looks of it. Cheers, yeti.

Ok, I found it. turned out it wasn't that long ago and affected open-jdk7 in vivid, it just seems very long ago in my memory, summer must have been too good :)

[http://ubuntuforums.org/showthread.php?t=2279153](http://ubuntuforums.org/showthread.php?t=2279153)

Can't find any bug report.

**Edited: **Checked installed files in synaptic for my openjdk packages in vivid (I have both openjdk 7 and 8 but default is 8) For openjdk-8-jre I found /usr/share/applications/openjdk-8-java.desktop but there is no corresponding .desktop file for openjdk-7-jre.

---

### Post by yetimon_64 on 2015-08-31
> **monkeybrain20122 said:**
> Ok, I found it. turned it wasn't that long ago and affected open-jdk7 in vivid, it just seems very long ago in my memory, summer must have been too good :)

[http://ubuntuforums.org/showthread.php?t=2279153](http://ubuntuforums.org/showthread.php?t=2279153)

Can't find any bug report.

A massive thank you. Just followed your instructions in the link only changing all references to "8" to "7". Saved the desktop config file and double clicked "jdiskreport-1.4.0.jar" in my home folder and it opened and ran =d>. 
Now that is a much much quicker method than my first post here, thanks. :D

---

### Post by henry50 on 2015-09-07
I have already tried this and with no success.

---

### Post by henry50 on 2015-09-07
Thanks I already use wine on my mac but thought I read somewhere that it is not needed for Ubuntu.

---

### Post by monkeybrain20122 on 2015-09-07
> **henry50 said:**
> Thanks I already use wine on my mac but thought I read somewhere that it is not needed for Ubuntu.

You don't need wine for java but .exe are Windows executables, of course they won't work without Wine. You won't need Wine if you install software that natively works on Linux instead of trying to install Windows software in your Linux box.

---

