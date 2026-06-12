---
title: "JWM Startup Questions"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-18
How do I get programs to start in JWM?  I looked at the configuration help on the JWM configure page

[http://joewing.net/programs/jwm/config.shtml](http://joewing.net/programs/jwm/config.shtml)

and this is the only thing I could think that would even remotely come close


StartupCommand  	A command to run when JWM starts.

so my questions are

Is this the command?

Where do I put it in the .jwmrc?

---

### Post by kerry_s on 2008-06-18
> Is this the command? yes
> Where do I put it in the .jwmrc? anywhere in the jwmrc between the jwm tags.

didn't i give you a copy of my .jwmrc?

```

<?xml version="1.0"?>

<JWM>
<StartupCommand>
conky
</StartupCommand>

<RootMenu height="15" onroot="3">
      <Program label="Terminal">x-terminal-emulator</Program>
      <Program label="WWW Browser">x-www-broser</Program>
      <Program label="Synaptic">sudo synaptic</Program>
      <Separator/>
      <Restart label="Restart"/>
      <Menu label="Exit">
      <Exit label="Exit WM" confirm="false"/>
      <Program label="Reboot">sudo reboot</Program>
      <Program label="Shutdown">sudo halt</Program>
      </Menu>
</RootMenu>

   <Tray  x="0" y="-1" height="28">
      <TrayButton label="Debian  ">root:3</TrayButton>
      <TrayButton label="_">showdesktop</TrayButton>
      <TrayButton label=" T  ">exec:rxvt</TrayButton>
      <TrayButton label=" FM  ">exec:rox</TrayButton>
      <TrayButton label="WWW">exec:iceweasel</TrayButton>
      <TaskList/>
      <Dock/>
      <Clock format="  %H:%M  ">asmix -g +820+670</Clock>
      <Pager/>
      <TrayButton label=" X  ">exec:xset dpms force off</TrayButton>
   </Tray>

   <Group>
      <Name>abiword</Name>
      <Name>soffice</Name>
      <Name>xedit</Name>
      <Option>maximized</Option>
   </Group>

   <WindowStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
        <Text>yellow</Text>
        <Title>#6B6D6B:#4A494A</Title>
        <Corner>yellow</Corner>
        <Outline>black</Outline>
      </Active>

      <Inactive>
        <Text>white</Text>
        <Title>#4A494A:#6B6D6B</Title>
        <Corner>yellow</Corner>
        <Outline>black</Outline>
      </Inactive>
   </WindowStyle>

   <TaskListStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <ActiveForeground>yellow</ActiveForeground>
      <ActiveBackground>#303438:black</ActiveBackground>
      <Foreground>white</Foreground>
      <Background>#303438:black</Background>
   </TaskListStyle>

   <TrayStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Background>black</Background>
      <Foreground>white</Foreground>
   </TrayStyle>

   <PagerStyle>
     <Outline>black</Outline>
     <Foreground>yellow</Foreground>
     <Background>black</Background>
     <ActiveForeground>white</ActiveForeground>
     <ActiveBackground>#303438</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Foreground>white</Foreground>
      <Background>#303438</Background>
      <ActiveForeground>yellow</ActiveForeground>
      <ActiveBackground>#303438:black</ActiveBackground>
   </MenuStyle>

   <PopupStyle enabled="false">
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>
   <Desktops count="3">
   <Background type="solid">black</Background>
   </Desktops>

   <DoubleClickSpeed>400</DoubleClickSpeed>
   <DoubleClickDelta>2</DoubleClickDelta>
   <FocusModel>click</FocusModel>
   <SnapMode distance="10">border</SnapMode>
   <MoveMode>outline</MoveMode>
   <ResizeMode>outline</ResizeMode>
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
   <Key mask="A" key="F1">root:3</Key>
   <Key mask="A" key="F2">exec:grun</Key>
   <Key mask="" key="Print">exec:scrot %T.png -e 'gpicview $f'</Key>
   <Key mask="A" key="Print">exec:rxvt -g 40x1+0+0 -e scrot -cd 5 %T.png -e 'gpicview $f'</Key>
   <Key mask="C" key="Print">exec:rxvt -g 15x1+0+0 -e scrot -sb %T.png -e 'gpicview $f'</Key>

</JWM>


```

---

### Post by AnLGP on 2008-06-18
Yes, you did.  Thanks for the info.

I plugged that into the .jwmrc and nothing has changed.  Conky didn't start when I rebooted (I have it).

Is there a certain file I have to point towards the .jwmrc?

---

### Post by kerry_s on 2008-06-18
> **AnLGP said:**
> Yes, you did.  Thanks for the info.

I plugged that into the .jwmrc and nothing has changed.  Conky didn't start when I rebooted (I have it).

Is there a certain file I have to point towards the .jwmrc?

hmmm, non that i know, i just put it there and it works. let me see your jwmrc.

---

### Post by AnLGP on 2008-06-19
I'm getting good at hosing installs.  I did something so I couldn't log in (doh) and I installed slitaz.  I think I'll install Debian as a second partition that way I have both..  but maybe not.  I don't know.  I think it still goes on jwm tho.

This is the one listed as "simple.jwmrc"

<?xml version="1.0"?>

<JWM>

   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="26" onroot="123">
      <Program icon="" label="XTerminal">
         xterm -bg black -fg white
      </Program>

      <Menu icon="applications.png" label="Applications">
         <Program icon="" label="Clex File manager">xterm -e clex</Program>
         <Program icon="" label="Htop System monitor">
            xterm -bg black -fg white -e htop
         </Program>
         <Program icon="" label="Nano Text editor">xterm -e nano</Program>
         <Program icon="" label="Retawq Web browser">
            xterm -bg black -fg white -e retawq
         </Program>
      </Menu>
      
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="-1" height="26">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="SliTaz">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <!-- <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow> -->

      <Clock>xclock</Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>FreeSans-9:bold</Font>
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
      <Font>FreeSans-11:bold</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>FreeSans-11:bold</Font>
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
      <Font>FreeSans-11:bold</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>FreeSans-10</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/Images/Icons
   </IconPath>
   <IconPath>
      /usr/share/pixmaps
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
      <Background type="gradient">#BFB06B:#D6C885</Background>

   </Desktops>

   <!-- Startup and shutdown commands. -->
   <StartupCommand></StartupCommand>
   <ShutdownCommand>
      killall Xvesa; clear; sleep 2; clear; echo "JWM exit OK. Press ENTER to continue... "
   </ShutdownCommand>

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

"system.jwmrc"

<?xml version="1.0"?>

<JWM>

   <!--
      SliTaz GNU/Linux RootMenu's build for the famous JWM version 2.0.1
      
      Note: The panel menu is dynamicly generated from standards desktop 
      files found in /usr/share/application or ~/.local/share/applications.
      You can configure the panel with the graphical interface or by editing
      ~/.config/lxpanel/default/config. The panel is powered by lxpanel from
      the LXDE project.
      
      The root menu, if this is undefined you will not get a menu. 
      Additional RootMenu attributes: onroot, labeled, label 
   -->
   
   <!-- JWM menu for all buttons (123) -->

   <RootMenu height="17" onroot="123">
      
      <!-- Go $HOME (~) -->
      <Program icon="go-home.png" label="Home">emelfm2 --one=~</Program>
      
      <!-- Favorites menu -->
      <Menu icon="emblem-favorite.png" label="Favorites">
         <Program icon="utilities-terminal.png" label="Terminal">xterm</Program>
         <Program icon="media-flash.png" label="Mount Devices">subox mountbox</Program>
         <Program icon="mozicon.png" label="Web Browser">firefox</Program>
         <Program icon="accessories-text-editor.png" label="Text Editor">leafpad</Program>
         <Program icon="gpicview.png" label="Images Viewer">gpicview</Program> 
      </Menu>
      
      <!-- 
         Desktop Effects menu. Composite manager can also be started with 
         JWM by adding a StartupCommand.
         
         Composite manager example : xcompmgr -c -f -r 10
         Opacity with transet-df   : transset-df --actual --max 0.40
      -->
      <Menu icon="preferences-system-windows.png" label="Desktop Effects">
         <Program icon="preferences-system-session.png" label="Active composite">
            killall xcompmgr; exec xcompmgr
         </Program>
         <Program icon="preferences-system-session.png" label="Active shadows">
            killall xcompmgr; exec xcompmgr -c -r 10
         </Program>
         <Program icon="preferences-system-session.png" label="Active shadows/fade">
            killall xcompmgr; exec xcompmgr -c -f -r 10
         </Program>
         <Separator/>
         <Program icon="preferences-system-windows.png" label="Set opacity (actual)">
            exec transset-df --actual
         </Program>
         <Program icon="preferences-system-windows.png" label="Set opacity 0.6 (actual)">
            exec transset-df --actual --max 0.6
         </Program>
         <Program icon="preferences-system-windows.png" label="Set opacity (click)">
            exec transset-df --click
         </Program>
         <Separator/>
         <Program icon="/usr/share/icons/Tango/16x16/actions/gtk-stop.png" label="Stop effects">
            killall xcompmgr
         </Program>
      </Menu>

      <!-- SliTaz Live -->
      <Menu icon="slitaz-menu.png" label="SliTaz Live">
         <Program icon="tazlito.png" label="Tazlito LiveCD Tool">
            subox tazlitobox
         </Program>
         <Program icon="system-installer.png" label="TazUSB Writefs (none)">
            subox 'xterm -e tazusb writefs'
         </Program>
         <Program icon="system-installer.png" label="TazUSB Writefs (gzip)">
            subox 'xterm -e tazusb writefs gzip'
         </Program>
         <Program icon="system-installer.png" label="TazUSB Writefs (lzma)">
            subox 'xterm -e tazusb writefs lzma'
         </Program>
      </Menu>
      
      <!-- Documentation menu -->
      <Menu icon="text-x-generic.png" label="Documentation">
         <Program icon="text-html.png" label="SliTaz Local doc">
            firefox /usr/share/doc/slitaz/index.html
         </Program>
         <Program icon="text-html.png" label="Tazpkg manual">
            firefox /usr/share/doc/tazpkg/tazpkg.html
         </Program>
         <Program icon="text-html.png" label="Tazlito manual">
            firefox /usr/share/doc/tazlito/tazlito.html
         </Program>
         <Program icon="text-html.png" label="TazUSB manual (en)">
            firefox /usr/share/doc/tazusb/tazusb.en.html
         </Program>
         <Program icon="text-html.png" label="Tazwok manual">
            firefox /usr/share/doc/tazwok/tazwok.html
         </Program>
         <Program icon="text-x-generic.png" label="GNU General Public License">
            xterm -T "General Public License" -e less -M /usr/share/licenses/gpl.txt
         </Program>
      </Menu>
      
      <Desktops icon="user-desktop.png"/>
      
      <Separator/>

      <!-- JWM desktop -->
      <Menu icon="preferences-desktop.png" label="JWM Desktop">
         <Program icon="image.png" label="JWM Wallpaper">
            jwmbgconf
         </Program>
         <Program icon="preferences-system-windows.png" label="JWM Menu and Theme">
            geany $HOME/.jwmrc
         </Program>
         <Separator/>
         <Kill icon="applications-other.png" label="Kill a window"/>
         <Program icon="view-refresh.png" label="Restart LXpanel">
            killall lxpanel; exec lxpanel
         </Program>
         <Separator/>
         <Restart icon="view-refresh.png" label="Restart JWM"/>
         <Exit icon="system-log-out.png" label="Exit JWM" confirm="false"/>
      </Menu>
      
      <!-- Actions menu -->
      <Menu icon="applications-other.png" label="System actions">
         <Program icon="system-shutdown.png" label="Reboot">reboot</Program>
         <Program icon="system-shutdown.png" label="Reboot (forced)">reboot -f</Program>
         <Program icon="system-shutdown.png" label="Shutdown">poweroff</Program>
      </Menu>
      
   </RootMenu>

   <!--
      End of SliTaz JWM RootMenu's
   -->
   
   <!--
      Additional tray attributes: autohide, width, border, layer, layout
      Start with top tray for the pager.
   -->

   <Tray x="0" y="-1" height="22" halign="center" border="0">

      <!-- Additional Pager attributes; width, height -->
      <Pager/>
      
      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList maxwidth="260"/>
      
      <!-- Dock is used by applications like Xpad, Sylpheed or Pidgin. -->
      <Dock/>

   </Tray>

   <!--
      Visual Styles.
      Voir [http://www.slitaz.org/doc/handbook/jwm.html](http://www.slitaz.org/doc/handbook/jwm.html) pour des informations
      en Frensh sur la config d'un style pour JWM.
   -->

   <WindowStyle>

      <Font>FreeSans-10:bold</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
         <Title>#880000:#FFA500</Title>
         <Corner>white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#000000:#666666</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>FreeSans-11:bold</Font>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#880000:#FFA500</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>#f3f3f3</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>FreeSans-11:bold</Font>
      <Background>gray96</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>lightgrey</Foreground>
      <Background>#666666</Background>
      <ActiveForeground>#DF8F06</ActiveForeground>
      <ActiveBackground>#3D3D3D</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>FreeSans-11</Font>
      <Foreground>black</Foreground>
      <Background>gray98</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#880000:#FFA500</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>FreeSans-16</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>gold</Background>
   </PopupStyle>

   <!-- Icons path. -->
   <IconPath>$HOME/Images/Icons</IconPath>
   <IconPath>/usr/share/pixmaps</IconPath>
   <IconPath>/usr/share/icons/Tango/jwm</IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- 
         Default background. Note that a Background tag can be contained
         within a Desktop tag to give a specific background for that desktop.
         Backgroud support: solid, gradient, image and tile.
         
         Note: Background can be configured graphicaly by 'jwmbgconf'
         
      -->
      
      <Background type="image">/usr/share/images/slitaz-background.png</Background>
      <!-- <Background type="gradient">#BFB06B:#D6C885</Background> -->
      <!-- <Background type="tile">$HOME/Images/Wallpapers/slitaz.png</Background> -->

   </Desktops>

   <!-- Startup and shutdown commands. -->
   <StartupCommand>alsaplayer -i text /usr/share/sounds/login.ogg</StartupCommand>
   <ShutdownCommand></ShutdownCommand>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>sloppy</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="5">border</SnapMode>

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

   <!-- SliTaz add key bindings. -->
   <Key mask="A" key="F5">exec:firefox</Key>
   <Key mask="A" key="F6">exec:emelfm2</Key>
   <Key mask="A" key="o">exec:transset-df --actual --max 0.6</Key>

</JWM>

-----

I don't know why it has two .jwmrc's.  EDIT:  yes I do.  One is for the one when you click on the desktop the other is the main WM.

---

