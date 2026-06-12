---
title: "Howto: Install and configure Pekwm"
date: 2008-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by urukrama on 2008-01-08
[SIZE="3"][COLOR="DarkRed"]**Contents**[/COLOR][/SIZE]

[LIST=1]
[*]Introduction
[*]Installing Pekwm
[*]Creating a Session entry for Pekwm
[*]Pekwm basics
[*]Configuring Pekwm
[*]Pekwm themes
[*]Conclusion
[/LIST]

[SIZE="3"][COLOR="DarkRed"]**1. Introduction**[/COLOR][/SIZE]

[Pekwm]("http://www.pekwm.org/projects/pekwm") is a fast, functional, and flexible window manager, originally based on aewm++. It supports tabbed windows (like Fluxbox), key chains, pixmap themes, xinerama support and much more. If you like [Fluxbox]("http://fluxbox.sourceforge.net/") or [Openbox]("http://icculus.org/openbox/index.php/Main_Page") chances are you'll like Pekwm too, as it resembles both in looks and functionality. Pekwm is still actively developped.

Here is what Pekwm can look like: 

[CENTER][[IMG]http://img504.imageshack.us/img504/3620/pekwmgroove2le7.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=pekwmgroove2le7.jpg)			 [[IMG]http://img100.imageshack.us/img100/4634/fearlesspekwm01ji7.th.jpg[/IMG]](http://img100.imageshack.us/my.php?image=fearlesspekwm01ji7.jpg)		 [[IMG]http://img203.imageshack.us/img203/8266/elegancenew01.th.jpg[/IMG]](http://img203.imageshack.us/i/elegancenew01.jpg/)[/CENTER]
 
[CENTER]*(The first screenshot uses the [Groove Pekwm]("http://box-look.org/content/show.php/Groove?content=72941") and [Gtk theme]("http://gnome-look.org/content/show.php/Groove?content=66120"); the second uses the [Fearless]("http://box-look.org/content/show.php/Fearless?content=73021") Pekwm theme and a modified [Royalty]("http://gnome-look.org/content/show.php/Royalty?content=67866") gtk theme); the third uses the [Elegance Pekwm theme](http://box-look.org/content/show.php?content=79594).*[/CENTER]


Pekwm has excellent documentation, which you can find [here]("http://www.pekwm.org/files/pekwm/doc/0.1.10/html/index.html"). Everything you need to know to use Pekwm can be found there, and though it can be daunting at times I strongly recommend reading it. This guide is not meant to repeat or replace the official documentation, but rather to help Ubuntu users new to Pekwm getting started.


[SIZE="3"][COLOR="DarkRed"]**2. Installing Pekwm**[/COLOR][/SIZE]

The latest version of Pewkm (0.1.11) is both in the Ubuntu Karmic (9.10) and Lucid (10.04) repostories. Installing Pekwm 0.1.11 on Karmic and Lucid is, in other words, very easy. Just install the package through Synaptic, or through a terminal (*sudo aptitude install pekwm*).

[SIZE="2"][COLOR="DarkRed"]**2.2 Building Pekwm from source**[/COLOR][/SIZE]

Older versions of Ubuntu up until Hardy (8.04) have older versions of Pekwm in their [repositories](""http://packages.ubuntu.com/search?keywords=pekwm"). If you don't use Karmic or Lucid, or prefer to build from source, you can get Pekwm installed in just a few steps . Here is how to do it.
[LIST]
[*]**Preparation**
[INDENT]Since you will have to build from source, you will need the basic building tools installed. If you have never build a package from source before, you'll have to install [build-essential](http://packages.ubuntu.com/karmic/devel/build-essential). I also recommend installing [checkinstall](http://packages.ubuntu.com/karmic/admin/checkinstall), as it makes it much easier to remove the package you've installed later on. Checkinstall will first create a .deb package and install that. This means that it will show up in Synaptic and can be removed with Apt or Aptitude.

You can install these with the following command:

```
sudo aptitude install build-essential checkinstall
```

Next install the needed dependencies for Pekwm:

```
sudo apt-get build-dep pekwm
```[/INDENT]

[*]**Download the source code from the Pekwm site.**
[INDENT]Use your favourite web browser to surf to the [Pekwm site]("http://pekwm.org/projects/pekwm") and click on the download link for Pekwm 0.1.11 to download the latest stable version, or download it with the following command:

```
wget http://www.pekwm.org/projects/pekwm/files/pekwm-0.1.11.tar.bz2
```[/INDENT]

[*]**Unpack the archive**
[INDENT]Once the source code archive has been downloaded, it is time to unpack it. Use a file browser to navigate to the directory where you saved the file and unpack the archive to the directory of your choice. Alternatively, you can use the command line as follows:
```
cd /path/to/the/directory/where/the/archive/is/saved
tar xjvf pekwm-0.1.11.tar.bz2
```[/INDENT]
[*]**Configure the package to make it ready to compile**
[INDENT]Now you have to compile the package. Open a terminal and navigate with the cd ('change directory') command to the directory where the unpacked archive is:
```
cd pekwm-0.1.11/
```
Then run the configure script to prepare the source for installation with the following command:
```
./configure
```
You can add several options to this. Using this command, the package will be installed in /usr/local/. If you'd like the package to be installed in another directory, for example /usr/, use the following command:
```
./configure --prefix='/usr'
```
If you would like Xinerama support (if you have more than one screen), you'll have to specify that now as well by adding the *--enable-xinerama *option:
```
./configure --enable-xinerama
```
There are more options (see [here]("http://www.pekwm.org/files/pekwm/doc/0.1.10/html/overview/compiling.html#overview-compiling-configure")), but unless you really know what you are doing, you need not be concerned with them.

The configure script will look for dependencies and basic system settings. Just let it all run. You don't need to worry about what it tells you, unless you encounter an error and the process is aborted: only the first error message is then of importance as it will help you figure out what went wrong. If all goes well, you should see something like this:
```
* pekwm version 0.1.11 configured successfully.
*
* PREFIX: /usr/local
* FEATURES:  XShape Xrandr Xft image-xpm image-png menus harbour
* CXXFLAGS: -g -O2  -I/usr/include -I/usr/include/freetype2
* LIBS:   -L/usr/X11R6/lib -lX11 -lXext -lXrandr -lXft -lX11 -lfreetype -lz -lfontconfig -lXrender -lX11 -lXpm -lpng
```
If you changed the destination directory, as explained above, the 'PREFIX' line will give the directory you specified. If you have configured with the xinerama option, the 'FEATURES' line will include Xinerama.  You can ignore the rest.[/INDENT]
[*]**Build the package**
[INDENT]Once all this is done, you have to build the package. At the command prompt type the following command:
```
make
```
A lot of information will appear. If no errors show up, none of it is really important and can safely be ignored. Note that this may take a while.[/INDENT]
[*]**Install Pekwm**
[INDENT]If all this went smoothly and no errors were encountered, you can finally install the package with the following command:
```
sudo checkinstall
```
(If you prefer not to use checkinstall, type 'sudo make install' instead.)

Checkinstall will then build a .deb package and install that. If you'd rather build the .deb now, but install the package later using that deb, enter the following command instead to install:
```
sudo checkinstall -D
```
Checkinstall will ask for confirmations three times in the beginning of the process, so keep an eye on it. The defaults are fine, so you can just press enter when it asks for something.

If all goes well, Pekwm is now installed. If you encounter any error messages in this process, post them in this thread, and perhaps someone can help.[/INDENT]
[/LIST]


[COLOR="DarkRed"][SIZE="3"]**3. Creating a Session entry for Pekwm**[/SIZE][/COLOR]

If you use Karmic or Lucid and have installed the Pekwm package from the repositories, you can skip this step. 

If you compiled Pekwm from source and if you use a display and session manager, such as GDM, KDM or Slim, you will not have an entry for Pekwm in the Sessions menu of your login screen. But don't worry, this is easily created. Open a terminal and enter the following command (you can replace nano by any other text editor, such as mousepad, leafpad, vim or gedit):

```
sudo nano /usr/share/xsessions/Pekwm.desktop
```

An empty file will open. Add the following to this:

```
[Desktop Entry] 
Encoding=UTF-8 
Name=PekWM
Comment=Start PekWM
Exec=/usr/local/bin/pekwm
Icon= 
Type=Application
```

(If you have installed Pekwm to /usr/ (as mentioned above), change the Exec line to 'Exec=/usr/bin/pekwm')

Save and close the file and make the file executable with the following command:

```
sudo chmod +x /usr/share/xsessions/Pekwm.desktop
```

When you restart your computer, you will be able to choose Pekwm in the sessions menu (which is accessed with F10 > Sessions if you use GDM or KDM, the default login manager of (X)Ubuntu and Kubuntu respectively).

If you don't use a session manager, edit your ~/.xinitrc file (create one if you don't have one already), so that it looks something like this:

```
#!/bin/sh
xsetroot -solid black &

exec /usr/local/bin/pekwm

```

If you have installed Pekwm to /usr/ (as mentioned above), change the exec line to 'exec /usr/bin/pekwm'. When you start X with the command *startx* you will start a new Pekwm session.

[COLOR="DarkRed"][SIZE="3"]**4. Pekwm basics**[/SIZE][/COLOR]

When you first log into Pekwm, you won't see much apart from a blank screen. This is normal. Pekwm doesn't come with a panel, or a desktop manager. Pekwm is fairly straightforward. It is a window manager, and does not much more than managing windows. Here are a few basics of Pekwm:

**Windows**
[LIST]
[*]Pekwm supports tabbed windows. You can group windows together by middle-clicking the titlebar of one window and dragging it to another window title. To group the next launched window with the current one, press the windows key + T to tag the current window. Until untagged with the same command, all new windows will be opened as tabs within that window.

[*]Apart from maximizing, windows can also 'fill' in Pekwm: they will grow (either vertically, horizontally or both) until they reach another window border or an edge of the screen.

[*]Every window can be stripped of their titlebar or their borders or both.
[/LIST]

**Menus**
[LIST]
[*]Pekwm comes with several menus. You have the root menu, which is editable and generally contains entries to launch your applications. There is a active window menu (the GoTo menu), which contains a list of all active windows on all workspaces. The GoToClient menu list all active windows with their tabs. The Icon menu lists the iconified windows.

[*]Right click on the desktop, and you'll have your root menu. Middle click and you have the active window menu. You can also click on the screen edges to call up these menus, which means you don't have to iconify all windows to use the menu. 

[*]To see the Icon menu, press Windows key+Shift+I, to use the GoToClient menu, press Windows key+C
[/LIST]

**Other**
[LIST]
[*]Pekwm does not come with any panels, pagers, system trays. It does have a 'harbour', where you can load dockapps, and which is similar to (though less developed than) the slit of Fluxbox or the dock of Openbox. The order in which the dockapps are loaded can be specified in the autoproperties file (see below).

[*]Pekwm has a command dialog, which can be launched by pressing the Windows key + D. It can be used to execute commands to launch applications, but also to performs Pekwm actions. For a list of actions, see [here.]("http://www.pekwm.org/files/pekwm/doc/0.1.8/html/config/keys_mouse.html#config-keys_mouse-actions")
[/LIST]


[COLOR="DarkRed"][SIZE="3"]**5. Configuring Pekwm**[/SIZE][/COLOR]

All of Pekwm's configuration happens in the ~/.pekwm directory. In there you will find 7 files: config, menu, keys, mouse, autoproperties, start, and vars.

There are no graphical tools to change the settings in these files (apart from a text editor ;-)). Any changes you make to these files will not be applied until you reconfigure (in the root menu) or restart Pekwm. 

In case you accidentally delete these files, the defaults can be found at /usr/local/etc/pekwm

[SIZE="2"]_**Config**_[/SIZE]
	This is the general configuration file. Here you can control the basic behaviour of Pekwm. It controls the workspace settings, the menu and harbour behaviour, window edge resistance, and more. The settings are very well explained in the official Pekwm [documentation.]("http://www.pekwm.org/files/pekwm/doc/0.1.8/html/index.html")

_[SIZE="2"]**Menu**[/SIZE]_
As you could have guessed, this is the file that controls your menu. You can edit this file to add, edit or remove entries or submenus to your root menu and (towards the end of the file) your window menu (the menu that pops up when you right click a window header). Any custom menu you'd like to setup will have to be added to this file.

When you first run Pekwm you will already have a rather full default menu, with possibly plenty of applications you don't have installed. It might be a useful basis to create your own menu. You could also run **[Menumaker]("http://menumaker.sourceforge.net/") **to set up menus of all your installed applications. Run it with the following command:
```
mmaker --no-desktop pekwm
```
(Note that this will not overwrite your existing menu file. If you want it to overwrite, add the **-f **flag to the above command.


The syntax for the menu file is fairly straightforward. A simple entry has the following structure:
```
Entry = "NAME" { Actions = "Exec COMMAND &" }
```
A submenu has the following syntax:
```
Submenu = "NAME" {
				Entry = "NAME" { Actions = "Exec COMMAND &" }
                                Entry = "NAME" { Actions = "Exec COMMAND &" }
			}
```
(Make sure these brackets are always closed, or you will have errors and your menu will not display)

To add a separator line to the menu, use the following:
```
Separator {}
```
Pekwm also supports dynamic menus. These are basically menu entries or submenus that display the output of a script that is run every time the entry or submenu is accessed. 

You can find some dynamic menus online. Check the exact syntax the menu requires, as they can vary. There are not that many dynamic menu scripts around, unfortunately. You can find dynamic menus for Gmail and network connections [here,]("http://www.hewphoria.com/?p=submission&type=config") and one to display the time and date [here.]("http://urukrama.wordpress.com/2008/01/02/show-the-date-and-time-in-pekwms-menu/")

[SIZE="2"]_**Keys**_[/SIZE]
This file controls all the keyboard bindings and keychains used in Pekwm. You can add keyboard bindings to launch programs or to perform actions in Pekwm, such as show a menu, move a window, switch desktops, etc. For a full list of Pekwm's actions, see the [documentation.]("http://www.pekwm.org/files/pekwm/doc/0.1.8/html/config/keys_mouse.html#config-keys_mouse-actions") 

The syntax structure of this file resembles that of the menu file and should be fairly self-evident. Mod1 is the Alt key, Mod4 the Windows key.

You can have more than one action assigned to one key combination. To do so, just separate the actions by a semicolon. Here is an example:

```
KeyPress = "Ctrl Mod1 R" { Actions = "Exec osdctl -s 'Reconfiguring'; Reload" }
```

When you press Ctrl+Alt+R Pekwm will display on the screen the text 'Reconfiguring' (osdctl -s 'Reconfiguring') and reconfigure (Reload). (Note that this requires [osdsh]("http://osdsh.sourceforge.net/") to be installed)

_[SIZE="2"]**Mouse**[/SIZE]_
This file controls all the mouse actions used in Pekwm. For a full list of Pekwm's actions, see the [documentation.]("http://www.pekwm.org/files/pekwm/doc/0.1.8/html/config/keys_mouse.html#config-keys_mouse-actions") 

Pekwm is set up by default to focus windows when the mouse moves over them (as opposed to the 'click to focus' style). If you'd like to change this, look for the following lines in the file and do what they say (there are quite a few of the first, but only one occurrence of the second):
```
# Remove the following line if you want to use click to focus.
# Uncomment the following line if windows should raise when clicked.
```

For some ideas of what you can do with the Mouse and Keys file, have a look [here]("http://urukrama.wordpress.com/2007/12/30/some-pekwm-configurations/").

[SIZE="2"]_**Autoproperties**_[/SIZE]
If you'd like certain applications to open on certain workspaces, have a certain title, skip the (window) menus, or be automatically tabbed together, you can specify all that here. The syntax is a little confusing at first, but it is well documented in the [documentation]("http://www.pekwm.org/files/pekwm/doc/0.1.8/html/config/autoprops.html") and the default autoproperties file contains plenty of examples.

_[SIZE="2"]**Start**[/SIZE]_
This file is used to start applications when Pekwm is started. If you'd like to display a wallpaper or launch a panel whenever Pekwm is started, you can add entries for these things here. Note, though, that these applications are run every time Pekwm is started -- including when you run 'Restart' in the root menu. The commands are executed only after Pekwm is started. 

To add an application, use the following structure:
```
nameofapplication &
```

The & at the end is crucial, or anything after it won't be run. To give you an idea of what this file could look like, here is an example:

```
# Auto-mounting drives 
gnome-volume-manager & 
# To set the background image
hsetroot -tile "/home/urukrama/Images/Desktops/Abandoned.jpg" &
fbpanel &
conky &
# To have visual feedback when changing the volume
osdsh & 
(sleep 1 && osdctl -m 1) &
```

Before you can use this file, you will have to make it executable with the following command:
```
chmod +x ~/.pekwm/start
```

_[SIZE="2"]**Vars**[/SIZE]_
Finally, the vars file contains variables that are applied throughout Pekwm. The default entry should be clear enough:
```
$TERM="xterm -fn fixed +sb -bg white -fg black"
```
Whenever the variable $TERM is used in any of Pekwm's configuration files, the command *xterm -fn fixed +sb -bg white -fg black* will be run.


[COLOR="DarkRed"][SIZE="3"]**6. Themes**[/SIZE][/COLOR]

Unlike some other window managers, Pekwm themes govern all visual aspects: window headers and borders, menus, the harbour, fonts, as well as the position *and* functions of window buttons (like close, iconify, etc.).

Themes are installed in ~/.pekwm/themes or /usr/local/share/pewkm/themes (/usr/share/pekwm/themes if you have changed the default installation directory). To install a theme, unpack the theme archive, and copy the folder that contains the 'theme' file and possibly image files to the above mentioned folders. The name of the theme folder is the name that will appear in the menu. You can change the theme also manually by editing the Pekwm config file (in the first section 'Files').

You can download pekwm themes from the following places:

[LIST]
[*][Box-look]("http://box-look.org/index.php?xcontentmode=7403") 
[*][FreshMeat]("http://themes.freshmeat.net/search/?q=pekwm&section=projects")
[/LIST]
The theme settings have changed in more recent versions of Pekwm, so themes written for older versions are most likely unusable. You'll be able to tell straight away whether a theme is broken or not. :-)


[COLOR="DarkRed"][SIZE="3"]**7. Conclusion**[/SIZE][/COLOR]

Since Pekwm is just a window manager, it doesn't control the desktop, provide ways of changing Gtk settings such as themes, icons or fonts, manage the (un)mounting of devices, etc. Solutions to these are the same in Pekwm as in Fluxbox, Openbox or Icewm. If you need help with these, have a look at [my Openbox guide]("http://urukrama.wordpress.com/openbox-guide/"), which discusses these at length. 

Like Fluxbox and Openbox, Pekwm is small and light, but highly configurable. Explore its many potentials and find a setup that works for you.

For additional support of Pekwm read the documentation, join the[ mailing list]("http://lists.pekwm.org/mailman/listinfo/pekwm-users"), enter #pekwm at irc.freenode.net, or leave a message here on these forums.

---

### Post by AndreiMe on 2008-02-28
this is great... thanks alot... will surely play with it

---

### Post by thyultimate on 2008-03-03
that was amazingly well written and explained....kudos!!!

just installed it, will toy around and report back :biggrin:

---

### Post by Iandefor on 2008-03-04
A well-written introduction to PekWM. Thanks for this!

---

### Post by strankan on 2008-03-12
Great work mate!

I have a question and I think it has to do with PekWM. I use skype alot to communicate with my family. The problem is when i minimize skype to tray (and I have tried all available trays...) I can't get it to show again. It just doesn't appear when I click the icon. The weird thing is that Gajim works, amsn works, xchat works. It's just skype that doesn't want to play. It works with the exact same setup if I try openbox or fluxbox though. Do you have any idea what could be causing this? 

Love PekWM, but without a working skype it's a no go for me :(

---

### Post by mindepinde on 2008-03-15
If you did everything right and can't login to the PekWM environment, i.e. after login you get the message "No Exec line in the session file: Pekwm.", here's the tip (took me half a day to figure out) to get it working:

-  in the Pekwm.desktop file comment (use '#') the line with 'Encoding=UTF-8'. For some reason this line prevented the gdm finding the Exec line for me. Don't know why it is so, but it worked for me.

---

### Post by urukrama on 2008-03-26
> **strankan said:**
> Great work mate!

I have a question and I think it has to do with PekWM. I use skype alot to communicate with my family. The problem is when i minimize skype to tray (and I have tried all available trays...) I can't get it to show again. It just doesn't appear when I click the icon. The weird thing is that Gajim works, amsn works, xchat works. It's just skype that doesn't want to play. It works with the exact same setup if I try openbox or fluxbox though. Do you have any idea what could be causing this? 

Love PekWM, but without a working skype it's a no go for me :(

I have no idea what might be causing that. I don't use Skype and (like you) have had no problem with other apps that have a tray icon.

Do you get any error messages if you launch Skype from the terminal when you try to make Skype appear again? Or could you post the contents of your ~/.xsession-errors here (after you've tried to make Skype reappear)?

---

### Post by mossgarden on 2008-04-21
> Configure the package to make it ready to compile

    Now you have to compile the package. Open a terminal and navigate with the cd ('change directory') command to the directory where the unpacked archive is:
    Code:

  ```
  cd pekwm-0.1.6/
```

    Then run the configure script to prepare the source for installation with the following command:
    Code:
```

    ./configure
```


I got this far when I was stopped by the error:

> checking for X... no
checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11.

I'm not sure what this means?
(I installed the 0.1.5 version just using the sudo aptitude install pekwm, but naturally I would prefer the newest version :/)

**EDIT: never mind, I found a solution :)**

---

### Post by urukrama on 2008-04-25
> **mossgarden said:**
> **EDIT: never mind, I found a solution :)**

It might help others who have the same problem if you posted your solution here. :-)

---

### Post by njakol on 2008-05-18
I had the same problem with:

> checking for X... no
checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11. 

but I found the solution here:
[http://ubuntuforums.org/showthread.php?t=28400]("http://ubuntuforums.org/showthread.php?t=28400")

i used:
```
apt-get build-dep pekwm
```

but you can also use auto-apt.

---

### Post by Mos_Barbuta on 2008-05-23
Thanks for this guide, the installation went perfectly

It really seems like the perfect window manager for me (I love the screen edges) but I have a big problem with the panel behaviour : when I click on the panel, the window gets focused, but stays under the other maximised windows. 

I tried all the panels out there (xfce, perlpanel, barpanel, bmpanel, tint, fbpanel, lxpanel...) but I have the same problem.

The only one that works is pypanel...but I have another problem : all the windows related with another window stay on the panel, even after being closed or minimised (ex: plugins config for audacious, search in synaptic, any application that goes into tray, etc). These windows disappear from the panel only after closing the main application.

It's very frustrating because I really love pekwm.

What panel/dock do you use with pekwm? Did you have the same problems?

Thanks for your help

---

### Post by urukrama on 2008-05-23
If I use a panel, I use pypanel with Pekwm. The problems you encounter with it are well-known, and there isn't a workaround yet. It is fixed in the git version of Pekwm, though (See [here]("http://pekwm.org/projects/pekwm") under "Development"), which should be released as 0.1.7 'soon'. 

I haven't experienced the problems with other panels you mentioned, but then I rarely use other panels. I'll try it out myself.

Btw, thanks for mentioning barpanel. I hadn't seen that one before. :)

---

### Post by Mos_Barbuta on 2008-05-23
Thanks for your answer.

I'll be waiting for the 0.17 release (and keep using pypanel in the meantime)

---

### Post by droog on 2008-06-01
Anyone else have problems with shading windows when using xcompmgr? After shading a window it leaves artifacts of the window on the desktop and it gets all glitchy
 and if you move the titlebar around it leaves a trail.
It happens when using most themes but a few like elegant brit and blackwhite it works perfectly.

I have no problems using xcompmgr in fvwm openbox fluxbox or any other wm, only pek.

---

### Post by jviscosi on 2008-06-10
> **urukrama said:**
> If I use a panel, I use pypanel with Pekwm. The problems you encounter with it are well-known, and there isn't a workaround yet. It is fixed in the git version of Pekwm, though (See [here]("http://pekwm.org/projects/pekwm") under "Development"), which should be released as 0.1.7 'soon'. 

I haven't experienced the problems with other panels you mentioned, but then I rarely use other panels. I'll try it out myself.

Btw, thanks for mentioning barpanel. I hadn't seen that one before. :)

I grabbed the git version and it still had the problem of windows not raising when clicking on them in the fbpanel taskbar, so I added a line to fbpanel's taskbar.c file (borrowed from the method that gets called when you right-click on the task icon and select "Raise", which *does* work) and that seems to have fixed it.  This is nasty and hackish, but it makes me happy; now I can move on to messing with my PekWM configuration ...

I can post the change I made to taskbar.c if anyone's interested, although I'm not sure this is the appropriate spot for that sort of thing.

---

### Post by Sammm_ on 2008-06-17
Brilliant guide but I can't actually load the session. When I select the PekWM session from GDM it complains that there isn't a "Exec" line and it reverts to the failsafe xterm session, any ideas what could be up?

Cheers.

**Edit:** Solved the problem, after some google-fu.

```

[Desktop Entry]
Encoding=UTF-8
Name=PekWM
Comment=Use PekWM as your window manager
Exec=pekwm
TryExec=pekwm
# no icon yet, only the top three are currently used
Icon=
Type=Application

```

Another question now... any idea how I can get the XFCE quit dialog to show? I.e. is there a command I can run from the menu for it?

---

### Post by canistra on 2008-06-24
how to set up normal window behaviour in pekwm ? thanks ! cheers ! :)

---

### Post by jviscosi on 2008-06-24
> **canistra said:**
> how to set up normal window behaviour in pekwm ? thanks ! cheers ! :)

I'm not sure what you consider normal, but Urukrama has a very helpful [blog post]("http://urukrama.wordpress.com/2007/12/30/some-pekwm-configurations/") that I used as the basis for my pekwm settings.  That might help you out.

---

### Post by canistra on 2008-06-25
when I say normal , I mean a behaviour like in xfce or other normal WM // DE

---

### Post by lkajdflkjaoeif on 2008-07-02
> **jviscosi said:**
> I grabbed the git version and it still had the problem of windows not raising when clicking on them in the fbpanel taskbar, so I added a line to fbpanel's taskbar.c file (borrowed from the method that gets called when you right-click on the task icon and select "Raise", which *does* work) and that seems to have fixed it.  This is nasty and hackish, but it makes me happy; now I can move on to messing with my PekWM configuration ...

I can post the change I made to taskbar.c if anyone's interested, although I'm not sure this is the appropriate spot for that sort of thing.

Same problem here. Would be really nice if you could post your changes here. You should commit your changes or send a patch to the developers.

Thank you in advance,
lkajdflkjaoeif

---

### Post by jviscosi on 2008-07-03
> **lkajdflkjaoeif said:**
> Same problem here. Would be really nice if you could post your changes here. You should commit your changes or send a patch to the developers.

Thank you in advance,
lkajdflkjaoeif

Unfortunately I've found that it still doesn't work perfectly ... if the icon you're clicking on is the only window on another desktop, it will minimize/restore the window on the other desktop rather than taking you to that desktop and focusing the window.  I should fix that, but I've drifted back to OpenBox/Fluxbox due to some other niggling issues with PekWM (flaky behavior from some KDE applications, progress dialogs that get stuck and sticky across all desktops, etc.)  I'll probably try PekWM again after a few more releases because I did really like it.

When I get home, I'll post the change I made to fbpanel.  Maybe someone can take that and use it to fix the only-window-on-another-desktop issue.

---

### Post by jviscosi on 2008-07-04
Okay, here's the change I made to the fbpanel 4.12 source code that made it work better with PekWM.  It's still not perfect but I could live with it.  (I must qualify this code by saying that while I am a programmer, I'm not a C programmer, nor am I a programmer of X or window managers.)

This is in file plugins/taskbar.c.  The line I added is in bold just above *DBG("XRaiseWindow %x\n", tk->win);*

```

static void
tk_raise_window( task *tk, guint32 time )
{
    if (tk->desktop != -1 && tk->desktop != tk->tb->cur_desk){
        Xclimsg(GDK_ROOT_WINDOW(), a_NET_CURRENT_DESKTOP, tk->desktop, 0, 0, 0, 0);
        XSync (gdk_display, False);
    }
    if(use_net_active) {
        Xclimsg(tk->win, a_NET_ACTIVE_WINDOW, 2, time, 0, 0, 0);
    }
    else {
        XRaiseWindow (GDK_DISPLAY(), tk->win);
        XSetInputFocus (GDK_DISPLAY(), tk->win, RevertToNone, CurrentTime);
    }
    **XMapRaised(GDK_DISPLAY(), tk->win);**

    DBG("XRaiseWindow %x\n", tk->win);
}

```

---

### Post by lkajdflkjaoeif on 2008-07-06
Hello jviscosi,

sorry for the delayed response. I was quite busy the previous days. Today I've occupied myself with it again and spoke with some developers in #pekwm on Freenode about it. *shared* has found a solution for the problem. It seems to be a problem with PekWM. On page two of this thread *urukrama* has said that the bug has already been fixed in the Git version but the problem still persists in the most current version. Here is how to fix the raise issues in fbpanel; You need to add by add *raise();* before *giveInputFocus();* to pekwm/src/Frame.cc on line #2055. Note that this refers to the most current Git snapshot. To get the source, run *GIT_SSL_NO_VERIFY=true git clone [https://projects.pekdon.net/git/pekwm.git](https://projects.pekdon.net/git/pekwm.git)*. *GIT_SSL_NO_VERIFY=true* is necessary. Otherwise you might get messages like:
```
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?
``` By the way, in the latest snapshot there are some new workspace features such as *WorkspacesPerRow* (something like viewports but better), *WorkspaceNames* (you can now name your workspaces) and *ShowWorkspaceIndicator* (when moving to an other workspace, an indicator will show you all other workspaces and highlight the current one; it is similar to Compiz' indicator in GNOME).

Good luck.

Best regards,
lkajdflkjaoeif

---

### Post by jviscosi on 2008-07-06
> **lkajdflkjaoeif said:**
> Hello jviscosi,

sorry for the delayed response. I was quite busy the previous days. Today I've occupied myself with it again and spoke with some developers in #pekwm on Freenode about it. *shared* has found a solution for the problem. It seems to be a problem with PekWM.

Oh, so it's not an fbpanel issue!  Cool, thanks for finding out this information!  I'm actually back on PekWM because I liked it so much, I decided to tolerate the fbpanel issue and use different applications that play more nicely with it.  I made several attempts to fix fbpanel the rest of the way but wasn't successful, so I will make this source change and see how it works.

---

### Post by canistra on 2008-07-08
Hi there, i've got a question related pekwm, I use bmpanel, and vlc to watch videos, but when i Fullscreen the video, it stays below the panel, and i need everytime to close the bmpanel when I want to watch videos, how can i fix this ? thx in advance ...

---

### Post by lkajdflkjaoeif on 2008-07-08
> **canistra said:**
> Hi there, i've got a question related pekwm, I use bmpanel, and vlc to watch videos, but when i Fullscreen the video, it stays below the panel, and i need everytime to close the bmpanel when I want to watch videos, how can i fix this ? thx in advance ...

You need to change the autoproperties for the BMPanel. Here are the settings for my fbpanel (put them into ~/.pekwm/autoproperties):

> Property = "panel,fbpanel" {
	applyon = "start new reload";
    skip = "menus focustoggle";
	sticky = "true"; titlebar = "false"
	border = "false"; layer = "normal"
}

---

### Post by canistra on 2008-07-08
> **lkajdflkjaoeif said:**
> You need to change the autoproperties for the bmpanel. Here are the settings for my fbpanel (put them into ~/.pekwm/autoproperties):

that didn't really helped :(

---

### Post by lkajdflkjaoeif on 2008-07-08
> **canistra said:**
> that didn't really helped :(
It does but you have to modify it for the BMPanel. I am using fbpanel so that I cannot tell you how to do it with BMPanel, sorry. I guess, you just have to replace "fbpanel" by "bmpanel" but I do not know whether it works.

---

### Post by canistra on 2008-07-08
> **lkajdflkjaoeif said:**
> It does but you have to modify it for the BMPanel. I am using fbpanel so that I cannot tell you how to do it with BMPanel, sorry. I guess, you just have to replace "fbpanel" by "bmpanel" but I do not know whether it works.

well of course I replaced it, and it didn't work :( 

This problem remains open, but I'll give u another one :) when i use conky it is shown in task list in my bmpanel, how to fix that ?

---

### Post by lkajdflkjaoeif on 2008-07-08
> **canistra said:**
> well of course I replaced it, and it didn't work :( 

This problem remains open, but I'll give u another one :) when i use conky it is shown in task list in my bmpanel, how to fix that ?

I have set this in my .conkyrc:
> own_window yes
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,skip_pager,skip_taskbar

---

### Post by canistra on 2008-07-09
> **lkajdflkjaoeif said:**
> I have set this in my .conkyrc:

haha ! big thanks for that !!

But can someone help me with the vlc and bmpanel problem, that's very important for me :(

---

### Post by urukrama on 2008-07-09
> **canistra said:**
> But can someone help me with the vlc and bmpanel problem, that's very important for me :(

You'll have to use the autoproperties file, as lkajdflkjaoeif suggested. The important thing is to get the Property right. To do so, type the following in a terminal:

> xprop WM_CLASS

Your mouse cursor should turn into a cross. Click on the application you are interested in (in this case BMpanel). You should get something like the following in the terminal:

```
WM_CLASS(STRING) = "urxvt", "URxvt"
```

(This is using urxvt as an example. I don't have BMPanel installed on this computer, otherwise I would given that as an example.)

The two terms above ('urxvt' and 'URxvt') is what you need. It is case sensitive. Add those terms to the Properties line in your autoproperties file, preceded by ^:

> Property = "**^PROP_1**,**^PROP_2**" {
applyon = "start new reload";
skip = "menus focustoggle";
sticky = "true"; titlebar = "false"
border = "false"; layer = "normal"
}

You'll have to restart Pekwm for the changes to take effect.

If you need more info, the [Pekwm documentation on autoproperties]("http://adresh.com/pekwm/015_docs/html/config/autoprops.html") is good.

I hope this helps.

---

### Post by canistra on 2008-07-09
> **urukrama said:**
> You'll have to use the autoproperties file, as lkajdflkjaoeif suggested. The important thing is to get the Property right. To do so, type the following in a terminal:



Your mouse cursor should turn into a cross. Click on the application you are interested in (in this case BMpanel). You should get something like the following in the terminal:

```
WM_CLASS(STRING) = "urxvt", "URxvt"
```

(This is using urxvt as an example. I don't have BMPanel installed on this computer, otherwise I would given that as an example.)

The two terms above ('urxvt' and 'URxvt') is what you need. It is case sensitive. Add those terms to the Properties line in your autoproperties file, preceded by ^:



You'll have to restart Pekwm for the changes to take effect.

If you need more info, the [Pekwm documentation on autoproperties]("http://adresh.com/pekwm/015_docs/html/config/autoprops.html") is good.

I hope this helps.

thanks for the answer, but when i click on bmpanel with the click from WM_CLASS it says WM_CLASS: not found :(

---

### Post by urukrama on 2008-07-09
What about xprop WM_NAME?

Some applications don't have either, though, and don't behave very nicely in Pekwm (skippy is another one of those).

---

### Post by canistra on 2008-07-09
> **urukrama said:**
> What about xprop WM_NAME?

Some applications don't have either, though, and don't behave very nicely in Pekwm (skippy is another one of those).

the same thing :((

---

### Post by lkajdflkjaoeif on 2008-07-23
Thanks urukrama, I did not know about xprop. > xprop WM_CLASS is not working for BMPanel because it does not set the WM_CLASS property whereas fbpanel sets it in panel.c: > gtk_window_set_wmclass(GTK_WINDOW(p->topgwin), "panel", "fbpanel"); I modified the main-function in bmpanel.c a bit so that it sets the WM_CLASS property of the window. The difference to the method of fbpanel is, that we have to use the X-functions. fbpanel is GTK-based.

Sorry, I am no C programmer. I copied parts from other code I found using Google but it seems to work. :)

> int main(int argc, char **argv)
{
	XClassHint		*classHint;

	log_attach_callback(log_console_callback);
	parse_args(argc, argv);
	LOG_MESSAGE("starting bmpanel with theme: %s", theme);

	initX();
	initP(theme);
	init_render(P.theme, X.display, P.win, X.visual, X.colmap, P.width);

	signal(SIGHUP, sighup_handler);
	signal(SIGINT, sigint_handler);

	rebuild_desktops();
	update_tasks();

	render_update_panel_positions(&P);
	render_panel(&P);

    /* Set ClassHint */
    if (! (classHint = XAllocClassHint())) {
		printf("Can't allocate memory for class hints!\n");
		cleanup();
		exit(1);
	}

    classHint->res_name  = "panel";
    classHint->res_class = "bmpanel";

    XSetClassHint(X.display, P.win, classHint);
    XFree(classHint);

	init_and_start_loop();

	cleanup();
	return 0;
}

Now xprop shows:
> tim@tim-laptop:~$ xprop WM_CLASS
WM_CLASS(STRING) = "panel", "bmpanel"

By the way, the issues when raising a window in those panels have now been officially fixed: [http://pekwm.org/projects/3/commits/1604](http://pekwm.org/projects/3/commits/1604). Hopefully the new version will be released soon.

---

### Post by jviscosi on 2008-07-23
For anyone who's interested, the latest version of PekWM from git solves [some problems]("http://ubuntuforums.org/showthread.php?t=828604") I was having with KDE applications like Amarok and Klipper.

---

### Post by Just-trevor on 2008-08-07
>  Re: Howto: Install and configure Pekwm
It might help others who have the same problem if you posted your solution here. 
for example, it would really help me

---

### Post by jviscosi on 2008-08-14
Should I be worried that pekwm.org has been MIA for two days?

EDIT:  It's back.

---

### Post by kimara on 2008-08-17
Hi all!!

Anyone know, how to run Pekwm with Gnome?

Kimmo

---

### Post by jviscosi on 2008-08-19
> **kimara said:**
> Hi all!!

Anyone know, how to run Pekwm with Gnome?

Kimmo

I think you can just kill the window manager, start Pekwm, and then save the session, or you can edit the Gnome startup items to start Pekwm instead of Metacity (or Compiz).  There might be something in the Gnome control center or gconf-editor that tells it what window manager to use, I'm not sure.  Or you could just start the Pekwm session and then start the Gnome session manager and the other parts of Gnome you want, like the panel or whatever.

I've never used Gnome all that much, so somebody who has might be able to offer better (or easier to follow) advice ...

---

### Post by urukrama on 2008-08-21
Since a new version of Pekwm has been released, I've updated the guide to help you all install Pekwm 0.1.7

There might be a few more changes that I've missed. If you find some, please let me know.

---

### Post by InfinityCircuit on 2008-09-01
I am now the Debian Maintainer for pekwm, and have just pushed the update to 0.1.7 along with a few bug fixes to the buildds through my sponsor.  For those who run Ubuntu Hardy Heron, I have made a backport of the pekwm deb on my ppa:

[https://launchpad.net/~dmoerner/+archive](https://launchpad.net/~dmoerner/+archive)

It is now built and uploaded.

---

### Post by InfinityCircuit on 2008-11-04
I have pushed pekwm-0.1.8 to my PPA; pekwm has now also has an integrated debian-menu.

---

### Post by urukrama on 2008-12-17
I've updated the guide for Pekwm 0.1.8. If you find anything I forgot to change, please let me know.

---

### Post by InfinityCircuit on 2009-01-11
I now have pekwm-0.1.9a backports for both Hardy and Intrepid on my PPA.

---

### Post by InfinityCircuit on 2009-01-31
They have changed the PPA addresses a bit.

The PPA is now at:

```
deb http://ppa.launchpad.net/dmoerner/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/dmoerner/ppa/ubuntu intrepid main
```

I have just pushed pekwm-0.1.10 to this, and I will request a sync for Jaunty. I didn't provide a hardy backport this time since it's a pain to revert back from dh 7.

These packages now include the upstream's contrib/ scripts, which allow automatic savings of autoproperties and manipulation of the theme. Read /usr/share/doc/pekwm/README.Debian for more information.

---

### Post by Danyael X on 2009-02-03
I FUBAR:ed with mmaker and didnt backup the original menu config file ](*,) . I cant find the default files on pekwm.org or anywhere else on the  net. 

Could someone please post the default config files here in their entirety so that people like me can undo their folly? 	[-o<

Or perhaps send the files to me in a PM (though a forum post would benefit the general public)

Big thanks for any help you can give me on this topic!

Chris

---

### Post by Danyael X on 2009-02-03
I use 1.10.0 compiled from source and the files I'm looking for doesn't exist as back ups in /usr/share/docs/pekwm unfortunately

---

### Post by Danyael X on 2009-02-03
ah.. found it with the help of the nice ppl at #pekwm @ freenode. it's in /usr/local/etc/pekwm yay!

chris

---

### Post by InfinityCircuit on 2009-02-03
For future reference, you can always grab the menu file from the Debian git:

[http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=data/menu.in;h=2b8998c8847edc5dc256d8284c509d9f2627617c;hb=HEAD](http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=data/menu.in;h=2b8998c8847edc5dc256d8284c509d9f2627617c;hb=HEAD)

Patch to install default menu as distributed in Debian:

[http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=debian/patches/make-new-default-menu.diff;h=15f3341d8727f546eb040823905329e35d7a5a28;hb=HEAD](http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=debian/patches/make-new-default-menu.diff;h=15f3341d8727f546eb040823905329e35d7a5a28;hb=HEAD)

---

### Post by alelinuxbsd on 2009-03-01
I am using pekwm from some day someone may help to resolve some doubts?

I read the documentation but I am not clear how to proceed.

I would have, at the bottom of the system:
the current date of the system, 
the percentage of processor usage 
the bandwidth (up and down) of internet.

Thanks.

---

### Post by InfinityCircuit on 2009-03-01
Use conky.

---

### Post by alelinuxbsd on 2009-03-02
Initially I had thought of dockapps but in the end I think that Conky is the best choice.

Thanks for the suggestions. :)

Note:
Now i see the topic:
[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by alelinuxbsd on 2009-03-03
I have two questions based on keys files:
1) How create an action - assigned to one key combination - that iconified all the frame on the desktop?
2) How create an action to reverse?

---

### Post by j0nash on 2009-03-27
Hi everybody

I have some trouble trying to use various themes.  I download the
themes from box-look.org, unpack them and move them to either
~./pekwm/themes or /usr/share/pekwm/themes

But when I try to use them it just looks reallt messed up.

[http://custor.rejas.se/~jonash/2009-03-27-000822_800x480_scrot.png](http://custor.rejas.se/~jonash/2009-03-27-000822_800x480_scrot.png)

My menu looks weird and I loose all decor (titlebar and borders) for
all applications.

I wonder if this has to do with the fact that I am using version 0.1.5

$ pekwm --info
pekwm: version 0.1.5 Built on Sat Apr 12 05:35:41 UTC 2008
features:  XShape Xinerama Xrandr Xft pcre image-xpm image-jpeg
image-png menus harbour

The ugly blue defualt theme works fine, but that's about it.

Does anyone have a clue what this is all about?

thanks

ps is something wrong with the pekwm mailinglist, or am I just dumb. I've joined and tryed to send a mail and all I got back was:
[I] This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]pekwm-users@lists.pekwm.org[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.1.1 <pekwm-users@lists.pekwm.org>: Recipient address rejected: User unknown in local recipient table (state 14).[/I]

---

### Post by InfinityCircuit on 2009-03-27
It definitely has to do with your decision to use 0.1.5. There is not really support for backwards compatibility in themes. You should upgrade to 0.1.10.

---

### Post by j0nash on 2009-03-28
I successfully upgraded to the newest version of pekwm. But I still got this strange problem. Only the default theme works...

When I try to change theme in the menu nothing happends.

When I try to do it manually by only having my wanted theme in ~/.pekwm/themes or /usr/share/pekwm/themes it's like I had no theme at all. My menu looks messed up and all my decor is lost.:(
and it's the same problem with all themes

Is there any other program or lib that I must install to get this to work?

Please help me someone

---

### Post by InfinityCircuit on 2009-03-28
How are you installing the theme? You should untar the theme into the ~/.pekwm/themes directory such that there is a directory with the theme name in it. The script in the menu only searches for directories inside ~/.pekwm/themes. (Blame me for this, I wrote the patch that causes this to fix another bug :))

---

### Post by InfinityCircuit on 2009-06-01
I have now packaged Adriano Foschi's contributed pekwm themes ([http://adrinux.wordpress.com/pekwm-themes/](http://adrinux.wordpress.com/pekwm-themes/)) for Debian. If you want to install them on Ubuntu just fetch them from my alioth space:

[http://alioth.debian.org/~dmoerner-guest/pekwm-themes_1.0.5-1_all.deb](http://alioth.debian.org/~dmoerner-guest/pekwm-themes_1.0.5-1_all.deb)

---

### Post by truecolor on 2009-06-10
[[color=#FFFFFF]_simulation credit auto_[/color]](http://simulationcreditauto.net/)
Great stuff, Thanks for the quality tutorial :D

---

### Post by j0nash on 2009-07-08
Hi again.
I'm having problems to fully understand the autoproperties and I wonder if someone could help me with a couple of small things:

1.
I use conky. And it's all of my my four workspaces but I only want it to appear on workspace 1, how can this be done?

2.
I have this settings for aterm:
```

Property = "^aterm,^XTerm" {
        ApplyOn = "Start New"
        FrameGeometry = "69+33+0+0"
        Border = "False"; Titlebar = "False"
        #Sticky = "True"
        Layer = "Desktop"
}
```

In my pekwm start-file I have aterm & and conky &
I would like aterm to have a a titlebar, but just that one that startups 
first, all other aterm's should be normal: Border = "False"; Titlebar = "False"
I would also like this startup aterm to be set as taged and prehaps as a group and with a xterm.

Could someone help me out a bit?

---

### Post by the dsc on 2009-08-01
PekWM seems good :D. Anyone knows if it is possible to do three things:

- raise windows without clicking, when hovering with the cursor, *but with a delay of a few milliseconds* (just like it's possible in fluxbox and openbox)

- some other way than a panel to have a system tray (a pipemenu, maybe)

- some way to have a clock on the title bar? Just on the active one, that's how I think it would be nice.



I think that the replacement of the taskbar by the title bar would be the logic move for those minimalistic WMs, but funnily enough I think that the titlebar is always underexploited. On openbox I was using it to call either both the root-menu (right click) and the menu with all the windows (middle click). So I don't need to have some empty space to call the root-menu.

Apparently just by touching the border of the screen you achieve the same result on pekwm, that's somewhat nice too, but I'll make some adjustments to be just like I've used to have on openbox.

---

### Post by kevinguillorytraining on 2009-10-09
this is great... thanks alot... will surely play with it

---

### Post by renkinjutsu on 2009-10-12
anyone gotten xcompmgr to do it's job properly in pekwm?
anything composited looks like crap with black spaces all over (gnome-do docky awn etc.)

This bug is ages old!

---

### Post by Gorgamel on 2009-10-21
Anyone that have installed 0.1.11 successfully?
For me it installed just fine, but as I tried to log in it said that there were no 'Exec line' in the session file.

Have tried to look around on forums and comparing to the gnome file. But to me it seems that it is PekWM that is faulty on this one.

---

### Post by urukrama on 2010-02-24
I have updated the tutorial for Pekwm 0.1.11.

---

### Post by mayacreator on 2010-04-14
Hi. I have a problem, my pekwm freezes from time to time, window buttons became inactive, right-click menu does not work too. It lasts about one minute and then anything works fine again. Does anybody know how to fix this bug?

---

### Post by TheDexter1111 on 2010-10-01
thank you very much for the awesome tutorial.

I've installed pekwm on my ubuntu lucid and the only thing i cant figure out is how to get my wireless to connect..?? 

also how to set wallpaper? do i need somthing like jdesk?

thanks :D

---

### Post by TheDexter1111 on 2010-10-02
Im also having trouble browsing files... is there a file browser in pekwm? anything equivalent to nataulis? 

also, I've edited the menu with things such as Exec = $firefox and Exec = $thunderbird but they dont execute... am I doing this correctly? I can launch them in the terinal but want them to be in my menu...  

still also no wireless conection :(

---

### Post by TheDexter1111 on 2010-10-04
> **TheDexter1111 said:**
> Im also having trouble browsing files... is there a file browser in pekwm? anything equivalent to nataulis? 

also, I've edited the menu with things such as Exec = $firefox and Exec = $thunderbird but they dont execute... am I doing this correctly? I can launch them in the terinal but want them to be in my menu...  

still also no wireless conection :(

right, so forget file browser, i figured that out :P (was a bit drunk when trying to use pekwm for the first time.. bad idea) but still no luck on the wireless or sucessfully editing the menu... at the moment im launching everything from the terminal :P

---

### Post by casbahdk on 2010-11-07
> **mayacreator said:**
> Hi. I have a problem, my pekwm freezes from time to time, window buttons became inactive, right-click menu does not work too. It lasts about one minute and then anything works fine again. Does anybody know how to fix this bug?

Did you find a solution to your issue? I am having a similar problem. The thread is here - [http://ubuntuforums.org/showthread.php?p=10083828#post10083828]("http://ubuntuforums.org/showthread.php?p=10083828#post10083828")

---

### Post by sosek on 2011-04-14
Hi, 
I've got a strange problem with pekwm - it doesn't keep the settings from gnome-appearance-properties . Every time i'm starting the WM, I need to run the properties once again to have the shape and colors of windows I've defined before. Does anyone know the solution to this problem?

:)

---

