---
title: "Saucy Salamander HUD failure"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by Thechromester420 on 2013-11-07
THis is a new installation of "Saucy Salamander" Ubuntu 13.10 (I think it is that version anyway.) I have to do a whole lot of searching on the hard drive and such to open up stuff like Mozilla Firefox, I'm even doing the HUD shortcut key, what does HUD do anyway? also, the "launcher" apparently is not working, I am putting the mouse where I am suposed to but I don't see any HUD thing. but on the login screen, I can see the top bar. :confused:

---

### Post by stinkeye on 2013-11-08
Pressing the Super (Windows logo) key should bring up the **dash**
showing lens's for applications files etc.

Pressing alt should bring up the hud which is a search-based alternative to traditional menus.
It will enable you to search the currently focused application.

If you can open the dash type in "help".

---

### Post by Thechromester420 on 2013-11-14
Ok, thanks

---

### Post by Thechromester420 on 2013-11-14
It doesn't seem to work...
I am smashing "SUper" ad "Alt" so do I need a key combination, or is there a difference between right super left super/right alt left alt, anything?

---

### Post by stinkeye on 2013-11-15
> **Thechromester420 said:**
> It doesn't seem to work...
I am smashing "SUper" ad "Alt" so do I need a key combination, or is there a difference between right super left super/right alt left alt, anything?
So are you saying you can't open the dash using the Super key or clicking on the dash icon in the launcher on the left.
Left or right Super should work.

You can try setting unity back to defaults via terminal (ctrl+alt+t  should load gnome-terminal).
 ```
dconf reset -f /org/compiz/
```

Log out/in

---

### Post by Thechromester420 on 2013-11-15
I don't even have the launcher, I only have the desktop and that is about left.

---

### Post by stinkeye on 2013-11-15
> **Thechromester420 said:**
> I don't even have the launcher, I only have the desktop and that is about left.
The ubuntu session uses compiz as the window manager.
The unity interface is a plugin for compiz.
The Unity plugin may be disabled.

If you have no way to open a terminal, right click on the desktop and select new folder.
Click on the created folder to open the file browser.
Navigate to **/usr/share/applications** and click on "Terminal"

In the terminal run ...
```
dconf reset -f /org/compiz/
```
This will set unity back to defaults.
You could now run **setsid unity** to reload unity/compiz but on occasions I find it does not reload properly
and you may need to do a hard reboot,
so it may be safer to log out.....
```
gnome-session-quit --no-prompt
```
Log back in to see if unity now shows.

If not, you may want to install the gnome flashback session while you try and fix the ubuntu session.
```
sudo apt-get install gnome-panel
```
This will give you a **gnome-flashback** and a **gnome-flashback (no effects)** session
to choose from at the login screen.

Use the **gnome-flashback (no effects) ** session as it uses Metacity and not Compiz as the window manager.

---

### Post by Thechromester420 on 2013-11-17
Thanks, I will try to use this as quick as possible and tell you my results, also, I can use stuff like Terminal by shortcut, and I just need a simple HTML file to launch firefox, so I think I have hope!

---

### Post by stinkeye on 2013-11-17
> **Thechromester420 said:**
> Thanks, I will try to use this as quick as possible and tell you my results, also, I can use stuff like Terminal by shortcut, and I just need a simple HTML file to launch firefox, so I think I have hope!

You can open applications in terminal even if your unsure of the start command, using Tab completion.
eg type " fi" hit tab and it will show you commands starting with" fi".
Type "fir", hit Tab and it will autocomplete firefox unless you have another application starting with "fir".

---

### Post by Thechromester420 on 2013-11-17
Oh, Thanks! even though I have an alternate way to start firefox, This is my first time using ANYTHING linux related, so I really aprecieate (Excuse my dyslexia) the help!

---

### Post by Thechromester420 on 2013-11-17
Hmm, Im at the stage where I am currently trying your gnome-panel, also, If I got to like, virtualbox's website for example and I click a linux download link, it opens the store/manager/thingy, so I can access that without much of a problem.

---

### Post by Thechromester420 on 2013-11-17
Hmm, It seems like the gnome-panel isn't opening correctly, and the first solution didn't help either.

---

### Post by stinkeye on 2013-11-17
> **Thechromester420 said:**
> Hmm, It seems like the gnome-panel isn't opening correctly, and the first solution didn't help either.
You don't see a  panel?
When in the **gnome-flashback(no effects)** session, run via terminal...
```
gnome-panel
```

Any panel or does the terminal give errors?

Install a small application called wmctrl...
```
sudo apt-get install wmctrl
```

Then to confirm your desktop session and window manager, run....
```
echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/ {print $2}'
```

eg my output for the **ubuntu**/unity session....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/ {print $2}'**
ubuntu
Compiz
```
or 
the **gnome-flashback(no effects)** session...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/ {print $2}'**
gnome-fallback
Metacity
```

---

### Post by Thechromester420 on 2013-11-19
Oh, I can use the Gnome-Flashback thing, (however that is the only thing I can use...) Thanks for the help I can see the top applications tab, the bottom bar, A lot of more stuff is seen now!

---

### Post by stinkeye on 2013-11-19
> **Thechromester420 said:**
> Oh, I can use the Gnome-Flashback thing, (however that is the only thing I can use...) Thanks for the help I can see the top applications tab, the bottom bar, A lot of more stuff is seen now!
What your using is similar to how ubuntu looked a few years ago.
It's a version of the old gnome2 panel to work with the new gnome3 enviroment.
You don't have any of the benefits (arguably) of what unity offers.
Use super+alt+right mouse to interact with the gnome-panel.
This session was intended as a fallback for those with unsupported gfx.

If you want to try and get the ubuntu/unity session running, log into the "ubuntu" session.
Once logged in confirm session and window manager....
```
echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/ {print $2}'
```
Should be **ubuntu** and **compiz**.

Check if the unity plugin is enabled.
```
dconf read /org/compiz/profiles/Default/plugins/core/active-plugins | grep unityshell
```
eg```
[COLOR="#008000"]glen@Saucy:~$ [/COLOR]**dconf read /org/compiz/profiles/Default/plugins/core/active-plugins | grep unityshell**
['core', 'composite', 'opengl', 'obs', 'copytex', 'imgjpeg', 'decor', 'compiztoolbox', 'resize', 'regex', 'water', 'winrules', 'imgpng', 'animation', 'gnomecompat', 'grid', 'vpswitch', 'dbus', 'imgsvg', 'extrawm', 'text', 'workspacenames', 'mousepoll', 'place', 'titleinfo', 'move', 'wobbly', 'commands', 'workarounds', 'session', 'fade', 'cube', 'scale', 'expo', 'scaleaddon', 'rotate', 'ezoom', 'showmouse', 'unitymtgrabhandles', '[COLOR="#FF0000"]unityshell[/COLOR]']
```
If this doesn't give you an output you'll need to install ccsm...
```
sudo apt-get install compizconfig-settings-manager
```

Once installed to run compizconfig-settings-manager,
```
ccsm
```
Navigate to 
ccsm > Desktop > Ubuntu Unity Plugin
and check it is enabled.

---

### Post by Thechromester420 on 2013-11-19
Ohh, A thought just popped into my head, I think I know why the regular Ubuntu HUD doesn't work correctly, I have an old (and I mean OLD) graphics card, and if I open settings, Ubuntu notes the Graphic driver as "Unknown" or "Null" so I guess that is what was causing the trouble, I guess I might need to stay in Gnome-Flashback, but that is OK with me, I really wish I could thank you in a different way then just saying "Thank You"
I will also try to use the ccsm thing, but so far, I think I have a fix for ubuntu.

---

### Post by Thechromester420 on 2013-11-19
The "Ubuntu Unity Plugin" cannot work because my graphics card is incompatible with OpenGL, I know of a program on windows that lets me use OpenGL, (it is called "Scitech OpenGL" or something like that) so is there like, an Ubuntu variant of a program like that?

---

### Post by stinkeye on 2013-11-19
> **Thechromester420 said:**
> The "Ubuntu Unity Plugin" cannot work because my graphics card is incompatible with OpenGL, I know of a program on windows that lets me use OpenGL, (it is called "Scitech OpenGL" or something like that) so is there like, an Ubuntu variant of a program like that?
Whats your graphics...
```
/usr/lib/nux/unity_support_test -p 
```
eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p **
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: [COLOR="#FF0000"]GeForce GTX 550 Ti[/COLOR]/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 313.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```
Normally you would check for available drivers by running...
```
software-properties-gtk
```
but the Additional Drivers tab will probably show nothing if your old gfx isn't recognized.
[ATTACH=CONFIG]247944[/ATTACH]


Many have switched to xfce, which is a lightweight desktop environment and is under active development.
You can install an xfce session with
```
sudo apt-get install xfce4
```
Then choose the **xfce session** at login.

If you want the the full xfce desktop environment (includes all the default applications) you can install xubuntu-desktop```
sudo apt-get install xubuntu-desktop
```
Be aware that the xubuntu-desktop install will download and install an extra 100-250mb.

As you can't run unity and  if xfce appeals to you, may want to do a fresh install of [**_[COLOR="#B22222"]Xubuntu[/COLOR]_**]("http://xubuntu.org").

---

### Post by Thechromester420 on 2013-11-20
I didn't do the last bit of code, but here are the results of my test run:
```
chromester@chromester-Dimension-2400:~$ /usr/lib/nux/unity_support_test -p
Error: OpenGL rendering is not supported by the root visual
chromester@chromester-Dimension-2400:~$ software-properties-gtk
(When searching for my GFX driver, I couldn't find it, the rest of the code follows)
gpg: /tmp/tmpvjo57n/trustdb.gpg: trustdb created
chromester@chromester-Dimension-2400:~$ sudo apt-get install xfce4
[sudo] password for chromester: 
*CENSORED*Sorry, try again.
[sudo] password for chromester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  elinks-data libfsplib0 libtre5 linux-headers-3.11.0-12
  linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic
  linux-image-extra-3.11.0-12-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  desktop-base exo-utils gtk2-engines-xfce libexo-1-0 libexo-common
  libexo-helpers libgarcon-1-0 libgarcon-common libglade2-0 libjpeg-progs
  libjpeg-turbo-progs libkeybinder0 libthunarx-2-0 libtumbler-1-0
  libunique-1.0-0 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 orage tango-icon-theme
  thunar thunar-data thunar-volman tumbler tumbler-common
  xfce-keyboard-shortcuts xfce4-appfinder xfce4-mixer xfce4-notifyd
  xfce4-panel xfce4-session xfce4-settings xfce4-volumed xfconf xfdesktop4
  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data
Suggested packages:
  sox kdelibs-data thunar-archive-plugin thunar-media-tags-plugin
  tumbler-plugins-extra xfce4-goodies xfce4-power-manager gtk3-engines-xfce
  fortunes-mod menu xfwm4-themes xfishtank xdaliclock xscreensaver-gl fortune
  qcam streamer gdm3 kdm-gdmcompat
The following NEW packages will be installed:
  desktop-base exo-utils gtk2-engines-xfce libexo-1-0 libexo-common
  libexo-helpers libgarcon-1-0 libgarcon-common libglade2-0 libjpeg-progs
  libjpeg-turbo-progs libkeybinder0 libthunarx-2-0 libtumbler-1-0
  libunique-1.0-0 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 orage tango-icon-theme
  thunar thunar-data thunar-volman tumbler tumbler-common
  xfce-keyboard-shortcuts xfce4 xfce4-appfinder xfce4-mixer xfce4-notifyd
  xfce4-panel xfce4-session xfce4-settings xfce4-volumed xfconf xfdesktop4
  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.8 MB of archives.
After this operation, 61.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe desktop-base all 7.0.3ubuntu1 [5,808 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfce4util-common all 4.10.1-1 [56.5 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfce4util6 i386 4.10.1-1 [28.1 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfconf i386 4.10.0-2 [113 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfconf-0-2 i386 4.10.0-2 [29.7 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce-keyboard-shortcuts all 4.10.0-3 [5,006 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfce4ui-1-0 i386 4.10.0-3 [140 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libexo-common all 0.10.2-2 [16.4 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libexo-helpers i386 0.10.2-2 [19.3 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libexo-1-0 i386 0.10.2-2 [465 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libgarcon-common all 0.2.1-1 [52.3 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libgarcon-1-0 i386 0.2.1-1 [45.3 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main libglade2-0 i386 1:2.6.4-1ubuntu3 [43.7 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe thunar-data all 1.6.3-1ubuntu1 [1,399 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libthunarx-2-0 i386 1.6.3-1ubuntu1 [83.4 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libtumbler-1-0 i386 0.1.29-2 [23.3 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe exo-utils i386 0.10.2-2 [51.2 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-panel i386 4.10.1-1ubuntu1 [925 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-settings i386 4.11.0-1ubuntu1 [621 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-session i386 4.10.1-1ubuntu1 [785 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe gtk2-engines-xfce i386 3.0.1-2 [30.8 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libjpeg-turbo-progs i386 1.3.0-0ubuntu1 [65.0 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libjpeg-progs i386 8c-2ubuntu8 [2,192 B]
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libkeybinder0 i386 0.3.0-2 [10.4 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main libunique-1.0-0 i386 1.1.6-4build1 [25.2 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfce4ui-utils i386 4.10.0-3 [39.5 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe libxfce4util-bin i386 4.10.1-1 [6,066 B]
Get:28 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe orage i386 4.8.4-2ubuntu1 [2,222 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe tango-icon-theme all 0.8.90-5 [1,645 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe thunar i386 1.6.3-1ubuntu1 [322 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe thunar-volman i386 0.8.0-2 [138 kB]
Get:32 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe tumbler-common all 0.1.29-2 [76.9 kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe tumbler i386 0.1.29-2 [73.7 kB]
Get:34 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfwm4 i386 4.10.1-2ubuntu1 [554 kB]
Get:35 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfdesktop4-data all 4.10.2-3ubuntu1 [449 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfdesktop4 i386 4.10.2-3ubuntu1 [154 kB]
Get:37 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-appfinder i386 4.10.1-1 [125 kB]
Get:38 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-mixer i386 1:4.10.0-1ubuntu2 [108 kB]
Get:39 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4 all 4.10.1 [5,094 B]
Get:40 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-notifyd i386 0.2.4-2 [78.7 kB]
Get:41 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xfce4-volumed i386 0.2.0-0ubuntu1 [13.5 kB]
Get:42 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xscreensaver-data i386 5.15-3ubuntu1 [128 kB]
Get:43 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe xscreensaver i386 5.15-3ubuntu1 [850 kB]
Fetched 17.8 MB in 16s (1,074 kB/s)                                            
Extracting templates from packages: 100%
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 newline in field name `../../../../../share/pyshared/duplicity/backends/cloudfilesbackend.py'
E: Sub-process /usr/bin/dpkg returned an error code (2)
chromester@chromester-Dimension-2400:~$
```
Is there any more sooper-dooper superpowers you have up your sleeve? If you don't I really don't mind needing to stick with Gnome-Flashback
I can imagine this:
GFX driver: :oops:
Also, *CENSORED* Isn't my password, but it is quite literally *CENSORED*

---

### Post by stinkeye on 2013-11-20
To fix the error try this....
```
sudo dpkg --clear-avail
```

Then update and upgrade available packages...
```
sudo apt-get update && sudo apt-get upgrade
```

....and try again to install xfce...
```
sudo apt-get install xfce4
```

---

### Post by Thechromester420 on 2013-11-21
Results of Test Number Two:
```
chromester@chromester-Dimension-2400:~$ sudo dpkg --clear-anvil
[sudo] password for chromester: 
*CENSORED*Sorry, try again.
[sudo] password for chromester: 
dpkg: error: unknown option --clear-anvil

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
chromester@chromester-Dimension-2400:~$ sudo dpkg --clear-avail
chromester@chromester-Dimension-2400:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy InRelease
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy Release.gpg
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy Release
Err cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en
Ign http://us.archive.ubuntu.com saucy InRelease                               
Ign http://us.archive.ubuntu.com saucy-updates InRelease                       
Ign http://archive.ubuntu.com saucy InRelease                                  
Ign http://us.archive.ubuntu.com saucy-backports InRelease                     
Ign http://archive.canonical.com saucy InRelease                               
Ign http://security.ubuntu.com saucy-security InRelease                        
Ign http://extras.ubuntu.com saucy InRelease                                   
Ign http://us.archive.ubuntu.com saucy-proposed InRelease                      
Hit http://archive.ubuntu.com saucy Release.gpg                                
Hit http://us.archive.ubuntu.com saucy Release.gpg                             
Hit http://archive.canonical.com saucy Release.gpg                             
Get:1 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Get:2 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Get:3 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Hit http://archive.ubuntu.com saucy Release                                    
Hit http://us.archive.ubuntu.com saucy-backports Release.gpg                   
Get:4 http://us.archive.ubuntu.com saucy-proposed Release.gpg [933 B]          
Hit http://us.archive.ubuntu.com saucy Release                                 
Get:5 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Hit http://archive.canonical.com saucy Release                                 
Hit http://extras.ubuntu.com saucy Release                                     
Get:6 http://us.archive.ubuntu.com saucy-updates Release [49.6 kB]             
Hit http://archive.ubuntu.com saucy/restricted Sources                         
Hit http://archive.canonical.com saucy/partner Sources                         
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://archive.ubuntu.com saucy/main Sources                               
Hit http://us.archive.ubuntu.com saucy-backports Release                       
Get:7 http://us.archive.ubuntu.com saucy-proposed Release [49.6 kB]            
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Get:8 http://security.ubuntu.com saucy-security/restricted Sources [14 B]      
Hit http://us.archive.ubuntu.com saucy/restricted Sources                      
Hit http://us.archive.ubuntu.com saucy/universe Sources                        
Hit http://us.archive.ubuntu.com saucy/multiverse Sources                      
Hit http://us.archive.ubuntu.com saucy/main Sources                            
Get:9 http://security.ubuntu.com saucy-security/universe Sources [6,195 B]     
Hit http://us.archive.ubuntu.com saucy/main i386 Packages                      
Get:10 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]    
Hit http://us.archive.ubuntu.com saucy/restricted i386 Packages                
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages                  
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages                
Get:11 http://security.ubuntu.com saucy-security/main Sources [10.8 kB]        
Hit http://us.archive.ubuntu.com saucy/main Translation-en                     
Get:12 http://security.ubuntu.com saucy-security/main i386 Packages [36.7 kB]  
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en               
Hit http://us.archive.ubuntu.com saucy/universe Translation-en                 
Get:13 http://us.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:14 http://us.archive.ubuntu.com saucy-updates/universe Sources [14.7 kB]   
Get:15 http://us.archive.ubuntu.com saucy-updates/multiverse Sources [1,351 B] 
Get:16 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Get:17 http://security.ubuntu.com saucy-security/universe i386 Packages [13.9 kB]
Get:18 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://extras.ubuntu.com saucy/main Translation-en
Get:19 http://us.archive.ubuntu.com saucy-updates/main Sources [38.4 kB]       
Get:20 http://us.archive.ubuntu.com saucy-updates/main i386 Packages [93.6 kB] 
Get:21 http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Get:22 http://us.archive.ubuntu.com saucy-updates/universe i386 Packages [40.1 kB]
Get:23 http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,800 B]
Get:24 http://us.archive.ubuntu.com saucy-updates/main Translation-en [42.4 kB]
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en       
Hit http://security.ubuntu.com saucy-security/main Translation-en              
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en        
Hit http://security.ubuntu.com saucy-security/restricted Translation-en        
Get:25 http://security.ubuntu.com saucy-security/universe Translation-en [8,077 B]
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en       
Get:26 http://us.archive.ubuntu.com saucy-updates/universe Translation-en [21.9 kB]
Hit http://us.archive.ubuntu.com saucy-backports/main Sources                  
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources           
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources              
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en           
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en     
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en     
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en       
Get:27 http://us.archive.ubuntu.com saucy-proposed/restricted i386 Packages [14 B]
Get:28 http://us.archive.ubuntu.com saucy-proposed/main i386 Packages [33.6 kB]
Get:29 http://us.archive.ubuntu.com saucy-proposed/multiverse i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com saucy-proposed/universe i386 Packages [22.1 kB]
Ign http://security.ubuntu.com saucy-security/main Translation-en_US           
Get:31 http://us.archive.ubuntu.com saucy-proposed/main Translation-en [18.3 kB]
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US     
Hit http://us.archive.ubuntu.com saucy-proposed/multiverse Translation-en      
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US       
Hit http://us.archive.ubuntu.com saucy-proposed/restricted Translation-en      
Get:32 http://us.archive.ubuntu.com saucy-proposed/universe Translation-en [13.8 kB]
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com saucy-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com saucy-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com saucy-proposed/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com saucy-proposed/universe Translation-en_US     
Fetched 572 kB in 12s (44.6 kB/s)                                              
W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
chromester@chromester-Dimension-2400:~$ sudo apt-get install xfce4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  elinks-data libfsplib0 libtre5 linux-headers-3.11.0-12
  linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic
  linux-image-extra-3.11.0-12-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  desktop-base exo-utils gtk2-engines-xfce libexo-1-0 libexo-common
  libexo-helpers libgarcon-1-0 libgarcon-common libglade2-0 libjpeg-progs
  libjpeg-turbo-progs libkeybinder0 libthunarx-2-0 libtumbler-1-0
  libunique-1.0-0 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 orage tango-icon-theme
  thunar thunar-data thunar-volman tumbler tumbler-common
  xfce-keyboard-shortcuts xfce4-appfinder xfce4-mixer xfce4-notifyd
  xfce4-panel xfce4-session xfce4-settings xfce4-volumed xfconf xfdesktop4
  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data
Suggested packages:
  sox kdelibs-data thunar-archive-plugin thunar-media-tags-plugin
  tumbler-plugins-extra xfce4-goodies xfce4-power-manager gtk3-engines-xfce
  fortunes-mod menu xfwm4-themes xfishtank xdaliclock xscreensaver-gl fortune
  qcam streamer gdm3 kdm-gdmcompat
The following NEW packages will be installed:
  desktop-base exo-utils gtk2-engines-xfce libexo-1-0 libexo-common
  libexo-helpers libgarcon-1-0 libgarcon-common libglade2-0 libjpeg-progs
  libjpeg-turbo-progs libkeybinder0 libthunarx-2-0 libtumbler-1-0
  libunique-1.0-0 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 orage tango-icon-theme
  thunar thunar-data thunar-volman tumbler tumbler-common
  xfce-keyboard-shortcuts xfce4 xfce4-appfinder xfce4-mixer xfce4-notifyd
  xfce4-panel xfce4-session xfce4-settings xfce4-volumed xfconf xfdesktop4
  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data
0 upgraded, 43 newly installed, 0 to remove and 15 not upgraded.
Need to get 0 B/17.8 MB of archives.
After this operation, 61.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Selecting previously unselected package desktop-base.
(Reading database ... 234082 files and directories currently installed.)
Unpacking desktop-base (from .../desktop-base_7.0.3ubuntu1_all.deb) ...
Selecting previously unselected package libxfce4util-common.
Unpacking libxfce4util-common (from .../libxfce4util-common_4.10.1-1_all.deb) ...
Selecting previously unselected package libxfce4util6.
Unpacking libxfce4util6 (from .../libxfce4util6_4.10.1-1_i386.deb) ...
Selecting previously unselected package xfconf.
Unpacking xfconf (from .../xfconf_4.10.0-2_i386.deb) ...
Selecting previously unselected package libxfconf-0-2.
Unpacking libxfconf-0-2 (from .../libxfconf-0-2_4.10.0-2_i386.deb) ...
Selecting previously unselected package xfce-keyboard-shortcuts.
Unpacking xfce-keyboard-shortcuts (from .../xfce-keyboard-shortcuts_4.10.0-3_all.deb) ...
Selecting previously unselected package libxfce4ui-1-0.
Unpacking libxfce4ui-1-0 (from .../libxfce4ui-1-0_4.10.0-3_i386.deb) ...
Selecting previously unselected package libexo-common.
Unpacking libexo-common (from .../libexo-common_0.10.2-2_all.deb) ...
Selecting previously unselected package libexo-helpers.
Unpacking libexo-helpers (from .../libexo-helpers_0.10.2-2_i386.deb) ...
Selecting previously unselected package libexo-1-0:i386.
Unpacking libexo-1-0:i386 (from .../libexo-1-0_0.10.2-2_i386.deb) ...
Selecting previously unselected package libgarcon-common.
Unpacking libgarcon-common (from .../libgarcon-common_0.2.1-1_all.deb) ...
Selecting previously unselected package libgarcon-1-0.
Unpacking libgarcon-1-0 (from .../libgarcon-1-0_0.2.1-1_i386.deb) ...
Selecting previously unselected package libglade2-0:i386.
Unpacking libglade2-0:i386 (from .../libglade2-0_1%3a2.6.4-1ubuntu3_i386.deb) ...
Selecting previously unselected package thunar-data.
Unpacking thunar-data (from .../thunar-data_1.6.3-1ubuntu1_all.deb) ...
Selecting previously unselected package libthunarx-2-0.
Unpacking libthunarx-2-0 (from .../libthunarx-2-0_1.6.3-1ubuntu1_i386.deb) ...
Selecting previously unselected package libtumbler-1-0.
Unpacking libtumbler-1-0 (from .../libtumbler-1-0_0.1.29-2_i386.deb) ...
Selecting previously unselected package exo-utils.
Unpacking exo-utils (from .../exo-utils_0.10.2-2_i386.deb) ...
Selecting previously unselected package xfce4-panel.
Unpacking xfce4-panel (from .../xfce4-panel_4.10.1-1ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-settings.
Unpacking xfce4-settings (from .../xfce4-settings_4.11.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-session.
Unpacking xfce4-session (from .../xfce4-session_4.10.1-1ubuntu1_i386.deb) ...
Selecting previously unselected package gtk2-engines-xfce.
Unpacking gtk2-engines-xfce (from .../gtk2-engines-xfce_3.0.1-2_i386.deb) ...
Selecting previously unselected package libjpeg-turbo-progs.
Unpacking libjpeg-turbo-progs (from .../libjpeg-turbo-progs_1.3.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package libjpeg-progs.
Unpacking libjpeg-progs (from .../libjpeg-progs_8c-2ubuntu8_i386.deb) ...
Selecting previously unselected package libkeybinder0.
Unpacking libkeybinder0 (from .../libkeybinder0_0.3.0-2_i386.deb) ...
Selecting previously unselected package libunique-1.0-0.
Unpacking libunique-1.0-0 (from .../libunique-1.0-0_1.1.6-4build1_i386.deb) ...
Selecting previously unselected package libxfce4ui-utils.
Unpacking libxfce4ui-utils (from .../libxfce4ui-utils_4.10.0-3_i386.deb) ...
Selecting previously unselected package libxfce4util-bin.
Unpacking libxfce4util-bin (from .../libxfce4util-bin_4.10.1-1_i386.deb) ...
Selecting previously unselected package orage.
Unpacking orage (from .../orage_4.8.4-2ubuntu1_i386.deb) ...
Selecting previously unselected package tango-icon-theme.
Unpacking tango-icon-theme (from .../tango-icon-theme_0.8.90-5_all.deb) ...
Selecting previously unselected package thunar.
Unpacking thunar (from .../thunar_1.6.3-1ubuntu1_i386.deb) ...
Selecting previously unselected package thunar-volman.
Unpacking thunar-volman (from .../thunar-volman_0.8.0-2_i386.deb) ...
Selecting previously unselected package tumbler-common.
Unpacking tumbler-common (from .../tumbler-common_0.1.29-2_all.deb) ...
Selecting previously unselected package tumbler.
Unpacking tumbler (from .../tumbler_0.1.29-2_i386.deb) ...
Selecting previously unselected package xfwm4.
Unpacking xfwm4 (from .../xfwm4_4.10.1-2ubuntu1_i386.deb) ...
Selecting previously unselected package xfdesktop4-data.
Unpacking xfdesktop4-data (from .../xfdesktop4-data_4.10.2-3ubuntu1_all.deb) ...
Selecting previously unselected package xfdesktop4.
Unpacking xfdesktop4 (from .../xfdesktop4_4.10.2-3ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-appfinder.
Unpacking xfce4-appfinder (from .../xfce4-appfinder_4.10.1-1_i386.deb) ...
Selecting previously unselected package xfce4-mixer.
Unpacking xfce4-mixer (from .../xfce4-mixer_1%3a4.10.0-1ubuntu2_i386.deb) ...
Selecting previously unselected package xfce4.
Unpacking xfce4 (from .../archives/xfce4_4.10.1_all.deb) ...
Selecting previously unselected package xfce4-notifyd.
Unpacking xfce4-notifyd (from .../xfce4-notifyd_0.2.4-2_i386.deb) ...
Selecting previously unselected package xfce4-volumed.
Unpacking xfce4-volumed (from .../xfce4-volumed_0.2.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package xscreensaver-data.
Unpacking xscreensaver-data (from .../xscreensaver-data_5.15-3ubuntu1_i386.deb) ...
Selecting previously unselected package xscreensaver.
Unpacking xscreensaver (from .../xscreensaver_5.15-3ubuntu1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Setting up desktop-base (7.0.3ubuntu1) ...
update-alternatives: using /usr/share/images/desktop-base/joy-wallpaper_1600x1200.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy-wallpaper_1920x1080.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy.xml to provide /usr/share/images/desktop-base/desktop-background.xml (desktop-background.xml) in auto mode
update-alternatives: using /usr/share/images/desktop-base/spacefun-splash.svg to provide /usr/share/images/desktop-base/desktop-splash (desktop-splash) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy-grub.png to provide /usr/share/images/desktop-base/desktop-grub.png (desktop-grub) in auto mode
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
update-initramfs: deferring update (trigger activated)
Setting up libxfce4util-common (4.10.1-1) ...
Setting up libxfce4util6 (4.10.1-1) ...
Setting up xfconf (4.10.0-2) ...
Setting up libxfconf-0-2 (4.10.0-2) ...
Setting up xfce-keyboard-shortcuts (4.10.0-3) ...
Setting up libxfce4ui-1-0 (4.10.0-3) ...
Setting up libexo-common (0.10.2-2) ...
Setting up libexo-helpers (0.10.2-2) ...
Setting up libexo-1-0:i386 (0.10.2-2) ...
Setting up libgarcon-common (0.2.1-1) ...
Setting up libgarcon-1-0 (0.2.1-1) ...
Setting up libglade2-0:i386 (1:2.6.4-1ubuntu3) ...
Setting up thunar-data (1.6.3-1ubuntu1) ...
Setting up libthunarx-2-0 (1.6.3-1ubuntu1) ...
Setting up libtumbler-1-0 (0.1.29-2) ...
Setting up exo-utils (0.10.2-2) ...
Setting up xfce4-panel (4.10.1-1ubuntu1) ...
Setting up xfce4-settings (4.11.0-1ubuntu1) ...
Setting up xfce4-session (4.10.1-1ubuntu1) ...
Setting up gtk2-engines-xfce (3.0.1-2) ...
Setting up libjpeg-turbo-progs (1.3.0-0ubuntu1) ...
Setting up libjpeg-progs (8c-2ubuntu8) ...
Setting up libkeybinder0 (0.3.0-2) ...
Setting up libunique-1.0-0 (1.1.6-4build1) ...
Setting up libxfce4ui-utils (4.10.0-3) ...
Setting up libxfce4util-bin (4.10.1-1) ...
Setting up orage (4.8.4-2ubuntu1) ...
Setting up tango-icon-theme (0.8.90-5) ...
Setting up thunar (1.6.3-1ubuntu1) ...
Setting up thunar-volman (0.8.0-2) ...
Setting up tumbler-common (0.1.29-2) ...
Setting up tumbler (0.1.29-2) ...
Setting up xfwm4 (4.10.1-2ubuntu1) ...
Setting up xfdesktop4-data (4.10.2-3ubuntu1) ...
Setting up xfdesktop4 (4.10.2-3ubuntu1) ...
Setting up xfce4-appfinder (4.10.1-1) ...
Setting up xfce4-mixer (1:4.10.0-1ubuntu2) ...
Setting up xfce4 (4.10.1) ...
Setting up xfce4-notifyd (0.2.4-2) ...
Setting up xfce4-volumed (0.2.0-0ubuntu1) ...
Setting up xscreensaver-data (5.15-3ubuntu1) ...
Setting up xscreensaver (5.15-3ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-14-generic

Processing triggers for libc-bin ...
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ saucy/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_saucy_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ saucy/main i386 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_saucy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
chromester@chromester-Dimension-2400:~$

```

---

### Post by stinkeye on 2013-11-21
So that means you can now login to an xfce session?
You appear to have changed some of the default settings in software and updates.
You have added your cd as a package source and have enabled the proposed repositories.
Enabling proposed is a good way to bork your system.

> "Pre-released Updates (saucy-proposed)". The testing area for updates. This repository is recommended only to those 
interested in helping to test updates and provide feedback.

---

### Post by Thechromester420 on 2013-11-25
Err... Ok.

---

### Post by stinkeye on 2013-11-25
err....
```
sudo apt-get **install** virtualbox
```

---

### Post by Thechromester420 on 2013-11-29
hahaha, my signature fails XD

---

### Post by Thechromester420 on 2013-11-29
There we go, I fixed it! :")

---

