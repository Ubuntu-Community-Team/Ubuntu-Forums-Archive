---
title: "A couple menu tricks to increase productivity and knowhow"
date: 2010-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Deadite81 on 2010-03-04
Hello everybody!  This howto is concerning the Debian menu and the little program mygtkmenu.   This is aimed more towards the new crowd who want to learn about some things on their computers they didn't know were there and to stop clicking the mouse so much just to get to a file. (This probably could have been 2 posts, but what the heck?)
[CENTER][SIZE=2]
Contents[/SIZE]
[/CENTER]
 [CENTER]Part 1: The Debian Menu
Part 2: mygtkmenu
Part 3: xkill and conky
Part 4: Edit Files With Ease/Running Terminal Based Apps and Scripts
Part 5: Using mygtkmenu to handle terminal functions (Blockcontrol/Moblock as examples)
Part 6: The End

[SIZE=1]
[/SIZE][/CENTER]
[SIZE=5]Part 1[/SIZE]
First, the Debian menu.  What's that you say?  The Debian menu specification is what some window managers/Linux distros use to organize and display the main menu.  Fluxbox, for example, uses it.  Ubuntu uses the [xdg specification]("http://standards.freedesktop.org/menu-spec/menu-spec-latest.html").

So why would you want the Debian menu?  When you enable the Debian menu system lots of choices not available on your regular "start" menu will become available, many of which you may have never found out about otherwise, including lots of little apps that can only be run from a terminal, like fortune, w3m, and xkill (more on that momentarily).

Now let's get down to it.  Enabling the Debian menu will not remove your current menu. In fact, it  becomes a supplement, another category, like "Office" or "System Tools".

First you need the packages "menu" and "menu-xdg" (Don't worry, they're tiny.)
 ```

sudo apt-get install menu menu-xdg
```You may already have "menu".  It's a dependency of the handy programs bleachbit, deborphan-gtk, sbackup, and a few others.

Now that the packages are installed open your menu editor, a.k.a. alacarte.  You can do this by right-clicking your panel main menu or by typing "alacarte" (no quotes) into a terminal.  After it opens, check the empty box next to "Debian" like so:

[IMG]http://dl.dropbox.com/u/4367247/alacarte-open.jpeg[/IMG]

[IMG]http://dl.dropbox.com/u/4367247/alacarte.jpeg[/IMG]

But, since you've installed menu and menu-xdg, go ahead and check the "Debian" box:

[IMG]http://dl.dropbox.com/u/4367247/deb-check.png[/IMG]

Now you should see a "Debian" entry in your main menu.  There are some screenshots at the bottom of the Debian menu in action.

Well, that's cool, you might say, but now I have to wade through another menu.  And it's missing icons.  And it's poorly organized. Geez! I don't even have some of these apps anymore!
True, true and true.  I normally don't keep it activated, I just wanted to see what apps I didn't know about.  For instance, the w3m text browser is installed on my computer (I don't think I put it there!).  This app allows me to browse the web with my terminal.  How else would I have known it was there?  I don't know!  By chance I guess.  Same with "fortune".  Apparently, if I type "fortune" in my terminal, I get a random quote from some famous (or infamous) person.  It will also contain all sorts of individual command options for a single apps, cli and gui.  It just depends what you've installed and what the original packager chose to include in his/her menu file.  (All the files for individual Debian menu entries are stored in /usr/share/menu.)

You can also use alacarte to see what command actually runs a particular function by clicking the app and selecting "Properties" over on the right. Then you can add it to your regular main menu and/or mygtkmenu.  I do not recommend alacarte for extensive menu rearranging.  It broke my menu completely so I learned [how to do it by hand]("http://ubuntufs.wordpress.com/2007/05/15/add-menu-items-in-gnome/").   It's up to you though.  It does seem to work well for simple modifications.

If you want to keep and cleanup the Debian Menu, well, that's beyond the scope of this howto. (There's still more to go!)  However, the menu package comes with documentation (usr/share/doc/menu)  and the official online material is [here]("http://www.debian.org/doc/packaging-manuals/menu.html/").

[SIZE=5][COLOR=black]Part 2[/COLOR][/SIZE]
Now onto mygtkmenu.
Mygtkmenu is a simple app that produces a user configurable menu you can call in various was.  You can add it to the panel, right-click, etc.  For more info on this cool app check out these links:

You can download it from the homepage [here]("http://sites.google.com/site/jvinla/mygtkmenu").
And/or follow this great tutorial to get you started [on this very forum]("http://ubuntuforums.org/showthread.php?t=875262&highlight=alacarte").

Here's a brief run down on how I use mygtkmenu, but you should really check out the above links if you don't know what the heck I'm going on about!  Once you're comfortable with the program read on!

Basically, you just have to stick the unpacked files in your home directory somewhere and it's installed.  It's making it work that must be configured.  The above tutorial uses the compiz viewport plugin so that any time you right/middle-click your desktop the menu will open.  If that works for you great.  I rarely even see my desktop, so I did this:
(This only applies if you use compiz.)

1. Open your CompizConfig Settings Manager
(If you don't have it, shame on you! sudo apt-get install ccsm)

2. Choose "Commands" in the "General" section.

3. Put this in one of the "Command line #" fields.  Substitute "you" with the name of your home directory, ".mygtkmenu" to the directory you saved mygtkmenu to, and finally, "menu_click.txt" with the name of your menu.txt file.

 ```
/home/you/.mygtkmenu/myGtkMenu /home/you/.mygtkmenu/menu_click.txt
```4. Assign a binding to the menu.  Choose the Button/Key Bindings tab and assign what you want to press to enact the menu relative to the command number.  I chose <Control>Button3 (ctrl + right-click).

(There are other programs and ways to get some of this same functioality.  Gnome Do, Cairo Dock, Avant Window Navigator, etc.  This is just another way, which I prefer because the overhead is so much lower on my lowly P4 @ 2.8Ghz.)

[SIZE=5]Part 3[/SIZE]
Now to the point.  You can assign virtually any command to your new menu, not just apps you see in your normal main menu.

For example:
When I learned about "xkill" through the Debian menu I was able to implement it in mygtkmenu.  Be warned, however, that sometimes xkill will only kill the x server (window), but not the process itself.  It seems to just depend on the program.  See "man xkill" for more info.

I added this to my menu text file:

```

item = XKill
cmd = xkill
icon = /path/to/icon.png
```This gives me an "xkill" option in mygtkmenu.  When I click it my pointer becomes a crosshair.  Any program I click on gets axed.  If I change my mind, I simply right-click and my pointer returns to normal.

I hear a lot of people complaining about the fact that they must have a terminal and multiple tabs open to test their conky configurations.  Mygtkmenu offers a simple solution....

Add a command to stop conky

```
   
item = Conky
cmd =gnome-terminal -e 'killall conky'
icon =  /path/to/icon.png
```

Notice the quotes around 'killall conky'.  If you use a terminal command with spaces, it must be quoted to be recognized as one command.  If you don't do this, mygtkmenu will simply run "killall" and fail.

Add a command to start conky

```

item = Conky
cmd = conky
icon = /path/to/icon.png
```And finally, add an entry to edit your conkyrc configuration file

    ```

item = conkyrc
cmd = gedit /home/YOU/.conkyrc
icon =  /path/to/icon.png
```[IMG]http://dl.dropbox.com/u/4367247/xkill-conky.jpeg[/IMG]

This technique can also be implemented to restart Firefox/Seamonkey/Thunderbird with one click while editing the userChrome.css file instead of installing addons or restarting them manually!

You can restart the panel too: gnome-terminal -e 'killall gnome-panel'

Basically, you can kill/restart just about anything that regularly gives you trouble in this simple way! 

[SIZE=5]Part 4[/SIZE]
As you've probably guessed, you can put all kinds of other shortcuts in your menu.  Just add a "gksu" command before "gedit" (or any other editor) to edit protected files:

```

item = PA daemon.conf
cmd = gksu geany /etc/pulse/daemon.conf
icon = /path/to/icon.xmp
        
item = sources.list
cmd = gksu gedit /etc/apt/sources.list
icon = /path/to/icon.png

item = sources.list (nano)
cmd = gnome-terminal -e 'sudo nano /etc/apt/sources.list'
icon = NULL 
```
Once again, note the quotes.  Also, since nano is a terminal based  text editor, I used "sudo" rather than "gksu".

You may have noticed the "-e" argument after "gnome-terminal".  This allows you to run a terminal based program/command with mygtkmenu.  When the above command is issued for nano, a terminal window will pop up and ask for your password, and then open the specified program for editing.  What I find convenient about this is that any command/program will be run in a terminal, but when it's done will close the terminal automatically.  

For example, if you wanted to run the htop system monitor without opening a new terminal and typing the command, your menu entry would look like this:

```

item = Htop
cmd = gnome-terminal -e htop
icon = /path/to/icon.png
```
([Htop]("http://htop.sourceforge.net/") is like top, but with customizable features.  It's color coded and shows full paths.)

If you just want to take a quick peak at your system processes, select the htop item in your menu.  Then quickly close it with <control>c.  Whereas <control>c would normally stop the htop process and return you to your terminal promt (which you likely don't need, especial if you already have a terminal window open for some other reason), when run through mygtkmenu with the -e option, the entire terminal window closes.

You can run your own scripts also, like this one to start Thunderbird in the systemtray with the app Alltray:

Script, saved as an executable .sh file (i.e. "thunderbird_tray_start.sh"):
```

#!/bin/bash

alltray /home/justin/apps/thunderbird/thunderbird -stask -na -st
```Menu entry:
```

    item = Thunderbird (tray)
    cmd = /home/justin/scripts/thunderbird_tray_start.sh
    icon = /path/to/icon.png
```A good place to learn a few basics about bash scripting is [here]("http://www.thegeekstuff.com/2010/03/introduction-to-bash-scripting/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+TheGeekStuff+%28The+Geek+Stuff%29") and the packages "abs-guide" and "bash-doc" make for good reading (sudo apt-get install abs-guide bash-doc).
[Alltray]("http://alltray.trausch.us/") can dock any app in the system tray. [ Kdocker]("https://launchpad.net/kdocker") and [gtrayicon]("http://gtrayicon.sourceforge.net/") too.

In the same vane as a script, you could run a bash alias from your menu.  (If you don't know what aliases are be careful, they can be dangerous.  Lean more  [here]("http://tldp.org/LDP/abs/html/aliases.html"), on this forum [here]("http://ubuntuforums.org/showthread.php?t=1416864"), and [here]("http://tldp.org/LDP/abs/html/sample-bashrc.html").)

Add this to your ~/.bash_aliases
```

# Record the desktop using ffmpeg(saving to /tmp/out.mpg, which may be changed to whatever)
alias record="ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/out.mpg"
```Save it and open a terminal.  Type "record" and hit enter.  Now your desktop is being recorded, for a YouTube video perhaps.  Since you can do this from a terminal, you can do it from your menu:
```

item = Record Desktop
cmd = gnome-terminal -e record
icon = /path/to/icon.svg
```
That's it. Now you can run your simplified alias command from the terminal or menu easily!

[SIZE=5]Part 5[/SIZE]
Now let's say you have a program that is used completely through the command line.  Or maybe you don't use it's gui frontend for whatever reason.  You can easily set up mygtkmenu to run any command you want associated with it.  For example, I stopped using Mobloqer because it started buggin' out and producing tons of errors.  So now I'm left with just the cmd line parts, Blockcontrol and Moblock.  So I made my menu look like this:

[IMG]http://dl.dropbox.com/u/4367247/blockcontrol.jpeg[/IMG]

My menu.txt "Web" submenu looks like this:

```

Submenu = Web

	icon = /home/justin/apps/mygtkmenu/gnome-icons/web.png
	
#	item = Chromium
#	cmd = chromium-browser
#	icon = /home/justin/apps/mygtkmenu/gnome-icons/chromium-browser.png
	
	item = Imageshack
	cmd = imageshack-uploader
	icon = /home/justin/apps/mygtkmenu/gnome-icons/imageshack.png
	
	item = _Firefox
	cmd = firefox
	icon = /home/justin/apps/mygtkmenu/gnome-icons/firefox.png
	
	item = Moblock (start)
	cmd = gnome-terminal -e 'sudo blockcontrol start'
	icon = /home/justin/apps/mygtkmenu/gnome-icons/mobloquer.png

	item = Moblock (stop)
	cmd = gnome-terminal -e 'sudo blockcontrol stop'
	icon = /home/justin/apps/mygtkmenu/gnome-icons/mobloquer.png
	
	item = Moblock (update)
	cmd = gnome-terminal -e 'sudo blockcontrol update'
	icon = /home/justin/apps/mygtkmenu/gnome-icons/mobloquer.png
	
	item = Moblock (tail)
	cmd = gnome-terminal -e 'tail -f /var/log/moblock.log'
	icon = /home/justin/apps/mygtkmenu/gnome-icons/mobloquer.png
	
	item = Moblock (reload)
	cmd = gnome-terminal -e 'sudo blockcontrol reload'
	icon = /home/justin/apps/mygtkmenu/gnome-icons/mobloquer.png

	item = Seamonkey
	cmd = /home/justin/apps/seamonkey/./seamonkey 
	icon = /home/justin/apps/mygtkmenu/gnome-icons/seamonkey.png
```

That should all be pretty self-explanatory. Very convenient.  As you can see from the above screenshot, there's lots of stuff you can add to your menu.  I especially find the gksu Nautilus cmd useful.

[SIZE=5]Part 6[/SIZE]
And finally, I recommend that you resize all the icons you use in your menu and move them all to one folder.  I put them all in the same folder as mygtkmenu, in the provided directory gnome-icons.  The load time of the menu is much faster if you do this.  "[Phatch]("http://photobatch.wikidot.com/getting-started")" is a good batch conversion program, the Nautilus script "[avconvert]("http://www.gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533")" is indispensable for coverting just about anything on the fly, and of couse there's the [Nautilus image converter extension]("http://packages.ubuntu.com/karmic/nautilus-image-converter") (sudo apt-get nautilus-image-converter).

Well, that's it!  Drop a comment: what you would change, and what are your shortcuts?

[IMG]http:///home/justin/Dropbox/Public/opens-alacarte.png[/IMG]

---

