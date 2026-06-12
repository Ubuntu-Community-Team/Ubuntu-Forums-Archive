---
title: "AwesomeWM - A Brief Introduction"
date: 2008-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by shearn89 on 2008-01-22
**UPDATE - 1st July 2008** This guide is terribly out of date... I'll try and update it soon - the awesomerc syntax has changed completely, but i'm not sure how long it will be before they release awesome-3, which will ruin this guide yet again... for now, post in one of the threads [[link]]("http://ubuntuforums.org/showthread.php?t=689649"), [[link]]("http://ubuntuforums.org/showthread.php?t=642808"), or the [Arch subforums]("http://ubuntuforums.org/forumdisplay.php?f=321") (where most of the awesome users are).

**UPDATE 24/01**: The guide has now been changed for 2.1. It should cover mostly everything - if there's something i missed out, just post at the end.

This guide has been written due to the increase of interest in tiling window managers such as Awesome, WMII, DWM, etc. It does not aim to be definitive, merely a starting point. PM me with questions, or post below. There are a number of other users of WMs like awesome on the forums, so a posted question in the right section should eventually get an answer!

This guide is based on the awesomeWM, but as awesome is a derivative of DWM, it should bear some relevance to both DWM and wmii.

*_Contents*_
1. Introduction
2. Disclaimer
3. Install
4. A brief tour
5. Autostarting
6. awesomerc
7. Statusbar scripts
8. Links


[B][U]1. Introduction

Introduction to Tiling Window Managers[/B][/U]
The window manager you're currently using (most likely gnome, or perhaps xfce or openbox. Or kde. Any of those) will probably be a floating window manager. This means that when a window is created (eg, opening nautilus/thunar), it is either maximised, or it "floats" on the desktop. It can be resized and moved freely. In a tiling window manager (*twm*), the windows are **tiled** on the desktop. For example, if I open my terminal program (urxvt), it opens fullscreen. If I open another one, they take up half the screen each. If I open a third, one will take half the screen, and the other two share the remaining space. This is the essence of a twm.

**_Why awesome is awesome**_
Awesome is a tiling window manager, but (in my opinion, among other things) one of the reasons it is my favourite is that you can set it to run as a normal floating window manager, albeit one whose windows have no borders. This, coupled with its very small size (114kb according to pacman on my system), make it a great choice for someone who doesn't need eye candy, and wants a fast system.

**_2. Disclaimer_**
*A word of warning*
The howto that follows should be totally safe, and in no way harm your system. However, I cannot be held responsible for anything that happens to your system.

**_3. Install_**

So, onto the guide!
NB - all entries in "code" tags should be entered into a terminal, like gnome-terminal or xterm.

**Get awesome...**

1. Install dependencies:
```

sudo apt-get install build-essential libxinerama-dev libxrandr-dev libcairo2-dev libxft-dev libconfuse-dev asciidoc xmlto doxygen

```

Download and compile confuse 2.6 (thanks **mali2297**:
```

cd
wget http://bzero.se/confuse/confuse-2.6.tar.gz
tar xf confuse-2.6.tar.gz
cd confuse-2.6
./configure
make
sudo make install

```

2. Download/install awesome:
```

cd
wget http://awesome.naquadah.org/download/awesome-2.1.tar.gz
tar xf awesome-2.1.tar.gz
cd awesome-2.1
./configure
make
sudo make install
cp awesomerc ~/.awesomerc

```


3. To add an entry to GDM, do the following (thanks to **Gigamo**):

"Just to help you, here is my GDM desktop entry (from when I was still running with GDM, ditched it now :D) (this should be named awesome.desktop and put in /usr/share/xsessions)

```
[Desktop Entry]
Encoding=UTF-8
Name=Awesome
Comment=Log in using the Awesome window manager
Exec=/home/**<username>**/awesome.sh
Icon=
Type=Application
```

where awesome.sh is the file that exec'd all the autostarted applications AND awesome on the end:
```
#!/bin/bash
#AUTOSTARTED APPS AND SETTINGS

#STATUSBAR TEXT

#Launch awesome
sleep 1 && exec awesome
```
Then, make this file executable:
```
chmod +x awesome.sh
```

You can put awesome.sh anywhere you like, but make sure you change the "Exec" line in awesome.desktop to match it.
NB - Gigamo's original code is below, i've simply edited it to save space. He has a nice script for the statusbar which includes a battery level for laptops etc.

If you're not running gdm, then you just need to edit your ~/.xinitrc file (backup first!):
```

cp .xinitrc .xinitrc.old
nano .xinitrc
#remove/comment out any entries for other WMs, and add:
exec awesome

```

4. Restart X, and then use "startx" to launch awesome. 
**For GDM**, simply logout, select awesome from the "sessions", and log back in.

5. Congratulations! Awesome should be sitting on your desktop! Now we'll move onto customising it, and making it really useable.
**NB - **this section was written with awesome-2.0. When i've had a chance to play with awesome-2.1, i'll rewrite it.

_**4. A brief tour**_
Welcome! The bar at the top of the screen is the "status bar", and contains tags (like workspaces), numbered 1 to 9. Next to these is the icon representing what layout you are currently using. Then is a space for the window title, then the status-text at the top right.

**Tags**
Tags are like workspaces, only better! In the awesome configuration file (more info later), you can assign tags to a program, so that it appears on 1, 2, or any number of different tags. So if you open xchat, you could get it to open on its own tag, and on an "internet" tag. Or whatever. They're much more powerful than workspaces.

**Layouts**
Awesome comes with 4 layouts - Right-tile, Left-tile, Maximised, and Floating. Right-tile means that it's in tiling mode, and the right-hand side is the secondary section, where windows that you're not focused on stack. Left-tile is the opposite, so they stack on the left. Maximised is maximised, and Floating is floating! You can also set different tags to be different layouts by default, so you could have a terminal tag which is tiled, a browser tag which is maximised, and an IM tag which is floating.

**Status**
At the moment your status-text won't say anything. Not very helpful. I'll show you how to change it a bit later.


_**5. Autostarting**_
Awesome has no autostart capabilities, so the easiest thing to do is make your own autostart script, call it something like autostart.sh, and add the following to it:
```

#!/bin/bash
sleep 1
conky &
nitrogen --restore

```
Or whatever. I put the "sleep" command in there to make sure that awesome has time to load before anything starts trying to use the desktop etc. I use nitrogen for my wallpapers, you may use something like feh instead, for which replace the nitrogen command with ```
~/.fehbg &
```

Then, to make awesome use your script, edit ~/.xinitrc again, and add this before "exec awesome":
```
/home/user/path/to/script &
```

That should make awesome launch and run all your stuff (conky, feh, etc.)


_**6. .awesomerc**_
All awesome-specific settings are controlled by **~/.awesomerc**, which has a number of different sections.

*general*
This is general settings - in 2.1, you'll need to add the "general" and "colour" sections : mine are included.

*border* is whether or not to show a border around the windows. *snap* is (I think) the number of pixels within which windows will "snap" to edges when floating. I'm not sure what *resize_hints* does. *opacity_unfocused* is used in conjunction with **xcompmgr** to make unfocused windows truely transparent, and the number following it is the percentage. *focus_move_pointer* is to make the mouse follow the window focus. *allow_lower_floats* is to dis/allow windows to be floating underneath other, non-floating windows. *font* is the statusbar font.
```

  general
    {
        border = 1
        snap = 8
        resize_hints = true
        focus_move_pointer = false
        allow_lower_floats = false
        new_become_master = true
        new_get_focus = true
        font = "gelly-8"
    }

```

*colors*
Again, in 2.1, you need to add these:
Fairly self-explanatory, focused/unfocused window default colours, and border colours.
```

    colors
    {
        normal_border = "#000000"
        normal_bg = "#000000"
        normal_fg = "#ffffff"
        focus_border = "#e71b3c"
        focus_bg = "#000000"
        focus_fg = "#e71b3c"
    }

```

*tags*
This is an important section - it controls the names and layouts of the tags along the top left. I have this in my file:
```

tags{ 
	tag term {layout = "tile"} 
	tag opera {layout = "max"} 
	tag max {layout = "max"} 
	tag floats {layout = "floating"}
    }

```
Layout can be "tile","max", "floating", and "tileleft". In 2.1, they have also added "spiral" and "dwindle". Spiral is each window getting smaller, in a fibonacci spiral, dwindle is each window getting smaller towards the corner.

*layouts*
These are simply the icons for the different layouts. You can set them to what you like, but you'll have to make .png files for them.

*statusbar*
position - again, self-explanatory. You can also add "height = <value>" and "width = <value>", if you want a specific h/w.

*taglist*
These are the mouse controls for interaction with the tag list in the top left. Leave them as they are, but read through so you know what they do.
The "Mod4" key is the windows, or super, key. Mouse1 is left click, Mouse2 is right, Mouse3 is middle, mouse4 is wheel-up, mouse5 is wheel-down. 

*tasklist*
the same as taglist - the mouse controls for interaction with the taskbar section.

*textboxes*
This section isn't in there by default, but if you want the status-text to say anything (top right), then add entries here. Each entry is a "widget" which text can be piped to. Loke has a post on it in this thread, a few posts down. I've covered it briefly a bit further down in the "status-text" section.
A typical entry is:
```

textbox mpd
      { text = "mpd" #gets changed by script }

```

*rules*
This is another important section - this is where you "tag" programs, and a typical entry looks like this:
```

rules{
	rule {name="xterm" tags="term"}
	rule {name="firefox" tags="internet"}
}

```


The other two sections are **mouse** and **keys**. These contain all the keybindings that are set by default, so the easiest way to start learning is to read through. There are A LOT of keybindings in there, and the thing to do is try and find the most useful ones and learn them first. 
All mouse related bindings go in *mouse*, and keyboard shortcuts go in *keys*. 
As an example, if you put the mouse in the tags section of the status bar and spin the wheel up, you'll flick through the tags. It doesn't work anywhere else.

You'll want to add some shortcuts for programs here, and the ones i use most regularly are here:
```

keys
{
    key
    {
        modkey = {"Mod4"}
        key = "t"
        command = "spawn"
        arg = "exec urxvt"
    }
    key
    {
        modkey = {"Mod4"}
        key = "o"
        command = "spawn"
        arg = "exec opera"
    }
    key
    {
        modkey = {"Mod4"}
        key = "f"
        command = "spawn"
        arg = "exec thunar"
    }
    key
    {
        modkey = {"Mod4"}
        key = "p"
        command = "spawn"
        arg = "exec pidgin"
    }
#MPC COMMANDS
    key
    {
        modkey = {"Mod4", "Control"}
        key = "space"
        command = "spawn"
        arg = "exec mpc toggle"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Left"
        command = "spawn"
        arg = "exec mpc prev"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Right"
        command = "spawn"
        arg = "exec mpc next"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Up"
        command = "spawn"
        arg = "exec mpc volume +1"
    }
    key
    {
        modkey = {"Mod4", "Control"}
        key = "Down"
        command = "spawn"
        arg = "exec mpc volume -1"
    }
#END MPC

```
The mpc commands are especially useful.
You may find that occaisonally some bindings don't work, or conflict with a program. The only way round it is to change the keybindings. Also, as a note, never launch a program without the "exec" command, as it messes up and you have to log out and edit the .awesomerc file from the console to get it back to normal...


**_7. Statusbar scripts_**
 My section looks like the following:
```

  textbox mpd
            {
                text = "mpd " #to be changed
            }
        textbox gmail
            {
                text = " gmail" #to be changed
            }

```
And the script that pipes text to it:
```

#!/bin/bash
while true
do
echo 0 widget_tell mpd "[mpd: `mpc | head -n1` @ `mpc | grep volume | cut -b8-11`] " | awesome-client
echo 0 widget_tell gmail " [`check_gmail`]" | awesome-client
sleep 10
done

```
This basically goes "echo <screen number> widget_tell <widget name> "text" | awesome-client".
Any script can be used to output to it. The awesome wiki has a few scripts that you can use.

**_8. Links_**
The [website]("http://awesome.naquadah.org/") has more info, and a brief [guided tour]("http://awesome.naquadah.org/doc/setup/"). They also have a link to their wiki, which is good for a few FAQs.
For menus and such, see [the awesome wiki]("http://awesome.naquadah.org/wiki/index.php/FAQ#Is_there_a_program-launcher.2C_menu..._in_awesome.3F").

---

### Post by urukrama on 2008-01-22
It seems awesome is only in the [Hardy repos]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=awesome&searchon=names"), not in the Dapper, Edgy, Feisty or Gutsy repos, shearn89. On Gutsy etc. you'll have to compile from source.

This looks like a decent guide, otherwise. I've never been fond of tiling window managers (I want most of my windows fullscreen), but perhaps I'll give this another try.

---

### Post by Gigamo on 2008-01-23
Great guide already. Also, thanks for the MPC binds. Those are extremely useful indeed :D

---

### Post by shearn89 on 2008-01-23
> **urukrama said:**
> It seems awesome is only in the [Hardy repos]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=awesome&searchon=names"), not in the Dapper, Edgy, Feisty or Gutsy repos, shearn89. On Gutsy etc. you'll have to compile from source.

This looks like a decent guide, otherwise. I've never been fond of tiling window managers (I want most of my windows fullscreen), but perhaps I'll give this another try.

Blast - okay, edits coming up! Thanks though!

EDIT: changes made, just need to check the dependencies... And run it through myself! Maybe i'll set up an "AweBuntu" machine...

---

### Post by Gigamo on 2008-01-23
> **shearn89 said:**
> Blast - okay, edits coming up! Thanks though!

EDIT: changes made, just need to check the dependencies... And run it through myself! Maybe i'll set up an "AweBuntu" machine...

Just to help you, here is my GDM desktop entry (from when I was still running with GDM, ditched it now :D) (this should be named awesome.desktop and put in /usr/share/xsessions)

```
[Desktop Entry]
Encoding=UTF-8
Name=Awesome
Comment=Log in using the Awesome window manager
Exec=/home/gig/awesome.sh
Icon=
Type=Application
```

where awesome.sh is the file that exec'd all the autostarted applications AND awesome on the end:

```
#!/bin/bash
xsetroot -bg black
export OOO_FORCE_DESKTOP="gnome"
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
eval `dbus-launch --sh-syntax --exit-with-session`
fi

xcompmgr -cC -t-3 -l-5 -r5 &
urxvtd -o -q -f &
thunar --daemon &
gnome-settings-daemon &
update-notifier &
nitrogen --restore &
restricted-manager --check &
trayer --expand true --widthtype request --transparent true --alpha 255 --edge bottom --align right &
/opt/wicd/tray.py &
(sleep 7 && urxvt -e screen) &

while true
do
    sleep 10
    echo "0 setstatustext [MPD: `mpc | sed -n '1p'`] :: `mpc | grep "#" | cut -c 1-9` :: [Bat: `sh 'readbattery.sh'`] :: [`date '+%A %d/%m/%Y %H:%M'`]"
done | awesome-client &

sleep 1 && exec awesome
```

---

### Post by shearn89 on 2008-01-23
excellent - thanks a lot Gigamo. I'm also putting a warning about 2.1 on here, as it could scare people away from awesome given how tricky it is...

---

### Post by ~LoKe on 2008-01-23
In Awesome 2.1m, which you linked to, the ~/.awesomerc is completely different.  Also, I feel I should make a note on the subject of setstatustext.  Well, it's gone.

This is how you'd do it now:
```
while true
do
echo 0 widget_tell mpd "[MPD: `mpc | sed -n '1p'`] :: `mpc | grep "#" | cut -c 1-9`" | awesome-client
echo 1 widget_tell clock "[`date '+%a %b %d %r'`]" | awesome-client
sleep 1
done
```

Now, because that doesn't make any sense, I feel the need to explain it.  Awesome 2.1 has support for multiple widgets, so now you can change the text on a lot of different things than before (it used to be only at the end of the status bar).  Basically, "widget_tell", as the name implies, tells the widget something.  In this case, we're telling the widget named "mpd" to echo the song information on screen 0.  That means we need a widget named mpd in our ~/.awesomerc (careful with this, you have to position it in the order you'd like it to appear, so it has to be after the tag list and layouts).  An example of ~/.awesomerc, for this to work: 

```
screen "0"
{
	general
	{
	    # gen section
	}
	statusbar "mystatusbar"
	{
		#statusbar properties
		{
		#mousebinds and whatnot
    	}
		textbox mpd  #<-- The money
		{
			text = "-" #the - will be replaced by mpd playing
		}
  	}
  	tags
	{
		#tags
	}
	colors
	{
		#colors
	}
	layouts
	{
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"}
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"}
    	layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"}
	    layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"}
	    layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"}
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"}
	}
}
```

---

### Post by Gigamo on 2008-01-23
LoKe, could I have a look at your awesome 2.1 awesomerc? I'm thinking of upgrading too... But then I'm going to convert my awesomerc beforehand :D

---

### Post by Lostincyberspace on 2008-01-23
I am going through on a xubuntu testbed and it says I need CAIRO What cairo do I need? A complete list of dependencies should be made and the different version.


Edit: I got it not sure what it is though but now it needs confuse 2.6+ gutsy repositories only have 2.5

---

### Post by Gigamo on 2008-01-23
```
sudo apt-get install libcairo2-dev
```

---

### Post by shearn89 on 2008-01-23
AARGH!!! Awesome 2.1 has totally screwed this guide over. I'm going to put a big notice at the top, and rework it. Sorry everyone.

---

### Post by Gigamo on 2008-01-23
> **shearn89 said:**
> AARGH!!! Awesome 2.1 has totally screwed this guide over. I'm going to put a big notice at the top, and rework it. Sorry everyone.

Sorry to hear it. It can only get better though. :)

---

### Post by mali2297 on 2008-01-23
> **Lostincyberspace said:**
> I am going through on a xubuntu testbed and it says I need CAIRO What cairo do I need? A complete list of dependencies should be made and the different version.


Edit: I got it not sure what it is though but now it needs confuse 2.6+ gutsy repositories only have 2.5

You need to compile confuse 2.6 as well.

First, get all dependencies.
```

sudo apt-get install build-essential checkinstall asciidoc xmlto libxft-dev libxinerama-dev libcairo2-dev libxrandr-dev

```

Next, download and compile confuse 2.6.
```

wget http://bzero.se/confuse/confuse-2.6.tar.gz                                                                          
tar xvzf confuse-2.6.tar.gz
cd confuse-2.6
./configure
make
sudo checkinstall
cd ..

```

Now you are ready for awesome!
```

wget http://awesome.naquadah.org/download/awesome-2.1.tar.gz
tar xvzf awesome-2.1.tar.gz
cd awesome-2.1
./configure
make
sudo checkinstall

```

(This works for me in Feisty at least.)

---

### Post by Lostincyberspace on 2008-01-23
Here is my results from trying to install, it looks like it might be easy to fix?
```
========================= Installation results ===========================
make  install-am
make[1]: Entering directory `/home/lee/awesome-2.1'
make[1]: *** No rule to make target `awesome.1', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/lee/awesome-2.1'
make: *** [install] Error 2
```I also included a deb of confuse 2.6 for any others who cant find it. it is in the attachments

---

### Post by Lostincyberspace on 2008-01-23
> **mali2297 said:**
> You need to compile confuse 2.6 as well.

First, get all dependencies.
```

sudo apt-get install build-essential checkinstall asciidoc xmlto libxft-dev libxinerama-dev libcairo2-dev libxrandr-dev

```

Next, download and compile confuse 2.6.
```

wget http://bzero.se/confuse/confuse-2.6.tar.gz                                                                          
tar xvzf confuse-2.6.tar.gz
cd confuse-2.6
./configure
make
sudo checkinstall
cd ..

```

Now you are ready for awesome!
```

wget http://awesome.naquadah.org/download/awesome-2.1.tar.gz
tar xvzf awesome-2.1.tar.gz
cd awesome-2.1
./configure
make
sudo checkinstall

```

(This works for me in Feisty at least.)
I understand that now thanks for trying to help but I had figured that out on my own I was just having a hard time trying to find an installable package for it and putting up any problems I ran into so they could get clarified better tin the how to.

---

### Post by Lostincyberspace on 2008-01-23
This might help it is another how to for gentoo

[http://gentoo-wiki.com/HOWTO_awesome](http://gentoo-wiki.com/HOWTO_awesome)

---

### Post by mali2297 on 2008-01-23
> **Lostincyberspace said:**
> Here is my results from trying to install, it looks like it might be easy to fix?
```
========================= Installation results ===========================
make  install-am
make[1]: Entering directory `/home/lee/awesome-2.1'
make[1]: *** No rule to make target `awesome.1', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/lee/awesome-2.1'
make: *** [install] Error 2
```I also included a deb of confuse 2.6 for any others who cant find it. it is in the attachments

Install **asciidoc** and **xmlto**. 

EDIT: ... and rerun ./configure.

---

### Post by Lostincyberspace on 2008-01-23
With the new and improved 2.0 version I get 

```

========================= Installation results ===========================
strip awesome
strip awesome-client
asciidoc -d manpage -b docbook awesome.1.txt
FAILED: unexpected error:
------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/bin/asciidoc", line 3947, in asciidoc
    config.load_all(GLOBAL_CONFIG_DIR)
  File "/usr/bin/asciidoc", line 3570, in load_all
    for f in os.listdir(filters):
OSError: [Errno 2] No such file or directory: '/etc/asciidoc/filters'
------------------------------------------------------------
make: *** [man] Error 1

```I cant tell what is erroring there is it awesome or ascIIdoc?
EDIT: It works with regular make install but not checkinstall so all is well here.

O and in 2 you need to change cd awsome-2.1 to 2.0 and there is nothing to ./configure

---

### Post by urukrama on 2008-01-23
> **Gigamo said:**
> It can only get better though. :)

Gigamo, that sounds like "It is so terrible now that it can't get any worse" ;-)

---

### Post by shearn89 on 2008-01-23
Updated with new install instructions.

edit: @urukrama - hahaha.... i know what you mean. It's definitely off to a rocky start. But that just teaches me to try and write an Ubuntu guide from Archlinux. Stupid.

---

### Post by urukrama on 2008-01-23
Shearn89, I didn't mean your guide was terrible. :-) I was under the impression Gigamo referred to Awesome itself, but now that I reread it I see he referred to your guide.

---

### Post by Lostincyberspace on 2008-01-23
Umm I don't have an .awesomerc in my home folder should it be there or is it some where else?

---

### Post by Gigamo on 2008-01-23
> **urukrama said:**
> Shearn89, I didn't mean your guide was terrible. :-) I was under the impression Gigamo referred to Awesome itself, but now that I reread it I see he referred to your guide.

Haha rofl I didn't mean that at all. :D

I meant that it could only get easier for outsiders this way because awesome 2.1 is the version they'll download.

---

### Post by shearn89 on 2008-01-23
> **Lostincyberspace said:**
> Umm I don't have an .awesomerc in my home folder should it be there or is it some where else?
there's an example awesomerc in the source folder, called "awesomerc". Just copy it to your home directory, rename it .awesomerc, and user that.

I'm just going through the awesomerc file in order to add notes about it.

---

### Post by Lostincyberspace on 2008-01-23
Thanks is the setup for background in the awesomerc?

---

### Post by Gigamo on 2008-01-23
> **Lostincyberspace said:**
> Thanks is the setup for background in the awesomerc?

You have to use a app like Nitrogen or Feh for that and add it to your autostarted apps (nitrogen --restore & for nitrogen)

---

### Post by Lostincyberspace on 2008-01-23
How do I get them they aren't in the repository's.
Or am I just being stupid and not finding it?

---

### Post by shearn89 on 2008-01-23
feh is in the repos - use "feh --bg-scale /full/path/to/file" to set it, and "~/.fehbg" to restore it (in autostart). Nitrogen i'm not sure about, but you can search for either with:
```

apt-cache search nitrogen (or feh)

```

---

### Post by rjmdomingo2003 on 2008-01-23
I'm looking forward to getting down & dirty again with the updated instructions. I've had little success in installing awesome last night, what with all the needed dependencies.

Thanks shearn, gigamo & all of yous!

---

### Post by vehka on 2008-01-24
Hi, and thanks for the great guide!

There's a typo in the apt-get install string, "xmltoo" instead of "xmlto".

Cheers,
Heikki

---

### Post by shearn89 on 2008-01-24
vehka - thanks. Changed!

awesomerc notes should be up sometime later this afternoon.

---

### Post by rjmdomingo2003 on 2008-01-24
Yey! Finally managed to install awesome. I'll do the customizations right after I kick my flux-addiction :) which may come soon..

---

### Post by shearn89 on 2008-01-24
Cool - did the guide help at all?

---

### Post by shearn89 on 2008-01-24
Updated finally. Should work fine for 2.1.

---

### Post by rjmdomingo2003 on 2008-01-24
> **shearn89 said:**
> Cool - did the guide help at all?
It helped a lot, shearn89! Thanks very much! You were very fast with the updates.

I'll post my first screenie after customizations are done. Thanks again!

---

### Post by rjmdomingo2003 on 2008-01-25
> **shearn89 said:**
> The [website]("http://awesome.naquadah.org/") has more info, and a brief guided tour. They also have a link to their wiki, which is good for a few FAQs.
For menus and such, see [the awesome wiki]("http://awesome.naquadah.org/wiki/index.php/FAQ#Is_there_a_program-launcher.2C_menu..._in_awesome.3F").
You could add this link for the brief guided tour: [http://awesome.naquadah.org/doc/setup/](http://awesome.naquadah.org/doc/setup/)

---

### Post by vehka on 2008-01-25
I'm really glad I installed awesomeWM, I like it a lot! (Thanks again Shearn89 for making this guide!)

I have a newbie question regarding fonts.

The "system" font size for too small now (I used Gnome before). How do I adjust this? Tried reading through some font FAQs like

[http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts)

[http://wiki.archlinux.org/index.php/XOrg_Font_Configuration](http://wiki.archlinux.org/index.php/XOrg_Font_Configuration)

but didn't find them really helpful. The only font setting in .awesomerc is about the title bar font, that I can change, but how do I change the the "system default font"?

Tried setting the display size and DPI in xorg.conf, but that didn't change anything. (Except maybe made the fonts look a bit crisper. =) )

I'd be really thankful for any tips!

-vehka

---

### Post by vehka on 2008-01-25
Of course I realized how to do it a couple of minutes after posting the question. I'll put the answer here, so that it might help some others too.

I created a file called .gtkrc-2.0 in my home directory, and put a line like this in the file:

gtk-font-name = "Sans 16"

Now I restarted the X server by pressing ctrl+alt+backspace, and voila, all the GTK apps like firefox and gnome-terminal have a new font size. (This font is actually a bit too wide to my taste, and probably way too big for most users, but at least now I know how to change it.)

-vehka

---

### Post by rjmdomingo2003 on 2008-01-25
When I change sessions to awesome in the GDM, and log into it, an message comes up

> Xsession: unable to launch "~/awesome.sh" Xsession --- "~/awesome.sh not found; falling back to default session.

then it logs into Gnome desktop. 

I'm sure I have awesome.sh in my home directory but what gives?

---

### Post by mali2297 on 2008-01-25
> **rjmdomingo2003 said:**
> 
I'm sure I have awesome.sh in my home directory but what gives?

My guess is that you need to specify the full path in awesome.desktop.
```

Exec=/home/<username>/awesome.sh

```

..or that you need to make awesome.sh executable. From the terminal,
```

chmod +x ~/awesome.sh

```

---

### Post by rjmdomingo2003 on 2008-01-26
> **mali2297 said:**
> ..or that you need to make awesome.sh executable. From the terminal,
```

chmod +x ~/awesome.sh

```
I'm an idiot! Thanks mali2297! We always forget!](*,)

---

### Post by Gigamo on 2008-01-26
This could maybe be added into the GDM part section of the guide - the chmod +x awesome.sh thing.

---

### Post by shearn89 on 2008-01-26
I've done it - just a note to make sure the path is correct, and make it executable.

---

### Post by rjmdomingo2003 on 2008-01-27
> **mali2297 said:**
> My guess is that you need to specify the full path in awesome.desktop.
```

Exec=/home/<username>/awesome.sh

```

..*[COLOR="Red"]or[/COLOR]* that you need to make awesome.sh executable. From the terminal,
```

chmod +x ~/awesome.sh

```
This shouldn't be an _or_ but an _and_ instruction. 

I've first tried making the script executable, however, I got the same error message of awesome.sh not being found. I then edited the awesome.desktop to indicate the full path instead of ~/awesome.sh, and finally got the awesome "interface".

Just need to get those huge fonts when I go home. Thanks guys!

---

### Post by rjmdomingo2003 on 2008-01-27
Oops, shearn already made those changes.. Dang! Sorry guys.](*,)

---

### Post by prototype_angel on 2008-08-06
Hey, has anyone been able to build awesome 3.0? I couldn't build it because package "cairo-xcb" is missing (I painstakingly installed/compiled all the remaining packages)

If so, can someone help me out?

The output of my "make" can be found here:
[http://ubuntuforums.org/showthread.php?p=5533444#post5533444](http://ubuntuforums.org/showthread.php?p=5533444#post5533444)

---

### Post by shearn89 on 2008-08-06
Hi there - on my arch system cairo-xcb conflicted with cairo, and so wasn't in the repos. Looking at the pkgbuild file, the source can be downloaded from:

[http://cairographics.org/releases/cairo-1.6.4.tar.gz](http://cairographics.org/releases/cairo-1.6.4.tar.gz)

and you need to compile with this configure line:
```

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var **--enable-xcb**

```

---

### Post by morngrar on 2008-11-17
just wondering if anyone has found/made a 3.0 guide or tutorial for ubuntu?

im trying to install 3.0, but xcb-util is giving me a headache...

here's the output:

```

bewar@bewar-eee:~/Desktop/xcb-util-0.3.0$ make
Making all in atom
make[1]: Entering directory `/home/bewar/Desktop/xcb-util-0.3.0/atom'
gperf --output-file atoms.c atoms.gperf
atoms.gperf: The input file is empty!
make[1]: *** [atoms.c] Error 1
make[1]: Leaving directory `/home/bewar/Desktop/xcb-util-0.3.0/atom'
make: *** [all-recursive] Error 1

```

---

### Post by shearn89 on 2008-11-17
I did submit a 3.0 howto to the forum, but had no reply. I've been running arch for a few months now, which makes it harder to write an ubuntu tutorial. If i remember rightly, you have to build xcb with cairo support, however, that error simply says that there's nothing in atoms.c

Are you in the right directory?

---

### Post by oxleyk on 2010-11-23
I looked around for more appropriate location but didn't find one.

Is it possible to restrict a client, namely my Empathy contact list, to a specific size?

Kent

---

