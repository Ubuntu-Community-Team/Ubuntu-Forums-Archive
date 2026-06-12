---
title: "Mupen64Plus v1.99.4 + CuteMupen GUI"
date: 2011-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by mips on 2011-02-12
Done on Ubuntu 10.10 64-bit

First install Mupen64Plus **v1.5** from the repos, there is method to this madness!
```
sudo apt-get install mupen64plus
```


Open Mupen64+, go Options -> Configure --> Plugins Tab --> Select "blight's SDL input plugin" --> Click Config and setup your gamepad/controller --> Apply changes & test that it works in a few games, exit mupen64+


Now we have to backup that config file for the gampad/controller.
```
cp ~/.config/mupen64plus/blight_input.conf ~/Desktop

```

Verify the file is on your desktop and that it contains the settings for you controller.


Now we can uninstall mupen64+,
```
sudo apt-get purge mupen64plus
```

Check to see that the config files were removed as well, if they are still there you can do,
```
rm -r ~/.config/mupen64plus
```


So why did we just go through this whole exercise? Well currently the is no GUI front end you can use to setup your gamepad/controller for Mupen64+ v1.99.4. The application itself no longer has a GUI (cli only) and the available frontends out there do not support configuration of the controller as yet so we need a backup copy of our v1.5 config file for later.


Lets get on to installing mupen64+ v1.99.4

First lets add the developers PPA to our repos,
```
sudo add-apt-repository ppa:sven-eckelmann/ppa-mupen64plus
```


Next we do an update and install the app,
```
sudo apt-get update
sudo apt-get install mupen64plus
```


Run mupen64+ so it creates a config folder and file,
```
mupen64plus
```



Next we install [CuteMupen]("http://sourceforge.net/projects/cutemupen/") front end, **[COLOR="Red"]get the 32-bit version if you are using 32-bit OS, check for newer files![/COLOR]** [http://sourceforge.net/projects/cutemupen/files/](http://sourceforge.net/projects/cutemupen/files/)
```
wget http://sourceforge.net/projects/cutemupen/files/0.1.0/cutemupen-linux64-0.1.0.tar.bz2
tar xvfj cutemupen-linux64-0.1.0.tar.bz2
```


Add CuteMupen to your menu,
Right click on Applications toolbar --> Edit Menus --> Games --> New Item
Type: Application
Name: CuteMupen
Cammand: /home/*username*/cutemupen-linux64-0.1.0/cutemupen


Open CuteMupen, it's going to prompt you for some default files & folder locations.

**Core libabrary file:** /usr/lib/libmupen64plus.so.2
**Plugins:** /usr/lib/mupen64plus   (or /home/**username**/.config/mupen64plus/plugins and copy the contents of /usr/lib/mupen64plus into it which is what I have done.)
**Data:** /home/**username**/.config/mupen64plus/data
**Config:** /home/**username**/.config/mupen64plus
**ROMs:** Wherever you have your ROM files stored.
If the folders don't exist create them.


Quit and restart CuteMupen. You can now setup your plugins and their setting to suite your needs.


If your controller/gamepad does not work out of the box you will have to edit your /usr/share/mupen64plus/InputAutoCfg.ini file with information from the ~/Destop/blight_input.conf file we backed up earlier.

Here are some examples that show how,
[http://www.emutalk.net/showthread.php?t=49731](http://www.emutalk.net/showthread.php?t=49731)
[http://code.google.com/p/mupen64plus/wiki/ControllerSetup](http://code.google.com/p/mupen64plus/wiki/ControllerSetup)


This post was compiled with info taken from:
[http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559](http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559)
[http://www.emutalk.net/forumdisplay.php?f=113](http://www.emutalk.net/forumdisplay.php?f=113)
[http://code.google.com/p/mupen64plus/w/list](http://code.google.com/p/mupen64plus/w/list)

---

### Post by drewmerc on 2011-04-25
wonderful worked great, thank you

---

### Post by mips on 2011-05-23
[COLOR="Red"]**[SIZE="4"][http://ubuntuforums.org/showthread.php?t=1686297](http://ubuntuforums.org/showthread.php?t=1686297)[/SIZE]**[/COLOR]


[SIZE="4"]**[COLOR="Red"]See the above thread for discussions, feedback & questions.[/COLOR]**[/SIZE]








.

---

