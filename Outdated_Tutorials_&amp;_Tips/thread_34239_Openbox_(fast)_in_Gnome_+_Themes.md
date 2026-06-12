---
title: "Openbox (fast) in Gnome + Themes"
date: 2005-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormy Eyes on 2005-05-14
[SIZE=5]_Introduction_[/SIZE]

Metacity, while a fair default, is not the only window manager you can use with GNOME. [Openbox](http://www.openbox.org) is a lightweight, customizable window manager that works either by itself or as a drop-in replacement for Metacity. Its advantages include the ability to switch desktops with the mouse wheel, a built-in, customizable menu that allows stand-alone operation with some GNOME components in order to build a GNOME-like system on low-end gear, and (this is subjective) better looking, cleaner themes that don't depend on resource-intensive pixmaps.

[SIZE=5]_Installation and Basic Usage_[/SIZE]

If you have the Universe repository, all you have to do to install Openbox is enter a command:

```
sudo apt-get install openbox obconf
```

Once you've installed it, you can replace Metacity with Openbox with a single command entered into GNOME's "Run" prompt, which can be accessed by hitting ALT+F2:

```
openbox --replace
```

[SIZE=5]_Installation and Selection of Themes_[/SIZE]

Now that you have Openbox running, you'll probably need some themes. I can help you with that, being an Openbox fan. But first, I should tell you how to obtain, install, and select themes.

Once you have downloaded a theme to your home directory, open a terminal and enter the following commands (This example assumes you've downloaded Mistodon to $HOME):

```
cd ~/.themes
tar xzvf ~/mistodon.tar.gz
```

Under GNOME, find "ObConf" in **Applications -> Other -> Obconf** and select your new theme.

[SIZE=5]_Theme List and Links_[/SIZE]

The following list names themes I've made available to the public, with screenshots and descriptions. As other users provide links to their themes, I will post them after my list.

[list]
[*][Mistodon](http://www.starbreaker.net/download/mistodon.tar.gz) [(Screenshot)](http://ubuntuforums.org/gallery/showimage.php?i=237): A clean theme to match the GTK2 theme "Mist".
[*][Pandora](http://www.starbreaker.net/download/pandora.tar.gz) [(Screenshot)](http://ubuntuforums.org/gallery/showimage.php?i=247): Named after a certain overly curious girl from Greek myth, Pandora is brown to match Ubuntu's coloring, and as clean as Mistodon.
[*][Martian](http://www.starbreaker.net/download/martian.tar.gz) [(Screenshot)](http://ubuntuforums.org/gallery/showimage.php?i=250&c=5): Made to match the default "Human" theme for Hoary. I call it *Martian* because I was reading Heinlein's *Stranger in a Strange Land* in the john when I realized that Pandora didn't quite match Ubuntu's colors.
[/list] 

Forum member [Smoon](http://www.ubuntuforums.org/member.php?u=15862) has his own [theme page.](http://nooms.de/?page=openbox) It's written in German, but the screenshots provide adequate explanation.

Also, [boxwhore.org](http://www.boxwhore.org) hosts Openbox themes with screenshots. (No, I didn't pick the name.)

More importantly, the developers/maintainers of Openbox provide documentation at [this location.](http://icculus.org/openbox/docs.php?page=toc.html) It covers the basic operating principles, though it doesn't offer in-depth coverage on how to theme Openbox. I may provide a section on advanced theming later on.

Since Openbox does not handle setting wallpapers, you have to use external tools. I recommend [feh](http://www.linuxbrit.co.uk/feh/), which is primarily an image viewer but includes "set wallpaper" functionality both in its menu and as a commandline tool.

[SIZE=5]_Fun with Keybindings; or, getting an ALT+Tab that rocks like ninja._[/SIZE]

Openbox's default **ALT+Tab** functionality is a bit limited compared to Metacity, which shows a dialog listing all the open apps on a given workspace similar to Windows. You don't have to settle for Openbox's anemic ALT+Tab. If you're using Openbox, try middle-clicking anywhere on your desktop. You'll see a menu listing each of your workspaces, starting with the first, and each workspace entry will have a submenu displaying the running windows on that workspace, with iconified (minimised) windows in brackets.

It's also possible to bind this menu, which is referred to internally as the "Client List Menu", to any key you like, and then to navigate that menu with your keyboard's arrow keys. Just follow the steps below.

1. Open a terminal and enter the following command:

```
gedit ~/.config/openbox/rc.xml
```

2. Once you've opened up Openbox's config file, scroll down until you see the following text:

```
<keybind key="A-Tab">
    <action name="NextWindow"/>
</keybind>
<keybind key="A-S-Tab">
    <action name="PreviousWindow"/>
</keybind>
```

3. Replace the text shown above with the following text:

```
<keybind key="A-Tab">
    <action name="ShowMenu"><menu>client-list-menu</menu></action>
</keybind>
<keybind key="A-S-Tab">
    <action name="ShowMenu"><menu>client-list-menu</menu></action>
</keybind>
```

4. Save your changes and close the editor.

5. If you're using Openbox as part of GNOME, and Openbox is part of your GNOME session, then typing **killall openbox** at the terminal *should* cause GNOME to restart Openbox for you. If GNOME won't play ball, you should be able to click on the *Applications* menu, select "Run Application", and type "openbox" into the prompt. Or, you could avoid all this by logging out and logging in again. If you're using Openbox on its own, then right-click on the desktop for the main menu, and choose the *Reconfigure* option. Openbox will reread its config file.

By following the above steps, you've modified the keybindings for ALT+Tab and SHIFT+ALT+Tab to bring up the same client list menu that appears when you middle-click on the desktop. You can navigate it using your arrow keys, and press "Enter" to go to a  running app, even if that app is on a different workspace.

[SIZE=5]_More Fun with Keybindings; or, opening apps without reaching for the rodent._[/SIZE]

So, are you tired of having to take your hands off the keyboard in order to open a program? I can help you with that too. The principles are the same as when you modified your config, (~/.config/openbox/rc.xml) to give you a sweet ALT+Tab.

Open your config file as explained in *"Fun with Keybindings; or, getting an ALT+Tab that rocks like ninja."* and do the following:

1. Find the line that reads "<chainQuitKey>C-g</chainQuitKey>". Create a blank line between this keybinding and the next. 

2. If you're using GNOME or have  gnome-panel running in Openbox, paste the following XML:

```
<keybind key="A-F1">
    <action name="execute"><execute>gnome-panel-control --main-menu</execute></action>
</keybind>
<keybind key="A-F2">
    <action name="execute"><execute>gnome-panel-control --run-dialog</execute></action>
</keybind>
```

The XML shown above uses GNOME's panel to trigger the menu and bring up GNOME's run dialog. It also uses the same keybindings for the menu and run dialog as Metacity, for the purpose of this demonstration. You can change the keybindings to suit your own needs.

If you aren't using GNOME or gnome-panel, but want a "Run Program" dialog, then run **sudo apt-get install gmrun** from a terminal. Once you've installed gmrun, paste the following XML into the editor at the blank line you created in step 1:

```
<keybind key="A-F1">
    <action name="ShowMenu"><menu>root-menu</menu></action>
</keybind>
<keybind key="A-F2">
    <action name="execute"><execute>gmrun</execute></action>
</keybind>
```

The above code will show you the menu Openbox provides when right-clicking the desktop if it is running as a stand-alone environment. gmrun is an optional package which should be available if you've enabled the Universe repository.

3. Save your changes, close the editor, and restart Openbox.

[SIZE=5]_Even More Fun with Keybindings: Switch to a Specific Desktop_[/SIZE]

It's possible to configure keybindings in Openbox to allow you to switch to a specific desktop. For the purpose of this demonstration, I'll show you how to use ALT+1 to switch to desktop 1, ALT+2 to switch to desktop 2, etc. Just paste the following code into your ~/.config/openbox/rc.xml file's <keyboard> section, save, and restart Openbox:

```
<keybind key="A-1">
    <action name="Desktop"><desktop>1</desktop></action>
</keybind>
<keybind key="A-2">
    <action name="Desktop"><desktop>2</desktop></action>
</keybind>
<keybind key="A-3">
    <action name="Desktop"><desktop>3</desktop></action>
</keybind>
<keybind key="A-4">
    <action name="Desktop"><desktop>4</desktop></action>
</keybind>
```

---

### Post by rpgcyco on 2005-05-14
Hey,

When the command **openbox --replace** is run, is it permanent, or can I logout and then back in again or reboot to go back to Metacity if I wish?

- Rpg Cyco

---

### Post by TravisNewman on 2005-05-14
If you choose to save your session on logout, it will take over on your next login as well. If you DON'T choose to save your session, logging out and back in will bring back metacity

---

### Post by Juippisi on 2005-05-14
Is there a way to get ALT+F<number> to change workspaces? I have readed the Openbox Documentation and edited the rc.xml and others, but it didn't go well. I'm running Openbox by using startx at TTY.

I'd change immediately to Openbox, if I only could get that keybinding to work.

Oh, by the way Stormy Eyes, nice themes. I like especially that Mistodon :).

---

### Post by Stormy Eyes on 2005-05-14
[QUOTE=panickedthumb]If you choose to save your session on logout, it will take over on your next login as well. If you DON'T choose to save your session, logging out and back in will bring back metacity[/QUOTE]


Also, if you decide you don't like Openbox, you can get Metacity back by clicking on "Run Program" and typing **metacity --replace** at the prompt.

---

### Post by Stormy Eyes on 2005-05-14
[QUOTE=Juippisi]Is there a way to get ALT+F<number> to change workspaces? I have readed the Openbox Documentation and edited the rc.xml and others, but it didn't go well. I'm running Openbox by using startx at TTY.

I'd change immediately to Openbox, if I only could get that keybinding to work.

Oh, by the way Stormy Eyes, nice themes. I like especially that Mistodon :).[/QUOTE]

Mind posting the keyboard section of your rc.xml? If you do the following in your "Keyboard" section, save the file, and then pick "Reconfigure" from the menu, it should work fine.

<keybind key="A-F1">
[indent]<action name="Desktop"><desktop>1</desktop></action>[/indent]
</keybind>

I'm glad you liked Mistodon. I've added a new theme, "Martian", for those who like Ubuntu's default colors.

---

### Post by Juippisi on 2005-05-14
```

 <keyboard>
  <chainQuitKey>C-g</chainQuitKey>
<keybind key="A-F1">
   <action name="Desktop"><desktop>1</desktop></action>
 </keybind>
  <keybind key="A-F10">
    <action name="MaximizeFull"/>
  </keybind>
  <keybind key="A-F5">
    <action name="UnmaximizeFull"/>
  </keybind>
  <keybind key="A-F12">
    <action name="ToggleShade"/>
  </keybind>
  <keybind key="C-A-Left">
    <action name="DesktopLeft"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Right">
    <action name="DesktopRight"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Up">
    <action name="DesktopUp"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Down">
    <action name="DesktopDown"><wrap>no</wrap></action>
  </keybind>
... and all unnecessary bindings

```
Pity that it didn't work :\. I have Googled those commands and tried like everything (firstdesktop, GoToDesktop,1 and stuff). I really do like Openbox :).

EDIT: I was thinking, that if I use xfce4-panel with openbox, I may not need that feature at all. I must consider, but thanks anyway :).

---

### Post by Stormy Eyes on 2005-05-14
[QUOTE=Juippisi]Pity that it didn't work :\. I have Googled those commands and tried like everything (firstdesktop, GoToDesktop,1 and stuff). I really do like Openbox :).[/quote]

That's unfortunate. I'd recommend filing a bug report.

[QUOTE=Juippisi]EDIT: I was thinking, that if I use xfce4-panel with openbox, I may not need that feature at all. I must consider, but thanks anyway :).[/QUOTE]

I've always been able to use CTRL+ALT+Left and CTRL+ALT+Right to switch desktops, along with my mouse wheel. Not that there's anything wrong with using xfce4-panel (hey, you get a clock that way), but have you tried these methods?

---

### Post by Juippisi on 2005-05-14
[QUOTE=Stormy Eyes]I've always been able to use CTRL+ALT+Left and CTRL+ALT+Right to switch desktops, along with my mouse wheel. Not that there's anything wrong with using xfce4-panel (hey, you get a clock that way), but have you tried these methods?[/QUOTE]

Yes, I don't like that method, it takes too many fingers ;). Mousescrolling works fine, but my Firefox doesn't leave any space for desktop, so that part is hard. 
Well, my temporary solution for this is to use xftaskbar4. With that, I just take cursor on top of taskbar and scroll mouse and it works. Thanks for your bother with my problem, but I think this is ok for me :). 

And now I'll have to make my own menu for my Openbox and then everything will be just great.

---

### Post by Stormy Eyes on 2005-05-14
[QUOTE=Juippisi]And now I'll have to make my own menu for my Openbox and then everything will be just great.[/QUOTE]

Start with the following command.

[indent]*cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml*[/indent]

This will give you a copy of the default menu to hack on.

---

### Post by benplaut on 2005-05-14
i tried openbox for a long time, but eventually just got annoyed that it wasn't really all that different than Metacity... what i want is something like Kwin, where you can save settings about a window, so that they apply the next time the window is opened. Right now, i'm using metacity again because at least it work with the Keep Above thing for Gimp toolboxes...  :roll:

---

### Post by bored2k on 2005-05-17
I just installed it. Thanks Stormy for making me try openbox :D. I also installed openbox-themes packages wich is awsome. 

edit - Just restarted gnome..wicked fast !

---

### Post by Eproxus on 2005-05-17
How about desktop icons?

---

### Post by Hertell on 2005-05-17
[QUOTE=panickedthumb]If you choose to save your session on logout, it will take over on your next login as well. If you DON'T choose to save your session, logging out and back in will bring back metacity[/QUOTE]

I did this, but now gnome (or KDE) does not start att all. It "hangs" with a blank screen and a lonely mouseicon :-(

Is there anyway I can manually edit any config-file to get metacity back?


ps
Or, is there a way to start eg nautilus from an other terminal?

---

### Post by oddabe19 on 2005-05-18
more themes are as follows:

apt-get install openbox-themes

faily good amount there.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=Eproxus]How about desktop icons?[/QUOTE]

Openbox doesn't support desktop icons internally. However, you can use a starterbar provided by either gdesklets or adesklets, or use Engage from the E17 project. You could also use ROX-Filer, I believe, as its "Pinboard" function allows desktop icons. But don't take what I say about ROX as gospel, as I haven't used it in two years.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=Hertell]I did this, but now gnome (or KDE) does not start att all. It "hangs" with a blank screen and a lonely mouseicon :-(

Is there anyway I can manually edit any config-file to get metacity back?


ps
Or, is there a way to start eg nautilus from an other terminal?[/QUOTE]

Are you sure you didn't select "Openbox" from the GDM Sessions menu by mistake? If so, you can get to the menu by right-clicking the desktop.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=oddabe19]more themes are as follows:

apt-get install openbox-themes

faily good amount there.[/QUOTE]

That's true. Hey, maybe I should talk to the openbox-themes maintainer and get mine included.

---

### Post by Stormy Eyes on 2005-05-19
On the other hand, maybe I should just make my own debs instead of bugging the maintainer. What do you guys think?

---

### Post by Gandalf on 2005-05-20
it's really fast but something annoying me, when  i double-click VLC to switch into fullscreen but the down and upper panel stay on the screen, is there a way to hide them???

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=Gandalf]it's really fast but something annoying me, when  i double-click VLC rto have it fullscreen the down and upper panel stay on the screen, is there a way to hide them???[/QUOTE]

Double click? By default, double-clicking the titlebar in Openbox *shades* the window so that only the titlebar shows, unlike Metacity's default behavior. If you want fullscreen VLC, just focus on the VLC window and press the "F" key. The GNOME panels *should* behave themselves and not superimpose themselves over the fullscreen VLC. If they don't, try setting the "always on top" option,.

---

### Post by johneboy on 2005-05-20
Thanks for the HOWTO Stormy Eyes,

Sorry if this is a bit obvious but when I run "openbox --replace" the following output is shown in the terminal window:

```
(openbox:8360): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/johne/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:8360): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/johne/.config/openbox/menu.xml"

```

I have executed the command:

```
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml

```
Is this normal?

Thanks 

John

---

### Post by Juippisi on 2005-05-20
I don't know if this solves the problem, but try installing the "menu" (sudo apt-get install menu).

---

### Post by kassetra on 2005-05-20
[QUOTE=johneboy]
```
(openbox:8360): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/johne/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:8360): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/johne/.config/openbox/menu.xml"

```

I have executed the command:

```
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml

```
Is this normal?
[/QUOTE]

yes, it's normal.... you have to create your own menu (~/.config/openbox/menu.xml) - here is some starter information:
[http://icculus.org/openbox/docs.php?page=config.html&PHPSESSID=9c7c41bdee22e1877886d828e0aa42bf#menus](http://icculus.org/openbox/docs.php?page=config.html&PHPSESSID=9c7c41bdee22e1877886d828e0aa42bf#menus)
[http://gentoo-wiki.com/HOWTO_Openbox](http://gentoo-wiki.com/HOWTO_Openbox)
[http://icculus.org/openbox/docs.php?page=details.html&PHPSESSID=dd6560d1661894ea2a1b26b6fe41f645#menus](http://icculus.org/openbox/docs.php?page=details.html&PHPSESSID=dd6560d1661894ea2a1b26b6fe41f645#menus)
[http://www.arrishq.net/html/docs/config.html](http://www.arrishq.net/html/docs/config.html)

*You may need to install another application or two to help you with your menu files.

---

### Post by kassetra on 2005-05-20
[QUOTE=Juippisi]I don't know if this solves the problem, but try installing the "menu" (sudo apt-get install menu).[/QUOTE]

If that's available for Openbox - then yes, that might solve the problem.  :)

---

### Post by smoon on 2005-05-20
Just wanted to let you know that I made some themes for Openbox3 as well.

My last one tries to fit nice with Gnome and its Clearlooks theme: [This is what it looks like](http://nooms.de/images/screenshots/ob_lookclear.png). You can get it (and four other themes made by me) at [http://nooms.de/?page=openbox](http://nooms.de/?page=openbox). The page is in german language, but I don't think this will be a great issue since the screenshots describe the themes even better than written words ;)

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=kassetra]If that's available for Openbox - then yes, that might solve the problem.  :)[/QUOTE]

Yes, the "menu" package includes Openbox functionality, but I do not use the "menu" package myself, as I prefer to create my own menus.

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=smoon]Just wanted to let you know that I made some themes for Openbox3 as well.

My last one tries to fit nice with Gnome and its Clearlooks theme: [This is what it looks like](http://nooms.de/images/screenshots/ob_lookclear.png). You can get it (and four other themes made by me) at [http://nooms.de/?page=openbox](http://nooms.de/?page=openbox). The page is in german language, but I don't think this will be a great issue since the screenshots describe the themes even better than written words ;)[/QUOTE]

Smoon, I've edited the HOWTO to include a link to your theme page. I hope you don't mind terribly. Your Lookclear theme matches Clearlooks quite well; my wife was impressed.

---

### Post by Stormy Eyes on 2005-05-20
By request of **bored2k**:

Openbox's default **ALT+Tab** functionality is a bit limited compared to Metacity, which shows a dialog listing all the open apps on a given workspace similar to Windows. You don't have to settle for Openbox's anemic ALT+Tab. If you're using Openbox, try middle-clicking anywhere on your desktop. You'll see a menu listing each of your workspaces, starting with the first, and each workspace entry will have a submenu displaying the running windows on that workspace, with iconified (minimised) windows in brackets.

It's also possible to bind this menu, which is referred to internally as the "Client List Menu", to any key you like, and then to navigate that menu with your keyboard's arrow keys. Just follow the steps below.

1. Open a terminal and enter the command **gedit ~/.config/openbox/rc.xml**.

2. Once you've opened up Openbox's config file, scroll down until you see the following text:

```
<keybind key="A-Tab">
[indent]<action name="NextWindow"/>[/indent]
</keybind>
<keybind key="A-S-Tab">
[indent]<action name="PreviousWindow"/>[/indent]
</keybind>
```

3. Replace the text shown above with the following text:

```
<keybind key="A-Tab">
[indent]<action name="ShowMenu"><menu>client-list-menu</menu></action>[/indent]
</keybind>
<keybind key="A-S-Tab">
[indent]<action name="ShowMenu"><menu>client-list-menu</menu></action>[/indent]
</keybind>
```

4. Save your changes and close the editor.

5. If you're using Openbox as part of GNOME, and Openbox is part of your GNOME session, then typing **killall openbox** at the terminal *should* cause GNOME to restart Openbox for you. If GNOME won't play ball, you should be able to click on the *Applications* menu, select "Run Application", and type "openbox" into the prompt. Or, you could avoid all this by logging out and logging in again. If you're using Openbox on its own, then right-click on the desktop for the main menu, and choose the *Reconfigure* option. Openbox will reread its config file.

By following the above steps, you've modified the keybindings for ALT+Tab and SHIFT+ALT+Tab to bring up the same client list menu that appears when you middle-click on the desktop. You can navigate it using your arrow keys, and press "Enter" to go to a  running app, even if that app is on a different workspace.

---

### Post by bored2k on 2005-05-20
[QUOTE=Stormy Eyes]
1. Open a terminal and enter the command **gedit ~/.config/rc.xml**.
[/QUOTE]

Do you mean .config/openbox/rc.xml ?

I'm configuring it as we speak ..

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bored2k]Do you mean .config/openbox/rc.xml ?

I'm configuring it as we speak ..[/QUOTE]

Yes, I did mean that. Thanks for catching that for me.

---

### Post by bored2k on 2005-05-20
[QUOTE=Stormy Eyes]By request of **bored2k**:[/QUOTE]
[CENTER]Thank you it's even better than metacity's !!
[img]http://img267.echo.cx/img267/4052/menu1mg.png[/img][/CENTER]
This is reaally nice. Thank you thank you. Where did you learn all this ? Now I'm interested in learning how to tweak Openbox !

By the way, you can just restart openbox with a right click on the menu > restart .

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bored2k][CENTER]Thank you it's even better than metacity's !!
[img]http://img267.echo.cx/img267/4052/menu1mg.png[/img][/CENTER][/quote]

You're welcome.

[QUOTE=bored2k]This is reaally nice. Thank you thank you. Where did you learn all this ? Now I'm interested in learning to tweak Openbox ![/quote]

I just read [the manual](http://icculus.org/openbox/docs.php?page=details.html&PHPSESSID=cdc91a019a7ef2bb0c567656a56126f9). :) I was tired of reaching for the trackball when I wanted to switch windows, and didn't want to have to first switch desktops and then ALT+Tab to the window I wanted. Doing so tends to waste a fair amount of time when you've got a bunch of terminals, Gvim windows, and an OpenOffice.org Writer window or three open at the same time. :)

[QUOTE=bored2k]By the way, you can just restart openbox with a right click on the menu > restart .[/QUOTE]

This is true, but I favor *Reconfigure* over *Restart* because it's less disruptive, IMHO.

---

### Post by bored2k on 2005-05-20
In about 1 minute I'll be reinstalling Hoary, but after that's done and I have my basic needs. I'll try to see how I could tweak Openbox til it breaks ;)

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bored2k]In about 1 minute I'll be reinstalling Hoary, but after that's done and I have my basic needs. I'll try to see how I could tweak Openbox til it breaks ;)[/QUOTE]

Reinstalling Hoary? How come?

---

### Post by kvidell on 2005-05-21
[QUOTE=Stormy Eyes]Reinstalling Hoary? How come?[/QUOTE]
 I think I convinced him inadvertantly to try Breezy and it broke on him >.>
d'oh
*gets sheepish and hides*

I however am loving Openbox on it's own. I still don't have a panel app that I like (PyPanel was hideous) and I'm having trouble figuring out how to get Ctrl+Alt+Number to switch to the corresponding worksapce.

Good stuff otherwise :)
- Kev

---

### Post by Stormy Eyes on 2005-05-21
[QUOTE=kvidell]I think I convinced him inadvertantly to try Breezy and it broke on him >.>
d'oh
*gets sheepish and hides*[/quote]

Bad kitty!

[quote=kvidell]I however am loving Openbox on it's own. I still don't have a panel app that I like (PyPanel was hideous) and I'm having trouble figuring out how to get Ctrl+Alt+Number to switch to the corresponding worksapce.[/quote]

Try pasting the following XML into the keyboard section of your rc.xml and you can use ALT+1, etc. to switch desktops.

```
<keybind key="A-1">
    <action name="Desktop"><desktop>1</desktop></action>
</keybind>
<keybind key="A-2">
    <action name="Desktop"><desktop>2</desktop></action>
</keybind>
<keybind key="A-3">
    <action name="Desktop"><desktop>3</desktop></action>
</keybind>
<keybind key="A-4">
    <action name="Desktop"><desktop>4</desktop></action>
</keybind>
```

As for panels: accept my condolences. I haven't found one that was exactly to my taste either, so I just use a seriously stripped-down gnome-panel that just has a search button, a trashcan icon, a pager, a notification area, a clock, and a weather applet.

---

### Post by kvidell on 2005-05-21
A) You scared me. I have a character in some circles that's a cat o.O
B) Just because I broke this file once before and it got very ~very~ angry at me, I'm going to ask a stupid question: As A corresponds to Alt, does C correspond to Ctrl? Because Alt+Number is apparently how FireFox does quick-switching for tabs, as does XChat (I use that one).

and, gnome's panel thingie huh? mm.. well.. maybe. I'll give it a shot later.
I'm not in ~dire~ need of one, I suppose I could fandangle something like gdesklets in to being what I usually require from a panel.

*is still wondering why you called him a kitty >.>* (Not a bad thing, I don't mind at all... Just caught me off guard :-P).
- Kev

---

### Post by Stormy Eyes on 2005-05-21
[QUOTE=kvidell]A) You scared me.[/quote]

Good. I'd hate to become utterly innocuous just because I'm married. :)

[QUOTE=kvidell]B) Just because I broke this file once before and it got very ~very~ angry at me, I'm going to ask a stupid question: As A corresponds to Alt, does C correspond to Ctrl? Because Alt+Number is apparently how FireFox does quick-switching for tabs, as does XChat (I use that one).[/quote]

You're right.

A = Alt
C = Control
S = Shift

I'm using the Epiphany browser, since it fits in better with other GNOME apps, so I didn't notice that Alt+1 is used to switch between tabs in Firefox and Xchat. Sorry about that.

[QUOTE=kvidell]and, gnome's panel thingie huh? mm.. well.. maybe. I'll give it a shot later. I'm not in ~dire~ need of one, I suppose I could fandangle something like gdesklets in to being what I usually require from a panel.[/quote]

Well, the Psi desklets do have a pager desklet, and IMHO the client-list-menu renders the taskbar irrelevant.

[QUOTE=kvidell]*is still wondering why you called him a kitty >.>* (Not a bad thing, I don't mind at all... Just caught me off guard :-P).[/quote]

Because I could. And because I was raised by alley cats.

---

### Post by bored2k on 2005-05-21
I just wanted to add.
By making nautilus **not** draw the desktop, you can just right click on the desktop for the Openbox icon to appear.

---

### Post by bored2k on 2005-05-21
And no I did not update to Breezy.

1. Scared
2. Wanted to learn more but, College is really starting to put some pressure on me, and who knews when  X won't load up just when I'd need it the most.

---

### Post by Stormy Eyes on 2005-05-21
[QUOTE=bored2k]I just wanted to add.
By making nautilus **not** draw the desktop, you can just right click on the desktop for the Openbox icon to appear.[/QUOTE]

That's true.

---

### Post by smoon on 2005-05-21
Another nifty feature of Openbox3 are pipe menus: Menus that are dynamically generated by some kind of program. For example, the following bash-script generates a menu of your GTK+2-Fileselector-Bookmarks:
```
#!/bin/bash

echo '<openbox_pipe_menu>'

for bookmark in `cat ${HOME}/.gtk-bookmarks` ; do
  echo '<item label="'`basename ${bookmark}`'">'
  echo '<action name="Execute"><execute>'
  echo "nautilus ${bookmark}"
  echo '</execute></action>'
  echo '</item>'
done

echo '</openbox_pipe_menu>'
```
If you paste this code in a file called gtk-bookmarks.sh, make it executable and add the following line to one of your menus (the root-menu is most likely <menu id="root-menu" label="Openbox3">...</menu> in ${HOME}./config/openbox/menu.xml):
```
<menu id="bookmark-menu" label="Bookmarks" execute="/path/to/gtk-bookmarks.sh" />
``` you'll get a submenu labeled "Bookmarks" with all your GTK+-bookmarks in it. Clicking on an entry in that menu will open the directory in nautilus.

There are some scripts out there to generate menus with recent headlines from newssites, Quake3 server stats, a desktop-background changer and many more.

---

### Post by Stormy Eyes on 2005-05-22
[QUOTE=smoon]Another nifty feature of Openbox3 are pipe menus: Menus that are dynamically generated by some kind of program. For example, the following bash-script generates a menu of your GTK+2-Fileselector-Bookmarks:[/QUOTE]

Smoon, this kicks ass. I'll include this in the main HOWTO, if you like, and credit you. And I'll patch this into my menu as well; now I won't have to do one myself.

---

### Post by bored2k on 2005-05-22
[QUOTE=Stormy Eyes]Smoon, this kicks ass. I'll include this in the main HOWTO, if you like, and credit you. And I'll patch this into my menu as well; now I won't have to do one myself.[/QUOTE]
 I still don't understand what smoon's stuff does.. screenshot please ?

---

### Post by jobezone on 2005-05-22
And you **use** Nautilus to draw the desktop, middle-click will give you that menu.

---

### Post by Stormy Eyes on 2005-05-22
[QUOTE=bored2k]I still don't understand what smoon's stuff does.. screenshot please ?[/QUOTE]

Smoon's hack will give you a reasonable facsimile of GNOME 2.10's **Places** menu. Just try it for yourself; a screenshot of this can be faked.

---

### Post by Stormy Eyes on 2005-05-22
[QUOTE=jobezone]And you **use** Nautilus to draw the desktop, middle-click will give you that menu.[/QUOTE]

Which menu? The Places menu? It didn't when I used Openbox in GNOME; it would give me the client list menu instead. Would you mind clarifying?

---

### Post by smoon on 2005-05-22
[QUOTE=Stormy Eyes]Smoon, this kicks ass. I'll include this in the main HOWTO, if you like, and credit you.[/QUOTE]
Yupp, that would be nice.

Maybe someone will find these menu generating scripts/programs useful:
[ACPI Monitor and Gmail Checker](http://gamma.pnosker.com/ob3.php) (this page has some nice themes as well). [http://www.gozer.org/my_stuff/c/](http://www.gozer.org/my_stuff/c/) has a little c-program that generates a menu of available themes, one creates a list of your wallpapers, ob3_headlines displays headlines using a RDF/RSS Feed and one creates a list of QuakeIII Arena servers.
That's all I found so far. Maybe someone comes up with some more nice, useful, cool, whatever little scripts :-)

Maybe I'll try to update my script to a full-featured Places-menu with "Recent documents", network connectios, etc.

---

### Post by jobezone on 2005-05-22
[QUOTE=Stormy Eyes]Which menu? The Places menu? It didn't when I used Openbox in GNOME; it would give me the client list menu instead. Would you mind clarifying?[/QUOTE]
 I meant the openbox menu with the list of opened apps.

---

### Post by smoon on 2005-05-22
In case anyone is interested: I improved my little Places-Script so that it now has bookmarks, recent documents and connected servers in it. This is what it looks like:
[IMG]http://nooms.de/misc/ob-places.png[/IMG]

The "Recent Documents" submenu has some limitations though: It only shows files that are stored locally and it uses run-mailcap to determine the filetype and open the selected file with an appropriate application. Since run-mailcap uses /etc/mailcap to find out which mimetype to open with which program, it might choose another one than Gnome may use (Note: you can copy /etc/mailcap to $HOME/.mailcap and edit it to your needs).
Entries in "Recent Documents" marked with a star (*) ceased to exist on your harddisk, so don't wonder why nothing happens when you click them ;)

Let me know if I missed something, when you've suggestions or you just can't get it to work.


*Edit*
Ooops, forgot to include the script: [http://nooms.de/misc/openbox/gnome-places.sh](http://nooms.de/misc/openbox/gnome-places.sh)

---

### Post by kvidell on 2005-05-28
I can't get .xsession or the screensaver apps to work :-\
I want to be able to lock my desktop like I could in gnome.
Argh.
- Kev

---

### Post by smoon on 2005-05-28
Ok, [here's oPerfection](http://nooms.de/misc/openbox/ob_oPerfection.tar.gz), a theme I just created out of boredom. It tries to fit with the [gPerfection ClearLooks theme](http://www.gnome-look.org/content/show.php?content=23563).

[Here's a screenshot](http://nooms.de/images/screenshots/ob_oPerfection.png). Hope, you like it.

---

### Post by bored2k on 2005-05-28
[QUOTE=smoon]Ok, [here's oPerfection](http://nooms.de/misc/openbox/ob_oPerfection.tar.gz), a theme I just created out of boredom. It tries to fit with the [gPerfection ClearLooks theme](http://www.gnome-look.org/content/show.php?content=23563).

[Here's a screenshot](http://nooms.de/images/screenshots/ob_oPerfection.png). Hope, you like it.[/QUOTE]
 Nice one :D

---

### Post by greenwom on 2005-05-29
I ran the terminal commands as the how-to dictated.

When I run openbox --replace I get

[COLOR=DarkOrange]mike1@mikesubuntu:~/.themes$ openbox --replace
I/O warning : failed to load external entity "/home/mike1/.config/openbox/rc.xml"
I/O warning : failed to load external entity /home/mike1/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:11383): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/mike1/.config/openbox/menu.xml"[/COLOR]

It looks like it works otherwise, is this anything I should be worried about?

---

### Post by kvidell on 2005-05-29
[QUOTE=smoon]Ok, [here's oPerfection](http://nooms.de/misc/openbox/ob_oPerfection.tar.gz), a theme I just created out of boredom. It tries to fit with the [gPerfection ClearLooks theme](http://www.gnome-look.org/content/show.php?content=23563).

[Here's a screenshot](http://nooms.de/images/screenshots/ob_oPerfection.png). Hope, you like it.[/QUOTE]
 Wow. That actually looks usable. Very nice.

I'm still trying to find one that matches my background image, though. Not having much luck at it :-\

Also, are you using openbox inside gnome or gnome-panel inside openbox?

Cheers,
- Kev

---

### Post by smoon on 2005-05-29
[QUOTE=kvidell]Wow. That actually looks usable. Very nice.

I'm still trying to find one that matches my background image, though. Not having much luck at it :-\

Also, are you using openbox inside gnome or gnome-panel inside openbox?

Cheers,
- Kev[/QUOTE]

I'm using Openbox inside Gnome at the moment. But I had it working the other way as well.

---

### Post by jonrkc on 2005-06-12
Just tried Openbox tonight for the first time and I like its look and feel very much.  I applied your suggestion for making ALT+TAB more functional--thanks!

I've seen several references to a toolbar, including in the Openbox documentation, but I fail to FIND a toolbar anywhere.  Not that it's all that necessary, but I'm puzzled that it's spoken of but doesn't appear to exist in my copy of Openbox....

---

### Post by kvidell on 2005-06-13
Anyone know a way to write an rc file for openbox that launches certain apps in specific desktops?
I have a total of 8 workspace/desktop things and it's a hassle to go through and start everything that needs to be somewhere specific...
IE:
1: terminals
2: firefox
3: gaim + a terminal for BX
4: thunderbird and sunbird
5: logjam gedit newton
6: bmp kstreamripper aumix
 etc etc etc :-\

Plus I want it to do sh .fehbg everytime and start up torsmo...

I can't get xsession or xinitrc or anything like that to work.. any other ideas?
I'm mostly concerned about start apps in the correct workspace for now...
- Kev

---

### Post by kvidell on 2005-06-13
[QUOTE=jonrkc]Just tried Openbox tonight for the first time and I like its look and feel very much.  I applied your suggestion for making ALT+TAB more functional--thanks!

I've seen several references to a toolbar, including in the Openbox documentation, but I fail to FIND a toolbar anywhere.  Not that it's all that necessary, but I'm puzzled that it's spoken of but doesn't appear to exist in my copy of Openbox....[/QUOTE]
 You have to find one you like and implement it yourself.
I use gnome-panel personally, but there's a pretty wide selection..
From the Gentoo wiki:> The three main panels I've tested so far are (all available in portage, just emerge app):

    * pypanel - A Python based panel, sporting icons, transparency and lots of other candy while remaining at 25 Kb (source).
    * FSPanel - F***ing Small Panel, a tiny panel, coming in at 9Kb of code.
    * FBPanel - Coming in at 77Kb source, FBPanel is based on FSPanel, with many more features.
    * kicker - KDE's kicker, works well except with some buttons not working (Logout, Lock Desktop, etc)
    * perlpanel - A perl based panel, has icons, and supports many applets. Also, its pretty easy to write applets for it.
    * KoolDock - A MacOSX like dock. Very nice ! 

---

### Post by smoon on 2005-06-13
[QUOTE=jonrkc]Just tried Openbox tonight for the first time and I like its look and feel very much.  I applied your suggestion for making ALT+TAB more functional--thanks!

I've seen several references to a toolbar, including in the Openbox documentation, but I fail to FIND a toolbar anywhere.  Not that it's all that necessary, but I'm puzzled that it's spoken of but doesn't appear to exist in my copy of Openbox....[/QUOTE]

I think you're talking about the "Dock"? You've to run apps that swallow into it to make it visible. Basically it looks like this: [http://nooms.de/images/gallery/screenshots/2004-05-28-135314_1280x1024_scrot.jpg](http://nooms.de/images/gallery/screenshots/2004-05-28-135314_1280x1024_scrot.jpg) (The thing at the bottom). You'll find the so called Dockapps at places like [http://dockapps.org/](http://dockapps.org/) or [http://www.bensinclair.com/dockapp/](http://www.bensinclair.com/dockapp/).

---

### Post by smoon on 2005-06-13
[QUOTE=kvidell]Anyone know a way to write an rc file for openbox that launches certain apps in specific desktops?
I have a total of 8 workspace/desktop things and it's a hassle to go through and start everything that needs to be somewhere specific...
IE:
1: terminals
2: firefox
3: gaim + a terminal for BX
4: thunderbird and sunbird
5: logjam gedit newton
6: bmp kstreamripper aumix
 etc etc etc :-\

Plus I want it to do sh .fehbg everytime and start up torsmo...

I can't get xsession or xinitrc or anything like that to work.. any other ideas?
I'm mostly concerned about start apps in the correct workspace for now...
- Kev[/QUOTE]

For starting apps on a specified desktop you can use [Devil's Pie](http://www.burtonini.com/blog/computers/devilspie) and/or [wmctrl](http://sweb.cz/tripie/utils/wmctrl/). Both should work fine for that, just test which method you like better.

Running torsmo and setting the background using feh should not be too difficult. Just edit ${HOME}/.Xsession and add the following lines:
```
#!/bin/sh

# Set Background using feh
eval `cat ${HOME}/.fehbg` &

# Run torsmo
/usr/bin/torsmo -d

# Add other apps here
# ...

# Start the window manager
exec /usr/bin/openbox
```
Make it executable (`chmod 0700 ${HOME}/.Xsession'). Try starting GDM, choose "Sessions" and select "Predefined system session" (or something similar, it's in german here and I'm not sure what the label is in english). Login as usual then and you should get a nice, clean Openbox desktop with torsmo running and the background set.

---

### Post by jonrkc on 2005-06-13
[QUOTE=kvidell]Anyone know a way to write an rc file for openbox that launches certain apps in specific desktops?[/QUOTE]

I don't know how to do this in openbox, but in IceWM it's easy, especially if you can get IceWMCP to work for configuring it.  But even without an intervening interface, editing IceWM config. files is straightforward....  Just an observation, not an attempt to convert.

[EDIT]  I posted this before I saw the post above neatly explaining how to do what you want.

---

### Post by jonrkc on 2005-06-13
[QUOTE=kvidell]You have to find one you like and implement it yourself.
I use gnome-panel personally, but there's a pretty wide selection..
From the Gentoo wiki:[/QUOTE][...etc.]

Thanks! I'll copy those possibilities and give some of them a try.

---

### Post by Artanis on 2005-06-23
Can anyone provide a working link to the Martian theme?

---

### Post by Juippisi on 2005-06-24
[QUOTE=greenwom]I ran the terminal commands as the how-to dictated.

When I run openbox --replace I get

[COLOR=DarkOrange]mike1@mikesubuntu:~/.themes$ openbox --replace
I/O warning : failed to load external entity "/home/mike1/.config/openbox/rc.xml"
I/O warning : failed to load external entity /home/mike1/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:11383): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
I/O warning : failed to load external entity "/home/mike1/.config/openbox/menu.xml"[/COLOR]

It looks like it works otherwise, is this anything I should be worried about?[/QUOTE]

Installing "menu" should fix that (sudo apt-get install menu).

---

### Post by Stormy Eyes on 2005-06-29
[QUOTE=Artanis]Can anyone provide a working link to the Martian theme?[/QUOTE]

I smacked my host around, and my account has been re-enabled. You should be able to use the link in the howto now. I apologise for the inconvenience; I've had to busy myself with other things while waiting for my new PC.

---

### Post by clarke.rainey on 2005-07-06
This may sound like a dumb question... but at the moment I am running openbox in the place of metacity and I am very much enjoying it...

woops!.. that was a statement... here is the question...

for some reason when I go to make the changes to the key combinations such as Alt-Tab and such I have no rc.xml file... what should I do?.. should I just make one?.. if so what do I need to put into it... openbox works fine so I am not too worried about not having an rc.xml file, but I do not want to screw things up by creating one if that is not what one should do... thanks!..

---

### Post by Stormy Eyes on 2005-07-14
[QUOTE=clarke.rainey]for some reason when I go to make the changes to the key combinations such as Alt-Tab and such I have no rc.xml file... what should I do?.. should I just make one?.. if so what do I need to put into it... openbox works fine so I am not too worried about not having an rc.xml file, but I do not want to screw things up by creating one if that is not what one should do... thanks!..[/QUOTE]

Start by doing the following to make your own rc.xml and menu.xml files:

```
mkdir -p ~/.config/openbox
cp /etc/xdg/openbox/rc.xml ~/.config/openbox/rc.xml
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
```

Openbox keeps default config files somewhere in /etc; in Ubuntu and Debian they live in /etc/xdg. You can copy them to ~/.config/openbox and hack on the copies, and Openbox will fall back to the default files if you screw up.

---

### Post by martyren on 2005-07-19
[QUOTE=Gandalf]it's really fast but something annoying me, when  i double-click VLC to switch into fullscreen but the down and upper panel stay on the screen, is there a way to hide them???[/QUOTE]

same problem for me :(

---

### Post by Stormy Eyes on 2005-07-20
[QUOTE=martyren]
[quote=gandalf]it's really fast but something annoying me, when i double-click VLC to switch into fullscreen but the down and upper panel stay on the screen, is there a way to hide them???[/quote]
same problem for me :([/QUOTE]

I've had that problem as well, but I don't know if it's Openbox not handling the fullscreen hint properly or if it's gnome-panel being stupid.

---

### Post by XaRP1Sh87g on 2005-07-27
Hi!
I have recently been playing around with ubuntu-linux and am now quite happy with a pretty striped down (server-expert) installation. X is installed and running correctly, and I have opted for openbox to be my ONLY windowmanager (No gnome or anything).
My problem is that I can't find my .xinitrc file in my home directory. Creating one does not help either. Strangely enough startx fires up my X+openbox perfectly, but without setting a background image or any other 'default' apps that I want such as a clock or a calender.
I can manually set a background though, using feh --bg-scale /pathtoimage (and I can of course start any app I want to...) but when I restart Openbox, everything is gone.
I know that one would normally set these type of 'defaults' in the users .xinitrc file, but ubuntu seems to manage this differently.

I've recently also installed gdm, thinking that it might generate a config file in which I could put my 'feh-command', to no avail. ](*,) 

Any help is welcome!

---

### Post by dbernar1 on 2005-07-27
Excellent. Very nice of you to think of those that like the default ubuntu theme, like me.
dabaR

---

### Post by Stormy Eyes on 2005-07-27
[QUOTE=hungrigerhaifisch]Any help is welcome![/QUOTE]

Once you've created your .xinitrc file, you have to link it to .xsession so that XDM, GDM, and the like will run it if you choose "Default Session". The command you need is **ln -s ~/.xinitrc ~/.xsession**. Once you've done that, everything should work correctly. Let me know how it turns out.

---

### Post by Stormy Eyes on 2005-07-27
[QUOTE=dbernar1]Excellent. Very nice of you to think of those that like the default ubuntu theme, like me.
dabaR[/QUOTE]

Actually, I was thinking of my wife, but you're welcome. :)

---

### Post by Stormy Eyes on 2005-07-27
I tend to use spaces in my directory names. When I add such a directory to my Places menu, Smoon's gtk-bookmark.sh script tends to display in the menu the HTML entity denoting a space instead of a space, so that an entry that should read like this:
```
I like kittens.
```
reads instead like this:
```
I%20like%20kittens.
```

Since this is ugly, I decided to RTFM and figure out how to make sed do a quick find 'n replace. Here is the result:

```
#!/bin/bash

echo '<openbox_pipe_menu>'

for bookmark in `cat ${HOME}/.gtk-bookmarks` ; do
#  echo '<item label="'`basename ${bookmark}`'">'
  echo '<item label="'`basename ${bookmark} | sed 's/%20/ /g'`'">'
  echo '<action name="Execute"><execute>'
  echo "nautilus --no-desktop ${bookmark}"
  echo '</execute></action>'
  echo '</item>'
done

echo '</openbox_pipe_menu>'
```

---

### Post by XaRP1Sh87g on 2005-07-28
Thanks for the reply, BUT:

I don't seem to have neither an .xinit file nor a .xsession file in my home directory.
What I do have is a .xsession-error file... :-?
Is it possible and wise though to maybe link my .xinit file (after creating it!) to the xinitrc in /etc/X11/xinit? or to some other file in the /etc/X11 directory?

---

### Post by Stormy Eyes on 2005-07-28
[QUOTE=hungrigerhaifisch]Thanks for the reply, BUT:

I don't seem to have neither an .xinit file nor a .xsession file in my home directory.
What I do have is a .xsession-error file... :-?
Is it possible and wise though to maybe link my .xinit file (after creating it!) to the xinitrc in /etc/X11/xinit? or to some other file in the /etc/X11 directory?[/QUOTE]

Don't try it. You'll only end up trying to overwrite a system file (all files in /etc are system config files, so don't mess with 'em unless you know what you're doing) with a symbolic link. 

Here's what you have to do.

1. Create ~/.xinitrc by typing **gedit ~/.xinitrc** at a terminal prompt.

2. Put the following text into the file, save it, and close the editor:

```
#!/usr/bin/env bash

export OOO_FORCE_DESKTOP=gnome

gnome-settings-daemon &
gnome-volume-manager &
xrdb -merge .Xdefaults &
nvidia-settings -l &
sh ./.fehbg

exec openbox
```

3. Now that you have your .xinitrc file, link it to .xsession:

```
ln -sf ~/.xinitrc .xsession
```

---

### Post by XaRP1Sh87g on 2005-07-28
I thought as much that it may be risky (or plain stupid) to link to a system file, so I asked... :neutral: 
but, before I try out your suggestion, could you maybe explain what the commands that I am to add to my .xinitrc file mean, just so I learn something while doing...

what is this "force-gnome" thing?
I don't have gnome installed (exept for a few libs...and gdm)
also, I don't have or use a nvidia card, its an ati radeon9800 and I have the ubuntu binary drivers/modules installed. (I was not able to build modules for my custom kernel, since the newest driver from ati seems to be broken with ubuntu's libc6...so I figuered...)(I am currently using the ubuntu stock kernel though...just in case you wondered)
and I also can't find any .xsession file in my home directory, so how is it that I can link to it?
(also no .Xdefaults)

Heeeelp?! :confused:

---

### Post by dbernar1 on 2005-07-29
Hey, what can be done for removing the shades in the context menu?

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=dbernar1]Hey, what can be done for removing the shades in the context menu?[/QUOTE]

I'm not sure what you mean by "shades in the context menu". Could you please clarify?

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=hungrigerhaifisch]but, before I try out your suggestion, could you maybe explain what the commands that I am to add to my .xinitrc file mean, just so I learn something while doing...[/quote]

No problem.

[QUOTE=hungrigerhaifisch]what is this "force-gnome" thing?
I don't have gnome installed (exept for a few libs...and gdm)[/quote]

$OOO_FORCE_DESKTOP is an environment variable that OpenOffice.org checks when starting up. If it's set to "gnome", OpenOffice.org will make itself look like any other GTK app (like GIMP, or Rhythmbox, or Evolution). It'll fit in with a GNOME desktop. If you set it to "kde" instead, OpenOffice.org would make itself look like a KDE app. Leave it unset, and it just looks ugly. Really ugly.

[QUOTE=hungrigerhaifisch]also, I don't have or use a nvidia card, its an ati radeon9800 and I have the ubuntu binary drivers/modules installed. (I was not able to build modules for my custom kernel, since the newest driver from ati seems to be broken with ubuntu's libc6...so I figuered...)(I am currently using the ubuntu stock kernel though...just in case you wondered)[/quote]

OK. If you don't have nVidia hardware, then the nvidia-settings line is irrelevant to you. You can take it out. Likewise the line referring to .Xdefaults. I have an .Xdefaults file because I prefer xterm over gnome-terminal and need to set xterm's fonts so it doesn't look ugly.

[QUOTE=hungrigerhaifisch]and I also can't find any .xsession file in my home directory, so how is it that I can link to it?[/QUOTE]

I'm sorry, I should have been clearer. The .xsession file does not exist, but the ln command I showed you will *create* a special file called '~/.xsession' that acts as a pointer to '~/.xinitrc'. Thus, if I were to do 'vim ~/.xsession' I'd really be editing '~/.xinitrc' instead. You can think of symbolic links as a concept similar to the shortcuts in Windows if you like.

---

### Post by austinz on 2005-07-29
Hi
The changes that I've made in my ~/.config/openbox/menu.xml files don't seem to have any effect on my menu. I've added several scripts that I've found and am storing in the appropriate directories (~/.config/openbox/scripts)  and have noted appropriately in the menu.xml file.  There is no change in my menu. For example:
```

</item>
  <!-- This requires the presence of the 'menu' package to work -->
  <menu id="Debian" />
  <menu id="config" execute="~/.config/openbox/scripts/cfgmenu.py -m" />
  <separator />
  <menu id="client-list-menu" />
  <separator />

```
Could this be because I'm using breezy badger?  Could it be that I have the menu package installed (does this override manual menu changes?)  

Next, to figure out the .xinitrc ....  

Austin

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=austinz]Could this be because I'm using breezy badger?  Could it be that I have the menu package installed (does this override manual menu changes?)  [/QUOTE]

I think it's more likely to be due to you not selecting "Reconfigure" from the menu after you've finished your changes. :) Try it and let me know if that fixes you up.

---

### Post by austinz on 2005-07-29
I've reconfigured and restarted openbox, as well as rebooting my laptop several times with no change. As far as I know I'm current with breezy updates as well.  Suggestions? 

Thanks!

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=austinz]I've reconfigured and restarted openbox, as well as rebooting my laptop several times with no change. As far as I know I'm current with breezy updates as well.  Suggestions? [/QUOTE]

This line is wrong:

```
<menu id="config" execute="~/.config/openbox/scripts/cfgmenu.py -m" />
```

Try this instead:

```
<menu id="config" label="Configuration" execute="/home/$userid/.config/openbox/scripts/cfgmenu.py -m" />
```

I don't think you can use ~ in an openbox menu; I think you have to use the full path. Make sure to replace $userid with your user name.

---

### Post by austinz on 2005-07-29
Success! 

 It worked like a charm. I actually had the full path in the file, but I didn't put it publically (not that it would have mattered, I guess...) .   

Thanks for the help, I'm now going to attempt to set my program defaults with an .xsession file.  If that doesn't work, I may be back.  

Austin

---

### Post by austinz on 2005-07-29
> 
This line is wrong:

Code:

<menu id="config"   execute="~/.config/openbox/scripts/cfgmenu.py -m" />


This forces me to ask:  

What is the "id" tag for, if it does not name the menu as it appears on the screen?  Is there a set action for the word config, or other words?

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=austinz]What is the "id" tag for, if it does not name the menu as it appears on the screen?  Is there a set action for the word config, or other words?[/QUOTE]

I would have to read the code and ask the Openbox maintainer, but I think the "id" tag is meant to be an internal identifier.

---

### Post by smoon on 2005-07-30
[QUOTE=Stormy Eyes]I would have to read the code and ask the Openbox maintainer, but I think the "id" tag is meant to be an internal identifier.[/QUOTE]

AFAIK this is correct. For example if you bind menus to actions you use this identifier:
```
<menu id="config" label="Configuration" execute="~/.config/openbox/scripts/cfgmenu.py -m" />
```
```
<keybind key="A-y">
  <action name="ShowMenu"><menu>config</menu></action>
</keybind>
```

Now if you hit Alt+y the "config" menu will pop up.

Btw.: the ~ for $HOME works for me.

---

### Post by Neo40 on 2005-07-30
Hello,

I dont know if I missed something but after I typed "openbox --replace", Metacity is gone and I have openbox running. Then if I right click on my destop, I still have the same menu like metacity?!

Also, is it possible to use fluxbox instead? I tried "fluxbox --replace" but it says another window manager already running on display :0.0...

Thanks

---

### Post by Stormy Eyes on 2005-07-30
[QUOTE=Neo40]
I dont know if I missed something but after I typed "openbox --replace", Metacity is gone and I have openbox running. Then if I right click on my destop, I still have the same menu like metacity?![/quote]

Under GNOME, Nautilus (the file manager) draws the desktop. It handles the wallpaper, the icons, and the menu that pops up when you right-click on the desktop in GNOME. Under GNOME, you don't really need the Openbox menu, as you can use the one provided by the GNOME panel. If you're running Openbox by itself, it'll provide its own menu.

[QUOTE=Neo40]Also, is it possible to use fluxbox instead? I tried "fluxbox --replace" but it says another window manager already running on display :0.0...[/QUOTE]

You'll have to consult the Fluxbox documentation. I neither use nor promote Fluxbox, so I don't know anything about it.

---

### Post by lassel on 2005-07-30
I have been running with openbox for a couple of days now.

I /really/ like the speed improvement over metacity. It is just amazing for such a little change to the system!

I have two things I don't like. The first i just a "oh I wish", the second is more important.

1) I spent good time configuring my keyboard shortcuts for metacity -- thinking that they were universal. Now I have to start over. Is there no program that can import my metacity keyboard settings to openbox so I don't have to redo it all by hand?

2) I find that when I use various programs in openbox the keyboard shortcuts for the particular program stops working. Even trivial stuff.
In firefox I find that page up/down never works. Ctrl + T for a new tab only works /sometimes/. Do a metacity --replace and everything just works. If I don't solve that one I will have to go back to metacity as I use keyboard shortcuts as much as possible.

---

### Post by XaRP1Sh87g on 2005-07-31
Ok, I finally got round to testing out what you suggested.
But, it didn't work.

What and where is the default 'init' file for openbox?
What and where is the default 'init' file for X?
I think that either X or Openbox is just ignoring my 'xinitrc' because it is using a different config file

Suggestions?

---

### Post by G.W. on 2005-07-31
I configured my Logitech MX500 as described in this thread: 

[http://www.ubuntuforums.org/showthread.php?t=28374](http://www.ubuntuforums.org/showthread.php?t=28374)

Everything works as it should in metacity. In openbox the mmb, wheel and up/down mousebuttons work, the forward/back ones do not... Do I have to configure them somewhere? Thanks for any advice!

Edit: I feel pretty stupid right now, somehow it seems to work now... which is kind of odd because i even rebooted a couple of times without success... Thanks anyways...

---

### Post by Stormy Eyes on 2005-07-31
[QUOTE=G.W.]I configured my Logitech MX500 as described in this thread: 
[/QUOTE]

I can't help you with hardware unfamiliar to me. I'm sorry.

---

### Post by dbernar1 on 2005-08-02
Hey, Stormy Eyes. Well, here is some info, you may know, and maybe you all know it, but anyhow.

Ok, a context menu is the menu that comes up when you right click, and is called that because it depends on where you right click. 

Shades are shadows, that you all know. Turn on the Martian theme(probably all the other ones you have posted, not sure) and right click on the desktop, for the openbox menu. You will see letters. Under the letters, you will see a reflection/shadow they cast onto the menu background. Again, try this, you may not get what I mean otherwise.

Now, if you have the same GUI taste as I do, or it may even just be bad GUI design, you will notice that it is very hard to read the letters, since they are doubled, and crossing over, basically hard to read for me.

Also, you can se this effect if you open two windows, and in the title bar(the top window border) of the inactive window(one that does not have the focus) the same thing is done, the letters have a shadow, and it is harder to read for me than were they not there. 

Make me a version of the theme without the shades :), if its not too hard. [-o<  

Ok, I hope you understand this time, and thanks Stormy Eyes!

dabaR

---

### Post by austinz on 2005-08-06
Hi again

I've made changes to my .xinitrc file, but nothing that I've changed actually happens when I load openbox.  I'm trying to load up my configured fbpanel, set my background with feh, then open X. Here's my .xinitrc file.  Is it the right format?  Nothing appears wrong to me, but I'm not sure:
```

#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)
fbpanel

feh --bg-scale /home/austin/buddhau_original.jpg
# invoke global X session script
. /etc/X11/Xsession
```


Also, I was hoping to add the gnome menus to my opoenbox menu, but I'm not sure where the gnome-menu.xml file is.  Do you have any suggestions?  Thanks for the help, sorry I'm clueless.

Austin

---

### Post by Stormy Eyes on 2005-08-07
[QUOTE=dbernar1]Make me a version of the theme without the shades :), if its not too hard. [-o<  [/QUOTE]

Oh, so you want a version without the drop shadows in the text, eh? Well, since you didn't say "please", and phrased it as a command instead of a polite request, you'll have to do it yourself. I don't take orders from strangers.

Open "~/.themes/Martian/openbox-3/themerc" in an editor, go all the way to the end of the file, and change shadows="y" to shadows="n". That'll get rid of the drop shadows in the text.

---

### Post by Stormy Eyes on 2005-08-07
[QUOTE=austinz]Also, I was hoping to add the gnome menus to my opoenbox menu, but I'm not sure where the gnome-menu.xml file is.  Do you have any suggestions?  Thanks for the help, sorry I'm clueless.[/QUOTE]

There is no reason to invoke /etc/X11/xsession. Try this for your .xinitrc file instead:

```

#!/usr/bin/env bash

export OOO_FORCE_DESKTOP=gnome

gnome-settings-daemon &
gnome-volume-manager &
xrdb -merge .Xdefaults &
sh ./.fehbg &

exec openbox
```

And make sure to run **ln -sf ~/.xinitrc ~/.xsession** to create a shortcut to .xinitrc that GDM will recognise.

As for the GNOME menu in Openbox, as far as I know, the GNOME menu isn't compatible with Openbox's format and can't be imported

---

### Post by dbernar1 on 2005-08-16
Hey, thanks a lot, Stormy Eyes. That is great that it can be done...

You know what happened with the please I think...

The last smiley, that is shown in text, instead of picture, is a smiley that has his hands in the please way... check him out under more under the smileys, he is the last/bottom one on the right...

So, yeah, sorry about that...please and thank you a lot. This will make the theme even better for me.

dabaR \\:D/

---

### Post by dbernar1 on 2005-08-16
Yay! :) ... :-/ :D

---

### Post by John.Michael.Kane on 2005-09-08
Stormy Eyes could you explain how i could use openbox alone with out the use of gnome. please! since you said it can be used alone.. thanks

---

### Post by Name on 2005-09-08
so I ran the install. Everything looked as documented here but when I closed my terminal window gnome panel died. No biggie in another term window I ran killall gnome-panel and it appeared but the panel that listed then windows I had open was not showing anything also in the individual windows the x [] _ were gone. I tried to killall openbox but got a message that there was no process to kill...


Am I missing something? Before I closed the term window however everything worked fine and it was fast...

Id really like some help with this because my only real complaint thus far was the desktop speed and it appears openbox can fix that if I can get it to work after closing the term window.

---

### Post by Name on 2005-09-08
NM I figured it out. I was running it from the terminal, once I ran it from the run box on the menu all was good. 

Very fast...

---

### Post by idn on 2005-09-23
I am having trouble getting the menu to work. When i middle click all I get is the change worksace menu nothing else. Im kinda stumped, any dieas?

---

### Post by anatole on 2005-10-04
first of all, thank you for this really nice howto! openbox is really smart :)

i have two questions:

1. what should i use for the windows keys and that "other button right to the winkey on the right"? the manual said "W" is for winkeys... if i bind something to "W", pressing 'w' will execute the job...

2. it was stated previously that if you don't have nautilus to draw the desktop, you'll have the openbox menu. this may not be the best place to ask this, but how to do that, without disablig other gnome thingies like gnome-panel, startup scripts and stuff?

thanks for the help in advance :)

---

### Post by anatole on 2005-10-09
[QUOTE=anatole]first of all, thank you for this really nice howto! openbox is really smart :)

i have two questions:

1. what should i use for the windows keys and that "other button right to the winkey on the right"? the manual said "W" is for winkeys... if i bind something to "W", pressing 'w' will execute the job...

2. it was stated previously that if you don't have nautilus to draw the desktop, you'll have the openbox menu. this may not be the best place to ask this, but how to do that, without disablig other gnome thingies like gnome-panel, startup scripts and stuff?

thanks for the help in advance :)[/QUOTE]

i figured out the first one, when used alone, those buttons are referred as Super_L, Super_R and Menu. still, a solution for the second problem would be nice :) i'm really tired of nautilus.

---

### Post by rhino on 2006-01-03
I'm having the same issue.  The context menu key (for those who dont know its the one on the lower right hand side usubally next to ctrl or alt) is some what usless so I bind it to launch a terminal. I've done a fair amount of googling on this and cant seem to find a soluton. xev says that the key name is "Menu" so i tried somting like ....


<keybind key="Menu">
    <action name="execute"><execute>gnome-terminal</execute></action>
</keybind>

But no dice.

Any Ideas ?

Thanks,

---

### Post by tafsen on 2006-01-06
How can I make the Start button + D minimize all windows?

---

### Post by sampoerna on 2006-03-19
[QUOTE=tafsen]How can I make the Start button + D minimize all windows?[/QUOTE]
Try this:
  <keybind key="W-d">
    <action name="ToggleShowDesktop"/>
  </keybind>

as stated in the [manual]("http://icculus.org/openbox/docs.php?page=details.html&PHPSESSID=cdc91a019a7ef2bb0c567656a56126f9") 'W'
is the key for the 'windows' key

however
[QUOTE=rhino]<keybind key="Menu">
<action name="execute"><execute>gnome-terminal</execute></action>
</keybind>

But no dice.[/QUOTE]

in above case, if we change the key to <keybind key="W"> then it will invokes the action whenever the key 'w' is pressed, instead of the 'window' key.

So i guess these key bindings only works in combination, otherwise it will be
taken as a single alphabetic key press on keyboard
This applies to the keys below as well:
> 
S - the Shift key
C - the Control key
A - the Alt key

---

### Post by macro on 2006-05-13
I want to switch to openbox, but each time I do Gnome-Panel displays a single "Untitled Window" for my applications I have running... rather than a single entry per window.

I've tried "killall gnome-panel" to get it to refresh but didnt help. I've heard its best to swtich to a different panel system but I dont know which to go for, and I'm too inexperienced to know how to configure it.

FYI I'm using Dapper, with dist-upgrade for the latest versions of everything, I don't know what log files to supply or anything so tell me what would be helpfull and i'll supply it :-)

As soon as I solve this I will switch over.

Anyone had a problem similar to this? How did you solve it?

---

### Post by jonrkc on 2006-07-01
[QUOTE=macro]I've heard its best to swtich to a different panel system but I dont know which to go for, and I'm too inexperienced to know how to configure it.
...
As soon as I solve this I will switch over.
...
Anyone had a problem similar to this? How did you solve it?[/QUOTE]
I don't use Gnome Desktop, but I do (sometimes) use Openbox, and I wanted a panel for it.  I found fbpanel and am using it.  (sudo apt-get install fbpanel)

It's a good panel with not many options; one nice feature is a button for showing desktop OR shading all windows, depending on whether you left-click or middle-click on it.  

The only thing I dislike about fbpanel is that it does not have auto-hide--or any kind of hide.  :)  Otherwise, it's fine.

---

### Post by patrick295767 on 2006-11-30
I use gnome-panel as panel
it s highly configurable

concerning the edge resistance and so on.., for when will it be possible to have it ? 

some ideas ? 
Metacity was missing it too for gnome

---

### Post by patrick295767 on 2006-11-30
> **SD-Plissken said:**
> Stormy Eyes could you explain how i could use openbox alone with out the use of gnome. please! since you said it can be used alone.. thanks

```
sudo apt-get -f -y install openbox obconf

openbox --replace
```

---

### Post by mikegabriel on 2007-01-05
Hello,  Installed Clearbox following the instructions on the first post.  Now when I go to open Obconf, it shows Starting Obconf in my panel and then disappears and does not load anything. 

Ideas?

---

### Post by happy-and-lost on 2007-01-07
```
jo@mithos:~$ obconf 
obconf: error while loading shared libraries: libobrender.so.1: cannot open shared object file: No such file or directory

```
:???:

Never mind! Problem solved by compiling ObConf from source

---

### Post by vicarious on 2007-01-10
I'm using Openbox with Gnome (openbox --replace). I have gnome-panel running at the top of the screen. For whatever reason, Openbox sometimes places new windows so that the titlebar is underneath gnome-panel. I have to grab these windows with Alt-Left Mouse Click to pull them out of there. Evolution does this a lot.

Does anyone else have this problem and know of a real solution (obviously, I could just move the panel to the bottom of the screen, but I don't want to :) )

I've used other panels with Openbox in the past and they usually had the option "set partial struts" that prevented this behavior. Does gnome-panel support this hint? Is there something else going on?

---

### Post by vicarious on 2007-01-17
> **vicarious said:**
> I'm using Openbox with Gnome (openbox --replace). I have gnome-panel running at the top of the screen. For whatever reason, Openbox sometimes places new windows so that the titlebar is underneath gnome-panel. I have to grab these windows with Alt-Left Mouse Click to pull them out of there. Evolution does this a lot.

Does anyone else have this problem and know of a real solution (obviously, I could just move the panel to the bottom of the screen, but I don't want to :) )

I've used other panels with Openbox in the past and they usually had the option "set partial struts" that prevented this behavior. Does gnome-panel support this hint? Is there something else going on?
Ok. I just moved the panel to the bottom. I would still appreciate it if anyone had insights on why this happens and which application is at fault. Note that this doesn't always happen with new windows. Usually it's transient windows (i.e. when I compose a new email in Evolution).

---

### Post by mabelrxu on 2007-06-09
> **Juippisi said:**
> ```

<keybind key="A-F1">
   <action name="Desktop"><desktop>1</desktop></action>

```
Pity that it didn't work :\. I have Googled those commands and tried like everything (firstdesktop, GoToDesktop,1 and stuff). I really do like Openbox :).

EDIT: I was thinking, that if I use xfce4-panel with openbox, I may not need that feature at all. I must consider, but thanks anyway :).

double check the <desktop> ... </desktop> section of your rc.xml ... the default names for the desktops are "one", "two", "three", and "four", not 1 2 3 4 ... try using those names instead

I've got a separate problem though ... openbox 3.3 gave me mouse buttons correct, but 3.4 switched my left and right mouse buttons ... :(

---

### Post by urukrama on 2007-06-09
> **vicarious said:**
> I'm using Openbox with Gnome (openbox --replace). I have gnome-panel running at the top of the screen. For whatever reason, Openbox sometimes places new windows so that the titlebar is underneath gnome-panel. I have to grab these windows with Alt-Left Mouse Click to pull them out of there. Evolution does this a lot.

I've had the same in Openbox without Gnome, but only with Opera. Since I've upgraded to 3.4, I haven't had the problem yet, but it could recur later. I don't have a solution for it, unfortunately.

---

### Post by hakki99 on 2007-09-03
I need also some starting help. 
I'm using 7.04 ubuntu and have installed openbox 3.4.

[[IMG]http://img232.imageshack.us/img232/7633/fensternq6.th.png[/IMG]](http://img232.imageshack.us/my.php?image=fensternq6.png)

If I choose out now one theme which I've included already (see picutre) the windows doesnt look like as in the theme self. 

I've black windows, so thats fine for me, but the rest is grey instead of white. 
Have noticed that those grey colors belongs to my Gnome GTK Theme. Also the whole icons and the mouse icon as well.

In my /etc/xdg/openbox/autostart.sh is someting mentioned about:

> # Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi

Thats means that the autostar loads the GTK look. If I put an "#" in front of the lines , the icons are standart as well as the mouse icon.

Now my question, where do I have to make some entrys to change that ?
I would like to get the themes working using obconf.

EDIT: Also I've noticed that in case if I'm starting i.e. rhythmbox, the windows and icons going back immidiately to the GTK Gnome Theme. How can that be ?

---

### Post by urukrama on 2007-09-05
Not sure what your problem is. Are you sure you have the correct gtk2-engines installed? You can also try to set the themes/icons/fonts for gtk using .gtkrc-2.0 and gtkrc-2.0.mine. See [this]("http://ubuntuforums.org/showpost.php?p=2634402&postcount=48") post for more info.

---

### Post by hakki99 on 2007-09-07
As I wrote above, the issue is that if I'm starting just Openbox alone(loggin window), I get the inner windows colors from my Gnome GTK Theme. The border Windows are o.k in oppenbox. just the inner windows does not match. (they are in GTK colors = like in Gnome)

GTK2 is insalled.

Currently I'm working in both "programs" . Just In Gnome or just with Openbox. I want to use in Gnome a different GTK Theme as in Openbox. Currenly thats not the case beacuse of my above mentioned problem. 
To get a clean theme in Openbox I've to change in openbox self , using terminal program ->  switch2, the GTK Theme.  Alright... than it works (I've right border windows and the colors are as in the theme file). But If I'm loggin the next time into Gnome instead of Openbox I see that my Gnome GTK Theme here (especially the colors) has changed to the changes which I've done in openbox before usign switch2.

Reg. my other question . "Why Openbox will appear to Gnome in case if I'm starting rhythmbox or nautilus i.e.".   Alright those applications belongs to Gnome.  The menu.xlm shld be edited with this here. ---> nautilus --no-Desktop or rhythmbox --no-Desktop.

---

### Post by Kangarooo on 2010-06-26
> **Stormy Eyes said:**
> [SIZE=5]_Introduction_[/SIZE]

[SIZE=5]_Fun with Keybindings; or, getting an ALT+Tab that rocks like ninja._[/SIZE]

Openbox's default **ALT+Tab** functionality is a bit limited compared to Metacity, which shows a dialog listing all the open apps on a given workspace similar to Windows. You don't have to settle for Openbox's anemic ALT+Tab. If you're using Openbox, try middle-clicking anywhere on your desktop. You'll see a menu listing each of your workspaces, starting with the first, and each workspace entry will have a submenu displaying the running windows on that workspace, with iconified (minimised) windows in brackets.

It's also possible to bind this menu, which is referred to internally as the "Client List Menu", to any key you like, and then to navigate that menu with your keyboard's arrow keys. Just follow the steps below.

1. Open a terminal and enter the following command:

```
gedit ~/.config/openbox/rc.xml
```

2. Once you've opened up Openbox's config file, scroll down until you see the following text:

```
<keybind key="A-Tab">
    <action name="NextWindow"/>
</keybind>
<keybind key="A-S-Tab">
    <action name="PreviousWindow"/>
</keybind>
```

3. Replace the text shown above with the following text:

```
<keybind key="A-Tab">
    <action name="ShowMenu"><menu>client-list-menu</menu></action>
</keybind>
<keybind key="A-S-Tab">
    <action name="ShowMenu"><menu>client-list-menu</menu></action>
</keybind>
```

4. Save your changes and close the editor.

5. If you're using Openbox as part of GNOME, and Openbox is part of your GNOME session, then typing **killall openbox** at the terminal *should* cause GNOME to restart Openbox for you. If GNOME won't play ball, you should be able to click on the *Applications* menu, select "Run Application", and type "openbox" into the prompt. Or, you could avoid all this by logging out and logging in again. If you're using Openbox on its own, then right-click on the desktop for the main menu, and choose the *Reconfigure* option. Openbox will reread its config file.

By following the above steps, you've modified the keybindings for ALT+Tab and SHIFT+ALT+Tab to bring up the same client list menu that appears when you middle-click on the desktop. You can navigate it using your arrow keys, and press "Enter" to go to a  running app, even if that app is on a different workspace.


in lubuntu its file ~/.config/openbox/lubuntu-rc.xml
and when installed lubuntu-desktop from using xubuntu i dont have gedit.
also making anyway this file rc.xml and putting that in info i got error [IMG]http://kangarooo.times.lv/rc.xml.png[/IMG]
and also nothing changes when i put even that whats in step 3. or step 4.

---

