---
title: "HOW-TO: Install, Customize, and Configure Openbox (lots of options)"
date: 2006-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by raublekick on 2006-06-08
Welcome to my Openbox guide. First, I must thank Fuscia, Stormy Eyes, benplaut the Gentoo and Ubuntu wiki pages. I plan to cover the installation and customization of Openbox as far as use and looks go. I am assuming that you have installed Ubuntu 6.06 with the full Gnome set up. If you are using Kubuntu, Xubuntu, or a server install, some things may change. I may or may not cover those areas. This guide will not cover how to integrate OpenBox into Gnome, KDE, or any other DE. Sorry if you find this a little (or a lot) verbose, but I hate reading guides that leave gaps. So, if I leave some gaps, let me know and I will try to fill them in. 

If you want a pure OpenBox installation without the requirement of Gnome, see [here.]("http://doc.gwos.org/index.php/Openbox_GnomeStraight")

For themes please see 
[http://www.boxwhore.org/modules/news/](http://www.boxwhore.org/modules/news/)
[http://hewphoria.com/?p=submission&type=theme&cat=7](http://hewphoria.com/?p=submission&type=theme&cat=7)


All of my instructions are based on using the command line. 


**[SIZE="6"]Installation:[/SIZE]**
To install Openbox, all that is necessary is
```
sudo apt-get install openbox
```

I recommend installing the themes, obconf, and pypanel as well.
```
sudo apt-get install openbox obconf openbox-themes pypanel
```

Now you are ready to use Openbox. Log out, and at the login screen select Openbox under sessions. 

Upon entry into Openbox you are provided with nothing more than a mouse cursor. Right-clicking will bring up the root menu, and as you will see it is pretty minimal, but provides all that you need to go on (the terminal). 



**[SIZE="6"]Setting Up the Menu:[/SIZE]**
The menu is the most important part of Openbox usability (in my opinion). The most basic way to edit the menu is to edit the menu.xml file. I will list three methods to edit the menu, which method you choose is up to you but I suggest checking out each method before actually editing the menu. In my opinion it is much easier to trim down a bloated menu than build up an empty menu. Thus, my reccomended method for seting up the Openbox menu is to run menumaker first and then use the XML or obmenu to trim it down.  

First, copy the default menu into your $HOME/.config/openbox directory.
```
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
```

*Important!* Every time you edit the menu, you must reconfigure by right-clicking to bring up the root menu and selecting reconfigure.

**A.) Edit the raw XML**
This method deals with editing the raw XML. Open the file by using
```
gedit ~/.config/openbox/menu.xml
``` 

Here you can see how to format the XML to add entries. This is about as far as I'll go here, because there are much easier ways to edit the menu, but this method can be very fast. 

**B.) Use obmenu**
The second method uses obmenu to edit the menu entries in a graphical interface. It is very easy to use and can create sub-menus and seperators. Obmenu must be installed from source, and has three dependencies that can be filled through apt/synaptic.

The obmenu homepage is here: [http://obmenu.sourceforge.net/index.html](http://obmenu.sourceforge.net/index.html) and the download page is here: [http://obmenu.sourceforge.net/download.html](http://obmenu.sourceforge.net/download.html)

1. To install the dependencies
```
sudo apt-get install python2.4 python2.4-glade2 python2.4-gtk2
```
The glade and gtk2 parts might be wrong, but I am fairly certain they are correct. 

2. Now to install obmenu simply
```
tar xzvf ~/obmenu-1.0.tar.gz
cd obmenu-1.0
sudo python setup.py install
```

3. Run obmenu
```
obmenu
```

4. Add entries, save, and reconfigure. 

I suggest adding obmenu first, so you have easy access to it. Also add obconf as well if you installed it. 

**C.) Use menumaker**
Menumaker is a tool that will generate a full menu of (almost) everything you have installed. Menumaker can be installed or run from the source tarball. I will show you how to use it without installing it.

1. Download the latest version here: [http://sourceforge.net/projects/menumaker](http://sourceforge.net/projects/menumaker) and unpack it
```
tar xzvf ~/menumaker-0.99.7.tar.gz
```

2. Go into the menumaker dir and run mmaker
```
cd ~/menumaker-0.99.7/
./mmaker OpenBox3
```

3. Reconfigure

Like magic, you have a new menu. Menu maker moves the reconfigure option into the OpenBox sub-menu. Now you have a pretty much fully working set up, but if you're like me, you want a clock, a panel, and a desktop bg, as well as some better looking themes. 



**[SIZE="6"]Setting the Background Image:[/SIZE]**
This one is simple, install feh if you don't have it. 
```
sudo apt-get install feh
```

Then simply run
```
feh --bg-scale path/to/the/image.ext
```
ex: feh --bg-scale ~/backgrounds/desktop.jpg

Be warned that the image will reset when you log out and back in. I will cover this soon. 



**[SIZE="6"]Installing and Using Themes and Window Decorations:[/SIZE]**
I will instruct you on how to install the exact theme and window decoration I use. 

Window decorations can be extracted to your .themes directory and changed in obconf.
1. Download the clearlooks-olive theme from here [http://hewphoria.com/get.php?t=theme&id=129](http://hewphoria.com/get.php?t=theme&id=129) and save it to your home folder.

2. Move the theme to .themes and extract it
```
mv ~/clearlooks-olive-0.2.tar.gz ~/.themes/clearlooks-olive-0.2.tar.gz
tar xzvf ~/.themes/clearlooks-olive-0.2.tar.gz
```

3. Open obconf (either from the menu or command line) and select Clearlooks-Olive from the list under Appearance.


Now, to get rid of those nast GTK controls. This part is pretty easy too, but for some reason the themes installed with Gnome don't work for me, so you have to extract your own to .themes like above. 

1. Download the Olive Suite theme from gnome-look.org here [http://www.gnome-look.org/content/download.php?content=35572&id=1](http://www.gnome-look.org/content/download.php?content=35572&id=1)

2. Move the theme to .themes and extract it, just like above but replace the file name. 

3. Install switch2
```
sudo apt-get install gtk-theme-switch
```

4. Run switch2 and select Olive, apply. 

Now you should have a much nicer looking windows and control scheme for GTK apps. 



**[SIZE="6"]Installing and Using a Panel:[/SIZE]**
If you haven't already, install pypanel. There are several other panels you can use, but pypanel is in the repos and easy to use. 
```
sudo apt-get install pypanel
```

To use pypanel, just run pypanel from the command line or add it to the menu. Pypanel can be configured through editing .pypanelrc found in your home directory. 


[B][SIZE="6"]
Getting Backgrounds and Panels to Show Up at Start:[/SIZE][/B]
I originally used the .xsession method, but benplaut provided a much more generic way to go about it. This is pretty much verbatim what he outlined in here [http://ubuntuforums.org/showpost.php?p=1109058&postcount=22](http://ubuntuforums.org/showpost.php?p=1109058&postcount=22)


First, make the file ~/.config/openbox/autostart.sh. In it modify the following to fit your needs.
```
gedit ~/.config/openbox/autostart.sh
```

Panels usually cooperate better if you let them load after the WM, so this is a bit different from others.

```
#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi
```

*Rauble's note* I commented out gnome-volume-manager and gnome-settings-daemon. These are not necessary but can be very useful. If you cannot use CDs, uncomment the gnome-volume-manager line. For me, my extra harddrive and CD-ROM drives work without it. **

Panels are finicky... the little thing at the end should help.

OK, here's for gdm:

First,
```
chmod +x ~/.config/openbox/autostart.sh
```

Now, edit the session file:
```
sudo gedit /usr/share/xsessions/openbox-autostart.desktop
```

and insert the following into the file:

```
[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/home/dapper/.config/openbox/autostart.sh 
Icon= 
Type=Application
```

Note: Edit the Exec line to match your user account

finally,
```
sudo chmod +x /usr/share/xsessions/openbox-autostart.desktop
```

(i'm not sure if that's required, but it can't hurt)

Now you must restart and log into the OpenBox Autostart session
```
sudo reboot
```


[B][SIZE="6"]
Using OpenBox Like a Pro:[/SIZE][/B]
Stormy Eyes has a great how-to here: [http://doc.gwos.org/index.php/Openbox_Gnome](http://doc.gwos.org/index.php/Openbox_Gnome) . It describes many things I have gone over, as well as how to add keybindings. I will leave his explaination be and just go over some extra stuff. 

Adding the following provides an easy way to capture screenshots.
```
  <keybind key="A-F11">
    <action name="execute"><execute>gnome-screenshot</execute></action>
  </keybind>
```

OpenBox has some great keybindings by default. Some of my favorites are the following:
alt-F10 (A-F10): Maximize window
alt-F5 (A-F5): Unmaximize window
alt-F12 (A-F12): Roll up window
ctrl-alt-left/right: switch to next/previous desktop
shift-alt-left/right (S-A-Left/Right): switches and sends program to next/previous desktop
ctrl-alt-d (C-A-d): show desktop (minimize all windows)

You may also want menu entries for reboot and shutdown. Logging out of openbox has been finnicky for me, sometimes it just goes to a light blue, hard to see login screen. So, here are some menu entries to try:
add a command for "sudo reboot" to restart the computer
or "sudo shutdown -t now" to shutdown
More info can be found here: [http://enterprise.linux.com/article.pl?sid=05/05/04/1219226&tid=89](http://enterprise.linux.com/article.pl?sid=05/05/04/1219226&tid=89)



**Credits:**
(I basically compiled a lot of good information into one source that makes it easy for me to follow, hopefully it will be easy for new OpenBox users as well)

[Random Openbox Chatter]("http://ubuntuforums.org/showthread.php?t=190476")

[Linux.xom | CLI Magic: shutdown]("http://enterprise.linux.com/article.pl?sid=05/05/04/1219226&tid=89") - Using the command line for shutdown commands. 

[OpenBox Gnome]("http://doc.gwos.org/index.php/Openbox_Gnome") - Stormy Eyes' HOW-TO on configuring OpenBox on its own and with Gnome. 

[Openbox - Ubuntu Wiki]("https://wiki.ubuntu.com/Openbox") - Ubuntu's wiki entry, good info but some of the suggestions are not preferred by me (like using Rox-filer)

[Gentoo Openbox Entry]("http://gentoo-wiki.com/HOWTO_Openbox") - Some great technical info.


*To be added*
- Using and configuring idesk
- Better use of docks and panels

---

### Post by Hanj on 2006-06-08
Nice howto! =D>  Just one suggestion:
If you start gnome-settings-manager at startup, you can launch the Gnome theme manager by executing gnome-theme-manager. It's better than gtk-theme-switch (at least IMO) and also gives you control over icon themes.

---

### Post by raublekick on 2006-06-08
ah, excellent for pointing that out! i figured that was the key, but using switch2 still didn't work... i didn't think to use the Gnome switcher! i'll add that in later.

---

### Post by Hanj on 2006-06-08
Oh, and one more thing: laptop users may want to add gnome-power-manager to their autostart script. If you run gnome-power-preferences after this you can  check "Always display icon" to get a battery indicator on your pypanel (only need to check this once).

---

### Post by bionnaki on 2006-06-08
screenshots?

---

### Post by Hanj on 2006-06-08
Here's one screenshot. Very minimalistic, but that's the reason I use OpenBox.
[IMG]http://85.8.5.144/filer/Screenshot.png[/IMG]

---

### Post by raublekick on 2006-06-08
[http://ubuntuforums.org/gallery/showimage.php?i=2818&original=1&c=13](http://ubuntuforums.org/gallery/showimage.php?i=2818&original=1&c=13)

there is my screen. i'll fix up my first post later tonight or tomorrow.

---

### Post by benplaut on 2006-06-09
i've got a bad feeling about the 'feh' line... i wouldve done it:

feh --bg-scale `cat $HOME/.fehbg` &

not sure what the diff is, tho.

Tomorrow i'll write up something on configuring idesk... it's pretty easy, especially with idesktool.

---

### Post by wtfacoconut on 2006-06-09
what about one of those DOCK thingies that I've heard that you cand use with openbox? How do you install and configure it for openbox? Sry If I missed anything.

---

### Post by fuscia on 2006-06-09
nice howto, dude. you may want to include instructions on how to get to openbox using *startx* (edit .xinitrc to say *exec openbox*). and you might want to have some links to some of the more hardcore minimal apps (dillo, links2, sylpheed-claws, etc.). i'm glad you warned everyone about the blank screen. somewhere on here, there is a thread of mine whining about openbox not working.

---

### Post by dimaash on 2006-06-10
I am having problems with swtich2 and gtk-engines. Basically when i run switch2 (to get a nicer look for gtk apps) i get the following:
```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
```, i tried to fix by apt-get'ing gtk-engines-pixmap but it didnt help. I guess i have to set it up somehow.

Runing openbox3; themes are in ~/.themes/

Any suggestions?
thx.

---

### Post by GarethMB on 2006-06-12
gtk theme switch has screwed my gnome themes. Now i have to use switch2 as well as the gnome theme manager to get gnome themes to display correctly.

I'd like to remove switch2 and restore gnome theme manager to its usual self. I tried purging gtk theme switch but no luck. What do i have to do.

---

### Post by saax on 2006-06-17
have Kubuntu 6.06 and installed Openbox.

I install bbpager ,but when i try to open it,i get this error 
ueulo@ubuntu:~$ bbpager
*** glibc detected *** free(): invalid pointer: 0x10056300 ***
Aborted
 
and how do i know what start up session i have ,should i edit .xinitrc or .xsession 

PLease help me

---

### Post by fuscia on 2006-06-18
[QUOTE=saax]
and how do i know what start up session i have ,should i edit .xinitrc or .xsession [/QUOTE]

if i'm not mistaken...if you're using *startx*, you would edit .xinitrc (*exec openbox*). if you're using a display manager and you installed openbox using synaptic, it should automatically appear in the sessions menu of the display manager (i've never used kdm or xdm, but this is true of both gdm and wdm). i don't know how to add openbox to a display manager if you installed openbox from source.

---

### Post by johannes on 2006-06-28
Thanks for this guide!

I made a Ubuntu Human-like theme for Openbox. I thought I should share it if anyone else wants it. It's attached to this post.

[[IMG]http://img399.imageshack.us/img399/1032/screenshot2av.th.png[/IMG]](http://img399.imageshack.us/my.php?image=screenshot2av.png)

To have the window titles look like in the screenshot you need to compile Openbox with the [split gradient patch]("https://bugzilla.icculus.org/attachment.cgi?id=836")

Here is how you can do it:
Save the patch text to a file named "split_gradient.patch" in your home folder.

Open a terminal and type:
```
sudo apt-get build-dep openbox
sudo apt-get install checkinstall
wget http://icculus.org/openbox/releases/openbox-3.3-rc2.tar.gz
tar -xzvf openbox-3.3-rc2.tar.gz
cd openbox-3.3-rc2
patch -Np1 -i ../split_gradient.patch
./configure --with-x --disable-nls
make
sudo checkinstall
```
Follow the instructions and install the new package with:
```
sudo dpkg -i <package-name>
```
And enjoy the latest (to this date) Openbox with nice window titles! :)

---

### Post by blacknyx on 2006-07-01
I don't know what's wrong.  But after I opened up obmenu and configured it.  
I tried to open it and got
Error: "/home/rain/.config/openbox/menu.xml" not found
How do I specify where I want the menu.xml to be located at?  Should I be untar-ing the entire folder IN the openbox folder in /rain?

Sorry sometimes I'm such a newbie I can't stand myself!!

---

### Post by TheDarrellMan on 2006-07-02
after i did ./mmaker OpenBox3 it didn't change anything about my right click menu at all..any suggestions? :-?

---

### Post by PenguinZdravko on 2006-07-07
When I try to run menumaker, i get the following error:
penguinzdravko@ghostwheel:~/menumaker-0.99.7$ ./mmaker OpenBox3
> Traceback (most recent call last):
  File "./mmaker", line 2, in ?
    import MenuMaker.CLI
  File "/home/penguinzdravko/menumaker-0.99.7/MenuMaker/CLI.py", line 227, in ?
    desktop = Prophet.Desktop.scan()
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 153, in scan
    result.append(App(os.path.join(w[0], x)))
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 266, in __new__
    self.__setup__(desktop)
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 286, in __setup__
    super(App, self).__setup__()
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/__init__.py", line 265, in __setup__
    self.setExename()
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 329, in setExename
    self.testGoodness(cmd)
  File "/home/penguinzdravko/menumaker-0.99.7/Prophet/__init__.py", line 261, in testGoodness
    if _shStart.search(cmd) or _shComplexCmd.search(cmd) :
TypeError: expected string or buffer


---

### Post by jurgnn on 2006-08-18
Is there way to change how 'show desktop' works with openbox?

In openbox 'show desktop' minimizes all windows, but when I unminimize one window from gnomepanel, it unminimizes all windows that I had before pressing 'show desktop'.
 
With metacity it unminimizes only the one that I asked.
I have openbox with gnome, nautilus is removed if that matters.

---

### Post by moore.bryan on 2006-08-26
*this was a great howto... good work raublekick.  i have one, kind-of, specific question.  i'm trying to get my gdesklets to autostart at the beginning.  when i add "gdesklets start" to the autostart.sh file, each starts in its own window.  any ideas?*

---

### Post by linuxismywife on 2006-08-26
cp: cannot create regular file `/home/leslie/.config/openbox/menu.xml': No such file or directory


anyone knows whats the reason?? i cant complete this step..

---

### Post by fuscia on 2006-09-02
> **linuxismywife said:**
> cp: cannot create regular file `/home/leslie/.config/openbox/menu.xml': No such file or directory


anyone knows whats the reason?? i cant complete this step..

see if there is a *menu.xml* file in */etc/X11/openbox*. if there is, check and make sure it's not empty, then copy it to */home/leslie/.config/openbox/*.

---

### Post by Shane10101 on 2006-09-03
Thanks for the great how-to!  It's just what I was looking for...and in just a second here, I'll find out whether it's worked for me ;)

I do have a question about the thing you did at the end, to make sure pypanel doesn't load before openbox:  Full disclosure:  I don't know the first thing about the language this is written in (C??), so forgive me if I'm way off-base here...but It looks like the idea is to see whether pypanel is loaded -- if it isn't, it's because it's failed, and so it's re-loaded at the same time as openbox is executed.  

If this is the case, isn't it possible that pypanel could be loaded, but about to fail at the time of the check ("pgrep"??), and wind up failing before openbox finishes executing??  Why use this method instead of loading pypanel in some other way, after openbox executes?  Maybe a time-delay or something.  (Again, I'm still really new to linux, so I'm not sure what's possible.)

Just wondering. 

Thanks again, and keep y'er fingers crossed!  (Rebooting now.)

;)

Shane

---

### Post by moore.bryan on 2006-09-10
*has anyone else had the problem of obconf not changing the theme?  i just ran into this... looks like i'll have to change it in rc.xml.*

---

### Post by SlugO on 2006-10-22
I compiled and installed Openbox 3.3.1 successfully but it won't add an entry to GDM's menu. Changing back to the repository version does add it.

Any idea how to compile the latest Openbox so that it will add a menu entry to GDM? /Me hates old software :mrgreen:

And I also have the same problem as PenguinZdravko. MenuMaker gives me this error:```
Traceback (most recent call last):
  File "./mmaker", line 2, in ?
    import MenuMaker.CLI
  File "/home/janne/menumaker-0.99.7/MenuMaker/CLI.py", line 227, in ?
    desktop = Prophet.Desktop.scan()
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 153, in scan
    result.append(App(os.path.join(w[0], x)))
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 266, in __new__
    self.__setup__(desktop)
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 286, in __setup__
    super(App, self).__setup__()
  File "/home/janne/menumaker-0.99.7/Prophet/__init__.py", line 265, in __setup__
    self.setExename()
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 329, in setExename
    self.testGoodness(cmd)
  File "/home/janne/menumaker-0.99.7/Prophet/__init__.py", line 261, in testGoodness
    if _shStart.search(cmd) or _shComplexCmd.search(cmd) :
TypeError: expected string or buffer
```What's wrong?

---

### Post by moore.bryan on 2006-10-22
*if you install it from the repos and then compile the tarball, it'll update itself.*

---

### Post by SlugO on 2006-10-23
> **moore.bryan said:**
> *if you install it from the repos and then compile the tarball, it'll update itself.*I tried it but after installing the new version the entry wasn't in the GDM menu anymore.

---

### Post by moore.bryan on 2006-10-26
*did you try manually editing it?*

---

### Post by paul6 on 2006-10-28
Does anyone know how to add a "shutdown" and "reboot" options to the menu config file? Adding "gksudo reboot" and "gksudo shutdown -h now" as seperate options seems to work, but you have to enter your password before you can reboot or shutdown!

---

### Post by moore.bryan on 2006-10-29
> **paul6 said:**
> Does anyone know how to add a "shutdown" and "reboot" options to the menu config file? Adding "gksudo reboot" and "gksudo shutdown -h now" as seperate options seems to work, but you have to enter your password before you can reboot or shutdown!
[I]you need to edit visudo...
```

sudo visudo

```in the area entitled "# Members of the admin group may gain root privileges" add
```

%shutdown ALL=(root) NOPASSWD:/sbin/shutdown

```now, when you obmenu, simply add the following in the execute section for reboot and shutdown:
```

sudo /sbin/shutdown -r now

```for reboot and
```

sudo /sbin/shutdown -h now

```for shutdown.
[/I]

---

### Post by draxen on 2006-11-06
try mmaker --no-desktop yourwindowmanager

> **SlugO said:**
> I compiled and installed Openbox 3.3.1 successfully but it won't add an entry to GDM's menu. Changing back to the repository version does add it.

Any idea how to compile the latest Openbox so that it will add a menu entry to GDM? /Me hates old software :mrgreen:

And I also have the same problem as PenguinZdravko. MenuMaker gives me this error:```
Traceback (most recent call last):
  File "./mmaker", line 2, in ?
    import MenuMaker.CLI
  File "/home/janne/menumaker-0.99.7/MenuMaker/CLI.py", line 227, in ?
    desktop = Prophet.Desktop.scan()
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 153, in scan
    result.append(App(os.path.join(w[0], x)))
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 266, in __new__
    self.__setup__(desktop)
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 286, in __setup__
    super(App, self).__setup__()
  File "/home/janne/menumaker-0.99.7/Prophet/__init__.py", line 265, in __setup__
    self.setExename()
  File "/home/janne/menumaker-0.99.7/Prophet/Desktop/__init__.py", line 329, in setExename
    self.testGoodness(cmd)
  File "/home/janne/menumaker-0.99.7/Prophet/__init__.py", line 261, in testGoodness
    if _shStart.search(cmd) or _shComplexCmd.search(cmd) :
TypeError: expected string or buffer
```What's wrong?

---

### Post by dagnabit dang doohickey on 2007-02-05
Thanks for the guide. It came in handy while putting a very slim X face on a server.

Something to note is it's not necessary to install **gtk-theme-switch**. All that is needed is a .gtkrc-2.0 file, in your home directory, configured to use your theme. Here is an example of a basic .gtkrc-2.0 file:
```

include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"
gtk-theme-name = "Clearlooks"
gtk-icon-theme-name = "Tango"
gtk-font-name = "Sans 8"
style "user-font"
{
        font_name = "Sans 8"
}
widget_class "*" style "user-font"

```
You might find apps that run as root (eg. synaptic) are not getting the gtk2 theme. You can take care of this with a symbolic link in /root to your .gtkrc-2.0 file.
```
sudo ln -sv ~/.gtkrc-2.0 /root/.gtkrc-2.0
```



And, here's a little **MenuMaker** doohickey. This command will create a MenuMaker menu that shows up as a sub-menu in the Openbox Menu rather than write over the Openbox Menu. It takes advantage of the default behavior of Openbox to include a Debian Menu if it exists. This command assumes MenuMaker has been untarred in your home directory.
```
~/menumaker*/mmaker -cv OpenBox3 | sed "s/\(.*\)root-menu\(.*\)OpenBox.3\(.*\)/\1Debian\2MenuMaker\3/" > ~/.config/openbox/debian-menu.xml
```

---

### Post by jseiser on 2007-03-01
I have openbox installed and working, love how quick it is, ii was able to only find 3 programs i had installed though.  How would i go about pretty much copying over my applications/places/system menus to openbox? or i mean make it so i have access to all those programs in openbox when i right click.  Also, in openbox is there a way to display a folder?  like, i keep my mp3's in /home/justin/music and i wanted to know if i can either link somehow to a folder in openbox or type something in the terminal to display the folder.

also my autostart looks like this 

#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
# Conky
exec conky &
eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi


pypanels didnt load, but i dont think i even want it, conky didnt load, and my background didnt load :(

---

### Post by Graduate on 2007-03-03
> **raublekick said:**
> 
[B][SIZE="6"]
Getting Backgrounds and Panels to Show Up at Start:[/SIZE][/B]
I originally used the .xsession method, but benplaut provided a much more generic way to go about it. This is pretty much verbatim what he outlined in here [http://ubuntuforums.org/showpost.php?p=1109058&postcount=22](http://ubuntuforums.org/showpost.php?p=1109058&postcount=22)


First, make the file ~/.config/openbox/autostart.sh. In it modify the following to fit your needs.
```
gedit ~/.config/openbox/autostart.sh
```

Panels usually cooperate better if you let them load after the WM, so this is a bit different from others.

```
#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi
```

*Rauble's note* I commented out gnome-volume-manager and gnome-settings-daemon. These are not necessary but can be very useful. If you cannot use CDs, uncomment the gnome-volume-manager line. For me, my extra harddrive and CD-ROM drives work without it. **

Panels are finicky... the little thing at the end should help.

OK, here's for gdm:

First,
```
chmod +x ~/.config/openbox/autostart.sh
```

Now, edit the session file:
```
sudo gedit /usr/share/xsessions/openbox-autostart.desktop
```

and insert the following into the file:

```
[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/home/dapper/.config/openbox/autostart.sh 
Icon= 
Type=Application
```

Note: Edit the Exec line to match your user account

finally,
```
sudo chmod +x /usr/share/xsessions/openbox-autostart.desktop
```

(i'm not sure if that's required, but it can't hurt)

Now you must restart and log into the OpenBox Autostart session
```
sudo reboot
```


I'm having trouble with this part of the tut. I followed it, and when I reboot everything is back to default. 

```

#!/bin/sh
# Auto-mounting drives
# gnome-volume-manager &
# GTK themes... this is just one method
gnome-settings-daemon &
#feh --bg-scale ~/Images/aflyingtree_1600x120.jpg
eval `cat $HOME/.fehbg` &
pypanel &
# This prevents the panel from failing if it loads too fast
if pgrep pypanel
then exec openbox
else pypanel && exec openbox
fi

```

This is what my autostart.sh looks like.

---

### Post by urukrama on 2007-04-15
Make sure you select "openbox-autostart" at the GDM login screen (under sessions). If you choose plain 'openbox', it will just start the basic Openbox, without your startup script.

---

### Post by MrGreen on 2007-05-01
Added autostart script but xsession complains that it cannot find autostart.sh 

even tried moving autostart.sh to /usr/sbin but it still does not work

could do with some help, please guys


```
 [ sbin ] > more autostart.sh 
#!/bin/sh 
# Auto-mounting drives 
gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi


[ sbin ] > cd /usr/share/xsessions/
[ xsessions ] > more openbox-autostart.desktop
[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/usr/sbin/autostart.sh 
Icon= 
Type=Application

```


:confused:

---

### Post by ynnhoj on 2007-05-02
have you made the script executable?
```
chmod 755 /usr/sbin/autostart.sh
```

---

### Post by MrGreen on 2007-05-02
[ sbin ] > ls -la autostart.sh 
-rwxr-xr-x 1 mrgreen mrgreen 339 2007-05-01 11:09 autostart.sh
[ sbin ] > 


looks ok?

---

### Post by ynnhoj on 2007-05-02
yep..  oh, did you mention in the other thread that you found the problem?

---

### Post by MrGreen on 2007-05-03
oops will sort that out ;-)

---

### Post by mazingaz on 2007-05-07
I have installed 7.04 server with Openbox Wm and it works and all but when I tried to to execute autoload of background image using feh and pypanel  it always loads openbox default screen(grey screen). 

I do not use any xsession (XDM. GMD KDM) so I figured configuring ~/.xinitrc would do but it is not working I even tried configuring /etc/xinit/xinitrc file but that didn't work either.

This is what my ~/.xinitrc looks like

```

exec openbox
pypanel &
conky &
eval `cat $HOME/.fehbg` &

```

Also i have noticed

After installing xorg then openbox, executing startx would start the openbox without having to configuring ~/.xinitrc or the /etc/xinit/xinitrc.  Where does ubuntu search for the WM execution command?

---

### Post by MrGreen on 2007-05-07
I would have put exec openbox last ... not first :confused:

---

### Post by mazingaz on 2007-05-09
Thank for the help dude.
It works now..

The next minor prob., is  the fonts from the menu bar of apps (firefox, other apps menu) are lil larger then i would like them to be.  Is there a way to make it smaller?

---

### Post by urukrama on 2007-05-10
> **mazingaz said:**
> The next minor prob., is  the fonts from the menu bar of apps (firefox, other apps menu) are lil larger then i would like them to be.  Is there a way to make it smaller?

Yes. Edit the themerc file for the theme, which can be found in /home/USERNAME/.themes/THEMENAME/openbox-3/themerc. The settings for the fonts are generally at the bottom of the file. You can change the font, the font size, bold/italic/normal., shadows, etc for the window headers and menus.

You can also change all other aspects of the theme through that file (colours, gradients, etc.)

---

### Post by mazingaz on 2007-05-10
My Themerc is in /usr/share/themes/Clear***/openbox-3/themerc
I see all the fonts config part all the way at the bottom of the file. 
When i made the changes to its pixel sizes i c the changes in the menu for the openbox (menubar) however 
The menu item fonts (File Edit View Bookmark et) of firefox and the window warning msg., are still large. I looked under /etc/firefoxrc and there was nothing useful for me to make the menu bar fonts smaller.

---

### Post by urukrama on 2007-05-10
> **mazingaz said:**
> My Themerc is in /usr/share/themes/Clear***/openbox-3/themerc
I see all the fonts config part all the way at the bottom of the file. 
When i made the changes to its pixel sizes i c the changes in the menu for the openbox (menubar) however 
The menu item fonts (File Edit View Bookmark et) of firefox and the window warning msg., are still large. I looked under /etc/firefoxrc and there was nothing useful for me to make the menu bar fonts smaller.

The application interface and menu fonts are not configured by Openbox, but by gtk. If you add the following to your .gtkrc file (/home/USERNAME/.gtk2rc)

```
gtk-font-name = "Sans 14"
```

all your gtk applications will use Sans font, size 14. The changes should be applied next time you load them.

---

### Post by mazingaz on 2007-05-10
> The application interface and menu fonts are not configured by Openbox, but by gtk. If you add the following to your .gtkrc file (/home/USERNAME/.gtk2rc)

Code:

gtk-font-name = "Sans 14"

all your gtk applications will use Sans font, size 14. The changes should be applied next time you load them.

Hmm.. no good..
still comes out the same..
is there global file for the gtk2rc? instead of local file?

---

### Post by urukrama on 2007-05-11
Sorry, perhaps my fault. Here is what my gtkrc-2.0 looks like:

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/urukrama/.themes/Clearlooks-Calla/gtk-2.0/gtkrc"

include "/home/urukrama/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

And my gtkrc-2.0.mine looks like this:

```
style "URW Gothic L"
{
font_name = "URW Gothic L 10"
}
widget_class "*" style "URW Gothic L"
gtk-font-name = "URW Gothic L 10"

gtk-icon-theme-name = "etiquette"
gtk-theme-name = "Clearlooks-gPerfection"

gtk-toolbar-style = GTK_TOOLBAR_ICONS
```

I think you could put the gktrc-2.0.mine info in the gtkrc-2.0 file, but it does get overwritten (ie. deleted) if you use another program like gtk-switch to change themes. Keeping it in the *mine file leaves it unchanged.

The font I use is called "URW Gothic L". Change that with whatever font you want to use.

The "gtk-toolbar-style" allows me to change the toolbars to icons only, text with icons, etc.

I know I have two different themes set in these files. I've discovered you get some sort of blend between the theme you specify in each file, and I quite like that. :-)

---

### Post by mazingaz on 2007-05-11
> I know I have two different themes set in these files. I've discovered you get some sort of blend between the theme you specify in each file, and I quite like that.

Thanks.. I got it to work.
My openbox w 7.04 is installed in p3 system and just intalled lightbroswer Links2 and i love abt its speed.  However does links2 not have capability to open Yahoo mail or gmail?

---

### Post by urukrama on 2007-05-12
Elinks might be able to do that. See [this thread]("http://ubuntuforums.org/showthread.php?t=126114&highlight=links2+yahoo"). Try it out.

---

### Post by mazingaz on 2007-05-15
urukrama

Thank you for your help dude.
Everything looks good and fine.

I am kind of new to ubunto W Openbox and i need a guide building system with OB with following criteria.
korean support (SCIM)
window network connection
printer sharing 
system proxy(epiphany)

What packages do i need to install to achieve above goals?

Thanks.

---

### Post by urukrama on 2007-05-16
SCIM etc. should not work differently in Openbox than in Gnome. Howtos you find on setting these up should work in Openbox.

Networking should be similar, I suppose, though you might have to install some extra applications that are installed by default in Gnome.

I suggest a forum and/or Google search, and then just trying to adjust the howtos where necessary.

---

### Post by cloneofme on 2007-05-17
being a total noob ,  i cant get the start up file to execute properly, ill post what my file shows 

[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/home/mark/.config/openbox/autostart.sh 
Icon= 
Type=Application

When i choose the autostart openbox from the sessions menu before i log in, i put the password and username in and hit enter, afterwards i get a error message saying it cannot find the file '/home/mark/.config/openbox/autostart.sh' . 

What am i doing wrong?

:confused:

---

### Post by urukrama on 2007-05-17
Did you make the file executable (as mentioned in the OP)? Otherwise double check your spelling: are there any extra spaces after the file name, or does one have capitals whereas the actual path doesn't (or vice versa), etc.

---

### Post by cloneofme on 2007-05-17
oh i dont think i did that. Whats the command for it?

i think it was supposed to have capitals , i just did a cut and paste job,but ill change it an see if it makes it work.

cheers for the help :)

---

### Post by urukrama on 2007-05-18
It is mentioned in the OP; type this in a terminal 

```
chmod +x /home/mark/.config/openbox/autostart.sh
```

Otherwise, this should work as well:

```
chmod 755 /home/mark/.config/openbox/autostart.sh
```

---

### Post by cloneofme on 2007-05-19
i finally got it working, after reading your post i went back and figured it all out ( the peoblem was that when i created the file innitally i created a folder instead, thats why it couldnt find it , after i removed the folder from the directory and re created the file it all worked )
just wanted to say thanks for your help

---

### Post by cloneofme on 2007-05-19
ok i got 2 questions now, 
1st is my background doenst seem to stay when i logout and log in, which is annoying cause feh has no problem loading the picture through terminal command, it just wolnt commit it to memory, is there anything i can do to fix this.

2nd, is i have an adesklet that i want to load at start up, do i just insert the 'adseklet' terminal command into the start up file?

cheers for any help.

---

### Post by urukrama on 2007-05-19
I'm glad to hear you got it working.

If you use feh to draw the background image, then you'll have to add the following to the autostart file:

```
eval `cat $HOME/.fehbg` &
```

(Feh stores the last loaded background in ~/.fehbg) I don't know if it really matters where it occurs in the start file, but I have it after the gnome-volume-manager.

I'm not sure what would be needed to start adesklets, but whatever command you normally use to start it should work. If the installed desklets start when you start the adesklets engine, try putting "adesklet &" in your autostart file. Double check whether it is adesklet or adesklet**s**.

---

### Post by kingmob on 2007-05-30
I have openbox working as part of a dedicated mythtv frontend. It worked fine but yesterday i wanted to setup some advanced options for the windows, to deal with the TV-overscan. Openbox doesn't seem to respect my rc.xml anymore however. The menu i edited through menu.xml stays, but whenever i reconfigure or restart the computer, openbox resets the theme (which i then change again through obconf, but it is also in the rc.xml). Also, the settings for the windows (firefox for instance) are completely ignored. Halfway through i suddenly had an old rc.xml where everything i added in the application section was completely gone ?
Ownership and read-write acces to the file seem to be fine (and is the same as menu.xml, which works). I tried overwriting the main rc.xml, but that didn't do anything...

Now it looks like almost all functionality is gone :|. When i booted the system up to fiddle with things yesterday, i could not even get the righ-click menu to work. The mouse works, but it seems like all the binds are gone!? Cannot even get an x-terminal and i cannot change tty because i will not get any image after i have started x (different problem). When i looked for the rc.xm through an ssh connection in .config/openbox/ it was simply gone! I copied it from the main, but that hasn't helped at all.

---

### Post by regomodo on 2007-07-01
awesome, apart from installing a load of apps and changing the theme, following the guide to the word has done absolutely eff all i'm going to try the guide at linux.com instead

i guess this guide relies on you to have a xubuntu/ubuntu/kubuntu-desktop as i've just done a server install

---

### Post by regomodo on 2007-07-02
Ok, i'm getting this annoying xsession error about not finding

"/home/jon/.config/openbox/autostart.sh"

and it then reverts back to the default.

I've just done an ls -la on the file and it says my name. 
i've done chmod +x and chmod 755 just to make sure
i've copied the autostart.sh to /usr/sbin just incase

here is my openbox-autostart-desktop.sh

```

[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/home/jon/.config/openbox/autostart.sh 
Icon= 
Type=Application
```

and here is the autostart.sh

```

#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
# eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi
```


Somebody please help. I've spent all day trying to get openbox working and i feel like jumping off something very high!

---

### Post by regomodo on 2007-07-03
bump

---

### Post by regomodo on 2007-07-03
bump

---

### Post by urukrama on 2007-07-04
Why don't you install Openbox 3.4? You can download it from [openbox.org]("openbox.org"). There is a deb for Feisty, but if you run Dapper or Edgy you'll have to compile it from source (see site for details). Settign up autostart with OB 3.4 is very easy and nicely documented. Openbox 3.4 has** a lot** of other improvements that make it worthwile.

Some of the other info of this thread (setting up of menus etc) is still applicable.

---

### Post by dagnabit dang doohickey on 2007-07-04
regomodo,

Assuming you start your X session with the startx command, my opinion on the autostart.sh part of this tutorial is that it's overkill. I disregarded it and, instead, stuck with the .xinitrc file. 

This is my current .xinitrc:
```

## Load X Resource defaults
        if [ -f $HOME/.Xdefaults ]; then
          xrdb -merge $HOME/.Xdefaults
        fi

## Load X keymappings
        if [ -f $HOME/.Xmodmap ]; then
          xmodmap $HOME/.Xmodmap
        fi

## Start gnome-keyring-daemon and export environment variables
        if [ -z $GNOME_KEYRING_PID ]; then
          eval "`gnome-keyring-daemon`"
          export GNOME_KEYRING_PID
          export GNOME_KEYRING_SOCKET
        fi

## Start system utilities and programs
clipboard-daemon &
#numlockx on &
unclutter &
eval `cat $HOME/.fehbg` &
conky &
#pypanel &
xfce4-terminal &

## Start window manager
exec openbox

```

An example .xinitrc to accomplish the same as your last posted autostart.sh is:

```

pypanel &
exec openbox

```


But if you use a display manager, you'll need to put this in an .xsession file instead of .xinitrc. An .xsession file, unlike .xinitrc, needs a shebang and also has to be executable.

```

#!/usr/bin/env bash

pypanel &
exec openbox

```

chmod +x ~/.xsession

---

### Post by Köntzä on 2007-09-03
Hi there!

My approach may not be unique, but I came up with it by myself, so I'm patting myself in the back for it :)

So here's my war story of it, perhaps it may help someone, or cheer someone's day ('I can't believe he did THAT!')

[LIST=1]
[*]Uninstalled E17, icewm, and anything related to those.
[*]I installed OpenBox from Ubuntu repos, and got Openbox added into GDM's session list.
[*]I copied **/usr/share/xsessions/Openbox.desktop** to **/usr/share/xsessions/Openbox-autostart.desktop**.
[*]I edited .desktop-file's Exec line to point to **/usr/bin/openbox-prep** instead of **/usr/bin/openbox**.
[*]I created openbox-prep in /usr/bin:
```
#!/bin/bash
if [ -f $HOME/.config/openbox/autostart.sh ]
then
    $HOME/.config/openbox/autostart.sh
fi
exec openbox

```
[*]My autostart.sh contains:
```
#!/bin/sh
pcmanfm &
(sleep 2 && pypanel )&

```Dunno about the necessity of the sleep command, but I found it in OpenBox web site's autostart guide.
[*]I bound Alt-F1 to show root-menu, as I've configured pcmanfm to control the desktop.
[/LIST]

With this approach, I can select which WM to use from GDM's session list. And this should apply to every user on my box.

Todo-list: tonight, after the rest of the family has gone to bed, when my nerd-time-of-the-day starts, I'll try the Feisty deb straight off Openbox site.

---

### Post by urukrama on 2007-09-03
Just download and install the latest version of Openbox (from [here]("http://icculus.org/openbox/index.php/Openbox:Download")) and you won't have to deal with all that autostart business. It is automatically taken care of in Opnebox 3.4 and up. There are lots of other improvements as well, so the upgrade is well worth it.

---

### Post by FlowingSnake on 2007-09-20
I am having a small problem. I have openbox running fine but I can not get pypanel to run at all ...I just keep getting this :
matt@matt:~$ pypanel
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in <module>
    PyPanel(display.Display())
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 124, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots


Any ideas?

---

### Post by herbster on 2007-09-27
Thanks, great guide!! Just started using Openbox, absolutely loving it :D :)

1: Is there any way to get the gnome volume control on pypanel like it sits on my gnome-panel? The tiny volume icon that can be clicked to adjust volume.

2: I tried using the same start-up command I use in Gnome to have my terminal embedded into the desktop, to start up at login to openbox, but it doesn't work. Is it not possible to have anything on the desktop in openbox? I added both devilspie and the script to run but nothing showed up.

TIA! :)

---

### Post by Kimm on 2007-09-27
> **Hanj said:**
> Nice howto! =D>  Just one suggestion:
If you start gnome-settings-manager at startup, you can launch the Gnome theme manager by executing gnome-theme-manager. It's better than gtk-theme-switch (at least IMO) and also gives you control over icon themes.

It would be better to use xfce-mcs-manager as it does the same thing, but is slightly smaller (then you need to use XFCE's theme manager of course)

---

### Post by leftorvo on 2008-02-09
great howto. thanks a lot!

---

### Post by urukrama on 2008-02-09
> **leftorvo said:**
> great howto. thanks a lot!

The howto is a bit outdated now (the autostart info for example is all redundant with the new Openbox 3.4 releases), but it helped me enormously when I got started with Openbox.

For a more up to date guide (and a bit more comprehensive), have a look at the link in my signature.

---

### Post by bend_r on 2010-01-14
Im having a prob getting SABnzbdplus to run from menu...

I usually run it from terminal by typing sudo /usr/bin/sabnzbdplus.

So I editted my sudoers file and added at the end:

%wheel  ALL=NOPASSWD:/usr/bin/sabnzbdplus

then in Obmenu I made a menu item and for Execute I put:
 sudo /usr/bin/sabnzbdplus

That didnt run SAbnzbd so I tried the command in terminal and it still wanted a passwd.

I read that I could put gksudo in there, but I dont want to have to put in the password everytime I want to run from menu, nor do I want to run sabnzbdplus with root.

Can anyone point me in the right direction?

---

### Post by cyb3r_sn4k3 on 2010-12-30
What if u want to start others apps like xcompmgr or pidgin ?

---

### Post by cyb3r_sn4k3 on 2010-12-30
Also is there a way to add a dynamic menu to the openbox menu?

Cuz i want a wine menu.

Sorry if its a double post or smthin :(

---

