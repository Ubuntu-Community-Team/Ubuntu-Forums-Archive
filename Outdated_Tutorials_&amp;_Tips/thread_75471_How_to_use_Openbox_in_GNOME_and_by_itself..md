---
title: "How to use Openbox in GNOME and by itself."
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormy Eyes on 2005-10-13
[SIZE=5]_Introduction_[/SIZE]

Metacity, while a fair default, is not the only window manager you can use with GNOME. [Openbox](http://www.openbox.org) is a lightweight, customizable window manager that works either by itself or as a drop-in replacement for Metacity. Its advantages include the ability to switch desktops with the mouse wheel, a built-in, customizable menu that allows stand-alone operation with some GNOME components in order to build a GNOME-like system on low-end gear, and (this is subjective) better looking, cleaner themes that don't depend on resource-intensive pixmaps.

[SIZE=5]_Installation and Basic Usage_[/SIZE]

If you have the Universe repository, all you have to do to install Openbox is enter a command:

```
sudo apt-get install openbox obconf
```

Once you've installed it, you can replace Metacity with Openbox with a single command entered into GNOME's "Run" prompt, which can be accessed by hitting ALT+F2. This prompt used to be reachable through the menu in GNOME 2.10, but the menu item was removed from GNOME 2.12.

```
openbox --replace
```

If you choose to save your session on logout, your next GNOME session will use Openbox as its window manager and not Metacity.

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

The original HOWTO can be found [here.](http://ubuntuforums.org/showthread.php?t=34239). Openbox has not changed much between Hoary and Breezy.

Caveat 0: When running Openbox by itself, running Nautilus without the **--no-desktop** option will cause Nautilus to take over the desktop, trashing your wallpaper and rendering your menu inaccessable. Keep this in mind when hacking your menu.

Caveat 1: This HOWTO may not work with Fluxbox due to possible incompatibility with the EWMH specs and definite lack of a **--replace** switch. Also, their config and menu file structures are not XML-based.

---

### Post by cokehabit on 2005-10-13
will this work on fluxbox? ;)

---

### Post by bdash on 2005-10-14
It depends how fluxbox is compliant with freedesktop wm-spec! If not you can have problems with panels and virtual desktops.

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=cokehabit]will this work on fluxbox? ;)[/QUOTE]

BDash is right about standards-compliance, and I can't guarantee that this HOWTO will work with Fluxbox for two reasons:

1. I don't know if Fluxbox is EWMH-compliant.
2. I do not use or recommend Fluxbox because I consider it slow and clunky.

---

### Post by theine on 2005-10-22
Instead of executing
```
openbox --replace
```
and saving your Gnome session afterwards, you can also put
```
export WINDOW_MANAGER="/usr/bin/openbox"
```
into your ~/.gnomerc

Next time you log into Gnome, openbox will be managing your windows.

---

### Post by joakim2 on 2005-10-23
Anyone know what happened to the theme links? I can't seem to get to the starbreaker server. Does anyone else have the themes to post somewhere?

---

### Post by zafar on 2005-10-23
I'm not sure about those links but I've found a really nice theme, a port of clearlooks. It can be downloaded at [http://hewphoria.com/?p=themes&id=127]("http://hewphoria.com/?p=themes&id=127") .

---

### Post by BoyOfDestiny on 2005-10-24
When I was playing with openbox I noticed obconf would also launch when you go Preferences->Windows (going from memory). 

I think having the other->obconf entry becomes a waste?

---

### Post by Stormy Eyes on 2005-10-24
[QUOTE=joakim2]Anyone know what happened to the theme links? I can't seem to get to the starbreaker server. Does anyone else have the themes to post somewhere?[/QUOTE]

My domain expired. I'm working on getting it re-registered. I apologise for the inconvenience. If somebody wants to provide a temp host and PM me with an email address, I'll be happy to send tarballs.

---

### Post by Stormy Eyes on 2005-10-24
[QUOTE=theine]Instead of executing
```
openbox --replace
```
and saving your Gnome session afterwards, you can also put
```
export WINDOW_MANAGER="/usr/bin/openbox"
```
into your ~/.gnomerc

Next time you log into Gnome, openbox will be managing your windows.[/QUOTE]

I never thought of that. Thanks for mentioning it.

---

### Post by LaSSarD on 2005-10-24
Just a theme suggestion:
[Shady Days [IMG]http://www.uoguelph.ca/~fanguelo/img/shadydays.png[/IMG]]("http://www.uoguelph.ca/~fanguelo/skins/shadydays.tar.bz2")

Screen by epicbard.

---

### Post by oddabe19 on 2005-10-24
also
```

apt-get install openbox-themes
```
includes alot

---

### Post by Stormy Eyes on 2005-10-24
OK. Here's an update for anybody looking for themes hosted at starbreaker.net. I've spoken with my domain name registrar and renewed for two years. It should take 48 hours for the DNS to catch up and point to my site again. You should be able to download themes by Wednesday night, at 6:15PM EST.

---

### Post by rimmer on 2005-10-25
Nice, very nice.

And I'm using it with Gnome at the moment. So how would I go about making openbox the the only WM on my system?, ie, running alone with out gnome in the background. I'm a fluxbox fan but I would like to give this a whirl.

---

### Post by Stormy Eyes on 2005-10-25
[QUOTE=rimmer]Nice, very nice.

And I'm using it with Gnome at the moment. So how would I go about making openbox the the only WM on my system?, ie, running alone with out gnome in the background. I'm a fluxbox fan but I would like to give this a whirl.[/QUOTE]

When logging in, GDM has a "Sessions" menu. You can pick Openbox instead of GNOME from there, but you'll have an extremely bare environment. You might want to refer to the custom X session howto listed in my sig.

---

### Post by Stormy Eyes on 2005-10-26
I've gotten the domain name registration sorted out, so [http://www.starbreaker.net](http://www.starbreaker.net) should be back up, along with all of the themes hosted there. Have fun!

---

### Post by alingatong on 2005-10-28
Stormy eyes, can you elaborate more on using openbox by itself? I want to use it as a stand alone, but i cant seem to configure the menu of openbox. I want to add the menu of openbox when i right click on the desktop.

also how can i put some wallpaper in openbox as a standalone?

thanks in advance.

---

### Post by fortytwo on 2005-10-28
Do you know if this will work for hoary as well?

---

### Post by johannes on 2005-10-30
edit: nevermind...

---

### Post by rimmer on 2005-10-31
alingatong
> also how can i put some wallpaper in openbox as a standalone?

I ain't a expert but what I found was FEH you can get it from the universal repos```
sudo apt-get install feh
```.
When you install it you should find a file in you home dir (hidden) called .fehbg. if you don't find it then run ```
feh --bg-scale FILE name of bg you want
``` from the console and that should create the file and will give you a background to openbox. The next thing to do is read [this]("https://wiki.ubuntu.com/CustomXSession") it will tell you how to get fehbg running from start up.

As for the menu I'm not sure if this is correct, but when I was using gnome I installed the debian menu ```
sudo apt-get install menu
```
```
update menu
```
(I did this in gnome) but when I switched to openbox and right click on the desktop 
the debian menu is there.

As for editing the menu I'm not sure I can't find a menu config file.

This is my experiance ! If there is something missing or wrong with the above then I appologise before hand.

---

### Post by joakim2 on 2005-11-03
On an unrelated note... Does anyone know of an Aqua/OS X like theme for Openbox?

---

### Post by SilentCacophony on 2005-11-03
[QUOTE=rimmer]alingatong


I ain't a expert but what I found was FEH you can get it from the universal repos```
sudo apt-get install feh
```.
When you install it you should find a file in you home dir (hidden) called .fehbg. if you don't find it then run ```
feh --bg-scale FILE name of bg you want
``` from the console and that should create the file and will give you a background to openbox. The next thing to do is read [this]("https://wiki.ubuntu.com/CustomXSession") it will tell you how to get fehbg running from start up.

As for the menu I'm not sure if this is correct, but when I was using gnome I installed the debian menu ```
sudo apt-get install menu
```
```
update menu
```
(I did this in gnome) but when I switched to openbox and right click on the desktop 
the debian menu is there.

As for editing the menu I'm not sure I can't find a menu config file.

This is my experiance ! If there is something missing or wrong with the above then I appologise before hand.[/QUOTE]

Good advice. I also use feh for backdrops, and the debian menu. Minor correction:

Rather than:
```
update menu
```
AFAIK, this is the correct syntax:
```
update-menus
```

Also, since there is no panel/taskbar, some may want to istall one. The ones that I have tried with openbox are fspanel, fbpanel, pypanel, and perlpanel. I believe they are all in the 'universe' repositories for Breezy.

Personally, I like pypanel, because it's simple and more configurable than the fs&fbpanels. Perlpanel looks nice as well, but I din't like the number of dependencies.

As for editing the menu, see:

[Configuring Openbox]("http://icculus.org/openbox/docs.php?page=config.html&PHPSESSID=2e020e69a17cfc32f53b68184c1897d6#menus")


> On an unrelated note... Does anyone know of an Aqua/OS X like theme for Openbox?
I seem to recall a couple that are somewhat similar in the openbox-themes package.

---

### Post by Single on 2005-11-06
How to increase the size of the window title without changing the theme? Setting the font preference from the System menu doens't work anymore.

---

### Post by ispmarin on 2005-11-07
Hello all: I really wants to try openbox, metacity is a little too heavy (even with an amd64 with 1GB of ram and a geforce 6200). So, how can this be done?

Thanks

Ivan

---

### Post by ispmarin on 2005-11-08
Nevermind, I found myself:
metacity --restore

Thanks anyway.

---

### Post by kamagurka on 2005-11-30
What do I have to do to get Openbox's menu when rightclicking on the desktop without ditching gnome? Is there some way of keeping the icons anyway?

---

### Post by ispmarin on 2005-12-01
I dunno...
Problems! My metacity, after restoring it, does not work anymore! I have to kill metacity after the X is up, and then do a metacity --restore... but if I reboot the machine, again I get 10 metacitys trying to open and none working... 
What is happening?

---

### Post by brass on 2005-12-10
how can I get the openbox menu when using the gnome/openbox setup?  right now, I right click and i get gnomes right-click menu.   

I havn't used gnome since '97, and i've been using fluxbox for the last two years.  I'm really impressed with gnome, but I miss being able to switch desktops with mouse wheel, and getting the menu from anywhere on the desktop.  Thanks for the tutorial, now I have desktop wheeling, but I'm still missing my menu.

---

### Post by martibs on 2005-12-22
Hi, I'm just wondering if there's an easy way of converting the gnome-panel main menu into an Openbox menu. The thing is that I want to remove the panel, but still need the shortcuts to the applications in the menu.

---

### Post by Stormy Eyes on 2005-12-29
[QUOTE=kamagurka]What do I have to do to get Openbox's menu when rightclicking on the desktop without ditching gnome? Is there some way of keeping the icons anyway?[/QUOTE]

No. Openbox by itself doesn't concern itself with icons.

---

### Post by ritger on 2006-01-02
Everything works fine after following the how-to, i just have one problem. When using OpenBox the window movement becomes choppy, without OpenBox throwing any errors. Weird thing is, only vertical movement is choppy, horizontal is fine. I've already tried turning off the window snap stuff, which didn't do much. Google also isn't much help. The problem occurs when both replacing Metacity and stand-alone.

Anyone else noticing this problem?

---

### Post by darkfox on 2006-01-07
Just a quick post to say thank you Stormy Eyes - this is a fantastic HowTo.  I followed it, learnt loads about the graphical environment in Linux quickly, and ended up ditching Gnome entirely in the end for a pure OpenBox experience (Gnome's fantastic but I just don't need most of the stuff it gives me, so why wait?!).

---

### Post by tafsen on 2006-01-07
How do I get rid of the drop shadow from the theme mistoden?

---

### Post by lleberg on 2006-01-08
I used this how-to, to try openbox!

Now i do have some problems with it!
Lets start with booting..
I can log in graficly, but nothing starts, openbox does though, because i can windowskey-r to start a terminal (bound it myself), wich is opened in openbox. I start the gnome-panel to have some thing to click on.

If i run a ps aux, i have, among others, but this seems less usual.

```

lleberg  22036  0.0  0.1   7756  1948 ?        Ss   18:19   0:00 openbox restart
lleberg  22038  0.0  0.1   7760  1944 ?        Ss   18:19   0:00 openbox restart
lleberg  22040  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22042  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22044  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart
lleberg  22046  0.0  0.1   7756  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22048  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22050  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart
lleberg  22052  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22054  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22056  0.0  0.1   7760  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22058  0.0  0.1   7756  1928 ?        Ss   18:19   0:00 openbox restart
lleberg  22060  0.0  0.1   7756  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22062  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22063  0.0  0.0      0     0 ?        R    18:19   0:00 [gnome-session]
lleberg  22064  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart

```

And it runs "as usual", without having a real Desktop... could probably start it if i knew how! Can't start gdm, don't know if it's because of this openbox-story, or why it is, but it's there! How could this be?

```
lleberg@Margit:~$ /etc/init.d/gdm start
 * Starting GNOME Display Manager...               [fail]
```

How do i.. undo all that has been done? ;)

Edit: "Undo, redo, or if you change your mind, you can redo what you last undid!" <- that takes me back to the days with.. some picturing-game i had when i was little.

Edit2: gnomepanel wasn't exactly.. flawless!

```
lleberg@Margit:~$ gnome-panel

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed
/usr/lib/gnome-app-install/AppInstall.py:196: GtkWarning: gtk_accel_label_set_ac cel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NU LL' failed
  LaunchpadIntegration.add_items (widget, -1, False, True);

(synaptic:15974): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:15974): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:15974): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(services-admin:28166): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!

```

---

### Post by marteus on 2006-01-14
[QUOTE=tafsen]How do I get rid of the drop shadow from the theme mistoden?[/QUOTE]

You can edit the ~/.themes/Mistodon/openbox-3/themerc

in section !! font me! (line 109) edit (or perhaps just remove) :shadow=y:shadowoffset=3 from each item

---

### Post by kuad on 2006-02-27
Hello I'm trying to use .xsession to have openbox working by itself. Below is my .xsession. I think gnome-settings-daemon is interfering (not sure of a better word) with pypanel and conky loading. Once I log in, I see the standard Ubuntu brown screen and then conky appears, except the fonts are very small. AFTER this I *believe* gnome-settings-daemon finishes loading because my wallpaper as in Gnome then appears, but this covers up conky, even though gnome-settings-daemon is before conky in .xsession. Note that pypanel doesn't even appear to load!

I know the fonts are related to gnome-settings-daemon because if I manually start pypanel or conky later, the fonts look as they do in Gnome. But if gnome-settings-daemon isn't running then the fonts look small on both.

I have changed around the order of the entries in .xsession but to no avail. Pypanel doesn't want to load and conky always shows up with small fonts. I've resorted to not attempting to run pypanel and conky from .xsession and am manually starting them.

So my problems are: getting pypanel to run and getting the fonts for both pypanel and conky to look "normal". Some help please?

I'm a noob so go easy on me.

```
gnome-settings-daemon &
gnome-volume-manager &
pypanel &
conky &

exec openbox
```

PS Openbox is cool, once I get round to it I'll post some Openbox scripts that I've hacked together as part of my learning experience.

---

### Post by Stormy Eyes on 2006-02-27
Try adding "sleep 10s" to your script. Put it right after the "gnome-settings-daemon &" call.

---

### Post by kuad on 2006-02-28
[QUOTE=Stormy Eyes]Try adding "sleep 10s" to your script. Put it right after the "gnome-settings-daemon &" call.[/QUOTE]

Thanks Stormy Eyes that worked. Actually I tried "sleep 1s" and it still worked.

-------------
Attached is my first python script. It'll generate an Openbox pipe menu to list all the graphic files in a directory and you can choose which to set as the background. I wrote it mostly because I wanted to use Openbox by itself but still be able to change the wallpaper. Since I was running gnome-settings-daemon anyway, I figured I could use gconftool to set the wallpaper. More details are in the file.

gnome-settings-daemon must be running.

---

### Post by Sutekh on 2006-04-11
Hey thanks a lot for this HOWTO Stormy Eyes!  

I installed Openbox on a fresh install of Dapper to have a play around and its flippin fantastic!   Running feh to cover the desktop, fbpanel, xterm, quod libet and at the moment that's about it.

My hardware is a bit of overkill, but I really love the speed and ability to customise.

My only question (at this stage) is how can I change the themes of GTK apps, without installing gnome-settings?

Cheers,

---

### Post by hugmenot on 2006-04-14
[QUOTE=Sutekh]Hey thanks a lot for this HOWTO Stormy Eyes!  

I installed Openbox on a fresh install of Dapper to have a play around and its flippin fantastic!   Running feh to cover the desktop, fbpanel, xterm, quod libet and at the moment that's about it.

My hardware is a bit of overkill, but I really love the speed and ability to customise.

My only question (at this stage) is how can I change the themes of GTK apps, without installing gnome-settings?

Cheers,[/QUOTE]


Install gtk-theme-switch!

---

### Post by Sutekh on 2006-04-14
[QUOTE=hugmenot]Install gtk-theme-switch![/QUOTE]
Beautiful!  Thanks for that.  I also found [gtk-chtheme](http://plasmasturm.org/code/gtk-chtheme/), both work great.

I don't suppose you know how to change the GTK theme of applications opened by sudo, ie Synaptic?  It sill has an ugly GTK theme.

---

### Post by hugmenot on 2006-04-16
[QUOTE=Sutekh]Beautiful!  Thanks for that.  I also found [gtk-chtheme](http://plasmasturm.org/code/gtk-chtheme/), both work great.

I don't suppose you know how to change the GTK theme of applications opened by sudo, ie Synaptic?  It sill has an ugly GTK theme.[/QUOTE]

I don't know. You could try &#8220;sudo -i gtk-theme-switch2&#8221;. -i changes to user's home first.

---

### Post by Sutekh on 2006-04-18
[QUOTE=hugmenot]I don't know. You could try “sudo -i gtk-theme-switch2”. -i changes to user's home first.[/QUOTE]
Of course that was obvious.  Thanks for the helping hand

---

### Post by greenwom on 2006-05-01
The how-to worked great but I wanted to go back.  
I ran 
```
metacity --replace
```

but now when I restart the computer GDM hangs when loading metacity....  Any clue?

---

### Post by RenZO on 2006-05-15
Yeah, great howto !
I'm using openbox with gnome. However, I've a little problem : when i use the display desktop button, in order to iconify all windows, it works. But if now I choose one window, it displays on first plan, but with all other windows in second plan !!

Is it possible to NOT restore all windows after displaying desktop ?
I'm french, sorry for syntax.

Thanks
RenZO

---

### Post by oss_monkey on 2006-07-21
Thanks for the tutorial, Stormy Eyes! I'm on OpenBox and I wonder what I've been doing with all that resources I've freed up.

I've got question, though.

Is there a repository of "toys" to put in the now-bare desktops? I mean, what would I need to get something like this:
[http://offload1.icculus.org/openbox/shots/full/cronos.jpg](http://offload1.icculus.org/openbox/shots/full/cronos.jpg)

Pretty impressive, IMHO.

I'll be installing gdesklets and fbpanel and see where I go from there. :)

---

### Post by Somenoob on 2006-12-06
Is it just me or is Open Box functioning improperly on Edgy? for example not being able to open ObConf and it crashes sometimes.

---

### Post by burek on 2006-12-08
I dont reply exactly but do u know:
kwin-baghira - KDE theme for Apple junkies :)

---

### Post by burek on 2006-12-08
> **joakim2 said:**
> On an unrelated note... Does anyone know of an Aqua/OS X like theme for Openbox?

I am looking too; what did you find the best one or closest one ?

---

### Post by patrick295767 on 2006-12-09
A very nice link about openbox:
[B]
[http://doc.gwos.org/index.php/Openbox_GnomeStraight](http://doc.gwos.org/index.php/Openbox_GnomeStraight)[/B]

---

### Post by Blindraven on 2007-10-04
> **Stormy Eyes said:**
> 
2. I do not use or recommend Fluxbox because I consider it slow and clunky.

That has got to be the most grosely profounded elitest statement I have seen on this, or any other linux forum to DATE.

Two thumbs WAY UP for effort on that one mate, 
Whats next, using vi for machine-code? ahh **** it, just C++ your own TE and go for gold.

I bet you used wcm or lynx to make that post. 


I'm speechless. (the thank god sentiment is used and tried, try - for allaah's kebabs sake, to be a little bit more original).

---

### Post by darkfox on 2007-10-04
Ah well: choice.  Freedom of thought and expression.  Its where we derive our strength.  You've got yours, he's got his.  'Nuff said?

---

### Post by Blindraven on 2007-10-04
> **darkfox said:**
> Ah well: choice.  Freedom of thought and expression.  Its where we derive our strength.  You've got yours, he's got his.  'Nuff said?

Ye, but when I grew up I was taught that If I didn't have anything nice to say, to keep it to myself. Maybe thats just an Australian thing, but there is** no** fine line between the freedoms of expression and irrational bias recommendations, its obvious.


If his post was "I don't like flux box for X & Y reasons" I'd have said less, though still put forward my 4th amendment, however, it was also a little bit more prejudiced than that and I simply cant stand people that probably don't have the first idea about WM's scrutinizing against them for the sake of sounding elite or, in this profoundly whack case, comparing an ant to an equal sized flee and asserting that the ant is somehow "sluggish" in comparison to its equally speedy counter-part.

People read the "built from the gound up and bla bla" crap and immediately think its something godly - or that it somehow implicates "trueness", wherein fact the exact demographic of openbox is the elitest community, knowing that making a WM with absa.fukin.loutely.nothing to work with but a menu from the get-go would appeal to the "hard-core"

So sure, working of your proportionated statement about, funnily enough, opinions - theres mine own for you.

:KS:KS

---

### Post by MetalMusicAddict on 2007-10-04
> **Blindraven said:**
> Ye, but when I grew up I was taught that If I didn't have anything nice to say, to keep it to myself.
Didnt you just do the same thing with your post? And you felt the need to respond in this way to a thread that hasnt had a post to it in almost a year? By a user who no longer comes to the forum?

Come on. I know you have better, more productive things to do. ;)

---

### Post by Blindraven on 2007-10-04
> **MetalMusicAddict said:**
> Didnt you just do the same thing with your post? And you felt the need to respond in this way to a thread that hasnt had a post to it in almost a year? By a user who no longer comes to the forum?

Come on. I know you have better, more productive things to do. ;)

Ye, my fiances sister just kicked my *** in dead or alive.
Not happy.

---

### Post by darkfox on 2007-10-04
Well I don't see the picture you paint.  I'm not too technical, or elitist.  I run Gnome on my reasonably fast desktop but OpenBox on my ancient laptop because Gnome or KDE are just too heavy for it.  I don't know which 'box is better, in fact I suspect that their set of plusses and minuses largely overlap, but it is thanks to an excellent HowTo written by StormyEyes a couple of years ago that I was able to get any productivity out of the laptop.  The point is that the Openbox community has always been courteous and helpful to me even though I'm no uber-geek, and I'm wondering what it is that you are frightened of here?

---

### Post by Blindraven on 2007-10-04
> **darkfox said:**
> Well I don't see the picture you paint.  I'm not too technical, or elitist.  I run Gnome on my reasonably fast desktop but OpenBox on my ancient laptop because Gnome or KDE are just too heavy for it.  I don't know which 'box is better, in fact I suspect that their set of plusses and minuses largely overlap, but it is thanks to an excellent HowTo written by StormyEyes a couple of years ago that I was able to get any productivity out of the laptop.  The point is that the Openbox community has always been courteous and helpful to me even though I'm no uber-geek, and I'm wondering what it is that you are frightened of here?


Where in any post on this forum have I put forward the notion that I was frightened?

This was a classic case of someone running down a WM, my saying "Is that really necessary" and someone else, (you), trying to subtly prove it is.

So again, its not.
And you are correct, all WM's have their +'s and _'s - but that is no reason to go around telling people "So and so is sluggish and horrible and I wildly refute any recommendation on its behalf" - because thats trolling, not posting.

Thanks.

---

### Post by Super Jamie on 2008-06-13
Thanks to the OP for the Howto and intro to Openbox.

I can't believe I've been missing out on this amazingly light yet powerful window manager for so long!

Could someone give an example of how to get a pipe menu script running? Perhaps paste the code from one of your working scripts? I've read the Openbox FAQ but don't really understand where the script files need to go, or how I call them to produce the piped menu text.

---

### Post by urukrama on 2008-06-13
This howto is quite outdated. Recent Openbox versions have a lot more features. For a more up to date and comprehensive guide, see the link in my signature.

You would put pipemenu scripts in your openbox configuration folder (~/.config/openbox/). Many pipe-menus tell you in the script itself (at the top of the file) how to use them (it differs from script to script).

---

### Post by dominiquec on 2008-06-24
Just discovered the minimalist beauty of OpenBox and am running it on 8.04.  One problem, though: can't seem to find any good documentation on getting sound to work.  Installed ALSA and it recognizes my sound card, so that doesn't seem to be the problem.  Couldn't make heads or tails of the PulseAudio stuff.

Any suggestions how I might get sound working?

---

### Post by alphane on 2008-06-24
In terminal type: alsaconfig

Make sure that all audio levels are up and not muted (MM = mute) press "m" to unmute.  

That was my problem on a recent Openbox install.

---

### Post by dominiquec on 2008-06-24
Thanks, but I can't seem to find alsaconfig in any of the packages.  As I understand, it was removed; am I correct?

Can you give me a list of all the packages that I need to install?

---

### Post by urukrama on 2008-06-25
You need [alsa-utils]("http://packages.ubuntu.com/hardy/alsa-utils"). Then unmute the audio channels through "alsamixer" (not alsaconfig) as described by alphane.

---

### Post by dominiquec on 2008-06-25
Tried that, but no such luck, though.

alsa does recognize the card, as I can see it in the alsamixer output.  Already unmuted and maxed out all the available controls but still no sound.

I suspect this has little to do with OpenBox, though.  I tried the command line music123 but still no output.

Under a normal Ubuntu desktop installation, I do get sound; it's in the bare-bones command-line (+ OpenBox) that I'm not getting anything.

---

### Post by antofthy on 2009-04-13
> **kamagurka said:**
> What do I have to do to get Openbox's menu when rightclicking on the desktop without ditching gnome? Is there some way of keeping the icons anyway?

Add a modifier to the binding so that it will not interfer with the normal menu of the 'root' display.

```
  <mouse>
    ...
    <!-- Gnome Desktop : Menus may not work -->
    <context name="Desktop">
      ...
      <mousebind button="W-Right" action="Press">
        <action name="ShowMenu">
          <!-- This is an OpenBox version of the Gnome Main Menu -->
          <menu>root-menu</menu>
        </action>
      </mousebind>
      ...
    </context>
    ...
  </mouse>
```
Now pressing the right mouse button while holding the "SUPER" key will pop up the menu.

---

### Post by antofthy on 2009-04-13
> **Stormy Eyes said:**
> Try adding "sleep 10s" to your script. Put it right after the "gnome-settings-daemon &" call.

Is their some way of determining when gnome-settings-daemon has finished mucking around with the system  It stuffs up my own X resources and other settings and I want to restore things correctly when it is finished!

---

### Post by antofthy on 2009-04-13
**Very Advanced Fun with Keybindings: Keyboard Macro Expansion.**

EG: Press a function key and the WM expands it to a Email Address or URL


First install the 'xautomation' package so you can get the 'xte' command to programmically generate keyboard bindings.

Now add (or replace) some extra keybindings, modify to suit...

```
    <keybind key="W-F1">
      <action name="Execute">
        <command>xte 'usleep 500000' \
                     'str A.Thyssen@griffith.edu.au'</command>
      </action>
    </keybind>
    <keybind key="W-F2">
      <action name="Execute">
        <command>bash -c "xte 'usleep 500000' \\\
               'str http://www.cit.gu.edu.au/'`printf '\176'`'anthony/'"
        </command>
      </action>
    </keybind>
```

Now when you reconfigure openbond.  Press Super-F1 and quickly release BOTH keys.   A monent later the email address will be printed.

The beauty is that it will do this int ANY normal input, even horrible programs that do not understand normal copy-paste handling!

The Second defintion is a URL to my home page.  the special '`printf '\176'`'  syntax is to insert a '~' character into the command without OpenBox trying to expand it into my 'home directory' Arrrgghhhh...


For reasons why the 'usleep' is needed see my page on X Window Event handling...
  [http://www.cit.gu.edu.au/~anthony/info/X/Event_Handling.txt](http://www.cit.gu.edu.au/~anthony/info/X/Event_Handling.txt)

ASIDE: I created that URL using that macro :-)

---

### Post by theZoid on 2009-09-10
> **theine said:**
> Instead of executing
```
openbox --replace
```
and saving your Gnome session afterwards, you can also put
```
export WINDOW_MANAGER="/usr/bin/openbox"
```
into your ~/.gnomerc

Next time you log into Gnome, openbox will be managing your windows.

Does anyone have an update for this with Jaunty gnome as this doesn't work anymore.  thanks as I can't find the right file for this.

---

### Post by Cortux on 2009-10-07
When I do the --replace, i get this:

(openbox:5174): Openbox-WARNING **: Openbox is configured for 4 desktops, but the current session has 1.  Overriding the Openbox configuration.
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"


Please help

---

### Post by Pirolocito on 2009-10-08
Openbox is very nice, i'll recommend it!!!

[http://linuxmadeasy.blogspot.com/2009/10/openbox-nice-and-lightweight-windows.html](http://linuxmadeasy.blogspot.com/2009/10/openbox-nice-and-lightweight-windows.html)

---

### Post by kevinguillorytraining on 2009-10-09
I am unable to open themes website. Is there any alternative website? I am using OpenDNS

---

### Post by johnnyhostile on 2009-12-13
> **theZoid said:**
> Does anyone have an update for this with Jaunty gnome as this doesn't work anymore.  thanks as I can't find the right file for this.

Don't know if you still need this, but I achieved this by editing ~/.dmrc as follows:

```
[Desktop]
Session=openbox
```

---

### Post by jonobe on 2010-08-27
> **Cortux said:**
> When I do the --replace, i get this:

(openbox:5174): Openbox-WARNING **: Openbox is configured for 4 desktops, but the current session has 1.  Overriding the Openbox configuration.
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"


Please help

I've got exactly the same problem in Ubuntu 10.04.
Any ideas, any one?

---

### Post by urukrama on 2010-08-29
> **jonobe said:**
> I've got exactly the same problem in Ubuntu 10.04.
Any ideas, any one?

This is really nothing serious. It only means that Openbox is configured (in the ~/.config/openbox/rc.xml configuration file) to have four workspaces but that your current session is set up to only have one, so Openbox will only use one workspace. Openbox allows other programs to override these settings, and will work fine with everything else.

Generally this means that your pager plugin in your panel is configured to only have one workspace. If you want to use more workspaces, you will have to tell Gnome to use more workspaces.

This guide is very outdated, by the way. If you install Openbox from the repositories, you should be able to login to a Gnome/Openbox session at the login screen and not have to switch to Openbox in Gnome with the *openbox --replace* command.

---

### Post by politenessman on 2010-12-10
Guess I am kind of late to this party - I've been playing with openbox and I like it a lot. I especially like the right click apps menu, but having gone though this process, I find myself with a working desktop (great!) which does seem to be using openbox, but my right click menu looks exactly the same as it was under gnome.

What do I need to do to get the openbox right click menu?

---

