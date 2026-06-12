---
title: "Add programs to the Launcher"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by Brad wilkinson on 2013-08-15
Hello everyone,

I've just started using my PC to control a ShapeOko CNC router and I am also using various Free/Open software to run it.

So Inkscape and FreeCAD both add themselves to the launcher (or I could click and add them) no worries and I can use them fine.

However there are two other tools I use, [pycam]("http://pycam.sourceforge.net/") and [UniversalGCodeSender]("https://github.com/winder/Universal-G-Code-Sender") that I want to add to the launcher as well.

However when I right click on the file and add it to the launcher, the icon on the launcher won't start the application.

The files and their locations in my file system are:

bradley/home/pycam-0.5.1/pycam
bradley/home/UniversalGCoseSender/start.sh

So pycam is a python exicutable and the start.sh is a shell script, and when you click on either of them they come up with a "do you want to run n or display its contents" dialogue box where you click "run" and away it goes.

In dos or windows I would have had to add them to the path file (or something - really delving back through the memories here) but I don't know how to do the same thing in Linux.

Can someone point me to the correct wiki or tutorial please?

Cheers,

Brad

---

### Post by deadflowr on 2013-08-15
You can't put just any ole file in the launcher.
You'll need to make a .desktop file.
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

When you've done that, then you can move the newly made icon into the launcher.

Quick tip: Most application launchers are in the system folder /usr/share/applications, but you can put them in the local user's home folder
location /home/user/.local/share/applications.
Doing so will let you avoid having to run as root.

---

### Post by vasa1 on 2013-08-15
> **deadflowr said:**
>  ... you can put them in the local user's home folder
location /home/user/.local/share/applications.
Doing so will let you avoid having to run as root.
One other possible advantage is that the .desktop file in ~/.local/share/applications will remain unchanged even if there's an update of the software. For example, I like to edit the .desktop file for my browser to suit my needs but an update would give me a brand new .desktop file (without my edits). Having the .desktop file in ~/.local/share/applications prevents that.

Of course, there's always a flip side: some necessary change to a .desktop file may be part of an update and such a change won't be automatically reflected in ~/.local/share/applications. But I'm willing to chance it for the convenience.

---

### Post by Brad wilkinson on 2013-08-16
Thanks deadflowr, I read the help files you linked to but I am still having problems, in that neither of the .desktop files I created work!

Since I cannot get the website to accept either of the files for upload, here is the text from each file:

```
[Desktop Entry]
Version=1.0
Name=PyCam
Comment=Make NC files from STL files
Exec=/home/pycam-0.5.1/pycam
Icon=/home/
Terminal=false
Type=Application
Categories=Utility;Application;
```

and 

```
[Desktop Entry]
Version=1.0
Name=UniversalGCodeSender
Comment=Send GCode (NC) files to GrblShield over USB
Exec=/home/UniversalGCodeSender/start.sh
Icon=/home/
Terminal=false
Type=Application
Categories=Utility;Application;
```

when I use the "desktop-file-validate" utility on them I get the following error messages:

pycam.desktop: error: value "/home/" for key "Icon" in group "Desktop Entry" is an absolute path to a directory, instead of being an absolute path to an icon or an icon name
pycam.desktop: warning: value "Utility;Application;" for key "Categories" in group "Desktop Entry" contains a deprecated value "Application"

and 

UniversalGCodeSender.desktop: error: value "/home/" for key "Icon" in group "Desktop Entry" is an absolute path to a directory, instead of being an absolute path to an icon or an icon name
UniversalGCodeSender.desktop: warning: value "Utility;Application;" for key "Categories" in group "Desktop Entry" contains a deprecated value "Application"

since there is no icon for either of them I am not surprised about the first error in each one, but I don't know if the second error in each (about the depreciated value "Application") is important.

I also tried both files with terminal=true but when I do that I get another error message as follows:

There was an error creating the child process for this terminal
Failed to execute child process "/home/pycam-0.5.1/pycam" (No such file or directory)

and I know there is a "pycam" in that directory because when I go there and click on it, it runs!

any ideas what I've done wrong?

---

### Post by 3rdalbum on 2013-08-16
> **Brad wilkinson said:**
> 
any ideas what I've done wrong?

The first thing you did wrong: Making things difficult for yourself by deciding to manually create a .desktop file! There's an easy GUI way mentioned on that page. Go to the Dash and type in "Main Menu" and use that program to create a menu item, which behind-the-scenes is actually a .desktop file. The menu item will be available in the Dash and you can drag it from the Dash to the Launcher.

The second thing you did wrong: Exec=/home/pycam-0.5.1/pycam   It should actually be something like: /home/brad/pycam-0.5.1/pycam

(assuming your username is "brad")

/home is not your home directory, it's the folder that contains everybody's home directories.

---

### Post by Frogs Hair on 2013-08-16
Alacarte is not installed by default and needs to be installed to have the main menu application . Those who have  installed Classic or the Gnome shell will have this application. Alacarte installs  the classic gnome panel as a recommended dependency.  ```
sudo apt-get install alacarte
```

---

### Post by Brad wilkinson on 2013-08-17
ok, got it.

thanks 3rdalbum it was the path to the directory I had wrong.

I'm gonna blame it on going ~8 months without using a Linux PC...........

---

### Post by r_avital on 2013-08-17
The problem with installing alacarte is that it hauls with it the entire gnome-fallback desktops and all attendant packages, which you don't want.

Simple procedure:

1. in a terminal:```
sudo apt-get install --no-install-recommends gnome-panel
```

DO NOT run gnome-panel after it installs.  This will install strictly what you need to proceed further.

2. ```
sudo gnome-desktop-item-edit /usr/share/applications/ --create-new
```

Whoa!  What just happened?  You get the good-old dependable, pretty, intuitive GUI tool to set up a new launcher, that your great-aunt Edna could handle.   See thumbnail below.

3. Pick application-type from the dropdown (make sure to select "in terminal" for anything that needs to run in a terminal, otherwise leave the default "Application" selected), enter a name, a valid executable name, pick an icon, comment is optional, and you're done, this tool just created a new myapplication.desktop file for you in /usr/share/applications/

4. Start the dash, and type myapplication (whatever you used for the NAME field in step #3 above).  Drag/drop the icon you set in step #3 above on the launcher.

5. Beer (if you're over 21).

Credit: [http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)

---

### Post by Brad wilkinson on 2013-08-20
thankyou r_atival!!!!

thankyou thankyou thankyou!!!!!!:D:D:D:D:D:D:D

---

