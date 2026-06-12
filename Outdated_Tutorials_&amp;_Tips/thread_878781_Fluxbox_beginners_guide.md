---
title: "Fluxbox beginners guide"
date: 2008-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by billgoldberg on 2008-08-03
This &#8220;guide&#8221; is meant for people who already have Ubuntu installed. Not for people with a server install.

It&#8217;s aimed at people new to Fluxbox and is meant to help them getting started.

Before you think about installing it beware Fluxbox isn&#8217;t exactly the most user friendly wm. So if you are having trouble with xfce/gnome/kde this won&#8217;t be for you.

On the other hand, if you are bored with those, by all means try Fluxbox.

-----

**1. Installation**

Open up your favorite cli client and use apt to install it for you.

```
sudo apt-get install fluxbox
```

**2. Start Fluxbox**

Log out and start Fluxbox (press the &#8220;session&#8221; button).

**3. Usage**

You open up the menu by right-clicking the background.

The menu will be made automatically when you installed it, so all your programs should be in there under &#8220;applications&#8221; and the various sub menu&#8217;s.

Have a look around.

You can&#8217;t display icons on the desktop. However there are ways around that.

**4. Shortcuts**

The config file for shortcuts is in /home/username/.fluxbox/keys .

Open it.

You should already see some shortcut, so learn them or modify them to your liking.

Before you start adding new ones, you&#8217;ll need to know this:

> Mod1 == Alt
Mod4 == Windows key
Control == Ctrl
Shift == Shift

So a short cut for &#8220;alt+f1&#8243; would be &#8220;Mod1 F1&#8243;.

Besides those keys, the rest is as you would expect.

I find it easy to assign programs to the function keys.

Because I do so, I hardly ever need to use the right-click menu and it saves me a lot of time.

This is my keys file:

    > OnDesktop Mouse1 :HideMenus
    OnDesktop Mouse2 :WorkspaceMenu
    OnDesktop Mouse3 :RootMenu
    OnDesktop Mouse4 :NextWorkspace
    OnDesktop Mouse5 :PrevWorkspace
    Mouse8 :NextWorkspace # top side button mouse -> next workspace
    Mouse9 :PrevWorkspace # bottom side button mouse -> prev workspace

    Mod1 Tab :NextWindow
    Mod1 Shift Tab :PrevWindow

    # Launch programs

    F12 :ExecCommand xterm # opens a cli client
    F11 :ExecCommand firefox # opens the firefox webbrowser client
    F10 :ExecCommand thunar # opens the thunar file manager
    F9 :ExecCommand mousepad # opens the mousepad text editor
    F8 :ExecCommand sonata # opens the sonata music player
    Mod1 F2 :Exec fbrun # opens a &#8220;run&#8221; dialog window, similar to &#8220;alt+f2&#8243; in gnome

    # Media keys

    #    System Volume
    F2 :Exec amixer sset Master,0 5%- # raise volume by 5%
    F3 :Exec amixer sset Master,0 5%+ # lower volume by 5%
    F4 :Exec amixer sset Master,0 toggle # mute volume

    #    MPC (music player command for music player deamon)
    F6 :Exec mpc next # plays next song in playlist
    F5 :Exec mpc prev # plays previous songs in playlist
    F7 :Exec mpc toggle # pauses or play the song

    # Visual

    F1 :ToggleDecor # removes or adds window decoration

    # Screen shot:

    Control F12 :Exec scrot -e &#8216;mv $f ~/Desktop&#8217; # takes a screen shot of the entire screen

(Exec or ExecCommand is the same)

If you wish to use nautilus, use the "nautilus --no-desktop" command.

**5. Visual improvement**

***5.1 Styles***

There are a few decent Fluxbox styles (right-click -> styles to choose them) but there are much better ones online.

A simple google search will tell you a lot, but I found [http://customize.org/fluxbox](http://customize.org/fluxbox) to be one of the better ones.

After you downloaded the .tar.gz extract it to /home/username/.fluxbox/styles .

After that the style will be available through the menu.

***5.2 Gtk themes***

Most if not all of the apps will use the default ugly grey nautilus colour (the one I reffer to as the win95 theme) and that isn&#8217;t real nice to look at.

There is a nice little program available that will let you set gtk themes for your apps.

```
sudo apt-get install  gtk-chtheme
```

Open it using a terminal and you&#8217;ll be able to pick the gtk themes you installed in /home/username/.themes .

The gtk-chtheme app will even preview the theme for you.

[IMG]http://linuxowns.files.wordpress.com/2008/07/gtk-chtheme.png[/IMG]

***5.3 Wallpaper***

You must have noticed that either you didn&#8217;t have a wallpaper or couldn&#8217;t change the one your theme set for you.

Use this command to set the wallpaper.

```
fbsetbg -f /path/to/image.png
```

***5.4 Conky***

If conky fits anywhere, it&#8217;s on a fluxbox box.

[Installations notes.]("http://linuxowns.wordpress.com/2008/01/18/conky/")

**6. Editing the startup file**

You can add programs/commands in this line to execute at startup.

The text we need is located in /home/user/.fluxbox/startup

It&#8217;s really easy to modify.

The default file looks something like this:

    > # fluxbox startup-script:
    #
    # Lines starting with a '#' are ignored.

    # You can set your favourite wallpaper here if you don't want
    # to do it from your style.
    #
    # fbsetbg -f ~/pictures/wallpaper.png
    #
    # This sets a black background

    /usr/local/bin/fbsetroot -solid black

    # This shows the fluxbox-splash-screen
    # fbsetbg -C /usr/local/share/fluxbox/splash.jpg

    # Other examples. Check man xset for details.
    #
    # Turn off beeps:
    # xset -b
    #
    # Increase the keyboard repeat-rate:
    # xset r rate 195 35
    #
    # Your own fonts-dir:
    # xset +fp $HOME/.font
    #
    # Your favourite mouse cursor:
    # xsetroot -cursor_name right_ptr
    #
    # Change your keymap:
    # xmodmap ~/.Xmodmap

    # Applications you want to run with fluxbox.
    # MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN & AT THE END.
    #
    # unclutter -idle 2 &
    # wmnd &
    # wmsmixer -w &
    # idesk &

    # And last but not least we start fluxbox.
    # Because it is the last app you have to run it with exec before it.

    exec /usr/local/bin/fluxbox
    # or if you want to keep a log:

    dsf
    # exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

Let&#8217;s say you want your wallpaper to be there when you start up your pc instead of having to type the command.

Look for the

> # fbsetbg -f ~/pictures/wallpaper.png

line and remove the &#8220;#&#8221; in front of it. Then adjust the path to point to the actual wallpaper.

Note that in Ubuntu ~/pictures/wallpaper.png won&#8217;t work. Everything in linux in case sensitive so it has to be ~/Pictures/wallpaper.png

Or lets say you want to add conky.

Look for this block of text

    > # Applications you want to run with fluxbox.
    # MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN & AT THE END.
    #
    # unclutter -idle 2 &
    # wmnd &
    # wmsmixer -w &
    # idesk &

And add &#8220;conky &&#8221; to the bottom without an &#8220;#&#8221;.

    Mine looks like this:

    > # fluxbox startup-script:
    #
    # Lines starting with a &#8216;#&#8217; are ignored.

    # You can set your favourite wallpaper here if you don&#8217;t want
    # to do it from your style.
    #
    fbsetbg -f /home/rw/Pictures/wall.jpg
    #
    # This sets a black background

    #/usr/bin/fbsetroot -solid black

    # This shows the fluxbox-splash-screen
    fbsetbg -C /usr/share/fluxbox/splash.jpg

    # Other examples. Check man xset for details.
    #
    # Turn off beeps:
    # xset -b
    #
    # Increase the keyboard repeat-rate:
    # xset r rate 195 35
    #
    # Your own fonts-dir:
    # xset +fp &#8220;/home/rw/.fonts&#8221;
    #
    # Your favourite mouse cursor:
    # xsetroot -cursor_name right_ptr
    #
    # Change your keymap:
    # xmodmap &#8220;/home/rw/.Xmodmap&#8221;

    # Applications you want to run with fluxbox.
    # MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN &#8221;&&#8221; AT THE END.
    #
    # unclutter -idle 2 &
    # wmnd &
    # wmsmixer -w &
    # idesk &
    conky &
    mpd &
    mediatomb &

    # And last but not least we start fluxbox.
    # Because it is the last app you have to run it with &#8221;exec&#8221; before it.

    exec /usr/bin/fluxbox
    # or if you want to keep a log:
    # exec /usr/bin/fluxbox -log &#8220;/home/rw/.fluxbox/log&#8221;

**7. Editing the menu**

Because the menu is automatically generated by ubuntu, you&#8217;ll see that /home/username/.fluxbox/menu points to /etc/X11/fluxbox/fluxbox-menu .

So let&#8217;s copy the content of that last file to /home/username/.fluxbox/menu .

The file is easy once you know what to do.

It basically goes like this:

    > [begin] (Fluxbox)
    [exec] (xterm) {xterm}
    [separator]
    [submenu] (Tools)
    [exec] (Galculator) {galculator}
    [exec] (Gnome Commander) {gnome-commander}
    [exec] (File Roller) {file-roller}
    [exec] (K3B) {k3b}
    [exec] (Gramps) {gramps}
    [end]

    [submenu] (fluxbox menu)
    [config] (Configure)
    [submenu] (Styles) {Choose a Style&#8230;}
    [stylesdir] (/usr/X11R6/share/fluxbox/styles)
    [end]
    [workspaces] (Workspace List)
    [submenu] (Tools)
    [exec] (Window name) {xprop WM_CLASS|cut -d \&#8221; -f 2|xmessage -file - -center}
    [end]
    [commanddialog] (Fluxbox Command)
    [reconfig] (Reload config)
    [restart] (Restart Fluxbox)
    [exec] (About) {fluxbox -v 2>/dev/null | head -n1 | xmessage -file - -center}
    [exit] (Exit Fluxbox)
    [separator]
    [exec] (Reboot) {shutdown -r now}
    [exec] (Shutdown) {shutdown -p now}
    [end]
    [end]

You always start with

    > [begin] (Fluxbox)

    [end]

Everything else goes in there. Kind of like the <html> </html> tags for those familiar with html.

If you want to list a program in the main menu, you use this code:

>     [exec] (xterm) {xterm}

Where (xterm) is the word that will appear in the menu and {xterm} the command to launch the app.

If you want a little separator, use this

>     [separator]

Most likely you&#8217;ll want sub-menu&#8217;s.

You use

    > [submenu] (name you come up with)

    [end]

So between those two, you can use the [exec] to list applications or open another submenu.

The second part of text in the example, is the fluxbox menu.

I didn&#8217;t touch it, but you could throw some things around in there if you like.

Mine looks like this:

> [begin] (Fluxbox)
[exec] (Xterm) {xterm}
[separator]
[submenu] (Tools)
[exec] (File Roller) {file-roller}
[exec] (Mirage Image Viewer) {mirage}
[exec] (Synaptic) {gksu synaptic}
[end]
[submenu] (Internet)
[exec] (Firefox) {firefox}
[exec] (Emesene) {emesene}
[exec] (Transmission) {transmission}
[exec] (Xchat) {xchat}
[exec] (Frostwire) {frostwire}
[exec] (Nicotine Plus) {nicotine}
[end]
[submenu] (Editors)
[exec] (Mousepad) {mousepad}
[exec] (Abiword) {abiword}
[exec] (Gnumeric) {gnumeric}
[end]
[submenu] (Multimedia)
[exec] (VLC Media Player) {vlc}
[exec] (Sonata) {sonata}
[exec] (Brasero) {brasero}
[exec] (Audio Tag Tool) {tagtool}
[exec] (Avidemux) {avidemux}
[end]
[submenu] (Graphics)
[exec] (Gimp) {gimp}
[exec] (Xpdf) {xpdf}
[end]
[separator]
[submenu] (Fluxbox Menu)
[config] (Configure)
[submenu] (Styles) {Choose a Style&#8230;}
[stylesdir] (/usr/X11R6/share/fluxbox/styles)
[end]
[workspaces] (Workspace List)
[submenu] (Tools)
[exec] (Window name) {xprop WM_CLASS|cut -d \&#8221; -f 2|xmessage -file - -center}
[end]
[commanddialog] (Fluxbox Command)
[reconfig] (Reload config)
[restart] (Restart Fluxbox)
[exec] (About) {fluxbox -v 2>/dev/null | head -n1 | xmessage -file - -center}
[exit] (Exit Fluxbox)
[separator]
[exec] (Reboot) {shutdown -r now}
[exec] (Shutdown) {shutdown -p now}
[end]
[end]

It&#8217;s nice and simple.

(watch first screenshot to view menu)

**8. Set your own icons**

Open up /home/username/.gtkrc-2.0 and add this line to it

>     gtk-icon-theme-name = &#8220;ALLBLACK&#8221;

ALLBLACK is the name of the folder containing my icon set in /home/username/.icons .

So just put the name of the theme you extracted there instead of ALLBLACK.

Note you can also set your gtk theme like that instead of using the app.

Use

>     gtk-theme-name = &#8220;NovaBlue&#8221;

for that, where NovaBlue would be the name of the folder containing your gtk theme in /home/username/.themes .

**9. Select your keyboard layout**

You will have to edit your xorg.conf file. Use this command to do so:

```
sudo mousepad /etc/X11/xorg.conf
```

(presuming you use mousepad, if not change to the editor of your liking)

In the first block of text you&#8217;ll see:

> Section &#8220;InputDevice&#8221;
Identifier &#8220;Generic Keyboard&#8221;
Driver &#8220;kbd&#8221;
Option &#8220;XkbRules&#8221; &#8220;xorg&#8221;
Option &#8220;XkbModel&#8221; &#8220;pc105&#8243;
Option &#8220;XkbLayout&#8221; &#8220;be&#8221;

You would change the last one to the keyboard layout you would like.

Mine is now &#8220;be&#8221; (azerty), so change that to yours.

You can put more that one.

You could set

> Option &#8220;XkbLayout&#8221; &#8220;be,us&#8221;

You could then switch between layouts by using the command

Code:

```
setxkbmap be
```

or

Code:

```
setxkbmap us
```

The first command would set your keyboard layout to azerty (be), the second one to qwerty (us).

Now, you could add those commands to your menu by editing your menu file.

Code:

```
sudo mousepad /home/username/.fluxbox/menu
```

You would use the following to add those:

> [exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap us}

But it would be best to add a submenu for changing keyboard layouts.

> [submenu] (Layouts)
[exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap en}
[end]


Then when you right-click your desktop, a mentioning of &#8220;Layouts&#8221; will be there, with the options to load the &#8220;azerty&#8221; or &#8220;qwerty&#8221; keyboard layouts.

&#8211;

Hope this helped.

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;

[[IMG]http://linuxowns.files.wordpress.com/2008/07/flux123.png?w=300&h=240[/IMG]]("http://linuxowns.files.wordpress.com/2008/07/flux123.png")

[[IMG]http://linuxowns.files.wordpress.com/2008/07/screen123465.png?w=300&h=240[/IMG]]("http://linuxowns.files.wordpress.com/2008/07/screen123465.png")

---------

Guide taken from my Ubuntu blog [http://linuxowns.wordpress.com](http://linuxowns.wordpress.com)

---

### Post by hanniph on 2008-08-18
Yay! Indeed nice tutorial for a beginner. Saved me a lot of time. :cool:

---

### Post by billgoldberg on 2008-08-18
Glad you liked it.

---

### Post by Anzan on 2008-08-18
I haven't booted into Gnome once on my main PC thanks to you, billgoldberg.

---

### Post by bobterri on 2008-08-19
My problem is that when I press the right button on my mouse nothing happens.  No menu, nothing.  Any ideas?

---

### Post by banewman on 2008-08-19
> My problem is that when I press the right button on my mouse nothing happens. No menu, nothing. Any ideas?

If that was your first time into fluxbox then ctrl+alt+bksp to logout and log back in and a menu should be there - else just copy the menu file above as a start :)

---

### Post by bobterri on 2008-08-19
I do not have a /etc/X11/fluxbox/fluxbox-menu file.

I have the following files in /etc/X11/fluxbox:

bob@bob-desktop:/etc/X11/fluxbox$ ls
fluxbox.menu-user  init  keys  system.fluxbox-menu

---

### Post by RedSquirrel on 2008-08-19
> **bobterri said:**
> My problem is that when I press the right button on my mouse nothing happens.  No menu, nothing.  Any ideas?
Have a look at the tutorial in my signature. ;)

---

### Post by bobterri on 2008-08-20
Thanks, RedSquirrel.  Your tutorial did the trick.

---

