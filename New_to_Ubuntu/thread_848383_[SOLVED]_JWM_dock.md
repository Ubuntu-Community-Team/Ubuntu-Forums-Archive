---
title: "[SOLVED] JWM dock?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-03
[screenshot]("http://www.slitaz.org/pics/screenshots/index-desktop-1280x800.png")

That screenshot is of slitaz using JWM.  It has a nice bar (dock/tray?) at the top and I was wondering where can I get one that will work with JWM?  Or is it integrated?

---

### Post by AnLGP on 2008-07-03
OK they use lxpanel

[http://freshmeat.net/projects/lxpanel/](http://freshmeat.net/projects/lxpanel/)

I installed it via synaptic and "lxpanel" in the terminal to start it and it says this:

tray: another systray already running

I'm willing to bet (as a non betting man) that's because of how JWM is set up.  Here's the .jwmrc
________________________________________
 <?xml version="1.0"?>
 
 <JWM>
<StartupCommand>
xstarfish
</StartupCommand>
 
    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="123">
       <Program icon="rxvt.png" label="terminal">x-terminal-emulator</Program>
          <Program icon="firefox.png" label="Www Browser">x-www-browser</Program>
 
 <!-- #DEBIAN
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
          <Program label="leafpad" confirm="false">/usr/bin/leafpad</Program>
          <Program label="gimp" confirm="false">/usr/bin/gimp</Program>
          <Program label="X Window Snapshot" confirm="false">xwd | xwud</Program>
          <Program label="Epiphany web browser (Gecko)" confirm="false">/usr/bin/epiphany-gecko</Program>
        <Menu label="Programming">
          <Program label="Python (v2.5)" confirm="false">x-terminal-emulator  -T "Python (v2.5)" -e sh -c "/usr/bin/python2.5"</Program>
        </Menu>
        <Menu label="Science">
          <Menu label="Mathematics">
            <Program label="Xcalc" confirm="false">xcalc</Program>
          </Menu>
        </Menu>
        <Menu label="Shells">
          <Program label="Bash" confirm="false">x-terminal-emulator  -T "Bash" -e sh -c "/bin/bash --login"</Program>
          <Program label="Sh" confirm="false">x-terminal-emulator  -T "Sh" -e sh -c "/bin/sh --login"</Program>
        </Menu>
        <Menu label="Sound">
          <Program label="Alsamixergui" confirm="false">/usr/bin/alsamixergui</Program>
          <Program label="AlsaPlayer" confirm="false">/usr/bin/alsaplayer -i gtk2</Program>
        </Menu>
        <Menu label="System">
          <Menu label="Administration">
            <Program label="alsaconf" confirm="false">x-terminal-emulator  -T "alsaconf" -e sh -c "su-to-root -p root -c /usr/sbin/alsaconf"</Program>
            <Program label="Aptitude" confirm="false">x-terminal-emulator  -T "Aptitude" -e sh -c "/usr/bin/aptitude"</Program>
            <Program label="Debian Task selector" confirm="false">x-terminal-emulator  -T "Debian Task selector" -e sh -c "su-to-root -c tasksel"</Program>
            <Program label="Editres" confirm="false">editres</Program>
            <Program label="Orphaner (all)" confirm="false">x-terminal-emulator  -T "Orphaner (all)" -e sh -c "su-to-root -c '/usr/sbin/orphaner -a'"</Program>
            <Program label="Orphaner - editkeep" confirm="false">x-terminal-emulator  -T "Orphaner - editkeep" -e sh -c "su-to-root -c '/usr/sbin/editkeep'"</Program>
            <Program label="Orphaner (libs)" confirm="false">x-terminal-emulator  -T "Orphaner (libs)" -e sh -c "su-to-root -c /usr/sbin/orphaner"</Program>
            <Program label="Xclipboard" confirm="false">xclipboard</Program>
            <Program label="Xfontsel" confirm="false">xfontsel</Program>
            <Program label="Xkill" confirm="false">xkill</Program>
            <Program label="Xrefresh" confirm="false">xrefresh</Program>
          </Menu>
          <Menu label="Hardware">
            <Program label="Xvidtune" confirm="false">xvidtune</Program>
          </Menu>
          <Menu label="Monitoring">
            <Program label="Pstree" confirm="false">x-terminal-emulator  -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
            <Program label="Top" confirm="false">x-terminal-emulator  -T "Top" -e sh -c "/usr/bin/top"</Program>
            <Program label="Xconsole" confirm="false">xconsole -file /dev/xconsole</Program>
            <Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
            <Program label="Xload" confirm="false">xload</Program>
          </Menu>
          <Menu label="Package Management">
            <Program label="Synaptic Package Manager" confirm="false">/usr/bin/su-to-root -X -c /usr/sbin/synaptic</Program>
          </Menu>
        </Menu>
        <Menu label="Terminal Emulators">
          <Program label="XTerm" confirm="false">xterm</Program>
          <Program label="X-Terminal as root (GKsu)" confirm="false">/usr/bin/gksu -u root /usr/bin/x-terminal-emulator</Program>
          <Program label="XTerm (Unicode)" confirm="false">uxterm</Program>
        </Menu>
        <Menu label="Viewers">
          <Program label="Xditview" confirm="false">xditview</Program>
          <Program label="Xpdf" confirm="false">/usr/bin/xpdf</Program>
        </Menu>
      </Menu>
      <Menu label="Help">
        <Program label="Info" confirm="false">x-terminal-emulator  -T "Info" -e sh -c "info"</Program>
        <Program label="Xman" confirm="false">xman</Program>
        <Program label="yelp" confirm="false">/usr/bin/yelp</Program>
      </Menu>
    </Menu>

         <Separator/>
<Menu label="Power">
       <Restart label="Restart" icon="restart.png"/>
<Program label="Reboot">sudo reboot</Program>
      <Program label="Shutdown">sudo halt</Program>
       <Exit label="Exit" confirm="true" icon="exit.png"/>
</Menu>    
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
    <Tray  x="0" y="-1" height="25">
 
       <!-- Additional TrayButton attribute: label -->
       <TrayButton label="Menu">root:1</TrayButton>
 
       <TrayButton label="-">showdesktop</TrayButton>
 
       <!-- Additional Pager attributes; width, height -->
       <Pager/>
 
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
 
       <Dock/>
 
       <!-- Additional Swallow attribute: height -->
       <Swallow name="xload" width="64">
          xload -nolabel -bg black -fg orange -hl white
       </Swallow>
 
       <Clock format="%H:%M">xclock</Clock>
 
    </Tray>
 
    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>orange</Text>
          <Title>black</Title>
          <Corner>orange</Corner>
          <Outline>white</Outline>
       </Active>
 
       <Inactive>
          <Text>white</Text>
          <Title>#808488:#303438</Title>
          <Corner>#aaaaaa</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <ActiveForeground>orange</ActiveForeground>
       <ActiveBackground>black</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>black</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Background>black</Background>
       <Foreground>orange</Foreground>
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
       <Foreground>orange</Foreground>
       <Background>black</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>black</ActiveBackground>
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
       <Background type="solid">black</Background>
 
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
 
    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key>
 
 </JWM>
_____________________________________________________
Does anyone know how I can do this?  If I can get lxpanel to work I'll be incredibly happy :)

---

### Post by f37u5g0d on 2008-07-03
I believe that you have to use the panels that come with you desktop.  AKA gnome panels on gnome and kde panels on kde.  You can try to get the gnome panel package in synaptic and run use it on kde but it won't work.  I'm not 100% sure about that though.  Sounds to me like JWM (I'm assuming is alternate to KDE and gnome) already has panels running.  There is one ray of hope for you though.  I know there is an app called kiba dock that works on gnome and KDE.  Try out kiba dock if you want but it stands to reason that I might be wrong about panels and desktop manager integration.

---

### Post by AnLGP on 2008-07-03
JWM stands for Joe's Window Manager.  It is an alternative to GNOME and KDE.  The part I believe to be in question is this:

<!-- Additional tray attributes: autohide, width, border, layer, layout -->
<Tray x="0" y="-1" height="25">

<!-- Additional TrayButton attribute: label -->
<TrayButton label="Menu">root:1</TrayButton>

<TrayButton label="-">showdesktop</TrayButton>

<!-- Additional Pager attributes; width, height -->
<Pager/>

<!-- Additional TaskList attribute: maxwidth -->
<TaskList/>

<Dock/>

<!-- Additional Swallow attribute: height -->
<Swallow name="xload" width="64">
xload -nolabel -bg black -fg orange -hl white
</Swallow>

<Clock format="%H:%M">xclock</Clock>

</Tray>

Mainly because it has the </Tray> attribute.

I figure if I can find out where the Tray starts then I can delete the tray and use lxpanel.  Thanks for your reply :)

---

### Post by kerry_s on 2008-07-03
just take out " <Dock/> " and your good to go. you can delete it or comment it out(<!-- <Dock/> -->).

---

### Post by kerry_s on 2008-07-03
i just looked at the screenshot, you know jwm can do that all on it own?

```
<Tray height="25" width="0" layer="0" valign="center">
<TrayButton icon="Menu.png">root:1</TrayButton>
<TrayButton icon="www.png">exec:firefox</TrayButton>
<TrayButton icon="rox.png">exec:rox</TrayButton>

<Dock/>
etc...
</Tray>

```
just a thought...

---

### Post by AnLGP on 2008-07-03
hey if it can do it all by itself then why would I want something else?  So all I do is C&P that into my JWMRC and I'm good to go..  as long as I add the right stuff?

Where would I add it in the .jwmrc?  Anywhere between the <JWM> tags?

---

### Post by kerry_s on 2008-07-03
i usually keep all the trays in the same section:

```
<?xml version="1.0"?>

<JWM>
<StartupCommand>
xstarfish
</StartupCommand>

<!-- The root menu, if this is undefined you will not get a menu. -->
<!-- Additional RootMenu attributes: onroot, labeled, label -->
<RootMenu height="15" onroot="123">
<Program icon="rxvt.png" label="terminal">x-terminal-emulator</Program>
<Program icon="firefox.png" label="Www Browser">x-www-browser</Program>

<!-- #DEBIAN
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
<Program label="leafpad" confirm="false">/usr/bin/leafpad</Program>
<Program label="gimp" confirm="false">/usr/bin/gimp</Program>
<Program label="X Window Snapshot" confirm="false">xwd | xwud</Program>
<Program label="Epiphany web browser (Gecko)" confirm="false">/usr/bin/epiphany-gecko</Program>
<Menu label="Programming">
<Program label="Python (v2.5)" confirm="false">x-terminal-emulator -T "Python (v2.5)" -e sh -c "/usr/bin/python2.5"</Program>
</Menu>
<Menu label="Science">
<Menu label="Mathematics">
<Program label="Xcalc" confirm="false">xcalc</Program>
</Menu>
</Menu>
<Menu label="Shells">
<Program label="Bash" confirm="false">x-terminal-emulator -T "Bash" -e sh -c "/bin/bash --login"</Program>
<Program label="Sh" confirm="false">x-terminal-emulator -T "Sh" -e sh -c "/bin/sh --login"</Program>
</Menu>
<Menu label="Sound">
<Program label="Alsamixergui" confirm="false">/usr/bin/alsamixergui</Program>
<Program label="AlsaPlayer" confirm="false">/usr/bin/alsaplayer -i gtk2</Program>
</Menu>
<Menu label="System">
<Menu label="Administration">
<Program label="alsaconf" confirm="false">x-terminal-emulator -T "alsaconf" -e sh -c "su-to-root -p root -c /usr/sbin/alsaconf"</Program>
<Program label="Aptitude" confirm="false">x-terminal-emulator -T "Aptitude" -e sh -c "/usr/bin/aptitude"</Program>
<Program label="Debian Task selector" confirm="false">x-terminal-emulator -T "Debian Task selector" -e sh -c "su-to-root -c tasksel"</Program>
<Program label="Editres" confirm="false">editres</Program>
<Program label="Orphaner (all)" confirm="false">x-terminal-emulator -T "Orphaner (all)" -e sh -c "su-to-root -c '/usr/sbin/orphaner -a'"</Program>
<Program label="Orphaner - editkeep" confirm="false">x-terminal-emulator -T "Orphaner - editkeep" -e sh -c "su-to-root -c '/usr/sbin/editkeep'"</Program>
<Program label="Orphaner (libs)" confirm="false">x-terminal-emulator -T "Orphaner (libs)" -e sh -c "su-to-root -c /usr/sbin/orphaner"</Program>
<Program label="Xclipboard" confirm="false">xclipboard</Program>
<Program label="Xfontsel" confirm="false">xfontsel</Program>
<Program label="Xkill" confirm="false">xkill</Program>
<Program label="Xrefresh" confirm="false">xrefresh</Program>
</Menu>
<Menu label="Hardware">
<Program label="Xvidtune" confirm="false">xvidtune</Program>
</Menu>
<Menu label="Monitoring">
<Program label="Pstree" confirm="false">x-terminal-emulator -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
<Program label="Top" confirm="false">x-terminal-emulator -T "Top" -e sh -c "/usr/bin/top"</Program>
<Program label="Xconsole" confirm="false">xconsole -file /dev/xconsole</Program>
<Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
<Program label="Xload" confirm="false">xload</Program>
</Menu>
<Menu label="Package Management">
<Program label="Synaptic Package Manager" confirm="false">/usr/bin/su-to-root -X -c /usr/sbin/synaptic</Program>
</Menu>
</Menu>
<Menu label="Terminal Emulators">
<Program label="XTerm" confirm="false">xterm</Program>
<Program label="X-Terminal as root (GKsu)" confirm="false">/usr/bin/gksu -u root /usr/bin/x-terminal-emulator</Program>
<Program label="XTerm (Unicode)" confirm="false">uxterm</Program>
</Menu>
<Menu label="Viewers">
<Program label="Xditview" confirm="false">xditview</Program>
<Program label="Xpdf" confirm="false">/usr/bin/xpdf</Program>
</Menu>
</Menu>
<Menu label="Help">
<Program label="Info" confirm="false">x-terminal-emulator -T "Info" -e sh -c "info"</Program>
<Program label="Xman" confirm="false">xman</Program>
<Program label="yelp" confirm="false">/usr/bin/yelp</Program>
</Menu>
</Menu>

<Separator/>
<Menu label="Power">
<Restart label="Restart" icon="restart.png"/>
<Program label="Reboot">sudo reboot</Program>
<Program label="Shutdown">sudo halt</Program>
<Exit label="Exit" confirm="true" icon="exit.png"/>
</Menu>
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
<Tray x="0" y="-1" height="25">

<!-- Additional TrayButton attribute: label -->
<!-- Additional Pager attributes; width, height -->
<Pager/>

<!-- Additional TaskList attribute: maxwidth -->
<TaskList/>

**<!-- <Dock/> -->**

<!-- Additional Swallow attribute: height -->
<Swallow name="xload" width="64">
xload -nolabel -bg black -fg orange -hl white
</Swallow>

<Clock format="%H:%M">xclock</Clock>

</Tray>

[B]<Tray height="25" width="0" layer="0" valign="center">
<TrayButton icon="Menu.png">root:1</TrayButton>
<TrayButton label="-">showdesktop</TrayButton>
<TrayButton label="X">exec:xterm</TrayButton>
<TrayButton icon="firefox.png">exec:firefox</TrayButton>
<TrayButton icon="rox.png">exec:rox</TrayButton>

<Dock/>
</Tray>[/B]

<!-- Visual Styles -->

<WindowStyle>

<Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
<Width>4</Width>
<Height>20</Height>

<Active>
<Text>orange</Text>
<Title>black</Title>
<Corner>orange</Corner>
<Outline>white</Outline>
</Active>

<Inactive>
<Text>white</Text>
<Title>#808488:#303438</Title>
<Corner>#aaaaaa</Corner>
<Outline>black</Outline>
</Inactive>

</WindowStyle>

<TaskListStyle>
<Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
<ActiveForeground>orange</ActiveForeground>
<ActiveBackground>black</ActiveBackground>
<Foreground>black</Foreground>
<Background>black</Background>
</TaskListStyle>

<!-- Additional TrayStyle attribute: insert -->
<TrayStyle>
<Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
<Background>black</Background>
<Foreground>orange</Foreground>
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
<Foreground>orange</Foreground>
<Background>black</Background>
<ActiveForeground>white</ActiveForeground>
<ActiveBackground>black</ActiveBackground>
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
<Background type="solid">black</Background>

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

<Key mask="A" key="Tab">nextstacked</Key>
<Key mask="A" key="F4">close</Key>
<Key mask="A" key="#">desktop#</Key>
<Key mask="A" key="F1">root:1</Key>
<Key mask="A" key="F2">window</Key>

</JWM>
```

---

### Post by AnLGP on 2008-07-03
I've got one at the top now.  It's  nice, centered and viewable.  So to add another Tray I would just close the other tray (which it should already be) and then start new Tray attributes and once I'm done with that close it as well?  Whoops - screenshot and .jwmrc are in the next post.

---

### Post by AnLGP on 2008-07-03
[http://s297.photobucket.com/albums/mm213/musicauniversalis/?action=view&current=2008-07-03-191643_1280x1024_scrot.png](http://s297.photobucket.com/albums/mm213/musicauniversalis/?action=view&current=2008-07-03-191643_1280x1024_scrot.png)

 <?xml version="1.0"?>
 
 <JWM>
 
    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="123">
       <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
          <Program icon="firefox.png" label="Www Browser">x-www-browser</Program>
 
 <!-- #DEBIAN
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
        <Menu label="Editors">
          <Program label="LeafPad" confirm="false">/usr/bin/leafpad</Program>
          <Program label="Nano" confirm="false">x-terminal-emulator  -T "Nano" -e sh -c "/bin/nano"</Program>
          <Program label="Xedit" confirm="false">xedit</Program>
        </Menu>
        <Menu label="File Management">
          <Program label="PCManFM" confirm="false">/usr/bin/pcmanfm</Program>
        </Menu>
        <Menu label="Graphics">
          <Program label="The GIMP" confirm="false">/usr/bin/gimp</Program>
          <Program label="X Window Snapshot" confirm="false">xwd | xwud</Program>
        </Menu>
        <Menu label="Network">
          <Menu label="Communication">
            <Program label="Xbiff" confirm="false">xbiff</Program>
          </Menu>
          <Menu label="Web Browsing">
            <Program label="Epiphany web browser (Gecko)" confirm="false">/usr/bin/epiphany-gecko</Program>
          </Menu>
        </Menu>
        <Menu label="Programming">
          <Program label="Python (v2.5)" confirm="false">x-terminal-emulator  -T "Python (v2.5)" -e sh -c "/usr/bin/python2.5"</Program>
        </Menu>
        <Menu label="Science">
          <Menu label="Mathematics">
            <Program label="Xcalc" confirm="false">xcalc</Program>
          </Menu>
        </Menu>
        <Menu label="Shells">
          <Program label="Bash" confirm="false">x-terminal-emulator  -T "Bash" -e sh -c "/bin/bash --login"</Program>
          <Program label="Sh" confirm="false">x-terminal-emulator  -T "Sh" -e sh -c "/bin/sh --login"</Program>
        </Menu>
        <Menu label="Sound">
          <Program label="Alsamixergui" confirm="false">/usr/bin/alsamixergui</Program>
          <Program label="AlsaPlayer" confirm="false">/usr/bin/alsaplayer -i gtk2</Program>
        </Menu>
        <Menu label="System">
          <Menu label="Administration">
            <Program label="alsaconf" confirm="false">x-terminal-emulator  -T "alsaconf" -e sh -c "su-to-root -p root -c /usr/sbin/alsaconf"</Program>
            <Program label="Aptitude" confirm="false">x-terminal-emulator  -T "Aptitude" -e sh -c "/usr/bin/aptitude"</Program>
            <Program label="Debian Task selector" confirm="false">x-terminal-emulator  -T "Debian Task selector" -e sh -c "su-to-root -c tasksel"</Program>
            <Program label="Editres" confirm="false">editres</Program>
            <Program label="Orphaner (all)" confirm="false">x-terminal-emulator  -T "Orphaner (all)" -e sh -c "su-to-root -c '/usr/sbin/orphaner -a'"</Program>
            <Program label="Orphaner - editkeep" confirm="false">x-terminal-emulator  -T "Orphaner - editkeep" -e sh -c "su-to-root -c '/usr/sbin/editkeep'"</Program>
            <Program label="Orphaner (libs)" confirm="false">x-terminal-emulator  -T "Orphaner (libs)" -e sh -c "su-to-root -c /usr/sbin/orphaner"</Program>
            <Program label="Xclipboard" confirm="false">xclipboard</Program>
            <Program label="Xfontsel" confirm="false">xfontsel</Program>
            <Program label="Xkill" confirm="false">xkill</Program>
            <Program label="Xrefresh" confirm="false">xrefresh</Program>
          </Menu>
          <Menu label="Hardware">
            <Program label="Xvidtune" confirm="false">xvidtune</Program>
          </Menu>
          <Menu label="Monitoring">
            <Program label="Conky" confirm="false">x-terminal-emulator  -T "Conky" -e sh -c "/usr/bin/conky"</Program>
            <Program label="Pstree" confirm="false">x-terminal-emulator  -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
            <Program label="Top" confirm="false">x-terminal-emulator  -T "Top" -e sh -c "/usr/bin/top"</Program>
            <Program label="Xconsole" confirm="false">xconsole -file /dev/xconsole</Program>
            <Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
            <Program label="Xload" confirm="false">xload</Program>
          </Menu>
          <Menu label="Package Management">
            <Program label="Synaptic Package Manager" confirm="false">/usr/bin/su-to-root -X -c /usr/sbin/synaptic</Program>
          </Menu>
        </Menu>
        <Menu label="Terminal Emulators">
          <Program label="XTerm" confirm="false">xterm</Program>
          <Program label="X-Terminal as root (GKsu)" confirm="false">/usr/bin/gksu -u root /usr/bin/x-terminal-emulator</Program>
          <Program label="XTerm (Unicode)" confirm="false">uxterm</Program>
        </Menu>
        <Menu label="Viewers">
          <Program label="Xditview" confirm="false">xditview</Program>
          <Program label="Xpdf" confirm="false">/usr/bin/xpdf</Program>
        </Menu>
      </Menu>
      <Menu label="Games">
        <Menu label="Toys">
          <Program label="Oclock" confirm="false">oclock</Program>
          <Program label="Xclock (analog)" confirm="false">xclock -analog</Program>
          <Program label="Xclock (digital)" confirm="false">xclock -digital -update 1</Program>
          <Program label="Xeyes" confirm="false">xeyes</Program>
          <Program label="Xlogo" confirm="false">xlogo</Program>
          <Program label="XStarfish" confirm="false">/usr/bin/xstarfish</Program>
        </Menu>
      </Menu>
      <Menu label="Help">
        <Program label="Info" confirm="false">x-terminal-emulator  -T "Info" -e sh -c "info"</Program>
        <Program label="Xman" confirm="false">xman</Program>
        <Program label="yelp" confirm="false">/usr/bin/yelp</Program>
      </Menu>
    </Menu>

         <Separator/>
       <Restart label="Restart" icon="restart.png"/>
       <Exit label="Exit" confirm="true" icon="exit.png"/>
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
    <Tray  x="0" y="10" height="25" width="900" autohide="false" halign="center">
 
       <!-- Additional TrayButton attribute: label -->
       <TrayButton label="menu">root:1</TrayButton>
       
       <TrayButton label="-">showdesktop</TrayButton>
       <TrayButton label="www">exec:/usr/bin/epiphany-gecko</TrayButton>
       <!-- Additional Pager attributes; width, height -->
       <Pager/>
 
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
 
       <Dock/>
 
       <!-- Additional Swallow attribute: height -->
       <Swallow name="xload" width="64">
          xload -nolabel -bg black -fg orange -hl white
       </Swallow>
 
       <Clock format="%H:%M">xclock</Clock>
 
    </Tray>
 
    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>black</Text>
          <Title>orange</Title>
          <Corner>black</Corner>
          <Outline>white</Outline>
       </Active>
 
       <Inactive>
          <Text>orange</Text>
          <Title>black</Title>
          <Corner>white</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <ActiveForeground>orange</ActiveForeground>
       <ActiveBackground>black</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>white</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Background>orange</Background>
       <Foreground>black</Foreground>
    </TrayStyle>
 
    <PagerStyle>
       <Outline>black</Outline>
       <Foreground>white</Foreground>
       <Background>black</Background>
       <ActiveForeground>black</ActiveForeground>
       <ActiveBackground>white</ActiveBackground>
    </PagerStyle>
 
    <MenuStyle>
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Foreground>white</Foreground>
       <Background>black</Background>
       <ActiveForeground>black</ActiveForeground>
       <ActiveBackground>orange</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Outline>black</Outline>
       <Foreground>white</Foreground>
       <Background>black</Background>
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
       <Background type="solid">black</Background>
 
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
 
    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key>
 
 </JWM>

---

### Post by kerry_s on 2008-07-03
very good, you even use words instead of icons like me. :)

the tray tag is very versatile, you can have as many as you want, i've even used them for desktop icons.

here's a pic of 1 of my old setups:
[http://img184.imageshack.us/img184/3791/015147ni5.png](http://img184.imageshack.us/img184/3791/015147ni5.png)

here's the .jwmrc:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;st=5](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;st=5)

you can look through that thread, i think i put other pics/.jwmrc's?

got to run, catch ya later.

---

### Post by AnLGP on 2008-07-03
:mrgreen: half my JWM ideas are yours.  I had no idea about it until you helped me set up my comp w/a base install.  I'll marked this solved.  Thanks :)

---

