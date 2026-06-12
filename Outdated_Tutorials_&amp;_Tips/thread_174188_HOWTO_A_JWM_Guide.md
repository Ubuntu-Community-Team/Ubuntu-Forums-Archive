---
title: "HOWTO: A JWM Guide"
date: 2006-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by bluevoodoo1 on 2006-05-11
JWM Window Manager (Joe's Window Manager)

"JWM is a window manager for the X11 Window System. JWM is written in C and uses only Xlib at a minimum. "

1. Download current version (v1.7) here...
[http://joewing.net/programs/jwm/index.shtml#description](http://joewing.net/programs/jwm/index.shtml#description)

and save it some place, let's say your home folder. 

2. Then we extract it. 
```
tar xvpfj jwm-1.7.tar.bz2
```

3. Install it. 
```

cd jwm-1.7
./configure
make
sudo checkinstall

```

4. Move the configuration file (XML file) to /home/$USER
```
cp jwm-1.7/example.jwmrc .jwmrc
```

5. Create a JWM session...
```
sudo gedit /usr/share/xsession/jwm.desktop
```

```

[Desktop Entry]
Encoding=UTF-8
Name=JWM
Comment=This is the JWM window manager
Exec=/PATH-TO/jwm-1.7/src/jwm
Type=Application

```

and save.

6. Logout and choose "JWM."

7. Potential Problems:
  -Icons not working. Be sure to check the path and icon names in the .jwmrc
  -Want to use a wallpaper? In the config file, I use the Esetroot command at startup.
  -Want GNOME options? From a terminal run "nohup gnome-settings-daemon &" (close the terminal)

More info on creating a startup script/wallpapers/other addons can be seen at my Blackbox guide.

---

### Post by eeried on 2008-02-19
It's a pity your howto is so thin as I'm looking for some manual.

---

### Post by yousifnet on 2008-05-11
Hello guys

Just finished installing JWM on Ubuntu and want to update this guide to reflect the changes that happened since this post was created

first off you no longer have to compile from source simply

```
sudo apt-get install jwm
```This would not automatically add JWM to the XSessions menu for some reason! So you have to manually copy the Jwm.desktop to the xsessions folder by doing this:

```
sudo cp /usr/share/jwm/xsessions/Jwm.desktop /usr/share/xsessions/Jwm.desktop
```Log off, change the session and you are gold! The first thing you will notice is that the right click menu doesn't have anything in it. To fix that you'll have to refere to [JWM's documentation ]("http://joewing.net/programs/jwm/config.shtml")as I haven't had the time to check it out yet.

Finally my ancient laptop is running as smooth as it used to in the old days!

---

### Post by eeried on 2008-05-13
It's okay, JWM's documentation is clear enough!

Have fun!

---

### Post by cogitordi on 2008-09-05
I have seen JWM in Damn Small Linux and I am impressed. I'd like to use JWM on my old Thinkpad. When you use JWM in Ubuntu, can the Network Manager still be used for wireless connectivity?

---

### Post by go_beep_yourself on 2009-07-21
> **eeried said:**
> It's a pity your howto is so thin as I'm looking for some manual.

Tried the official JWM website? You really should.

---

### Post by frenchn00b on 2009-10-18
-Icons not working. Be sure to check the path and icon names in the .jwmrc
  -Want to use a wallpaper? In the config file, I use the Esetroot command at startup.
  -Want GNOME options? From a terminal run "nohup gnome-settings-daemon &" (close the terminal)

More info on creating a startup script/wallpapers/other addons can be seen at my Blackbox guide.[/QUOTE]



to use a wallpaper: 
add at the beginning of .jwmrc:
```

<?xml version="1.0"?>

<JWM>

<StartupCommand>
xterm &
Esetroot -m $HOME/wallpapers/wallpaper.jpg
</StartupCommand>

```






[COLOR="Red"]**How to add a binding ; that "send to" the window to another desktop, without following ?**[/COLOR]

---

### Post by kerry_s on 2009-10-18
> **frenchn00b said:**
> -Icons not working. Be sure to check the path and icon names in the .jwmrc
  -Want to use a wallpaper? In the config file, I use the Esetroot command at startup.
  -Want GNOME options? From a terminal run "nohup gnome-settings-daemon &" (close the terminal)

More info on creating a startup script/wallpapers/other addons can be seen at my Blackbox guide.


to use a wallpaper: 
add at the beginning of .jwmrc:
```

<?xml version="1.0"?>

<JWM>

<StartupCommand>
xterm &
Esetroot -m $HOME/wallpapers/wallpaper.jpg
</StartupCommand>

```






[COLOR="Red"]**How to add a binding ; that "send to" the window to another desktop, without following ?**[/COLOR][/QUOTE]


dead thread revival. :)

jwm has built in feature to do it's own backgrounds, there's no need to use a external program.

---

### Post by jethro00 on 2009-10-29
I got a lot of good info from this thread, so I'd like to add a little trick I worked out.  The following will allow different images for each desktop:

    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="3">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->

       <Desktop Name="One">
       <Background type="image">/home/me/Pictures/1.png</Background>
       </Desktop>

       <Desktop Name="Two">
       <Background type="image">/home/me/Pictures/2.png</Background>
       </Desktop>

       <Desktop Name="Three">
       <Background type="image">/home/me/Pictures/3.png</Background>
       </Desktop>

    </Desktops>

---

### Post by Gnomeye on 2010-06-06
> **eeried said:**
> It's a pity your howto is so thin as I'm looking for some manual.

try here [ArchWiki]("http://wiki.archlinux.org/index.php/JWM")

---

### Post by oui on 2010-06-17
Hi

I am using JWM only in 10.04 and it works very well, really.

The only one deception is that I don't find access to the keyboard settings and I know that JWM has an effect on them.

One char, only one char :lolflag: , has two different actions under JWM and not under KDE, it is the combinaison of ' and c with the US keyboard layout 'accentos' beeing ç in Seamonkey etc. but &#263; in Kopete, Open Office and Konqueror ):P (yes, with the same keys combination!!!) . it is of course very bad for people writing Portuguese or French...

And I don't find the way to change it at all.

Analog the combination Alt+Home don't works (it would have to be 'home page' Seamonkey) at all.


There is also a little problem in following red lines:

[COLOR="Red"]       <!-- <Restart label="Restart" icon="restart.png"/> -->
       <Exit label="Exit" confirm="true" icon="exit.png"/>
       <!-- <Program label="Shutdown" confirm="false" icon="exit.png">/usr/lib/jwm/jwm-poweroff.sh</Program> -->[/COLOR]

Exit works well. After exit, you are in console modus again. You can restart the PC with Crtl+Alt+Dell, but not shutdown. To shutdown I enter 'sudo halt' and the required root password.

But the rest works perfectly.

See beelow my .jwmrc. The more important changes are in red. In blue a second very well tray bar. The part in yellow comes ready to use from the therefore installed standard programm Debian 'menu'; you find it under /etc/jwm/jwmrc fresh after X restart as often you install or remove programm. Nothing to do: only mark it and copy it into your ~HOME/.jwmrc. Only the line in green don't works: it works but the terminal for qemu don't stay on the screen :confused: . You have to search for diverse icons and transfer them into the adequat subdir in /urs/share. 


[FONT="Times New Roman"]<?xml version="1.0"?>
 
 <JWM>
 
    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="123">
[COLOR="Green"]       <Program icon="windows.png" label="windows 95">xterm -T "qemu" -e sh -c "qemu w512.img -boot c"</Program>[/COLOR]
[COLOR="Red"]       <Program icon="hdspmixer.png" label="alsamixer">xterm -T "alsamixer" -e sh -c "/usr/bin/alsamixer"</Program>
       <Program icon="/usr/share/pixmaps/grun.xpm" label="grun">grun</Program>
       <Program icon="konqueror.png" label="konqueror">konqueror</Program>
       <Program icon="kopete.png" label="kopete">kopete</Program>
       <Program icon="leafpad.png" label="leafpad">leafpad</Program>
       <Program icon="midori.png" label="midori">midori</Program>
       <Program icon="ooo-writer.png" label="OO writer">oowriter</Program>
       <Program icon="ooo-calc.png" label="OO calc">oocalc</Program>
       <Program icon="ooo-draw.png" label="OO draw">oodraw</Program>
       <Program icon="pcmanfm.png" label="pcmanfm">pcmanfm</Program>
       <Program icon="seamonkey.png" label="seamonkey">seamonkey</Program>
       <Program icon="skype.png" label="skype">skype</Program>
       <Program icon="vala-terminal.png" label="xterm">xterm</Program>
       <Program icon="zim.png" label="zim">zim</Program>
       <Program icon="gprolog.xpm" label="ciao Prolog">xterm -T "ciao Prolog" -e sh -c "/usr/bin/ciao"</Program>
       <Program icon="sun-jcontrol.png" label="Y Prolog">xterm -T "Y Prolog" -e sh -c "java -jar /home/f/YProlog.jar"</Program>[/COLOR]

     <Menu label="Debian">
[COLOR="Orange"]      <Menu label="Aide">
        <Program label="Info" confirm="false">x-terminal-emulator  -T "Info" -e sh -c "info"</Program>
      </Menu>
      <Menu label="Applications">
        <Menu label="Bureautique">
          <Program label="OpenOffice.org Calc" confirm="false">/usr/bin/oocalc</Program>
          <Program label="OpenOffice.org Writer" confirm="false">/usr/bin/oowriter</Program>
        </Menu>
        <Menu label="Dessin et image">
          <Program label="earth" confirm="false">/home/f/google-earth/googleearth</Program>
          <Program label="ImageMagick" confirm="false">/usr/bin/display logo:</Program>
          <Program label="mtPaint" confirm="false">/usr/bin/mtpaint</Program>
          <Program label="MyPaint" confirm="false">/usr/bin/mypaint</Program>
          <Program label="Picasa" confirm="false">/usr/bin/picasa</Program>
          <Program label="OpenOffice.org Draw" confirm="false">/usr/bin/oodraw</Program>
          <Program label="Rawstudio" confirm="false">/usr/bin/rawstudio</Program>
          <Program label="Xara LX" confirm="false">/usr/bin/xaralx</Program>
        </Menu>
        <Menu label="Éditeurs">
          <Program label="LeafPad" confirm="false">/usr/bin/leafpad</Program>
          <Program label="Nano" confirm="false">x-terminal-emulator  -T "Nano" -e sh -c "/bin/nano"</Program>
        </Menu>
        <Menu label="Émulateurs de terminaux">
          <Program label="XTerm" confirm="false">xterm</Program>
          <Program label="X-Terminal as root (GKsu)" confirm="false">/usr/bin/gksu -u root /usr/bin/x-terminal-emulator</Program>
          <Program label="XTerm (Unicode)" confirm="false">uxterm</Program>
        </Menu>
        <Menu label="Gestion de fichiers">
          <Program label="grun" confirm="false">/usr/bin/grun</Program>
          <Program label="PCManFM" confirm="false">/usr/bin/pcmanfm</Program>
        </Menu>
        <Menu label="Interpréteurs de commandes">
          <Program label="Bash" confirm="false">x-terminal-emulator  -T "Bash" -e sh -c "/bin/bash --login"</Program>
          <Program label="Dash" confirm="false">x-terminal-emulator  -T "Dash" -e sh -c "/bin/dash -i"</Program>
          <Program label="Sh" confirm="false">x-terminal-emulator  -T "Sh" -e sh -c "/bin/sh --login"</Program>
        </Menu>
        <Menu label="Net">
          <Menu label="Seamonkey Components">
            <Program label="Seamonkey Browser" confirm="false">/usr/bin/seamonkey</Program>
            <Program label="Seamonkey Composer" confirm="false">/usr/bin/seamonkey -edit</Program>
          </Menu>
        </Menu>
        <Menu label="Programmation">
          <Program label="Python (v2.6)" confirm="false">x-terminal-emulator  -T "Python (v2.6)" -e sh -c "/usr/bin/python2.6"</Program>
          <Program label="Sun Java 6 Web Start (32bit)" confirm="false">/usr/lib/jvm/ia32-java-6-sun-1.6.0.20/bin/javaws -viewer</Program>
        </Menu>
        <Menu label="Réseau">
          <Menu label="Communication">
            <Program label="Ayttm" confirm="false">/usr/bin/ayttm</Program>
            <Program label="Telnet" confirm="false">x-terminal-emulator  -T "Telnet" -e sh -c "/usr/bin/telnet"</Program>
          </Menu>
          <Menu label="Navigateurs web">
            <Program label="Midori" confirm="false">midori</Program>
            <Program label="w3m" confirm="false">x-terminal-emulator  -T "w3m" -e sh -c "/usr/bin/w3m /usr/share/doc/w3m/MANUAL.html"</Program>
          </Menu>
          <Program label="Seamonkey Navigator" confirm="false">/usr/bin/seamonkey</Program>
        </Menu>
        <Menu label="Sciences">
          <Menu label="Mathématiques">
            <Program label="Bc" confirm="false">x-terminal-emulator  -T "Bc" -e sh -c "/usr/bin/bc"</Program>
            <Program label="OpenOffice.org Math" confirm="false">/usr/bin/oomath</Program>
          </Menu>
        </Menu>
        <Menu label="Son et musique">
          <Program label="Echomixer" confirm="false">/usr/bin/echomixer</Program>
          <Program label="Envy24 control" confirm="false">/usr/bin/envy24control</Program>
          <Program label="HDSPConf" confirm="false">/usr/bin/hdspconf</Program>
          <Program label="HDSPMixer" confirm="false">/usr/bin/hdspmixer</Program>
          <Program label="MuseScore" confirm="false">mscore</Program>
          <Program label="Rmedigicontrol" confirm="false">/usr/bin/rmedigicontrol</Program>
        </Menu>
        <Menu label="Système">
          <Menu label="Administration">
            <Program label="Aptitude" confirm="false">x-terminal-emulator  -T "Aptitude" -e sh -c "/usr/bin/aptitude"</Program>
            <Program label="Debian Task selector" confirm="false">x-terminal-emulator  -T "Debian Task selector" -e sh -c "su-to-root -c tasksel"</Program>
            <Program label="DSL/PPPoE configuration tool" confirm="false">x-terminal-emulator  -T "DSL/PPPoE configuration tool" -e sh -c "/usr/sbin/pppoeconf"</Program>
            <Program label="Editres" confirm="false">editres</Program>
            <Program label="GNOME partition editor" confirm="false">su-to-root -X -c /usr/sbin/gparted</Program>
            <Program label="OpenJDK Java 6 Policy Tool" confirm="false">/usr/lib/jvm/java-6-openjdk/bin/policytool</Program>
            <Program label="pppconfig" confirm="false">x-terminal-emulator  -T "pppconfig" -e sh -c "su-to-root -p root -c /usr/sbin/pppconfig"</Program>
            <Program label="Sun Java 6 Plugin Control Panel (32bit)" confirm="false">/usr/lib/jvm/ia32-java-6-sun-1.6.0.20/bin/ControlPanel</Program>
            <Program label="Xfontsel" confirm="false">xfontsel</Program>
            <Program label="Xkill" confirm="false">xkill</Program>
            <Program label="Xrefresh" confirm="false">xrefresh</Program>
          </Menu>
          <Program label="clex" confirm="false">x-terminal-emulator  -T "clex" -e sh -c "/usr/bin/clex"</Program>
          <Menu label="Gestionnaires de paquets">
            <Program label="Synaptic Package Manager" confirm="false">/usr/bin/gksu /usr/sbin/synaptic</Program>
          </Menu>
          <Menu label="Matériel">
            <Program label="Xvidtune" confirm="false">xvidtune</Program>
          </Menu>
          <Menu label="Sécurité">
            <Program label="Sun Java 6 Policy Tool (32bit)" confirm="false">/usr/lib/jvm/ia32-java-6-sun-1.6.0.20/bin/policytool</Program>
          </Menu>
          <Menu label="Surveillance">
            <Program label="Pstree" confirm="false">x-terminal-emulator  -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
            <Program label="Top" confirm="false">x-terminal-emulator  -T "Top" -e sh -c "/usr/bin/top"</Program>
            <Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
          </Menu>
        </Menu>
        <Menu label="Vidéo">
          <Program label="gxine video player" confirm="false">/usr/bin/gxine</Program>
        </Menu>
      </Menu>[/COLOR]
    </Menu>

         <Separator/>
[COLOR="Red"]       <!-- <Restart label="Restart" icon="restart.png"/> -->
       <Exit label="Exit" confirm="true" icon="exit.png"/>
       <!-- <Program label="Shutdown" confirm="false" icon="exit.png">/usr/lib/jwm/jwm-poweroff.sh</Program> -->[/COLOR]
    </RootMenu>
 
    <Group>
       <Class>Pidgin</Class>
       <Option>sticky</Option>
    </Group>
 
    <Group>
       <Name>gkrellm2</Name>
       <Option>nolist</Option>
    </Group>
 
    <Group>
       <Name>rxvt</Name>
       <Option>vmax</Option>
    </Group>

    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
[COLOR="Blue"]
    <Tray autohide="true" insert="down" valign="center" halign="left" border="0" width="24" layout="vertical">
		<TrayButton popup="mixer" icon="hdspmixer.png" >exec:xterm -T "alsamixer" -e sh -c "/usr/bin/alsamixer"</TrayButton>
		<TrayButton popup="konqueror" icon="konqueror.png">exec:su-to-root -X -c /usr/bin/konqueror</TrayButton>
		<TrayButton popup="leafpad" icon="leafpad.png">exec:leafpad</TrayButton>
		<TrayButton popup="grun" icon="grun.xpm">exec:grun</TrayButton>
		<TrayButton popup="pcmanfm" icon="pcmanfm.png">exec:pcmanfm</TrayButton>
		<TrayButton popup="seamonkey" icon="seamonkey.png">exec:seamonkey</TrayButton>
		<TrayButton popup="console" icon="vala-terminal.png">exec:x-terminal-emulator</TrayButton>
		<TrayButton popup="zim" icon="zim.png">exec:zim</TrayButton>
		<TaskList/>
		<Dock/>
    </Tray>
[/COLOR]
[COLOR="Red"]
     <Tray autohide="true" x="0" y="-1" height="22">
        <!-- Additional TrayButton attribute: label -->
       <TrayButton label="menu">root:1</TrayButton>
        <TrayButton label="_">showdesktop</TrayButton>
        <!-- Additional Pager attributes; width, height -->
       <Pager/>
        <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
       <Dock/>
       <!-- Additional Swallow attribute: height -->
       <Swallow name="xload" width="64">
          xload -nolabel -bg black -fg red -hl white
       </Swallow>
       <Clock format="%H:%M">xclock</Clock>
    </Tray>
[/COLOR] 
    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>white</Text>
          <Title>#70849d:#2e3a67</Title>
          <Corner>white</Corner>
          <Outline>black</Outline>
       </Active>
 
       <Inactive>
          <Text>#aaaaaa</Text>
          <Title>#808488:#303438</Title>
          <Corner>#aaaaaa</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <ActiveForeground>black</ActiveForeground>
       <ActiveBackground>gray90:gray70</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Background>gray90</Background>
       <Foreground>black</Foreground>
    </TrayStyle>
 
    <PagerStyle>
       <Outline>black</Outline>
       <Foreground>gray90</Foreground>
       <Background>#808488</Background>
       <ActiveForeground>#70849d</ActiveForeground>
       <ActiveBackground>#2e3a67</ActiveBackground>
    </PagerStyle>
 
    <MenuStyle>
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Foreground>black</Foreground>
       <Background>gray90</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Outline>black</Outline>
       <Foreground>black</Foreground>
       <Background>yellow</Background>
    </PopupStyle>
 
[COLOR="Red"]    <IconPath>/usr/share/pixmaps</IconPath>
    <IconPath>/usr/share/icons/hicolor/48x48/apps/</IconPath>
    <IconPath>/usr/share/icons/</IconPath>
[/COLOR]
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="4">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->
 <!-- #DEBIAN change. Was bg.xpm -->
       <Background type="tile">$HOME/jwm-bg.xpm</Background>
 
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>sloppy</FocusModel>
 
    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">border</SnapMode>
 
    <!-- The move mode (outline or opaque) -->
    <MoveMode>opaque</MoveMode>
 
    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>opaque</ResizeMode>
 
[COLOR="Magenta"]    <!-- Key bindings
 
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="h">left</Key>
    <Key key="j">down</Key>
    <Key key="k">up</Key>
    <Key key="l">right</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>
 
 DEBIAN unused
    <Key mask="A" key="Tab">nextstacked</Key>
 #DEBIAN add
    <Key mask="A" key="Tab">next</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key> -->
[/COLOR]

 </JWM>
 [/FONT]

If you find ways to avoid the little problems above (change fonts, change double effect on different letters, activate Alt+Home as Home in Seamonkey, make that the qemu windows stays on the screen instead to disappear immediately, and activate shutdown) please answer here in this discussion and explain you solution!

---

### Post by oui on 2010-06-17
After adding of the comment marks in the part in color 'magenta' above, all keys of my keyboard works now normaly!

The key bindings seem to have a unlucky effect on complex keyboards.

---

### Post by frenchn00b on 2010-07-09
Does anyone here have a working .jwmrc file, with a "Debian" menu that lists most installed applications ?

---

### Post by AgentArmstrong on 2010-12-15
> **cogitordi said:**
> I have seen JWM in Damn Small Linux and I am impressed. I'd like to use JWM on my old Thinkpad. When you use JWM in Ubuntu, can the Network Manager still be used for wireless connectivity?

i am running jwm on ubuntu 10 and it is running just fine

---

### Post by AgentArmstrong on 2010-12-15
> **frenchn00b said:**
> Does anyone here have a working .jwmrc file, with a "Debian" menu that lists most installed applications ?


<?xml version="1.0"?>
 
 <JWM>
 
    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="123">
       <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
          <Program icon="firefox.png" label="Www Browser">x-www-browser</Program>
 
 <!-- #DEBIAN unused
       <Menu icon="folder.png" label="Applications">
          <Program icon="firefox.png" label="Iceweasel">iceweasel</Program>
 
          <Program icon="audacious.png" label="Audacious">audacious</Program>
          <Program icon="dia.png" label="Dia">dia</Program>
          <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
          <Program icon="gimp.png" label="Gimp">gimp</Program>
          <Program icon="gtk-gnutella.png" label="gtk-gnutella">
             gtk-gnutella
          </Program>
          <Program icon="gxine.png" label="gxine">gxine</Program>
          <Program icon="ooffice.png" label="Open Office">ooffice</Program>
       </Menu>
       <Menu icon="folder.png" label="Utilities">
          <Program icon="xcalc.png">xcalc</Program>
          <Program icon="xfontsel.png">xfontsel</Program>
          <Program icon="xmag.png">xmag</Program>
          <Program icon="xprop.png" label="xprop">
             xprop | xmessage -file -
          </Program>
       </Menu>
 -->
     <Menu label="Debian">
      <Menu label="Applications">
        <Menu label="Accessibility">
          <Program label="Xmag" confirm="false">xmag</Program>
        </Menu>
        <Menu label="Data Management">
          <Program label="Tomboy" confirm="false">/usr/bin/tomboy</Program>
        </Menu>
        <Menu label="Editors">
          <Program label="Gedit" confirm="false">/usr/bin/gedit</Program>
          <Program label="Nano" confirm="false">x-terminal-emulator  -T "Nano" -e sh -c "/bin/nano"</Program>
          <Program label="SubtitleEditor" confirm="false">/usr/bin/subtitleeditor</Program>
          <Program label="Xedit" confirm="false">xedit</Program>
        </Menu>
        <Menu label="File Management">
          <Program label="Baobab" confirm="false">/usr/bin/baobab</Program>
          <Program label="Brasero" confirm="false">/usr/bin/brasero</Program>
          <Program label="File-Roller" confirm="false">/usr/bin/file-roller</Program>
          <Program label="GNOME Search Tool" confirm="false">/usr/bin/gnome-search-tool</Program>
          <Program label="grun" confirm="false">/usr/bin/grun</Program>
          <Program label="Nautilus" confirm="false">/usr/bin/nautilus</Program>
          <Program label="Thunar" confirm="false">/usr/bin/thunar</Program>
          <Program label="Xfdesktop" confirm="false">xfdesktop</Program>
        </Menu>
        <Menu label="Graphics">
          <Program label="Agave" confirm="false">/usr/bin/agave</Program>
          <Program label="Blender (full screen)" confirm="false">/usr/bin/blender</Program>
          <Program label="Blender (windowed)" confirm="false">/usr/bin/blender -w</Program>
          <Program label="FontForge" confirm="false">/usr/bin/fontforge</Program>
          <Program label="GEM" confirm="false">/usr/bin/pd-gem</Program>
          <Program label="GNOME Screenshot Tool" confirm="false">/usr/bin/gnome-panel-screenshot</Program>
          <Program label="Hugin" confirm="false">/usr/bin/hugin</Program>
          <Program label="ImageMagick" confirm="false">/usr/bin/display logo:</Program>
          <Program label="Inkscape" confirm="false">/usr/bin/inkscape</Program>
          <Program label="Kino" confirm="false">/usr/bin/kino</Program>
          <Program label="OpenOffice.org Draw" confirm="false">/usr/bin/oodraw</Program>
          <Program label="Scribus (stable)" confirm="false">/usr/bin/scribus</Program>
          <Program label="Stopmotion" confirm="false">/usr/bin/stopmotion</Program>
          <Program label="The GIMP" confirm="false">/usr/bin/gimp</Program>
          <Program label="XSane" confirm="false">/usr/bin/xsane</Program>
          <Program label="X Window Snapshot" confirm="false">xwd | xwud</Program>
        </Menu>
        <Menu label="Network">
          <Menu label="Communication">
            <Program label="Evolution" confirm="false">/usr/bin/evolution</Program>
            <Program label="Manhole Twisted Client" confirm="false">/usr/bin/manhole</Program>
            <Program label="Telnet" confirm="false">x-terminal-emulator  -T "Telnet" -e sh -c "/usr/bin/telnet"</Program>
            <Program label="Terminal Server Client" confirm="false">/usr/bin/tsclient -f</Program>
            <Program label="Twisted Application Generator" confirm="false">/usr/bin/tkmktap</Program>
            <Program label="Twisted SSH Client" confirm="false">/usr/bin/tkconch</Program>
            <Program label="Xbiff" confirm="false">xbiff</Program>
          </Menu>
          <Menu label="File Transfer">
            <Program label="Nicotine-Plus" confirm="false">/usr/bin/nicotine</Program>
            <Program label="Transmission BitTorrent Client (GTK)" confirm="false">/usr/bin/transmission</Program>
          </Menu>
          <Menu label="Monitoring">
            <Program label="WICD" confirm="false">/usr/bin/wicd-gtk</Program>
          </Menu>
          <Menu label="Web Browsing">
            <Program label="Firefox Browser" confirm="false">/usr/bin/firefox</Program>
            <Program label="Links 2" confirm="false">/usr/bin/links2 -g</Program>
            <Program label="Links 2 (text)" confirm="false">x-terminal-emulator  -T "Links 2 (text)" -e sh -c "/usr/bin/links2"</Program>
            <Program label="w3m" confirm="false">x-terminal-emulator  -T "w3m" -e sh -c "/usr/bin/w3m /usr/share/doc/w3m/MANUAL.html"</Program>
          </Menu>
        </Menu>
        <Menu label="Office">
          <Program label="HPLIP Fax address book" confirm="false">/usr/bin/hp-fab</Program>
          <Program label="HPLIP Fax utility" confirm="false">/usr/bin/hp-sendfax</Program>
          <Program label="OpenOffice.org Calc" confirm="false">/usr/bin/oocalc</Program>
          <Program label="OpenOffice.org Impress" confirm="false">/usr/bin/ooimpress</Program>
          <Program label="OpenOffice.org Writer" confirm="false">/usr/bin/oowriter</Program>
        </Menu>
        <Menu label="Programming">
          <Program label="Erlang Shell" confirm="false">x-terminal-emulator  -T "Erlang Shell" -e sh -c "/usr/bin/erl"</Program>
          <Program label="GDB" confirm="false">x-terminal-emulator  -T "GDB" -e sh -c "/usr/bin/gdb"</Program>
          <Program label="Guile 1.8" confirm="false">x-terminal-emulator  -T "Guile 1.8" -e sh -c "/usr/bin/guile-1.8"</Program>
          <Program label="Python (v2.6)" confirm="false">x-terminal-emulator  -T "Python (v2.6)" -e sh -c "/usr/bin/python2.6"</Program>
          <Program label="Tclsh8.4" confirm="false">x-terminal-emulator  -T "Tclsh8.4" -e sh -c "/usr/bin/tclsh8.4"</Program>
          <Program label="Tclsh8.5" confirm="false">x-terminal-emulator  -T "Tclsh8.5" -e sh -c "/usr/bin/tclsh8.5"</Program>
          <Program label="TkWish8.4" confirm="false">x-terminal-emulator -e /usr/bin/wish8.4</Program>
          <Program label="TkWish8.5" confirm="false">x-terminal-emulator -e /usr/bin/wish8.5</Program>
        </Menu>
        <Menu label="Science">
          <Menu label="Astronomy">
            <Program label="wmSpaceWeather" confirm="false">/usr/bin/wmSpaceWeather</Program>
          </Menu>
          <Menu label="Mathematics">
            <Program label="Bc" confirm="false">x-terminal-emulator  -T "Bc" -e sh -c "/usr/bin/bc"</Program>
            <Program label="Dc" confirm="false">x-terminal-emulator  -T "Dc" -e sh -c "/usr/bin/dc"</Program>
            <Program label="GCalcTool" confirm="false">/usr/bin/gcalctool</Program>
            <Program label="OpenOffice.org Math" confirm="false">/usr/bin/oomath</Program>
            <Program label="Xcalc" confirm="false">xcalc</Program>
          </Menu>
        </Menu>
        <Menu label="Shells">
          <Program label="Bash" confirm="false">x-terminal-emulator  -T "Bash" -e sh -c "/bin/bash --login"</Program>
          <Program label="Dash" confirm="false">x-terminal-emulator  -T "Dash" -e sh -c "/bin/dash -i"</Program>
          <Program label="Sh" confirm="false">x-terminal-emulator  -T "Sh" -e sh -c "/bin/sh --login"</Program>
        </Menu>
        <Menu label="Sound">
          <Program label="Aconnectgui" confirm="false">/usr/bin/aconnectgui</Program>
          <Program label="aeolus" confirm="false">/usr/bin/aeolus</Program>
          <Program label="Ardour GTK2" confirm="false">/usr/bin/ardour2</Program>
          <Program label="Audacious" confirm="false">/usr/bin/audacious2</Program>
          <Program label="Audacity" confirm="false">/usr/bin/audacity</Program>
          <Program label="aumix" confirm="false">x-terminal-emulator  -T "aumix" -e sh -c "/usr/bin/aumix"</Program>
          <Program label="BEAST" confirm="false">/usr/bin/beast</Program>
          <Program label="bristol" confirm="false">/usr/bin/startBristol</Program>
          <Program label="cseditor" confirm="false">/usr/bin/cseditor</Program>
          <Program label="csound5gui" confirm="false">/usr/bin/csound5gui</Program>
          <Program label="Echomixer" confirm="false">/usr/bin/echomixer</Program>
          <Program label="Envy24 control" confirm="false">/usr/bin/envy24control</Program>
          <Program label="Freebirth" confirm="false">/usr/bin/freebirth</Program>
          <Program label="Freqtweak" confirm="false">/usr/bin/freqtweak</Program>
          <Program label="Genpo" confirm="false">genpo /usr/share/genpo/English-0.9.5.org</Program>
          <Program label="gmix (Gnome 2.0 Mixer)" confirm="false">/usr/bin/gnome-volume-control</Program>
          <Program label="grecord (GNOME 2.0 Recorder)" confirm="false">/usr/bin/gnome-sound-recorder</Program>
          <Program label="gtick" confirm="false">/usr/bin/gtick</Program>
          <Program label="HDSPConf" confirm="false">/usr/bin/hdspconf</Program>
          <Program label="HDSPMixer" confirm="false">/usr/bin/hdspmixer</Program>
          <Program label="Hydrogen" confirm="false">/usr/bin/hydrogen</Program>
          <Program label="Jackbeat" confirm="false">/usr/bin/jackbeat</Program>
          <Program label="JACK Bitmeter" confirm="false">/usr/bin/bitmeter</Program>
          <Program label="JACK Control" confirm="false">/usr/bin/qjackctl</Program>
          <Program label="jackeq" confirm="false">/usr/bin/jackeq</Program>
          <Program label="JACK meterbridge" confirm="false">/usr/bin/meterbridge -t vu alsa_pcm:playback_1 alsa_pcm:playback_2</Program>
          <Program label="JACK Rack" confirm="false">/usr/bin/jack-rack</Program>
          <Program label="JACK Timemachine" confirm="false">/usr/bin/timemachine</Program>
          <Program label="jamin" confirm="false">/usr/bin/jamin</Program>
          <Program label="LMMS" confirm="false">/usr/bin/lmms</Program>
          <Program label="MIDI Virtual Keyboard" confirm="false">/usr/bin/vkeybd</Program>
          <Program label="Mixxx" confirm="false">/usr/bin/mixxx</Program>
          <Program label="MusE" confirm="false">/usr/bin/muse</Program>
          <Program label="MuseScore" confirm="false">mscore</Program>
          <Program label="padevchooser" confirm="false">/usr/bin/padevchooser</Program>
          <Program label="paman" confirm="false">/usr/bin/paman</Program>
          <Program label="paprefs" confirm="false">/usr/bin/paprefs</Program>
          <Program label="Patchage" confirm="false">/usr/bin/patchage</Program>
          <Program label="pavucontrol" confirm="false">/usr/bin/pavucontrol</Program>
          <Program label="pavumeter" confirm="false">/usr/bin/pavumeter</Program>
          <Program label="PureData" confirm="false">/usr/bin/pd</Program>
          <Program label="Rhythmbox" confirm="false">/usr/bin/rhythmbox</Program>
          <Program label="Rmedigicontrol" confirm="false">/usr/bin/rmedigicontrol</Program>
          <Program label="Seq24" confirm="false">/usr/bin/seq24</Program>
          <Program label="SooperLooper" confirm="false">/usr/bin/slgui</Program>
          <Program label="STKDemo" confirm="false">/usr/bin/STKDemo</Program>
          <Program label="terminatorX" confirm="false">/usr/bin/terminatorX</Program>
          <Program label="TiMidity++" confirm="false">timidity -ia</Program>
          <Program label="TK-707" confirm="false">/usr/bin/tk707</Program>
          <Program label="winsound" confirm="false">/usr/bin/winsound</Program>
          <Program label="zynaddsubfx" confirm="false">/usr/bin/zynaddsubfx</Program>
        </Menu>
        <Menu label="System">
          <Menu label="Administration">
            <Program label="Aptitude" confirm="false">x-terminal-emulator  -T "Aptitude" -e sh -c "/usr/bin/aptitude"</Program>
            <Program label="bbrun" confirm="false">/usr/bin/bbrun</Program>
            <Program label="Debian Task selector" confirm="false">x-terminal-emulator  -T "Debian Task selector" -e sh -c "su-to-root -c tasksel"</Program>
            <Program label="DSL/PPPoE configuration tool" confirm="false">x-terminal-emulator  -T "DSL/PPPoE configuration tool" -e sh -c "/usr/sbin/pppoeconf"</Program>
            <Program label="Editres" confirm="false">editres</Program>
            <Program label="fluxconf" confirm="false">/usr/bin/fluxconf</Program>
            <Program label="fluxkeys" confirm="false">/usr/bin/fluxkeys</Program>
            <Program label="fluxmenu" confirm="false">/usr/bin/fluxmenu</Program>
            <Program label="fontmatrix" confirm="false">/usr/bin/fontmatrix</Program>
            <Program label="Gnome Control Center" confirm="false">/usr/bin/gnome-control-center</Program>
            <Program label="GNOME Network Tool" confirm="false">/usr/bin/gnome-nettool</Program>
            <Program label="gsetroot" confirm="false">/usr/bin/gsetroot</Program>
            <Program label="HPLIP File printing" confirm="false">/usr/bin/hp-print</Program>
            <Program label="Network Admin" confirm="false">/usr/bin/network-admin</Program>
            <Program label="OpenJDK Java 6 Policy Tool" confirm="false">/usr/lib/jvm/java-6-openjdk/bin/policytool</Program>
            <Program label="pppconfig" confirm="false">x-terminal-emulator  -T "pppconfig" -e sh -c "su-to-root -p root -c /usr/sbin/pppconfig"</Program>
            <Program label="Shares Admin" confirm="false">/usr/bin/shares-admin</Program>
            <Program label="TeXconfig" confirm="false">x-terminal-emulator  -T "TeXconfig" -e sh -c "/usr/bin/texconfig"</Program>
            <Program label="Time Admin" confirm="false">/usr/bin/time-admin</Program>
            <Program label="User accounts Admin" confirm="false">/usr/bin/users-admin</Program>
            <Program label="Xclipboard" confirm="false">xclipboard</Program>
            <Program label="Xfontsel" confirm="false">xfontsel</Program>
            <Program label="XFrun4" confirm="false">xfrun4</Program>
            <Program label="Xkill" confirm="false">xkill</Program>
            <Program label="Xrefresh" confirm="false">xrefresh</Program>
          </Menu>
          <Menu label="Hardware">
            <Program label="HPLIP Toolbox" confirm="false">/usr/bin/hp-toolbox</Program>
            <Program label="Xvidtune" confirm="false">xvidtune</Program>
          </Menu>
          <Menu label="Language Environment">
            <Program label="im-switch" confirm="false">x-terminal-emulator  -T "im-switch" -e sh -c "/usr/bin/im-switch"</Program>
          </Menu>
          <Menu label="Monitoring">
            <Program label="GNOME Log Viewer" confirm="false">/usr/bin/gnome-system-log</Program>
            <Program label="GNOME system monitor" confirm="false">/usr/bin/gnome-system-monitor</Program>
            <Program label="Pstree" confirm="false">x-terminal-emulator  -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
            <Program label="Top" confirm="false">x-terminal-emulator  -T "Top" -e sh -c "/usr/bin/top"</Program>
            <Program label="Xconsole" confirm="false">xconsole -file /dev/xconsole</Program>
            <Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
            <Program label="Xload" confirm="false">xload</Program>
          </Menu>
          <Menu label="Package Management">
            <Program label="Synaptic Package Manager" confirm="false">/usr/bin/gksu /usr/sbin/synaptic</Program>
          </Menu>
          <Menu label="Security">
            <Program label="Seahorse" confirm="false">/usr/bin/seahorse</Program>
          </Menu>
        </Menu>
        <Menu label="Terminal Emulators">
          <Program label="Eterm" confirm="false">/usr/bin/Eterm</Program>
          <Program label="Gnome Terminal" confirm="false">/usr/bin/gnome-terminal</Program>
          <Program label="Xfce Terminal" confirm="false">/usr/bin/xfce4-terminal</Program>
          <Program label="Xfterm4" confirm="false">x-terminal-emulator  -T "Xfterm4" -e sh -c "xfterm4"</Program>
          <Program label="XTerm" confirm="false">xterm</Program>
          <Program label="X-Terminal as root (GKsu)" confirm="false">/usr/bin/gksu -u root /usr/bin/x-terminal-emulator</Program>
          <Program label="XTerm (Unicode)" confirm="false">uxterm</Program>
        </Menu>
        <Menu label="Text">
          <Program label="Character map" confirm="false">/usr/bin/gucharmap</Program>
          <Program label="Fortune" confirm="false">sh -c 'while /usr/games/fortune | col -x | xmessage -center -buttons OK:1,Another:0 -default OK -file - ; do :; done'</Program>
          <Program label="GNOME Dictionary" confirm="false">/usr/bin/gnome-dictionary</Program>
        </Menu>
        <Menu label="Video">
          <Program label="Totem" confirm="false">/usr/bin/totem</Program>
          <Program label="VLC media player" confirm="false">/usr/bin/qvlc</Program>
        </Menu>
        <Menu label="Viewers">
          <Program label="Evince" confirm="false">/usr/bin/evince</Program>
          <Program label="Eye of GNOME" confirm="false">/usr/bin/eog</Program>
          <Program label="F-Spot" confirm="false">/usr/bin/f-spot</Program>
          <Program label="Me TV" confirm="false">/usr/bin/me-tv</Program>
          <Program label="Xditview" confirm="false">xditview</Program>
          <Program label="XDvi" confirm="false">/usr/bin/xdvi</Program>
        </Menu>
      </Menu>
      <Menu label="Games">
        <Menu label="Action">
          <Program label="Airstrike" confirm="false">/usr/games/airstrike</Program>
          <Program label="Allegro Demo" confirm="false">/usr/games/all-demo</Program>
          <Program label="Amphetamine" confirm="false">/usr/games/amph</Program>
          <Program label="Chocolate Doom" confirm="false">/usr/games/chocolate-doom</Program>
          <Program label="Gnibbles" confirm="false">/usr/games/gnibbles</Program>
          <Program label="PrBoom" confirm="false">/usr/games/prboom</Program>
        </Menu>
        <Menu label="Board">
          <Program label="Four-in-a-row" confirm="false">/usr/games/gnect</Program>
          <Program label="GL Chess" confirm="false">/usr/games/glchess</Program>
          <Program label="Gnome GYahtzee" confirm="false">/usr/games/gtali</Program>
          <Program label="Gnome Iagno" confirm="false">/usr/games/iagno</Program>
          <Program label="Gnome Lines" confirm="false">/usr/games/glines</Program>
          <Program label="Gnome Mahjongg" confirm="false">/usr/games/mahjongg</Program>
        </Menu>
        <Menu label="Card">
          <Program label="Gnome FreeCell" confirm="false">/usr/games/sol --variation freecell</Program>
          <Program label="Gnome Solitaire Games" confirm="false">/usr/games/sol</Program>
        </Menu>
        <Menu label="Puzzles">
          <Program label="gbrainy" confirm="false">/usr/games/gbrainy</Program>
          <Program label="Gnome Robots" confirm="false">/usr/games/gnobots2</Program>
          <Program label="Gnome Sudoku" confirm="false">/usr/games/gnome-sudoku</Program>
          <Program label="Gnome Tetravex" confirm="false">/usr/games/gnotravex</Program>
          <Program label="Gnomine" confirm="false">/usr/games/gnomine</Program>
          <Program label="Lights Off" confirm="false">/usr/games/lightsoff</Program>
          <Program label="Quadrapassel" confirm="false">/usr/games/quadrapassel</Program>
          <Program label="Swell Foop" confirm="false">/usr/games/swell-foop</Program>
        </Menu>
        <Menu label="Strategy">
          <Program label="Dopewars (GTK)" confirm="false">/usr/games/dopewars -w</Program>
          <Program label="Dopewars server" confirm="false">x-terminal-emulator  -T "Dopewars server" -e sh -c "/usr/games/dopewars -s"</Program>
          <Program label="Dopewars (text)" confirm="false">x-terminal-emulator  -T "Dopewars (text)" -e sh -c "/usr/games/dopewars -t"</Program>
        </Menu>
        <Menu label="Toys">
          <Program label="Oclock" confirm="false">oclock</Program>
          <Program label="Xclock (analog)" confirm="false">xclock -analog</Program>
          <Program label="Xclock (digital)" confirm="false">xclock -digital -update 1</Program>
          <Program label="Xeyes" confirm="false">xeyes</Program>
          <Program label="Xlogo" confirm="false">xlogo</Program>
        </Menu>
      </Menu>
      <Menu label="Help">
        <Program label="Info" confirm="false">x-terminal-emulator  -T "Info" -e sh -c "info"</Program>
        <Program label="TeXdoctk" confirm="false">/usr/bin/texdoctk</Program>
        <Program label="Xfce4-about" confirm="false">xfce4-about</Program>
        <Program label="Xfhelp4" confirm="false">xfhelp4</Program>
        <Program label="Xman" confirm="false">xman</Program>
        <Program label="yelp" confirm="false">/usr/bin/yelp</Program>
      </Menu>
      <Menu label="Screen">
        <Menu label="Locking">
          <Program label="Xflock4" confirm="false">x-terminal-emulator  -T "Xflock4" -e sh -c "xflock4"</Program>
        </Menu>
      </Menu>
    </Menu>

         <Separator/>
       <Restart label="Restart" icon="restart.png"/>
       <Exit label="Exit" confirm="true" icon="exit.png"/>
       <Program label="Shutdown" confirm="false" icon="exit.png">
         /usr/lib/jwm/jwm-poweroff.sh
      </Program>
    </RootMenu>
 
    <Group>
       <Class>Pidgin</Class>
       <Option>sticky</Option>
    </Group>
 
    <Group>
       <Name>gkrellm2</Name>
       <Option>nolist</Option>
    </Group>
 
    <Group>
       <Name>rxvt</Name>
       <Option>vmax</Option>
    </Group>
 
    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
    <Tray  x="0" y="-1" height="32">
 
       <!-- Additional TrayButton attribute: label -->
       <TrayButton label="JWM">root:1</TrayButton>
 
       <TrayButton label="_">showdesktop</TrayButton>
 
       <!-- Additional Pager attributes; width, height -->
       <Pager/>
 
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
 
       <Dock/>
 
       <!-- Additional Swallow attribute: height -->
       <Swallow name="xload" width="64">
          xload -nolabel -bg black -fg red -hl white
       </Swallow>
 
       <Clock format="%H:%M">xclock</Clock>
 
    </Tray>
 
    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>white</Text>
          <Title>#70849d:#2e3a67</Title>
          <Corner>white</Corner>
          <Outline>black</Outline>
       </Active>
 
       <Inactive>
          <Text>#aaaaaa</Text>
          <Title>#808488:#303438</Title>
          <Corner>#aaaaaa</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <ActiveForeground>black</ActiveForeground>
       <ActiveBackground>gray90:gray70</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Background>gray90</Background>
       <Foreground>black</Foreground>
    </TrayStyle>
 
    <PagerStyle>
       <Outline>black</Outline>
       <Foreground>gray90</Foreground>
       <Background>#808488</Background>
       <ActiveForeground>#70849d</ActiveForeground>
       <ActiveBackground>#2e3a67</ActiveBackground>
    </PagerStyle>
 
    <MenuStyle>
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Foreground>black</Foreground>
       <Background>gray90</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Outline>black</Outline>
       <Foreground>black</Foreground>
       <Background>yellow</Background>
    </PopupStyle>
 
    <IconPath>
       $HOME/.icons
    </IconPath>
 
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="4">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->
 <!-- #DEBIAN change. Was bg.xpm -->
       <Background type="tile">$HOME/jwm-bg.xpm</Background>
 
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>sloppy</FocusModel>
 
    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">border</SnapMode>
 
    <!-- The move mode (outline or opaque) -->
    <MoveMode>opaque</MoveMode>
 
    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>opaque</ResizeMode>
 
    <!-- Key bindings -->
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="h">left</Key>
    <Key key="j">down</Key>
    <Key key="k">up</Key>
    <Key key="l">right</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>
 
 <!-- #DEBIAN unused -->
    <Key mask="A" key="Tab">nextstacked</Key>
 -->
 <!-- #DEBIAN add -->
    <Key mask="A" key="Tab">next</Key>
 
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key>
 
 </JWM>
 
 \\:D/

---

### Post by AgentArmstrong on 2010-12-15
a little long but i have a lot on my system  but i hope that helps

---

