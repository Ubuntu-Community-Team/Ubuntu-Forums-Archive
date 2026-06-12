---
title: "HOWTO: Set up AwesomeWM 2.1"
date: 2008-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by ~LoKe on 2008-01-26
Recently I've been trying out several different WM's in order to find the one that suits me needs; one that fits perfectly.  I stumbled upon tiling window managers and started with DWM.  It seemed perfect.  It was then suggested to me to try "Awesome".  I figured, why not?  I came to find that one of the greatest things about Awesome is the ability to reload the config on the fly.  With DWM, you had to recompile and restart the xserver.  Granted, that wasn't too difficult, but it can become inconvenient.  With Awesome, a simple key combination (in my case, mod4 + ctrl + r) reloads the entire config without you haven't to compile anything, or lose any of your open programs.  In addition to this, Awesome also has magnificent support for multi-display setups.  You're able to have two completely different status bars, two completely different sets of tags, keybindings, color schemes, etc.  I couldn't ask for more.

So, here I am writing a guide for those considering trying Awesome.  Recently, version 2.1 was released and the configuration setup completely changed.  I figure it warrants another guide in order to clear up a bit of the conclusion.  There's already an excellent guide written [here](http://ubuntuforums.org/showthread.php?t=675292), but that's for the most basic set up ust to get things working and I'm inclined to provide as much information as I can get my hands on.  Perhaps we can all learn something here.  So, let's begin.

### **Step 1** -- Dependencies
In order to install Awesome, we need some dependencies.
```
sudo aptitude install build-essential libxinerama-dev libxrandr-dev libcairo2-dev libxft-dev asciidoc xmlto doxygen checkinstall rxvt-unicode feh ## feh is only necessary if you want to use it to set a wallpaper
```

And we need to compile libconfuse2.6 from source to get the latest version....
```
cd ~/ && wget http://bzero.se/confuse/confuse-2.6.tar.gz && tar xvf confuse*.tar.gz && cd confuse* && ./configure && make && sudo checkinstall
```

### **Step 2** -- Installing Awesome
Now we have to get Awesome itself!  What we'll do here it download it and extract it.  I've lumped everything together into one line like above to make it as easy as possible.
```
cd ~/ && wget http://awesome.naquadah.org/download/awesome-2.1.tar.gz && tar xvf awesome*.tar.gz && cd awesome* && ./configure && make && sudo checkinstall
```

### **Step 3** -- Starting Awesome
The easiest way to start Awesome is with a GDM entry.  To make one, type the following into the terminal.  I use Gedit with gksu, but you're free to use whichever editor you prefer.
```
gksu gedit /usr/share/xsessions/awesome.desktop
```
Paste the following in:
```
[Desktop Entry]
Encoding=UTF-8
Name=Awesome
Comment=AwesomeWM
Exec=/home/username/.scripts/awesome.sh
Icon=
Type=Application
```
Remember to change **username** to your username!

Now we need a start up script to get the ball rolling.
```
mkdir ~/.scripts
```
```
gedit ~/.scripts/awesome.sh
```

Paste in the following:
```
exec awesome
```
Then run this...
```
chmod +x ~/.scripts/awesome.sh
```

Now, if you're anything like me, you'll want to have several programs start automatically.  In the same file, **~/.scripts/awesome.sh**, you'll want to add a few things depending on what you want starting automatically.  We'll start with something simple: a wallpaper, pidgin and a clock.

```
~/.fehbg &
pidgin &
/usr/bin/awesome-monitor &
exec awesome ## this has to be the last line
```

### **Step 4** -- **~/.awesomerc**
This part will seem considerably confusing.  The file in general is a bit of a mess compared to the previous version, but I'll do my best to make it work.  To start, here's the most basic config to make it "just work".  This is for single display only.  Adding a config for a second display is easy, and I'll cover that later.  Type the following into the terminal:
```
gedit ~/.awesomerc
```
Then paste in the following:
```
screen "0"
{
	general
	{
		# this is the border around your windows
		border = 1
		# snap to edges within 8 pixels
		snap = 8
		resize_hints = true
		opacity_unfocused = 100
		focus_move_pointer = false
		allow_lower_floats = false
		sloppy_focus = true
		new_become_master = true
		new_get_focus = true
		# this is the font you'll see on your status bar, use whatever you'd like
		font = "sans-7"
	}
	statusbar "mystatusbar"
	{
		# you can put the status bar anywhere; top, bottom, left, right
		position = "top"
		height = 0
		width = 0
		# this section allows you to use the mouse to tag windows and switch to them, leave it as it is for now unless you know what you're doing
		taglist "mytaglist"
		{
			x = -1
			y = -1
			mouse 
			{
				modkey = {}
			        button = "1"
				command = "tag_view"
			}
			mouse
			{
		        	modkey = {"Mod4"}
		        	button = "1"
			        command = "client_tag"
			}
      			mouse
			{
			        modkey = {}
    		   		button = "3"
				command = "tag_toggleview"
   			}
      			mouse
			{
	        		modkey = {"Mod4"}
	        		button = "3"
	        		command = "client_toggletag"
		    	}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_viewnext"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_viewprev"
      			}
		}
		# this section is basically the same...
    		layoutinfo "mylayoutinfo"
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "1"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "3"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
    		}
		# and so is this one....
    		tasklist "mytasklist" 
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "client_focusnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "client_focusprev"
        			# arg = ""
     			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "4"
        			command = "client_swapnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "5"
        			command = "client_swapprev"
       				# arg = ""
      			}
      			align = "left"
      			show_icons = false
      			show_all = false
    		}
		# this section is rather important.  This is your statusbar widget for the clock.  This will put a clock at the far right side of your monitor. 
		# you can add other widgets too, like mpd info, gmail scripts, etc.
	    	textbox clock  # "clock" is the name of your widget
		{
			text = "-" # the - will be replaced by the date and time
		}
  	}
	# these are your tags.  Basically it defines how the statusbar is set up to look.  You can add/remove as many tags as you'd like, change their names, how their behave, etc.
  	tags
	{
		tag ":main" # :main is the display name of the tag.  You can change this to say whatever you want, it's completely up to you.
		{
			layout = "max" # this tells the tag how to display windows.  "max" forces all your windows in that tag to be...maximized!  You can still make them float by moving them by hand
			mwfact = 0.500000 # leave this for now
      			nmaster = 1 # leave this for now
      			ncol = 1 # leave this for now
    		}
    		tag ":devel"
		{
	      		layout = "tile"
	      		mwfact = 0.500000
 	     		nmaster = 1
	      		ncol = 1
		}
    		tag ":term"
		{
      			layout = "tile"
      			mwfact = 0.500000
     			nmaster = 1
      			ncol = 1
    		}
	}
	colors
	{
		# here we define our colors.  I'll have an example screenshot at the bottom of this page.  You can change these colors to whatever you want.
		normal_border = "#777777"  # window border when selected
        	normal_bg = "#000000" # background for the statusbar
        	normal_fg = "#a8bcff" # foreground color for the statusbar (unselected tags)
       		focus_border = "#000000" # border color of fucsed windows
        	focus_bg = "#000000" # focused background for the status bar, it's what decides the color for the background of the selected tag
        	focus_fg = "orange" # focused foreground color, the color of the selected tag and title
    		urgent_bg = "#000000" # background
    		urgent_fg = "orange" # foreground
    		tab_border = "#ff0000" # I have absolutely no idea.
	}
	layouts
	{
		# you can add whichever images you want here.  They'll display as the layout options on the statusbar.  I use a black background, and these images are black
		# basically that "hides" them, but they're still available to use.
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"} ## use tilew.png for white
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"} ## use tileleftw.png for white
    		layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"} ## use maxw.png for white
	   	layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"} ## use spiralw.png for white
	    	layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"} ## use dwindlew.png for white
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"} ## use floatingw.png for white
	}
	# padding around screen.
	padding
	{
    		top = 0
    		bottom = 0
    		right = 0
    		left = 0
  	}
}
# rules...the only kind I actually like!  These "rules" tell your windows where to go.  Basically, you can tell all your terminal to go to one tag
# and have your browser go to a different one.   There's no limit on how many rules you have, just make sure they have a corresponding tag.
# you can also tell these windows how to display, more information later!
rules
	{
	rule
	{
		name = "firefox" 		# this is the name of the window.  It's not case sensitive as far as I know
		tags = ":main" 			# this is the name of the tag you want Firefox to appear on.
		float = "false"			# this is the layout style.  You can have it maximized,  floating, etc.  We'll have Firefox maximized.
		screen = "0"				# which monitor to display on.  I have two monitors so I choose to have it on screen 0.  Leave it as it is.
		not_master = false 	# we want it to be the master window
	}
  	rule
	{
		name = "Gimp"
		tags = ":devel"
		float = "true"
		screen = 0
		not_master = false
	}
	rule
	{
		name = "urxvt"
		tags = ":term"
		float = "true"
		screen = 0
		not_master = true
	}
}
# this section allows you to set hotkeys.  These are most excellent because they remove the need for a menu.  You can have as many as you want.
keys
	{
	key
	{	
	    modkey = {"Mod4"} 	# mod4 by default is the windows key.
	    key = "Return" 			# this is the key on your keyboard
	    command = "spawn" # what it should do, usually always "spawn"
	    arg = "exec urxvt" 	# what to exec.  In this case, mod4 + enter will start urxvt
	}
	key
	{
		modkey = {"Mod4"}
		key = "f"
		command = "spawn"
		arg = "exec firefox"
	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "space"
	    	command = "tag_setlayout"
	    	arg = "+1"
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "space"
	    	command = "tag_setlayout"
	    	arg = "-1"
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "b"
	    	command = "statusbar_toggle"
	    	# arg = ""
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "j"
	    	command = "client_focusnext"
	    	# arg = ""
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "k"
	    	command = "client_focusprev"
	    	# arg = ""
	}
	key
	{
	   	modkey = {"Mod4"}
	    	key = "Tab"
	    	command = "focus_history"
	    	arg = "-1"
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "j"
	    	command = "client_swapnext"
	    	# arg = ""
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "k"
	    	command = "client_swapprev"
	    	# arg = ""
  	}
	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "j"
	    	command = "screen_focus"
	    	arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "k"
	    	command = "screen_focus"
	    	arg = "-1"
  	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "h"
	    	command = "tag_setmwfact"
	    	arg = "-0.05"
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "l"
	    	command = "tag_setmwfact"
	    	arg = "+0.05"
  	}
  	key
	{
    		modkey = {"Mod4", "Shift"}
    		key = "h"
    		command = "tag_setnmaster"
    		arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "l"
	    	command = "tag_setnmaster"
	   	arg = "-1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "h"
	    	command = "tag_setncol"
	    	arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	   	key = "l"
	    	command = "tag_setncol"
	    	arg = "-1"
  	}
 	key
	{
	    	modkey = {"Mod4"}
	    	key = "Escape"
	    	command = "tag_viewprev_selected"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "Left"
	    	command = "tag_viewprev"
	    	# arg = ""
  	}
  	key	
	{
	    	modkey = {"Mod4"}
	    	key = "Right"
	    	command = "tag_viewnext"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "m"
	    	command = "client_togglemax"
	    	# arg = ""
	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "Return"
	    	command = "client_zoom"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "space"
	    	command = "client_togglefloating"
	    	# arg = ""
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
	   	modkey = {"Mod4", "Shift"}
	    	key = "c"
	    	command = "client_kill"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "q"
	    	command = "quit"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "r"
	    	command = "exec"
	    	arg = "awesome"
  	}
  	key
	{
    		modkey = {"Mod4"}
    		key = "0"
    		command = "tag_view"
    		# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "0"
	    	command = "tag_toggleview"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "0"
	    	command = "client_tag"
	    	# arg = ""
	}
  	key
	{
	   	modkey = {"Mod4", "Shift", "Control"}
	    	key = "0"
	    	command = "client_toggletag"
	    	# arg = ""
  	}
  	keylist
	{
	    	modkey = {"Mod4"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "tag_view"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	}
  	keylist
	{
	    	modkey = {"Mod4", "Control"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "tag_toggleview"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    	modkey = {"Mod4", "Shift"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "client_tag"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    	modkey = {"Mod4", "Shift", "Control"}
    		keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
    		command = "client_toggletag"
    		arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
}
mouse
	{
	root
	{
	    	modkey = {}
	   	button = "3"
	    	command = "spawn"
	    	arg = "exec urxvt"
  	}
  	root
	{
	    	modkey = {}
	    	button = "4"
	    	command = "tag_viewnext"
	    	# arg = ""
  	}
  	root
	{
	    	modkey = {}
	    	button = "5"
	   	command = "tag_viewprev"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "1"
	    	command = "client_movemouse"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "2"
	    	command = "client_zoom"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "3"
	    	command = "client_resizemouse"
	    	# arg = ""
	}
}
```

*WHEW*

### **Step 5** -- A Clock?
Now, I do believe I promised a clock earlier on.  So let's make that happen.  Type this into the terminal:
```
gedit ~/awesome-monitor
```
And paste in the following:
```
while true
do
echo 0 widget_tell clock "[`date '+%a %b %d %r'`]" | /usr/local/bin/awesome-client
sleep 1
done
```
Then, we need to make it executable and put it in the proper directory.  So, save and close the file then type the following into the terminal:
```
sudo chmod +x ~/awesome-monitor && sudo mv ~/awesome-monitor /usr/bin/
```

Now we need to make it run.  If you followed my advice earlier, your ~/.scripts/awesome.sh should look something like this:
```
~/.fehbg &
pidgin &
/usr/bin/awesome-monitor &
exec awesome ## this has to be the last line
```

The second last line is what gives us the clock!

All should work now.  You're free to restart GDM and give Awesome a shot (Sessions -> Awesome).

I'll try to keep this guide updated with as much information as I can give you.  This is just the "basics" and I'll go through it to see if I've missed anything.  If you have any questions, ask them.  I'll try my best to answer them.

Oh, and as promised, a screenshot of Awesome 2.1.  Mind you, this is after a lot of customization, which I'll later show you how to do.

[[img]http://tn3-1.deviantart.com/fs23/300W/f/2008/026/1/a/Desktop_as_seen_on_01_26_08_by_IcedLoKi.png[/img]](http://icedloki.deviantart.com/art/Desktop-as-seen-on-01-26-08-75650440)

More of my desktop shots can be seen **[here](http://icedloki.deviantart.com/gallery/)**

---

### Post by ~LoKe on 2008-01-27
**FAQ**

**Question #1**: I started Awesome but I don't know what to do.  I have no start menu, and no right-click.  I think it's broken!
**Answer #1**: You're not alone here.  They had me confused for a while.  By default, Awesome doesn't have any menus.  To "get going", press mod4 + enter (mod4 is usually the Windows key).  This should open up a terminal, which allows you to do what you need.

**Question #2**: Whenever I load awesome I have this ugly gray screen with a blue and black status bar.  This is not what I set up in my ~/.awesomerc.
**Answer #2**: The screen you're seeing is the fall back config.  This means there's a problem with your ~/.awesomerc.  It's possible that you forgot a curly brace or something else as simple.  If you can't find the problem, post your **~/.awesomerc** here within the [co******de] [/co******de] tags.

**Question #3**: Awesome is ugly.  All my fonts are big and I can't find any themes for awesome.
**Answer #3**: This one is quite common.  By default, the only theming available to awesome is that of the statusbar.  However, you can use gnome-settings-daemon or gtk-theme-switch to apply one of your GTK themes.  To get it to apply automatically when awesome starts, add the necessary line to **~/.xinitrc**.  Here's an example of what I would use:
```
/usr/bin/awesome-monitor &
gnome-settings-daemon &

exec awesome
```

**Question #4**: How do I set a wallpaper?  There's no right-click menu!
**Answer #4**: This is usually what confuses most beginners.  There is no right click menu.  To set an image as your wallpaper, you can either open it up in an image viewer and choose view -> set as desktop wallpaper, or you can use an application like feh.
```
sudo apt-get install feh
```
Feh is run from the command line.  To set a wallpaper, type the following into the terminal:
```
feh --bg-scale /home/username/path/to/wallpaper.jpg
```
There are several different options for feh, so type **man feh** in the terminal to find them all.
|
|___ **Sub-question #1**: Every time I log out and log back in, my wallpaper is gone.  How do I make it stay?
|___ **Answer #1**: To have your wallpaper start automatically, add the following to **~/.xinitrc**:
```
feh --bg-scale /home/username/path/to/wallpaper.jpg &
```

**Question #5**: I use two monitors, so awesome is showing two status bars.  Can I make them look different, and have different tags for each?
**Answer #5**: Yes!  One of the greatest features of Awesome is its excellent support for dual display.  To add a customized statusbar on your second display, add this right above the **## rules** section of your **~/.awesomerc**:
```
screen "1"
{
	general
	{
		# this is the border around your windows
		border = 1
		# snap to edges within 8 pixels
		snap = 8
		resize_hints = true
		opacity_unfocused = 100
		focus_move_pointer = false
		allow_lower_floats = false
		sloppy_focus = true
		new_become_master = true
		new_get_focus = true
		# this is the font you'll see on your status bar, use whatever you'd like
		font = "sans-7"
	}
	statusbar "mystatusbar"
	{
		# you can put the status bar anywhere; top, bottom, left, right
		position = "top"
		height = 0
		width = 0
		# this section allows you to use the mouse to tag windows and switch to them, leave it as it is for now unless you know what you're doing
		taglist "mytaglist"
		{
			x = -1
			y = -1
			mouse 
			{
				modkey = {}
			        button = "1"
				command = "tag_view"
			}
			mouse
			{
		        	modkey = {"Mod4"}
		        	button = "1"
			        command = "client_tag"
			}
      			mouse
			{
			        modkey = {}
    		   		button = "3"
				command = "tag_toggleview"
   			}
      			mouse
			{
	        		modkey = {"Mod4"}
	        		button = "3"
	        		command = "client_toggletag"
		    	}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_viewnext"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_viewprev"
      			}
		}
		# this section is basically the same...
    		layoutinfo "mylayoutinfo"
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "1"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "3"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
    		}
		# and so is this one....
    		tasklist "mytasklist" 
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "client_focusnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "client_focusprev"
        			# arg = ""
     			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "4"
        			command = "client_swapnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "5"
        			command = "client_swapprev"
       				# arg = ""
      			}
      			align = "left"
      			show_icons = false
      			show_all = false
    		}
		# this section is rather important.  This is your statusbar widget for the clock.  This will put a clock at the far right side of your monitor. 
		# you can add other widgets too, like mpd info, gmail scripts, etc.
	    	textbox clock  # "clock" is the name of your widget
		{
			text = "-" # the - will be replaced by the date and time
		}
  	}
	# these are your tags.  Basically it defines how the statusbar is set up to look.  You can add/remove as many tags as you'd like, change their names, how their behave, etc.
  	tags
	{
		tag ":main" # :main is the display name of the tag.  You can change this to say whatever you want, it's completely up to you.
		{
			layout = "max" # this tells the tag how to display windows.  "max" forces all your windows in that tag to be...maximized!  You can still make them float by moving them by hand
			mwfact = 0.500000 # leave this for now
      			nmaster = 1 # leave this for now
      			ncol = 1 # leave this for now
    		}
    		tag ":devel"
		{
	      		layout = "tile"
	      		mwfact = 0.500000
 	     		nmaster = 1
	      		ncol = 1
		}
    		tag ":term"
		{
      			layout = "tile"
      			mwfact = 0.500000
     			nmaster = 1
      			ncol = 1
    		}
	}
	colors
	{
		# here we define our colors.  I'll have an example screenshot at the bottom of this page.  You can change these colors to whatever you want.
		normal_border = "#777777"  # window border when selected
        	normal_bg = "#000000" # background for the statusbar
        	normal_fg = "#a8bcff" # foreground color for the statusbar (unselected tags)
       		focus_border = "#000000" # border color of fucsed windows
        	focus_bg = "#000000" # focused background for the status bar, it's what decides the color for the background of the selected tag
        	focus_fg = "orange" # focused foreground color, the color of the selected tag and title
    		urgent_bg = "#000000" # background
    		urgent_fg = "orange" # foreground
    		tab_border = "#ff0000" # I have absolutely no idea.
	}
	layouts
	{
		# you can add whichever images you want here.  They'll display as the layout options on the statusbar.  I use a black background, and these images are black
		# basically that "hides" them, but they're still available to use.
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"} ## use tilew.png for white
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"} ## use tileleftw.png for white
    		layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"} ## use maxw.png for white
	   	layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"} ## use spiralw.png for white
	    	layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"} ## use dwindlew.png for white
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"} ## use floatingw.png for white
	}
	# padding around screen.
	padding
	{
    		top = 0
    		bottom = 0
    		right = 0
    		left = 0
  	}
}
```
Customize that to your hearts content; you can do **whatever** you want with it.

**MORE TO COME**

---

### Post by rjmdomingo2003 on 2008-01-27
Very good complement to shearn's excellent guide.

I'll tinker with the awesomerc now..:KS

---

### Post by mali2297 on 2008-01-27
I predict that awesome will become the new fluxbox/openbox.:popcorn:

Just two questions..

Why install libconfuse-dev from the repositories? (It will be the wrong version.)

Why not install confuse 2.6 with checkinstall as well?

---

### Post by ~LoKe on 2008-01-27
> **mali2297 said:**
> Why install libconfuse-dev from the repositories? (It will be the wrong version.)

Why not install confuse 2.6 with checkinstall as well?

That's what I get from carrying things over from the old installation. ;)  I'll modify the guide to remove that step.

As for checkinstall, I hadn't really thought too much about it.  I figured I'd just add it in for awesome itself (personally, I keep all libraries even if I don't need them).  But for the sake of consistency and elegance, I'll make the amendment.

Thanks!

---

### Post by PharaohSD on 2008-01-27
thanks loki!

actually got this to work on ubuntu this time lol, i moved to arch just to try awesome, liked it, but couldn't get my wireless to work, so i moved back and saw your post

----
few things i had to change from your guide

if i used your .xinitrc x gave me an error when loading awesome from gdm saying X-- could not find $HOME/.xinitrc and falling back to default (which was gnome)

what i changed was :
after gksudo blah blah awesome.desktop

> [Desktop Entry]
Encoding=UTF-8
Name=Awesome
Comment=GDM entry for AwesomeWM
Exec=/home/username/awesome.sh
Icon=
Type=Application

then 

sudo gedit /awesome.sh

> #!/bin/bash
#AUTOSTARTED APPS AND SETTINGS

#STATUSBAR TEXT

#Launch awesome
feh --bg-scale /home/username/path/to/pic.jpg &
gnome-settings-daemon &
restricted-manager --check &
sleep 5 && exec awesome

then 

> chmod +x awesome.sh

and then logged out, changed session, and it worked! :)

not sure why the original xinitrc didn't work.........

and another thing the awesome-monitor (clock) didn't work :s....

thanks again!

---

### Post by ~LoKe on 2008-01-27
Hm...not sure why it didn't work.  I thought I could skip the executable script, but apparently not.  Looks like I have a few edits to make. :)

**EDIT**: The corrections have been made.  Thanks again!  As for your clock, try editing /usr/bin/awesome-monitor and changing:
> echo 1 widget_tell clock
To...
> echo 0 widget_tell clock

---

### Post by PharaohSD on 2008-01-27
:S ok, so having the same problem i had with arch

when i login to Awesome right away *i set it to auto log me in when i boot up* my wireless doesn't work. but when i log in to gnome, the little wireless icon in the top right corner starts to work, and then i am connected. then i need to log out, then log in to awesome, then the internet works. can someone tell me how to get my wireless to work in awesome right away, aka what daemon or something do i need to add to my awesome.sh ?

another thing loke: how do i "move" my windows when i put it in floating mode. like all the windows are ontop of each other when i do (Mod 4, ctrl, space) until the mode is set to float, but i still can't re-positon/re-adjust the open programs.

---

### Post by ~LoKe on 2008-01-27
Ah, I'll add a section for that, too.  But quickly: Mod4 (windows key) + left click allows you to move a window.  Mod4 + right click for resizing.

As for your wireless; that's a good question.  I'll try to find out which daemon controls that (unless someone else finds it first).

---

### Post by Gigamo on 2008-01-27
I would suggest using WICD for wireless. That puts up a system daemon regardless of which WM/DE you're in.

---

### Post by rjmdomingo2003 on 2008-01-28
Is it possible to put icons on the desktop?

---

### Post by mali2297 on 2008-01-28
> **rjmdomingo2003 said:**
> Is it possible to put icons on the desktop?

Perhaps [idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page") will work? (In the repos.)

Personally, I prefer to have a clean desktop.

---

### Post by rjmdomingo2003 on 2008-01-28
> **mali2297 said:**
> Perhaps [idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page") will work? (In the repos.)

Personally, I prefer to have a clean desktop.
I just need very few icons for others who use my laptop (READ: the wife), and are boggled with the absence of these icons.

I currently have fluxbox as my preferred WM, and have set-up idesk for the icons. I'll try inserting idesk into ~/awesome.sh and see if it works.

---

### Post by PharaohSD on 2008-01-29
loke, how do i enable a native awesome theme, (your murina 333/ or your current theme (which is really cool btw :p) , i was using gnome-setting-blah, but i want something more lightweight.....not sure how to install your theme

---

### Post by ~LoKe on 2008-01-29
> **PharaohSD said:**
> loke, how do i enable a native awesome theme, (your murina 333), i was using gnome-setting-blah, but i want something more lightweight.....not sure how to install your theme

Well, simply extract the contents into ~/.themes and then use gtk-theme-switch to apply your theme.

```
sudo apt-get install gtk-theme-switch
cd ~ && tar xvf Murrina*.gz
mv Murrina* ~/.themes/
```
And add this to ~/.xinitrc or ~/.script/awesome.sh:
```
switch2 Murrina333 &
```

---

### Post by spomi on 2008-01-29
I just want to point out that you don't need to restart X after recompiling DWM. Just kill your current dwm process and start another one. All your x clients will still be there (although the tags you set might be gone).

---

### Post by rjmdomingo2003 on 2008-01-29
Finally got my awesome desktop set up last night! Thanks Loke~

I had around 7 tags, and was thinking how come the background is not displayed on the first tag, but displayed on the others. I looked for differences between them in my awesomerc, and changed the first tag's layout to floating (from max), and voila!, background now visible.

Is this behavior normal or what it's supposed to be? Regardless, I'm stoked!

---

### Post by ~LoKe on 2008-01-29
> **rjmdomingo2003 said:**
> Finally got my awesome desktop set up last night! Thanks Loke~

I had around 7 tags, and was thinking how come the background is not displayed on the first tag, but displayed on the others. I looked for differences between them in my awesomerc, and changed the first tag's layout to floating (from max), and voila!, background now visible.

Is this behavior normal or what it's supposed to be? Regardless, I'm stoked!

You mean your wallpaper wasn't displaying when your tag was set to max?  That'd odd and definitely shouldn't happen.  What *did* you see?

---

### Post by rjmdomingo2003 on 2008-01-29
> **~LoKe said:**
> You mean your wallpaper wasn't displaying when your tag was set to max?  That'd odd and definitely shouldn't happen.  What *did* you see?
Yes, the wallpaper wasn't displayed on the "maxed" tag. Only a black screen, with conky & the statusbar visible.

Also, my gnome-terminal is set to pseudo-transparency (don't have xcompmgr/transset installed yet). When I open the terminal, I see the portion of the wallpaper underneath the area covered by the terminal (that made sense?). Very similar behavior when I'm in fluxbox, when a maximized client (e.g. Kazehakase) is covered by a floating client (e.g. terminal), and I can see a portion of the wallpaper.

Weird.

---

### Post by Garret88 on 2008-01-29
Is there a deb of this wm?

only installing the first packages  [FONT=monospace]aptitude wants to install 336MB of  things :lolflag:


Not bad for a  "light" wm  :P


[/FONT][LEFT][FONT=monospace]In debian-packages  there is  [http://ftp.de.debian.org/debian/pool/main/a/awesome/awesome_2.1-1_i386.deb](http://ftp.de.debian.org/debian/pool/main/a/awesome/awesome_2.1-1_i386.deb)


But is not installable for a dependecy error(libc6  :()[/FONT][/LEFT]

---

### Post by ~LoKe on 2008-01-29
> **Garret88 said:**
> only installing the first packages  aptitude wants to install 336MB of  things

Most of those packages were compilers and other stuff needed to compile _anything_ from source.  If you needed all that, then your system must not be terribly up to date, or you've never compiled anything. ;)

I could make you a .deb from Hardy, but you'd need the dependencies just the same (and it would be a bad idea to install a Hardy package on anything but Hardy).

---

### Post by Garret88 on 2008-01-29
> **~LoKe said:**
> Most of those packages were compilers and other stuff needed to compile _anything_ from source.  If you needed all that, then your system must not be terribly up to date, or you've never compiled anything. ;)

I could make you a .deb from Hardy, but you'd need the dependencies just the same (and it would be a bad idea to install a Hardy package on anything but Hardy).

I hate compiling... i prefer .deb...

Ubuntu repo don't have awesome 2.0 too :mad:, they don't have nothing about awesome :(...

---

### Post by ~LoKe on 2008-01-29
> **Garret88 said:**
> Ubuntu repo don't have awesome 2.0 too :mad:, they don't have nothing about awesome :(...
Awesome 2.0 or older is in Gutsy repos, but Awesome 2.1 is available from source only.

---

### Post by Garret88 on 2008-01-29
> **~LoKe said:**
> Awesome 2.0 or older is in Gutsy repos, but Awesome 2.1 is available from source only.

Through synaptic searching"awesome" i don't find anything...

2.1 version has a long changelog than the 2.0 ?

---

### Post by Gigamo on 2008-01-29
awesome 2.0 is only in Hardy's repo's, not Gutsy's afaik. Your only option is to compile from source, and get the libs. You'll probably need them again at a later date when you want to compile something else, so where's the problem...

---

### Post by GamingMazter on 2008-01-29
Thanks Matey :D

---

### Post by ~LoKe on 2008-01-29
> **GamingMazter said:**
> Thanks Matey :D

You're very welcome. :)

---

### Post by rjmdomingo2003 on 2008-01-30
I use nautilus, and bound it to one of the keybindings (i.e. Mod4 + n) with the command "exec nautilus".

When I type the keybinding, the wallpaper changed to my gnome desktop! Odd that it has the same behavior as fluxbox.

I thought of making the command "exec nautilus --no-desktop". I don't know yet if it would work.

---

### Post by ~LoKe on 2008-01-30
Haha.  Yeah, running nautilus would present you with a second, overlaying desktop.  In fact, this is what I have in my **~/.awesomerc**
```
key
	{
		modkey = {"Mod4"}
		key = "n"
		command = "spawn"
		arg = "exec nautilus --no-desktop"
	}
```

---

### Post by rjmdomingo2003 on 2008-01-30
> **~LoKe said:**
> Haha.  Yeah, running nautilus would present you with a second, overlaying desktop.  In fact, this is what I have in my **~/.awesomerc**
```
key
	{
		modkey = {"Mod4"}
		key = "n"
		command = "spawn"
		arg = "exec nautilus --no-desktop"
	}
```
Thanks ~Loke! I really am enjoying tinkering with the awesomerc. I'll try to show a screenie sometime in the future for everyone to criticize. :)

---

### Post by Gigamo on 2008-01-30
LoKe, would you think it is possible to use conky / dzen (dzonky) to put info in the statusbar? A la XMonad-way.

The possibilities would be endless, and could use minimalistic icons then too, like in [this](http://phraok.free.fr/config/xmonad/31.12.2007/desktop-last-07..png) pic (the statusbar).

---

### Post by mali2297 on 2008-01-30
> **Gigamo said:**
> LoKe, would you think it is possible to use conky / dzen (dzonky) to put info in the statusbar? A la XMonad-way.

The possibilities would be endless, and could use minimalistic icons then too, like in [this](http://phraok.free.fr/config/xmonad/31.12.2007/desktop-last-07..png) pic (the statusbar).

I haven't tried to integrate conky with awesome myself but it should be possible. Have you read this [tip]("http://awesome.naquadah.org/wiki/index.php/Making_a_Status_Bar_III")?

---

### Post by Gigamo on 2008-01-30
Yep, I have tried that one. Didn't turn out to work very well, so that's why I'm asking here :)

---

### Post by mali2297 on 2008-01-30
> **Gigamo said:**
> Yep, I have tried that one. Didn't turn out to work very well, so that's why I'm asking here :)

In what way didn't it work? Is there some feature that you miss?

---

### Post by Gigamo on 2008-01-30
No, just the "echo 0 widget_tell" didn't work in conky. Instead of echo'ing to the widget, it just displayed "echo 0 widget_tell" in conky itself :D

---

### Post by ~LoKe on 2008-01-30
I'm not entirely sure as I haven't tried to do it, but have you tried something as simple as:
**~/.conkyrc**
```
background yes
no_buffers yes
out_to_console yes
update_interval 1
uppercase no
use_spacer no
total_run_times 0

TEXT
0 widget_tell sysinfo net: ${downspeedf eth0}/${upspeedf eth0}
```

And in your ~/.xinitrc:
```

exec conky &
```
Before exec awesome.

---

### Post by Gigamo on 2008-01-30
> **~LoKe said:**
> I'm not entirely sure as I haven't tried to do it, but have you tried something as simple as:
**~/.conkyrc**
```
background yes
no_buffers yes
out_to_console yes
update_interval 1
uppercase no
use_spacer no
total_run_times 0

TEXT
0 widget_tell sysinfo net: ${downspeedf eth0}/${upspeedf eth0}
```

And in your ~/.xinitrc:
```

exec conky &
```
Before exec awesome.

Yep. I did exactly what the wiki said. Instead of conky sending it to the widget, it just displayed "0 widget tell ...".

My textbox is called "mpd" and this was under the TEXT line in conkyrc:

```
0 widget_tell mpd ${color .... etc
```

EDIT: Another question; is it possible to make the statusbar thinner without changing the fontsize (when using a bitmapped font that has only 1 size)?

---

### Post by rjmdomingo2003 on 2008-01-30
Got idesk to work with awesome. Here's my first awesomeWM screenshot.

---

### Post by ~LoKe on 2008-01-31
> **Gigamo said:**
> 
EDIT: Another question; is it possible to make the statusbar thinner without changing the fontsize (when using a bitmapped font that has only 1 size)?

Unless I'm misunderstanding you, yes.  You can change this section in **~/.awesomerc**:
```
statusbar "mystatusbar"
	{
		position = "bottom"
		height = 0 ## here
		width = 0
```

---

### Post by Gigamo on 2008-01-31
> **~LoKe said:**
> Unless I'm misunderstanding you, yes.  You can change this section in **~/.awesomerc**:
```
statusbar "mystatusbar"
	{
		position = "bottom"
		height = 0 ## here
		width = 0
```

Thanks, that was it indeed.

To come back to the conky thing, I just tried again and still didn't work, this is my conkyrc:

```
background no
out_to_console yes
update_interval 2
use_spacer no
total_run_times 0
TEXT
0 widget_tell mpd $mpd_artist - $mpd_title ${mpd_bar 5,70} :: ${battery BAT1} :: ${execi 15 ~/.scripts/check_gmail.sh} :: ${time %d %b %H:%M}
```

my textbox

```
        textbox mpd
            {}
```

Just like explained in the wiki. However, this gave me no output in my statusbar, instead, it would display all that on the bottom left of my screen in its separate conky window, including "0 widget_tell mpd".

Hope anyone finds this out.

---

### Post by ~LoKe on 2008-01-31
I've been trying to figure it out for a while now.  I'm still clueless.  The conkyrc implies that conky knows how to handle widgets, which I didn't know.

---

### Post by Gigamo on 2008-01-31
> **~LoKe said:**
> I've been trying to figure it out for a while now.  I'm still clueless.  The conkyrc implies that conky knows how to handle widgets, which I didn't know.

Yes I was doubting about that as well. I was thinking, would it not be possible to tell the textbox in .awesomerc to exec conky?

---

### Post by ~LoKe on 2008-01-31
> **Gigamo said:**
> Yes I was doubting about that as well. I was thinking, would it not be possible to tell the textbox in .awesomerc to exec conky?

I tried exec conky | awesome-client
But that didn't work.

---

### Post by Gigamo on 2008-02-01
Hmmm, a new issue arose here. You know when you mouseover a window in awesome it automatically gets focus the second you mouseover it. Since today there is a delay doing so. It will take 2 to 3 seconds before the window i'm mousing over actually gets focus, and I have no idea why. This only happens with urxvt.

---

### Post by rjmdomingo2003 on 2008-02-01
> **Gigamo said:**
> Hmmm, a new issue arose here. You know when you mouseover a window in awesome it automatically gets focus the second you mouseover it. Since today there is a delay doing so. It will take 2 to 3 seconds before the window i'm mousing over actually gets focus, and I have no idea why. This only happens with urxvt.
Am using gnome-terminal, and that doesn't happen. Immediately, upon mouseover, window's focused. Maybe it's app-dependent?

---

### Post by Gigamo on 2008-02-01
Yeah I only have it when I switch from urxvt to urxvt windows, any other is working fine. It's weird.

---

### Post by rjmdomingo2003 on 2008-02-01
> **Gigamo said:**
> Thanks, that was it indeed.

To come back to the conky thing, I just tried again and still didn't work, this is my conkyrc:

```
background no
out_to_console yes
update_interval 2
use_spacer no
total_run_times 0
TEXT
0 widget_tell mpd $mpd_artist - $mpd_title ${mpd_bar 5,70} :: ${battery BAT1} :: ${execi 15 ~/.scripts/check_gmail.sh} :: ${time %d %b %H:%M}
```

my textbox

```
        textbox mpd
            {}
```

Just like explained in the wiki. However, this gave me no output in my statusbar, instead, it would display all that on the bottom left of my screen in its separate conky window, including "0 widget_tell mpd".

Hope anyone finds this out.
Could you try this:
```
$0 widget_tell mpd $mpd_artist - $mpd_title ${mpd_bar 5,70} :: ${battery BAT1} :: ${execi 15 ~/.scripts/check_gmail.sh} :: ${time %d %b %H:%M}
```

Adding the $ sign at the start could be the deal-breaker.

---

### Post by ~LoKe on 2008-02-01
Didn't do it for me, but I probably did something wrong. ;)

---

### Post by Gigamo on 2008-02-01
Didn't work here either.

---

### Post by mali2297 on 2008-02-01
I can confirm that the howto for conky doesn't work. I think it's outdated.

> **Gigamo said:**
> Hmmm, a new issue arose here. You know when you mouseover a window in awesome it automatically gets focus the second you mouseover it. Since today there is a delay doing so. It will take 2 to 3 seconds before the window i'm mousing over actually gets focus, and I have no idea why. This only happens with urxvt.

I don't experience this problem. Do you use some kind of transparency?

---

### Post by Gigamo on 2008-02-01
> **mali2297 said:**
> I can confirm that the howto for conky doesn't work. I think it's outdated.



I don't experience this problem. Do you use some kind of transparency?

I use inheritPixmap.

Here's the urxvt part of my Xdefaults:

```
!urxvt settings
urxvt*font: 		xft:DejaVu Sans Mono:pixelsize=9
urxvt*scrollBar:	false
urxvt.background:	#262626
urxvt.foreground:	#ffffff
URxvt.externalBorder:     1
URxvt.internalBorder:     2
URxvt.borderLess:         true
urxvt.tintColor:          #262626
!urxvt.urgentOnBell:       true
urxvt.mouseWheelScrollPage:   True
urxvt.cursorColor:        #99CCFF
urxvt.pointerColor:       #99CCFF
urxvt.borderColor:        #000000
urxvt.geometry:           80x21
urxvt.inheritPixmap:      true
!urxvt.shading:            50
URxvt.termName: rxvt
!URxvt.transparent: true
URxvt.imLocale: pl_PL.UTF-8
URxvt.saveLines: 500
URxvt.urlLauncher:      firefox
```

---

### Post by rjmdomingo2003 on 2008-02-02
I've managed to pipe conky info into the AwesomeWM statusbar. It was a workaround just to eliminate my conky instance, which adds another bar on my desktop.

This was how I did it:

1. Add the conky textbox in your awesomerc as so:

```
textbox conky
                {
                        fg = "#23b7f4"        
                        text = "-"
                }
```

Make sure this comes before or after other textboxes, whichever sequence you want it to appear in the statusbar.

2. Add this line into your awesome-monitor:

```
echo 0 widget_tell conky "`conky` " | /usr/local/bin/awesome-client
```

3. Here's my conkyrc:

```
background yes
no_buffers yes
out_to_console yes
update_interval 1
use_spacer no
total_run_times 0
alignment top_left

TEXT
[Dubai - ${execi 100 /home/melski/scripts/weather/weather.sh "MEA|AE|AE005|DUBAI"}]  [HDD - ${fs_free /media/sda2} free, ${execi 300 nc localhost 7634 | cut -c29-30 ;}C]
```

Note that "0 widget_tell ..." ain't included since it's in your awesome-monitor. 

About the *alignment top_left*, I'll explain later.

4. Edit your ~/awesome.sh or your startup script (i.e. ~/.xinitrc) by removing *conky &*, **IF IT'S THERE**.

5. Restart.

6. Upon reaching the Awesome desktop, type into your console:

```
killall conky
```

Then you should get the screenshot.

Now some explanations..

a) In my conkyrc, I've placed it in top left since another conky instance appears at the bottom left. Maybe conky's default position?! I've placed my statusbar on top, so it actually covers this conky's instance.

b) Now, you'll notice just dashes &/or non-conky info in your statusbar, but upon doing step 6, conky will be piped into the statusbar.

I've tried adding *killall conky* into awesome.sh, but still, I need to do step 6 for conky info to be displayed.

Guess we're a step closer to "perfection". Feedback please on what you're getting so we can help each other.

---

### Post by Gigamo on 2008-02-02
You rock! Giving this a try.

---

### Post by rjmdomingo2003 on 2008-02-02
> **Gigamo said:**
> You rock! Giving this a try.
Tell me if it works for you too.. even if it's just a workaround. :)

---

### Post by ~LoKe on 2008-02-02
I tried it out, but it's only "half" working for me.  I see "CPU0: " in my status bar, but that it.  However, I see a complete conky instance elsewhere on my screen.

```
while true
do
#echo 0 widget_tell mpd "[MPD: `mpc | sed -n '1p'`] :: `mpc | grep "#" | cut -c 1-9`" | /usr/local/bin/awesome-client &
echo 1 widget_tell clock "[`date '+%a %b %d %r'`]" | /usr/local/bin/awesome-client
echo 0 widget_tell conky "`conky` " | /usr/local/bin/awesome-client
sleep 1
done
```
```
background yes
no_buffers yes
out_to_console yes
update_interval 1
use_spacer no
total_run_times 0
alignment bottom_right

TEXT
${color}CPU0: ${color D7D3C5}${cpu cpu1}% ${color}CPU1: ${color D7D3C5}${cpu cpu2}% ${color}CPU2: ${color D7D3C5}${cpu cpu3}% ${color}CPU3: ${color D7D3C5}${cpu cpu4}%
```

---

### Post by Gigamo on 2008-02-02
Before I try, is it possible to show small .xbm images in conky? If so, how?

---

### Post by rjmdomingo2003 on 2008-02-02
> **~LoKe said:**
> I tried it out, but it's only "half" working for me.  I see "CPU0: " in my status bar, but that it.  However, I see a complete conky instance elsewhere on my screen.

```
while true
do
#echo 0 widget_tell mpd "[MPD: `mpc | sed -n '1p'`] :: `mpc | grep "#" | cut -c 1-9`" | /usr/local/bin/awesome-client &
echo 1 widget_tell clock "[`date '+%a %b %d %r'`]" | /usr/local/bin/awesome-client
echo 0 widget_tell conky "`conky` " | /usr/local/bin/awesome-client
sleep 1
done
```
```
background yes
no_buffers yes
out_to_console yes
update_interval 1
use_spacer no
total_run_times 0
alignment bottom_right

TEXT
${color}CPU0: ${color D7D3C5}${cpu cpu1}% ${color}CPU1: ${color D7D3C5}${cpu cpu2}% ${color}CPU2: ${color D7D3C5}${cpu cpu3}% ${color}CPU3: ${color D7D3C5}${cpu cpu4}%
```

Try this:

```
TEXT
CPU0: ${cpu cpu1}% CPU1: ${cpu cpu2}% CPU2: ${cpu cpu3}% CPU3: ${cpu cpu4}%
```

Guess the *fg color* in the conky textbox somehow conflicts with your conky's various color.

For the other conky instance , move it to where the statusbar is.

---

### Post by ~LoKe on 2008-02-02
Ah, yes, that's better!  It's displaying in my statusbar correctly (though, it's not refreshing), so I just gotta tinker with it some more.

Thanks!

I'll add it to the FAQ and credit you, unless you're against it.

---

### Post by Gigamo on 2008-02-02
Still trying to figure out how I can display some small images in conky :)

Some of these is what I'd like to use: [http://phraok.free.fr/config/dzen/bitmaps/](http://phraok.free.fr/config/dzen/bitmaps/)

---

### Post by Gigamo on 2008-02-02
> **Gigamo said:**
> Still trying to figure out how I can display some small images in conky :)

Some of these is what I'd like to use: [http://phraok.free.fr/config/dzen/bitmaps/](http://phraok.free.fr/config/dzen/bitmaps/)

Hmm, well, I tried out dzen2 together with conky (and a script called dzonky! :D), and it works out pretty well. However, I'm having an issue that apart from conky outputting info to dzen, its also still putting its own window up on the bottom left of my screen.

Just editing this one, here's my progress, as you can see theres conky on the bottom as well, but I like my new statusbar info:

---

### Post by ~LoKe on 2008-02-02
Conky still won't work for me.  It updates on my desktop, but the one that appears in my statusbar won't refresh.

---

### Post by rjmdomingo2003 on 2008-02-03
> **~LoKe said:**
> Ah, yes, that's better!  It's displaying in my statusbar correctly (though, it's not refreshing), so I just gotta tinker with it some more.

Thanks!

I'll add it to the FAQ and credit you, unless you're against it.
The reason, maybe, why conky is not refreshing is coz of the awesome.sh (or xinitrc) not having *conky &*.
Now that you've mentioned it, I remember the statusbar clock stuck to the time in the screenie. I'll try adding *conky &* into awesome.sh, and see if it refreshes.

I would be honored if you'd credit me in the FAQ.

I really am keen in solving this issue with you guys so let's help each other, yeah?

---

### Post by rjmdomingo2003 on 2008-02-03
> **Gigamo said:**
> Hmm, well, I tried out dzen2 together with conky (and a script called dzonky! :D), and it works out pretty well. However, I'm having an issue that apart from conky outputting info to dzen, its also still putting its own window up on the bottom left of my screen.

Just editing this one, here's my progress, as you can see theres conky on the bottom as well, but I like my new statusbar info:
Add:

```
alignment top_left
```

into your conkyrc, and see what happens.

Congratulations in managing to have those images in the statbar but what struck me the most is that you're d'ling Dexter Season 2. You're a fan? I am. That's a great series, of course, 2nd only to Lost. Enjoy watching, & I'll stop with the off-topic.:)

---

### Post by Gigamo on 2008-02-03
Haha yes; Dexter owns :D

I also have another question. Is is possible to resize the images for the layouts manually? I'd like them to be a little smaller. At the moment they resize according to the size of the statusbar.

---

### Post by rjmdomingo2003 on 2008-02-03
> **Gigamo said:**
> Haha yes; Dexter owns :D

I also have another question. Is is possible to resize the images for the layouts manually? I'd like them to be a little smaller. At the moment they resize according to the size of the statusbar.
Have you tried using Gimp for resizing?

---

### Post by Gigamo on 2008-02-03
> **rjmdomingo2003 said:**
> Have you tried using Gimp for resizing?

Well the problem is even when I use a 8x8 image it will still resize to the size of the statusbar;

---

### Post by ~LoKe on 2008-02-03
Can I get your ~/.conkyrc, /usr/bin/awesome-monitor, and relevant conky section from ~/.awesomerc?  I gotta get this figured out before I can put it in the guide.  Maybe .xinitrc/awesome.sh as well.

---

### Post by rjmdomingo2003 on 2008-02-03
> **~LoKe said:**
> Can I get your ~/.conkyrc, /usr/bin/awesome-monitor, and relevant conky section from ~/.awesomerc?  I gotta get this figured out before I can put it in the guide.  Maybe .xinitrc/awesome.sh as well.
Guess you're referring to me? If so, I'll give these to you later..quite busy in the office..:)

I've actually removed conky from the statbar since it ain't refreshing, and adapted scripts & commands to display the info I need (e.g. free disk space, battery, weather).

By the way, I preferred your previous avatar (the pink girl).. just an opinion.

---

### Post by ~LoKe on 2008-02-04
Ah, so it wasn't refreshing for you either, then?  I see. :D

As for my avatar, well...[text](http://ubuntuforums.org/showthread.php?t=686317).

---

### Post by rjmdomingo2003 on 2008-02-04
> **~LoKe said:**
> As for my avatar, well...[text](http://ubuntuforums.org/showthread.php?t=686317).
OK, now I get it. Thanks for the heads up.

---

### Post by rjmdomingo2003 on 2008-02-04
> **~LoKe said:**
> Can I get your ~/.conkyrc, /usr/bin/awesome-monitor, and relevant conky section from ~/.awesomerc?  I gotta get this figured out before I can put it in the guide.  Maybe .xinitrc/awesome.sh as well.
~Loke, still awake? Attached as you wish..:)

---

### Post by rjmdomingo2003 on 2008-02-04
Am afraid I was the one sleeping..:)

OK here they are, ~Loke.

---

### Post by Gigamo on 2008-02-14
Version 2.2-rc1 is out. I have tried it but they made massive changes to the config again, and I can't be arsed fiddling around with it atm. The features look promising though.

---

### Post by ~LoKe on 2008-02-18
Hm...version 2.2 looks moderately interesting.  Of course, being the person I am, I can't resist trying it even though I have to re-write my config.

---

### Post by miggys on 2008-02-18
I love awesome!  Is anybody still struggling to/interested in getting conky info to the status bar?  I may have some suggestions if you're curious.

---

### Post by rjmdomingo2003 on 2008-02-19
> **miggys said:**
> I love awesome!  Is anybody still struggling to/interested in getting conky info to the status bar?  I may have some suggestions if you're curious.
Please share your suggestions. I've abandoned conky and adopted scripts to output system info in the statbar. It would be kewl if we could manage to display conky flawlessly.

---

### Post by Gigamo on 2008-02-19
I think you should use dzen2 in combo with conky to do that succesfully. Also, the new features like graphs, progressbars etc are in my opinion even better than conky :)

---

### Post by rjmdomingo2003 on 2008-02-19
> **Gigamo said:**
> I think you should use dzen2 in combo with conky to do that succesfully. Also, the new features like graphs, progressbars etc are in my opinion even better than conky :)
Do these new features come with v 2.2rc? If so, maybe you could start a how-to for that version?:KS

---

### Post by Gigamo on 2008-02-19
> **rjmdomingo2003 said:**
> Do these new features come with v 2.2rc? If so, maybe you could start a how-to for that version?:KS


They were there in 2.1 as well. You just define a graph section, like a textbox, but with graph properties (look up "man awesomerc").

And the info you pipe to a graph or progressbar needs to be a percentage (scale of 100), but without the % (you need to sed/cut that out).

From 2.1 to 2.2 is totally not hard however, you will mostl ikely only have to change/remove 5 lines of code. And the new tool in 2.2, "awesome -k" tells you what is wrong in your config file. I'm using it for 2 days so far and I've hadno problems, and I'm loving it =D

---

### Post by miggys on 2008-02-19
I think conky will be faster/more efficient than running a bunch of bash scripts though its probably not too significant.  So, you probably already have something feeding awesome-client, include something like this:

```
while true; do
...
conky -c /pathto/conkyrc | awesome-client &
sleep 2;
done

```

and in your conky include something like this (here's mine at least):

```

background yes
no_buffers yes
out_to_console yes
update_interval 1 
uppercase no
use_spacer no
total_run_times 1 # this part is important!

Text
0 widget_tell info1 ${variable1} [,${variable2}]
...

```

you will only pipe to awesome-client once it is done giving output so you need conky to run once and then stop and then just call it again.

Now, if you already have conky installed through a package it will probably also put all your TEXT to the desktop.  To avoid that try compiling conky from source from its website with simply ./configure, make, make install.  But in the configure line do this:

```

./configure --disable-own-window --disable-x11 --disable-double-buffer --disable-xdamage --disable-xft

```

and any other customization you want.  It's possible that --disable-x11 is enough but I haven't tried that yet.  I just disabled all the things that seemed to have anything to do with X.

Let me know if there are any issues.

Miggys

---

### Post by miggys on 2008-02-19
PS.  I also am a fan of the progressbars and graphs in awesome.  I haven't tried to pass a conky graph/progressbar to awesome.  I kind of doubt its possible.  However, I do pipe conky values to awesome progressbars.  I don't have any graphs because I can't think of anything that would be useful to have as a graph but they are cool enough that I might just make one anyway.

---

### Post by Gigamo on 2008-02-19
I'm putting cpuload in my graphs :)

miggys: can you show your own conkyrc, if you are piping to multiple widgets at the same time from 1 conkyrc?

---

### Post by miggys on 2008-02-19
No problem.

Please note that I now have **background no** otherwise conky would keep announcing it was going to the background.
```

background no
no_buffers yes
out_to_console yes
update_interval 1 
uppercase no
use_spacer no
total_run_times 1 
TEXT
0 widget_tell tb_mem ${mem}
0 widget_tell pb_mem ${memperc},${swapperc}
0 widget_tell tb_cpu ${cpu cpu0}
0 widget_tell tb_artist ${mpd_artist}
0 widget_tell tb_album ${mpd_album}
0 widget_tell tb_song ${mpd_title}
0 widget_tell pb_mpd ${mpd_percent}

```

Additionally, here's my status script

```

#!/bin/sh

awesomestatus() {
  MYTIME=`date +"%a %m.%d %I:%M%p"`
  PCMVOL=`amixer sget PCM | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
  MASTVOL=`amixer sget Master | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
  WAVVOL=`amixer sget Wave | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
}

sleep 1;
while true; do
  awesomestatus
  echo -e "0 widget_tell tb_time $MYTIME \n 0 widget_tell pb_vol $PCMVOL,$MASTVOL,$WAVVOL" | /usr/bin/awesome-client
  conky -c /home/mike/.awesome/conky | /usr/bin/awesome-client &
  sleep 2;
done

```

---

### Post by Gigamo on 2008-02-19
> **miggys said:**
> No problem.

Please note that I now have **background no** otherwise conky would keep announcing it was going to the background.
```

background no
no_buffers yes
out_to_console yes
update_interval 1 
uppercase no
use_spacer no
total_run_times 1 
TEXT
0 widget_tell tb_mem ${mem}
0 widget_tell pb_mem ${memperc},${swapperc}
0 widget_tell tb_cpu ${cpu cpu0}
0 widget_tell tb_artist ${mpd_artist}
0 widget_tell tb_album ${mpd_album}
0 widget_tell tb_song ${mpd_title}
0 widget_tell pb_mpd ${mpd_percent}

```

Additionally, here's my status script

```

#!/bin/sh

awesomestatus() {
  MYTIME=`date +"%a %m.%d %I:%M%p"`
  PCMVOL=`amixer sget PCM | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
  MASTVOL=`amixer sget Master | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
  WAVVOL=`amixer sget Wave | grep 'Front Left: Playback' | awk '{print $5}' | sed 's/\[//' | sed 's/%//' | sed 's/\]//'`
}

sleep 1;
while true; do
  awesomestatus
  echo -e "0 widget_tell tb_time $MYTIME \n 0 widget_tell pb_vol $PCMVOL,$MASTVOL,$WAVVOL" | /usr/bin/awesome-client
  conky -c /home/mike/.awesome/conky | /usr/bin/awesome-client &
  sleep 2;
done

```

Cool. Could you post a screenshot as well? :p

---

### Post by miggys on 2008-02-19
This is my first screenshot for anything ever so I hope I did it right :)

[[IMG]http://img220.imageshack.us/img220/1900/feb19hz4.th.jpg[/IMG]](http://img220.imageshack.us/my.php?image=feb19hz4.jpg)

The only thing I'm not totally satisfied with (at the moment) are the layout icons.  (ie tiling/float/max/dwindle/etc..)  I do not have the talent to make them myself (or perhaps just not the patience), and I haven't seen any anywhere...though I haven't looked too hard.

---

### Post by ~LoKe on 2008-02-22
I usually use the black ones so they blend in better.

---

### Post by Gigamo on 2008-02-24
**Conky update**

With credit to sec_ at the #awesome IRC channel, who created this modified version of Conky, this conky understands the "0 widget_tell widget" line, and by simply running conky (not in any loop or no | awesome-client behind it) will feed to widgets correctly.

And here's how you do it:

First remove any existing Conky from synaptic.

- Download the Conky 1.4.9 source from [http://conky.sourceforge.net](http://conky.sourceforge.net)

- Extract it to a directory.

- Then download the modified files here: [http://ca.hnvc.net/awesome-git/conky_p.tar](http://ca.hnvc.net/awesome-git/conky_p.tar)

Extract the 3 files in $PATH/conky-1.4.9/src/

Now compile:

```
./configure --disable-own-window --disable-x11 --disable-double-buffer --disable-xdamage --disable-xft
```
```
make
```
```
sudo checkinstall
``` (or sudo make install)

My conkyrc to make it all work:

```
background yes
no_buffers yes
update_interval 1 
uppercase no
use_spacer no
total_run_times 0
TEXT  
0 widget_tell cpu_freq ${freq_g}GHz 
0 widget_tell cpu0 ${cpu cpu0}
0 widget_tell cpu1 ${cpu cpu1}
0 widget_tell membar ${memperc},${swapperc}
0 widget_tell net ${downspeedf wlan0_rename}/${upspeedf wlan0_rename} 
0 widget_tell battery ${battery BAT1} (${battery_time BAT1})
0 widget_tell datum  ${time %a %b %d %H:%M} 

```

And what my statusbar looks like:

---

### Post by mali2297 on 2008-02-24
> **Gigamo said:**
> 
With credit to sec_ at the #awesome IRC channel, who created this modified version of Conky, this conky understands the "0 widget_tell widget" line, and by simply running conky (not in any loop or no | awesome-client behind it) will feed to widgets correctly.


Thanks, it seems to work.

---

### Post by miggys on 2008-02-24
Gigamo,

is your volume bar two-toned in that screenshot?  Is that a part of 2.2?

---

### Post by Gigamo on 2008-02-24
> **miggys said:**
> Gigamo,

is your volume bar two-toned in that screenshot?  Is that a part of 2.2?

What do you mean by two toned? And the widgets havent changed in 2.2, all you can do in 2.2 you can do in 2.1 (in terms of widgets).

---

### Post by foureight84 on 2008-03-01
I'm using arial size 8 for my status bar. however, upon startup, the fonts look a lot bigger than size 8. it is only after restarting awesome with mod4+ctrl+r that i get the set font size of 8. i'm thinking that the gnome-settings-daemon is causing that. I have tried using switch2 but the windows don't look as nice and i can't seem to change the font size for that. any advice?

also, is there anyway to center windows on the screen when you open them?

---

### Post by drcranium on 2008-03-03
Foureight:

I would look into Devilspie.  You can set workspaces, geometries etc for apps you specify.

Gigamo:

Thank you so much for putting that howto with conky up.  I've got a small problem now though.  Calling conky in my script that starts awesome does nothing.  Conky does not start until I start it in a terminal.  I've tried simply calling another script with sleep then calling conky but that does not work either.  Any ideas would be helpful.  I'm probably just overlooking something.

~/.scripts/awesome.sh:

```
exec /usr/bin/xbindkeys & 
exec nitrogen --set-scaled /home/luke/van.png &
exec trayer --transparent true --alpha 253 --width 5 --edge bottom --align right --distance 27 &
exec nm-applet &
exec xrdb -merge ./.Xdefaults &
exec conky & 
exec xcompmgr -c -C -f &
exec awesome

```

Xinitrc
```
# The following variable defines the session which is started if the user doesn't explicitly select a session

DEFAULT_SESSION=/home/luke/.scripts/awesome.sh

case $1 in
xfce4)
	exec startxfce4
	;;
fluxbox)
	exec startfluxbox 
	;;
*) 
	exec $DEFAULT_SESSION
	;;
esac

```

---

### Post by mali2297 on 2008-03-03
@drcranium:

Try removing *exec* in front of conky.

Here is the end of my xinitrc file:
```

conky &
exec awesome

```

---

### Post by drcranium on 2008-03-03
That didn't seem to work.  Now that I notice it, xcompmgr isn't being called correctly either.  The '-C' option should exclude trays from shadows but it is not being applied correctly either.  Now I'm just confused.

Edit:  I also tried putting the full path to each app.  No dice.

---

### Post by foureight84 on 2008-03-03
thanks for replying with devilspie. i actually found that but i can't seem to get it to work. i made a firefox.ds in the .devilspie directory. ran devilspie but it doesn't apply to current windows or new windows.

here is a copy of my devilspie's firefox.ds config:
```

(if
        (is (application_name) "firefox-bin")
    (begin
        (geometry "340x630+50+150")
    )
)

```
[B]
EDIT: it doesn't look like devilspie works with awesomewm[/B]

---

### Post by drcranium on 2008-03-03
Foureight:

I think I remember reading a post by Phrakture on the arch forums with a similar problem to yours.  He was using ratpoison but it he couldn't center windows or something.  I believe he tried PekWM and Devilspie.  Also, I dunno if you could try making your own layout?  That sounds impossible though.  Look at client_moveresize here:
[http://www.calmar.ws/awesome/awesomerc.5.html](http://www.calmar.ws/awesome/awesomerc.5.html)

I dunno if that helps you.

---

### Post by Yes on 2008-03-04
Does anyone know why nothing seems to be updating?  I've added things to ~/.scripts/awesome.sh and changed the font in .awesomerc, but when I restart it nothing changes.

e:  Ok, I got that working now by reinstalling Awesome.  But now the windows don't tile like they used to - if I open Firefox, it maximizes it's self, and then anything else I open are put on top of it.

e2:  I thing I got that, too.  Whenever I move the windows it goes into what I think is "max" mode, as apposed to tiled.  Is there anyway to switch back to tiled?  Also, is there any documentation on .awesomerc?  I've seen the man page and the wiki, but neither of those really explains what everything is.

Thanks.

---

### Post by aimran on 2008-03-27
Just an observation:

Some of the screenshots here don't actually show Awesome as a tiling window manager! I see windows on top of each other etc. :D

Is there something to modify the nature of Awesome to do this?

---

### Post by mali2297 on 2008-03-27
> **aimran said:**
> Just an observation:

Some of the screenshots here don't actually show Awesome as a tiling window manager! I see windows on top of each other etc. :D

Is there something to modify the nature of Awesome to do this?

You can change window layout on the fly: press **Mod4+Space** or click on the layout icon on the status bar.

You can also set rules so that certain applications (like Gimp) always have their windows *floating*.

---

### Post by aimran on 2008-03-27
> **mali2297 said:**
> You can change window layout on the fly: press **Mod4+Space** or click on the layout icon on the status bar.

You can also set rules so that certain applications (like Gimp) always have their windows *floating*.

Thank you :)

I'll try it out when I get home

---

### Post by mali2297 on 2008-03-27
**Version 2.2** (Morning Lemon) has been released. :-o
The development is rapid, it's hard to keep pace with it.

Time for a new HOWTO? :-s

---

### Post by corney91 on 2008-03-27
> **mali2297 said:**
> **Version 2.2** (Morning Lemon) has been released. :-o
The development is rapid, it's hard to keep pace with it.

Time for a new HOWTO? :-s
Dammit. I've only just got used to 2.1. Does anyone now if anything drastic about the .awesomerc has changed?

---

### Post by mali2297 on 2008-04-03
> **corney91 said:**
> Dammit. I've only just got used to 2.1. Does anyone now if anything drastic about the .awesomerc has changed?

I wouldn't say drastic, but there some options that have become obsolete and some other options that are new.

* In the *general* section, the options *focus_move_pointer* and *allow_lower_floats* are no longer.
* The widget *focustitle* has been removed, you can get the same function with *tasklist* though (with the option *show =  "focus"*).
* In the *rules* section, *not_master = false* has been replaced by *master = true*.

Those were the things that I had to change. 

Among the new options are *floating_placement* and two additional layout modes. Check the [man page]("http://www.calmar.ws/awesome/awesomerc.5.html") for further info.

---

### Post by corney91 on 2008-04-06
> **mali2297 said:**
> I wouldn't say drastic, but there some options that have become obsolete and some other options that are new.

* In the *general* section, the options *focus_move_pointer* and *allow_lower_floats* are no longer.
* The widget *focustitle* has been removed, you can get the same function with *tasklist* though (with the option *show =  "focus"*).
* In the *rules* section, *not_master = false* has been replaced by *master = true*.

Those were the things that I had to change. 

Among the new options are *floating_placement* and two additional layout modes. Check the [man page]("http://www.calmar.ws/awesome/awesomerc.5.html") for further info.
Awesome (no pun intended). Thanks. I have yet to install it, but when I find the time, I can't wait :)

---

### Post by MediaMike on 2008-04-11
Would someone mind looking at my awesomerc config and tell why whenever I try and add a key shortcut and the default tag I want it to open in causes me to start in the failover .awesomerc config.  My .awesomerc file is listed.

```
screen "0"
{
	general
	{
		# this is the border around your windows
		border = 1
		# snap to edges within 8 pixels
		snap = 8
		resize_hints = true
		opacity_unfocused = 100
		focus_move_pointer = false
		allow_lower_floats = false
		sloppy_focus = true
		new_become_master = true
		new_get_focus = true
		# this is the font you'll see on your status bar, use whatever you'd like
		font = "sans-7"
	}
	statusbar "mystatusbar"
	{
		# you can put the status bar anywhere; top, bottom, left, right
		position = "top"
		height = 0
		width = 0
		# this section allows you to use the mouse to tag windows and switch to them, leave it as it is for now unless you know what you're doing
		taglist "mytaglist"
		{
			x = -1
			y = -1
			mouse 
			{
				modkey = {}
			        button = "1"
				command = "tag_view"
			}
			mouse
			{
		        	modkey = {"Mod4"}
		        	button = "1"
			        command = "client_tag"
			}
      			mouse
			{
			        modkey = {}
    		   		button = "3"
				command = "tag_toggleview"
   			}
      			mouse
			{
	        		modkey = {"Mod4"}
	        		button = "3"
	        		command = "client_toggletag"
		    	}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_viewnext"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_viewprev"
      			}
		}
		# this section is basically the same...
    		layoutinfo "mylayoutinfo"
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "1"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "tag_setlayout"
        			arg = "+1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "3"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "tag_setlayout"
        			arg = "-1"
      			}
    		}
		# and so is this one....
    		tasklist "mytasklist" 
		{
      			x = -1
      			y = -1
      			mouse
			{
        			modkey = {}
        			button = "4"
        			command = "client_focusnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {}
        			button = "5"
        			command = "client_focusprev"
        			# arg = ""
     			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "4"
        			command = "client_swapnext"
        			# arg = ""
      			}
      			mouse
			{
        			modkey = {"Mod4"}
        			button = "5"
        			command = "client_swapprev"
       				# arg = ""
      			}
      			align = "left"
      			show_icons = false
      			show_all = false
    		}
		# this section is rather important.  This is your statusbar widget for the clock.  This will put a clock at the far right side of your monitor. 
		# you can add other widgets too, like mpd info, gmail scripts, etc.
	    	textbox clock  # "clock" is the name of your widget
		{
			text = "-" # the - will be replaced by the date and time
		}
  	}
	# these are your tags.  Basically it defines how the statusbar is set up to look.  You can add/remove as many tags as you'd like, change their names, how their behave, etc.
  	tags
	{
		tag ".:Main:." # :main is the display name of the tag.  You can change this to say whatever you want, it's completely up to you.
		{
			layout = "max" # this tells the tag how to display windows.  "max" forces all your windows in that tag to be...maximized!  You can still make them float by moving them by hand
			mwfact = 0.500000 # leave this for now
      			nmaster = 1 # leave this for now
      			ncol = 1 # leave this for now
    		}
    		tag ".:Inet:."
		{
	      		layout = "max"
	      		mwfact = 0.500000
 	     		nmaster = 1
	      		ncol = 1
		}
		tag ".:Torrent:."
		{
			layout = "max"
			mwfact = 0.500000
			nmaster = 1
			ncol = 1
		}
    		tag ".:Term:."
		{
      			layout = "floating"
      			mwfact = 0.500000
     			nmaster = 1
      			ncol = 1
    		}

		tag ".:IM:."
		{
			layout = "floating"
			mwfact = 0.500000
			nmaster = 1
			ncol = 1
		}
	}
	colors
	{
		# here we define our colors.  I'll have an example screenshot at the bottom of this page.  You can change these colors to whatever you want.
		normal_border = "#777777"  # window border when selected
        	normal_bg = "#000000" # background for the statusbar
        	normal_fg = "#a8bcff" # foreground color for the statusbar (unselected tags)
       		focus_border = "#000000" # border color of fucsed windows
        	focus_bg = "#000000" # focused background for the status bar, it's what decides the color for the background of the selected tag
        	focus_fg = "orange" # focused foreground color, the color of the selected tag and title
    		urgent_bg = "#000000" # background
    		urgent_fg = "orange" # foreground
    		tab_border = "#ff0000" # I have absolutely no idea.
	}
	layouts
	{
		# you can add whichever images you want here.  They'll display as the layout options on the statusbar.  I use a black background, and these images are black
		# basically that "hides" them, but they're still available to use.
		layout "tile"		{image = "/usr/local/share/awesome/icons/layouts/tile.png"} ## use tilew.png for white
		layout "tileleft"	{image = "/usr/local/share/awesome/icons/layouts/tileleft.png"} ## use tileleftw.png for white
    		layout "max"		{image = "/usr/local/share/awesome/icons/layouts/max.png"} ## use maxw.png for white
	   	layout "spiral"		{image = "/usr/local/share/awesome/icons/layouts/spiral.png"} ## use spiralw.png for white
	    	layout "dwindle"	{image = "/usr/local/share/awesome/icons/layouts/dwindle.png"} ## use dwindlew.png for white
		layout "floating"	{image = "/usr/local/share/awesome/icons/layouts/floating.png"} ## use floatingw.png for white
	}
	# padding around screen.
	padding
	{
    		top = 1
    		bottom = 1
    		right = 1
    		left = 1
  	}
}
# rules...the only kind I actually like!  These "rules" tell your windows where to go.  Basically, you can tell all your terminal to go to one tag
# and have your browser go to a different one.   There's no limit on how many rules you have, just make sure they have a corresponding tag.
# you can also tell these windows how to display, more information later!
rules
	{
	rule
	{
		name = "firefox" 		# this is the name of the window.  It's not case sensitive as far as I know
		tags = ".:Inet:." 			# this is the name of the tag you want Firefox to appear on.
		float = "false"			# this is the layout style.  You can have it maximized,  floating, etc.  We'll have Firefox maximized.
		screen = 0				# which monitor to display on.  I have two monitors so I choose to have it on screen 0.  Leave it as it is.
		not_master = false 	# we want it to be the master window
	}
  	rule
	{
		name = "pidgin"
		tags = ".:IM:."
		float = "true"
		screen = 0
		not_master = false
	}
	rule
	{
		name = "urxvt"
		tags = ".:Term:."
		float = "true"
		screen = 0
		not_master = false
	}
	{
		name = "azureus"
		tags = ".:Torrent:."
		float = "false"
		screen = 0
		not_master = false
	}
}
# this section allows you to set hotkeys.  These are most excellent because they remove the need for a menu.  You can have as many as you want.
keys
	{
	key
	{	
	    modkey = {"Mod4"} 	# mod4 by default is the windows key.
	    key = "t" 			# this is the key on your keyboard
	    command = "spawn" # what it should do, usually always "spawn"
	    arg = "exec urxvt" 	# what to exec.  In this case, mod4 + enter will start urxvt
	}
	key
	{	
	    modkey = {"Mod4"}
	    key = "a" 
	    command = "spawn"
	    arg = "exec azureus"
	}
	key
	{
		modkey = {"Mod4"}
		key = "f"
		command = "spawn"
		arg = "exec firefox"
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "space"
	    	command = "tag_setlayout"
	    	arg = "+1"
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "space"
	    	command = "tag_setlayout"
	    	arg = "-1"
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "p"
	    	command = "spawn"
	        arg = "pidgin"
	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "k"
	    	command = "client_focusprev"
	    	# arg = ""
	}
	key
	{
	   	modkey = {"Mod4"}
	    	key = "Tab"
	    	command = "focus_history"
	    	arg = "-1"
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "j"
	    	command = "client_swapnext"
	    	# arg = ""
	}
	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "k"
	    	command = "client_swapprev"
	    	# arg = ""
  	}
	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "j"
	    	command = "screen_focus"
	    	arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "k"
	    	command = "screen_focus"
	    	arg = "-1"
  	}
	key
	{
	    	modkey = {"Mod4"}
	    	key = "h"
	    	command = "tag_setmwfact"
	    	arg = "-0.05"
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "l"
	    	command = "tag_setmwfact"
	    	arg = "+0.05"
  	}
  	key
	{
    		modkey = {"Mod4", "Shift"}
    		key = "h"
    		command = "tag_setnmaster"
    		arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "l"
	    	command = "tag_setnmaster"
	   	arg = "-1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "h"
	    	command = "tag_setncol"
	    	arg = "+1"
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	   	key = "l"
	    	command = "tag_setncol"
	    	arg = "-1"
  	}
 	key
	{
	    	modkey = {"Mod4"}
	    	key = "Escape"
	    	command = "tag_viewprev_selected"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "Left"
	    	command = "tag_viewprev"
	    	# arg = ""
  	}
  	key	
	{
	    	modkey = {"Mod4"}
	    	key = "Right"
	    	command = "tag_viewnext"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4"}
	    	key = "m"
	    	command = "client_togglemax"
	    	# arg = ""
	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "Return"
	    	command = "client_zoom"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "space"
	    	command = "client_togglefloating"
	    	# arg = ""
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
	   	modkey = {"Mod4", "Shift"}
	    	key = "c"
	    	command = "client_kill"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "q"
	    	command = "quit"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "r"
	    	command = "exec"
	    	arg = "awesome"
  	}
  	key
	{
    		modkey = {"Mod4"}
    		key = "0"
    		command = "tag_view"
    		# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Control"}
	    	key = "0"
	    	command = "tag_toggleview"
	    	# arg = ""
  	}
  	key
	{
	    	modkey = {"Mod4", "Shift"}
	    	key = "0"
	    	command = "client_tag"
	    	# arg = ""
	}
  	key
	{
	   	modkey = {"Mod4", "Shift", "Control"}
	    	key = "0"
	    	command = "client_toggletag"
	    	# arg = ""
  	}
  	keylist
	{
	    	modkey = {"Mod4"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "tag_view"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	}
  	keylist
	{
	    	modkey = {"Mod4", "Control"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "tag_toggleview"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    	modkey = {"Mod4", "Shift"}
	    	keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
	    	command = "client_tag"
	    	arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
  	keylist
	{
	    	modkey = {"Mod4", "Shift", "Control"}
    		keylist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
    		command = "client_toggletag"
    		arglist = {"1", "2", "3", "4", "5", "6", "7", "8", "9"}
  	}
}
mouse
	{
	root
	{
	    	modkey = {}
	   	button = "3"
	    	command = "spawn"
	    	arg = "exec urxvt"
  	}
  	root
	{
	    	modkey = {}
	    	button = "4"
	    	command = "tag_viewnext"
	    	# arg = ""
  	}
  	root
	{
	    	modkey = {}
	    	button = "5"
	   	command = "tag_viewprev"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "1"
	    	command = "client_movemouse"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "2"
	    	command = "client_zoom"
	    	# arg = ""
  	}
  	client
	{
	    	modkey = {"Mod4"}
	    	button = "3"
	    	command = "client_resizemouse"
	    	# arg = ""
	}
}
```

---

### Post by MediaMike on 2008-04-11
Okay, it appears that the rules section is my issue.  As soon as I remove it from the .awesomerc config file and restart xorg I am back to normal.

What gives, what am I missing with applying rules?  I copied the one that works (urxvt), but still nothing.  Trying to make firefox open in the Inet tag broke it too.

---

### Post by mali2297 on 2008-04-11
> **MediaMike said:**
> 
What gives, what am I missing with applying rules?  I copied the one that works (urxvt), but still nothing.  Trying to make firefox open in the Inet tag broke it too.

Which version are you using?  If it's 2.2, then you need to replace not_master, see post #103.

For troubleshooting, you could take a look at /var/log/Xorg.0.log and see if you find any relevant error messages.

---

### Post by MediaMike on 2008-04-11
I am running version 2.1

---

### Post by hanzomon4 on 2008-06-04
> **PharaohSD said:**
> :S ok, so having the same problem i had with arch

when i login to Awesome right away *i set it to auto log me in when i boot up* my wireless doesn't work. but when i log in to gnome, the little wireless icon in the top right corner starts to work, and then i am connected. then i need to log out, then log in to awesome, then the internet works. can someone tell me how to get my wireless to work in awesome right away, aka what daemon or something do i need to add to my awesome.sh ?

another thing loke: how do i "move" my windows when i put it in floating mode. like all the windows are ontop of each other when i do (Mod 4, ctrl, space) until the mode is set to float, but i still can't re-positon/re-adjust the open programs.

just add nm-applet to the startup script, like the clock

---

### Post by Nythain on 2008-06-11
are the changes between 2.1 and 2.3.1 very drastic and has anyone considered creating a thread based on 2.3 covering installation (if any dependencies or versions have changed), the current layout of the .awesomerc if much has changed, and any new and improved widget implementations with example scripts, etc for us total newbs out there?

---

### Post by kaiju on 2008-06-12
> **Nythain said:**
> are the changes between 2.1 and 2.3.1 very drastic and has anyone considered creating a thread based on 2.3 covering installation (if any dependencies or versions have changed), the current layout of the .awesomerc if much has changed, and any new and improved widget implementations with example scripts, etc for us total newbs out there?

according to the homepage, 2.3 is the latest stable version, and 2.3.1 only fixes some bugs. that means that you should be able to find all the relevant informations regarding configuration and scripting on [the wiki]("http://awesome.naquadah.org/wiki/index.php/Main_Page"). and i'm sure the site must have some sort of a changelog, too ;)

---

### Post by vibhu.dubey on 2008-06-17
i am using pidgin in awesome. but each time a chat window opens it occupies
the full screen. Is there a pidgin version where only one window is opened.
As i use the full screen mode, it becomes hard if lot many windows are opened.
Any work arounds ?

---

### Post by kaiju on 2008-06-18
> **vibhu.dubey said:**
> i am using pidgin in awesome. but each time a chat window opens it occupies
the full screen. Is there a pidgin version where only one window is opened.
As i use the full screen mode, it becomes hard if lot many windows are opened.
Any work arounds ?

It's possible to make apps open up in floating mode, by changing the config file. for awesome 2.3.1, that's done through entries like 'rule { name = "Gimp" float = true }'. if you're using another version, that might look completely different though.

---

### Post by bongo on 2008-07-22
> **~LoKe said:**
>    text 

That terminal you are using, what is it? The one in the latest screenshot, screen? Whats the config? I like the bar at the bottom.

---

### Post by mali2297 on 2008-07-22
> **bongo said:**
> That terminal you are using, what is it? The one in the latest screenshot, screen? Whats the config? I like the bar at the bottom.

The terminal is urxvt (or rxvt-unicode). 

The bar belongs to GNU Screen. The configuration is posted here:
[http://ubuntuforums.org/showpost.php?p=4210866&postcount=1126](http://ubuntuforums.org/showpost.php?p=4210866&postcount=1126)

---

### Post by ~LoKe on 2008-08-04
Sorry I haven't been around to answer questions, the military keeps me busy.

If you have any prevalent questions, go ahead and ask.

---

### Post by Ewwmg on 2008-08-05
> **~LoKe said:**
> Sorry I haven't been around to answer questions, the military keeps me busy.

If you have any prevalent questions, go ahead and ask.

Thanks for the HOWTO, we appreciate the time you took to write them out.

[Awesome 3rc1]("http://awesome.naquadah.org/download/") [[http://awesome.naquadah.org/download/]("http://awesome.naquadah.org/download/")] was just released, have you given it a try yet?

Cheers!

---

### Post by Ru$$i@N on 2008-08-10
i'd say, wait a little bit with installing the new awesomewm.
rc2 came out couple days ago, and it looks like the developers are progressing pretty quickly. As far as i know, there are still some problems to be worked out in awesome-3 versions that are out there, but i think it won't be long.

---

### Post by kaiju on 2008-08-11
> **Ru$$i@N said:**
> i'd say, wait a little bit with installing the new awesomewm. rc2 came out couple days ago...

i installed rc2 yesterday, and its working really good.
and with only one week between the two release candidates, it looks like stable is coming out pretty soon indeed :)

---

### Post by nicol_bolas on 2008-08-14
How do I get x to load Awesome without a Graphic login manager?

many thanks

---

### Post by mali2297 on 2008-08-14
> **nicol_bolas said:**
> How do I get x to load Awesome without a Graphic login manager?

many thanks

Create a file **~/.xinitrc** that contains lines like this:
```

xsetroot -solid gray &
xterm &
exec awesome

```
(Adapt it to include whatever programs that you want to run at startup.)
Then you start Awesome from a console with
```

startx

```
See *man startx* for more info.

---

### Post by kaiju on 2008-08-15
> **nicol_bolas said:**
> How do I get x to load Awesome without a Graphic login manager?

in addition to the ~/.xinitrc entry ('exec awesome') mentioned by mali2297, you can add the following lines to your ~/.bash_profile:
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi
```
this way, startx will be automatically executed every time you log in on the first tty, and you will be logged out again right after closing the x session. what that means is that tty1 will work as a pure text login screen for x ;) (taken from [this archwiki page]("http://wiki.archlinux.org/index.php/Start_X_at_boot")).

---

### Post by Sammm_ on 2008-08-16
Awesomewm keeps crashing my computer. It runs fine for an unpredictable amount of time and then eventually crashes, needing a hard shutdown. Does anyone know if this a problem with dependencies? What logs can I check to work it out?

Help would be appreciated because I love AwesomeWM!

---

### Post by ~LoKe on 2008-08-25
Have any of you tried out Awesome 3.0?  What do you think of it, worth the switch?  How much does the config syntax change (again)?

---

### Post by Ewwmg on 2008-08-28
> **~LoKe said:**
> Have any of you tried out Awesome 3.0?  What do you think of it, worth the switch?  How much does the config syntax change (again)?

I personally haven't gotten a chance to try it out, but so far I've only heard positive things about it. The development rate is very fast, with a new release being delivered at an average of 7 or 8 days, so a stable version may be out very soon indeed.

---

### Post by Nythain on 2008-09-20
> **~LoKe said:**
> Have any of you tried out Awesome 3.0?  What do you think of it, worth the switch?  How much does the config syntax change (again)?
not sure if 3 weeks is dead or not, but i was pissed at awesome 3

i like a lot of its functionality, but im no programmer, and i couldnt, for the life of me get my .awesomerc.lua to behave correctly. im actually upset that for most tiling wm's now you have to be a borderline programmer just to customize them, awesome with lua, xmonad with haskel and well, the others just arent as great :P

---

### Post by kaiju on 2008-09-22
im no programmer either, but i cant say it was especially hard to fit rc.lua to my needs. true, i didnt really change much except for the default layout, adding some floatapps and porting my keybindings from xbindkeysrc.
id say make sure you have the newest version of rc.lua ```
cp /etc/xdg/awesome/rc.lua ~/.config/awesome/rc.lua
``` and take a peek at [the wiki]("http://awesome.naquadah.org/wiki/index.php?title=Awesome_3_configuration") and everything should be fine.

---

### Post by Gigamo on 2008-10-14
> **~LoKe said:**
> Have any of you tried out Awesome 3.0?  What do you think of it, worth the switch?  How much does the config syntax change (again)?

Using it for about a week now, after a day or two I got used to the config/lua syntax and now I like it better than any previous version. You can simply do soooo much more, you have a lot more control over the WM, not to mention the extensibility.

Config and screenshot:

[[img]http://www.gigamo.be/pics/currentdeskt.png[/img]](http://www.gigamo.be/pics/currentdesk.png)

```
--[[ 
awesome 3 configuration file
by Gigamo <gigamo@archlinux.us>
last update: 13/10/2008
]]

require("awful")
require("tabulous")
require("beautiful")
require("wicked")
require("eminent")
-- FIXME: Lua MPD library instead of calling mpc.
-- require("mpdlib") 

-- {{{ Variable definitions

config = {}
modkey = "Mod4"

config.terminal = "urxvtc"
config.browser = "firefox"
config.filemanager = config.terminal.." -e vifm"

config.layouts =
{
    "tile",
    "tilebottom",
    "floating"
}

config.layouts_symbols = 
{
    ["tile"] = " []= ",
    ["tilebottom"] = " -_- ",
    ["floating"] = " <>< "
}

config.floatapps =
{
    ["MPlayer"] = true,
    ["gimp"] = true,
    ["Mirage"] = true
}

config.apptags =
{
    ["Firefox"] = { screen = 1, tag = 2 },
    ["Minefield"] = { screen = 1, tag = 2 },
    ["Gimp"] = { screen = 1, tag = 3 }
}

config.use_titlebar = false
config.warp_mouse = false

config.theme_path = os.getenv("HOME").."/.config/awesome/themes/gigamo"

-- Autostart apps with awesome (instead of xinitrc)
config.startup = { 
    "xset m 0 0",
    "xsetroot -cursor_name left_ptr",
    "urxvtd -o -q -f",
    "mpd",
    --"xbindkeys",
    "unclutter -root -idle 3"
}

-- }}}

-- {{{ Initialization

beautiful.init(config.theme_path)
awful.beautiful.register(beautiful)

for i,v in pairs(config.startup) do
	awful.spawn(v)
end

function layout_symbols(layout)
    return config.layouts_symbols[layout]
end

-- }}}

-- {{{ Eminent

-- Name the first 3 tags
-- eminent.tag.name( Tag_Number, Screen_Number, Name )
eminent.tag.name(1, 1, "1:t")
eminent.tag.name(2, 1, "2:w")
eminent.tag.name(3, 1, "3:d")

-- Set default amount of tags to 9
-- eminent.newtag( Screen_Number, Amount )
eminent.newtag(1, 4)

-- }}}

-- {{{ Markup helper functions

-- Easier for handling widget markup
beautiful.markup = {}
function beautiful.markup.bg(color, text)
    return '<bg color="'..color..'" />'..text
end
function beautiful.markup.fg(color, text)
    return '<span color="'..color..'">'..text..'</span>'
end
function beautiful.markup.font(font, text)
    return '<span font_desc="'..font..'">'..text..'</span>'
end

-- }}}

-- {{{ Widgets

spacer = " "

-- Taglist
taglist = widget({ type = "taglist", name = "taglist" })
taglist:buttons({
    button({ }, 1, function (object, tag) awful.tag.viewonly(tag) end),
    button({ modkey }, 1, function (object, tag) awful.client.movetotag(tag) end),
    button({ }, 3, function (object, tag) tag.selected = not tag.selected end),
    button({ modkey }, 3, function (object, tag) awful.client.toggletag(tag) end),
    button({ }, 4, awful.tag.viewnext),
    button({ }, 5, awful.tag.viewprev)
})
function taglist.label(t) 
    if not eminent.isoccupied(t.screen, t) and not t.selected then return end
    return awful.widget.taglist.label.all(t, bg_focus, fg_focus) end
taglist.label = taglist.label

-- Layout symbol
layouticon = {}
for s = 1, screen.count() do
    layouticon[s] = widget({ type = "textbox", name = "layouticon" })
    layouticon[s]:buttons({
        button({ }, 1, function () awful.layout.inc(config.layouts, 1) end),
        button({ }, 3, function () awful.layout.inc(config.layouts, -1) end),
    })
    layouticon[s].text = layout_symbols("tile")
end

-- Tasklist
--[[tasklist = widget({ type = "tasklist", name = "tasklist" })
tasklist:buttons({
    button({ }, 1, function (object, c) client.focus = c; c:raise() end),
    button({ }, 4, function () awful.client.focus.byidx(1) end),
    button({ }, 5, function () awful.client.focus.byidx(-1) end)
})
-- Only show focused client in tasklist
function tasklist.label(c)
    if c == client.focus then return "<bg color='"..beautiful.bg_focus.."'/><span color='"..beautiful.fg_focus.."'>"..spacer..c.name.."</span>" end
end
tasklist.label = tasklist.label
]]

-- Separator icon
separator = widget({ type="imagebox", name = "separator", align = "right" })
separator.image = image(os.getenv("HOME").."/.config/awesome/icons/separators/link2.png")

-- Clock
clockwidget = widget({ type = "textbox", name = "clockwidget", align = "right" })
clockwidget.text = " "
clockformat = "%d.%m.%Y %T"

-- CPU Usage
cpuwidget = widget({ type = "textbox", name = "cpuwidget", align = "right" })
wicked.register(cpuwidget, "cpu", function (widget, args)
    return spacer..args[1].."%"..spacer
end, 3)

-- Mem Usage
memwidget = widget({ type = "textbox", name = "memwidget", align = "right" })
wicked.register(memwidget, "mem", spacer.."$1% ($2/$3)"..spacer, 20)

-- Battery
batterywidget = widget({ type = "textbox", name = "batterywidget", align = "right" })
function batteryInfo()
    local capacity = io.open("/proc/acpi/battery/BAT1/info"):read("*a"):match("last full capacity:%s+(%d+)")
    local current = io.open("/proc/acpi/battery/BAT1/state"):read("*a"):match("remaining capacity:%s+(%d+)")
    local state = io.open("/proc/acpi/battery/BAT1/state"):read("*a")
    battery = ((current * 100) / capacity)
    bat = math.floor(battery * 10 ^ 2) / 10 ^ 2
    
    -- Add little direction symbols based on the battery state
    if state:match("charged") then
        dir = "="
    elseif state:match("discharging") then
        dir = "v"
    else
        dir = "^"
    end
    return spacer..dir..bat..dir..spacer
end
wicked.register(batterywidget, batteryInfo, function(widget, args)
    return args[1]
end, 20)

-- Gmail
gmailwidget = widget({ type = "textbox", name = "gmailwidget", align = "right" })
gmailwidget:buttons({ button({ }, 1, function () wicked.update(gmailwidget) end) })
function readGmail(format)
    local f = io.open('/tmp/gmail-temp')
    if f == nil then 
        return {'n/a'}
    end
    local n = f:read()
    if n == nil or f == ' ' or f == '' then
        f:close()
        return {'n/a'}
    end
    return {n}
end
wicked.register(gmailwidget, read_gmail_temp, function (widget, args)
    local n = args[1]
    local out = spacer
    -- Urgent bg/fg when new mail
    if n ~= "n/a" and tonumber(n) > 0 then
        out = out..beautiful.markup.bg(beautiful.bg_urgent, beautiful.markup.fg(beautiful.fg_urgent, tostring(n)))
    else
        out = out..tostring(n)
    end
    out = out..spacer
    return out
end, 120)

-- MPD
mpdwidget = widget({ type="textbox", name = "mpdwidget", align = "right" })
mpdwidget:buttons({ button({ }, 1, function () awful.util.spawn(libs.mpd.toggle_play()) end)}) 
function mpdInfo()
    local mpd_file = io.popen("mpc")
    local song = mpd_file:read()
    local state = mpd_file:read()

    -- Prefix symbols based on mpd's state
    local show_info = true
    if not state then 
    	show_info = false
    elseif state:match("playing") then
        txt = ">>: "
    elseif state:match("paused") then
        txt = "||: "
    end
    
    if show_info then
        return spacer..txt..song..spacer
    else
        return spacer.."[]: not playing"..spacer
    end
end
wicked.register(mpdwidget, mpdInfo, function(widget, args)
    return args[1]
end, 5)

-- Prompt
promptbox = widget({ type = "textbox", name = "promptbox", align = "left" })

-- Systray (not that I use it but anyway)
mysystray = widget({ type = "systray", name = "mysystray", align = "right" })

-- Statusbar (wibox), and add widgets to it
statusbar = {}
for s = 1, screen.count() do
    statusbar[s] = wibox({ position = "top", height = "14", name = "statusbar" .. s,
                             fg = beautiful.fg_normal, bg = beautiful.bg_normal })
    -- Add widgets to the statusbar - order matters
    statusbar[s]:widgets({
        taglist,
        layouticon[s],
        --tasklist,
        promptbox,
        mpdwidget,
        separator,
        batterywidget,
        separator,
        cpuwidget,
        separator,
        memwidget,
        separator,
        gmailwidget,
        separator,
        clockwidget,
        s == 1 and mysystray or nil
    })
    statusbar[s].screen = s
end
-- }}}

-- {{{ Mouse bindings

awesome.buttons({
    button({ }, 3, function () awful.util.spawn(config.terminal) end),
    button({ }, 4, awful.tag.viewnext),
    button({ }, 5, awful.tag.viewprev)
})

-- }}}

-- {{{ Key bindings

keybinding({ modkey }, "F1", eminent.tag.prev):add()
keybinding({ modkey }, "F2", eminent.tag.next):add()
keybinding({ modkey, "Shift" }, "F1", function () awful.client.movetotag(eminent.tag.getprev(mouse.screen)) end):add()
keybinding({ modkey, "Shift" }, "F2", function () awful.client.movetotag(eminent.tag.getnext(mouse.screen)) end):add()

-- Apps
keybinding({ modkey }, "x", function () awful.util.spawn(config.terminal) end):add()
keybinding({ modkey }, "f", function () awful.util.spawn(config.browser) end):add()
keybinding({ modkey }, "t", function () awful.util.spawn(config.filemanager) end):add()

-- Multimedia keys (no more need for xbindkeys)
keybinding({ }, "#160", function () awful.util.spawn("dvol -t") end):add()
keybinding({ }, "#174", function () awful.util.spawn("dvol -d 2") end):add()
keybinding({ }, "#176", function () awful.util.spawn("dvol -i 2") end):add()
keybinding({ }, "#162", function () awful.util.spawn("mpc toggle") end):add()
keybinding({ }, "#164", function () awful.util.spawn("mpc stop") end):add()
keybinding({ }, "#153", function () awful.util.spawn("mpc next") end):add()
keybinding({ }, "#144", function () awful.util.spawn("mpc prev") end):add()
keybinding({ }, "#159", function () awful.util.spawn("urxvtc -e ncmpcpp") end):add()

-- Reload/Quit
keybinding({ modkey, "Control" }, "r", function ()
                                           promptbox.text =
                                               awful.util.escape(awful.util.restart())
                                        end):add()
keybinding({ modkey, "Shift" }, "q", awesome.quit):add()

-- Client manipulation
keybinding({ modkey }, "m", awful.client.maximize):add()
keybinding({ modkey }, "c", function () client.focus:kill() end):add()
keybinding({ modkey }, "j", function () awful.client.focus.byidx(1); client.focus:raise() end):add()
keybinding({ modkey }, "k", function () awful.client.focus.byidx(-1);  client.focus:raise() end):add()
keybinding({ modkey, "Shift" }, "f", function () client.focus.fullscreen = not client.focus.fullscreen end):add()
keybinding({ modkey, "Shift" }, "j", function () awful.client.swap(1) end):add()
keybinding({ modkey, "Shift" }, "k", function () awful.client.swap(-1) end):add()
keybinding({ modkey, "Control" }, "j", function () awful.screen.focus(1) end):add()
keybinding({ modkey, "Control" }, "k", function () awful.screen.focus(-1) end):add()
keybinding({ modkey, "Control" }, "space", awful.client.togglefloating):add()
keybinding({ modkey, "Control" }, "Return", function () client.focus:swap(awful.client.master()) end):add()
keybinding({ modkey }, "o", awful.client.movetoscreen):add()
keybinding({ modkey }, "Tab", awful.client.focus.history.previous):add()
keybinding({ modkey }, "u", awful.client.urgent.jumpto):add()
keybinding({ modkey, "Shift" }, "r", function () client.focus:redraw() end):add()

-- Layout manipulation
keybinding({ modkey }, "space", function () awful.layout.inc(config.layouts, 1) end):add()
keybinding({ modkey, "Shift" }, "space", function () awful.layout.inc(config.layouts, -1) end):add()

-- Prompt
keybinding({ modkey }, "r", function ()
                                 awful.prompt.run({ prompt = "Run: " }, promptbox, awful.util.spawn, awful.completion.bash,
os.getenv("HOME") .. "/.cache/awesome/history") end):add()

--- Tabulous, tab manipulation
keybinding({ modkey, "Control" }, "y", function ()
    local tabbedview = tabulous.tabindex_get()
    local nextclient = awful.client.next(1)

    if not tabbedview then
        tabbedview = tabulous.tabindex_get(nextclient)

        if not tabbedview then
            tabbedview = tabulous.tab_create()
            tabulous.tab(tabbedview, nextclient)
        else
            tabulous.tab(tabbedview, client.focus)
        end
    else
        tabulous.tab(tabbedview, nextclient)
    end
end):add()

keybinding({ modkey, "Shift" }, "y", tabulous.untab):add()

keybinding({ modkey }, "y", function ()
   local tabbedview = tabulous.tabindex_get()

   if tabbedview then
       local n = tabulous.next(tabbedview)
       tabulous.display(tabbedview, n)
   end
end):add()
-- }}}

-- {{{ Hooks

-- Hook function to execute when focusing a client.
function hookFocus(c)
    if not awful.client.ismarked(c) then
        c.border_color = beautiful.border_focus
    end
end

-- Hook function to execute when unfocusing a client.
function hookUnfocus(c)
    if not awful.client.ismarked(c) then
        c.border_color = beautiful.border_normal
    end
end

-- Hook function to execute when marking a client
function hookMarked(c)
    c.border_color = beautiful.border_marked
end

-- Hook function to execute when unmarking a client
function hookUnmarked(c)
    c.border_color = beautiful.border_focus
end

-- Hook function to execute when the mouse is over a client.
function hookMouseEnter(c)
    -- Sloppy focus, but disabled for magnifier layout
    if awful.layout.get(c.screen) ~= "magnifier"
        and awful.client.focus.filter(c) then
        client.focus = c
    end
end

-- Hook function to execute when a new client appears.
function hookManage(c)
    if config.use_titlebar then
        -- Add a titlebar
        awful.titlebar.add(c, { modkey = modkey })
        c.titlebar.border_width = beautiful.border_width
        c.titlebar.border_color = beautiful.border_focus
    end
    -- Add mouse bindings
    c:buttons({
        button({ }, 1, function (c) client.focus = c; c:raise() end),
        button({ modkey }, 1, function (c) c:mouse_move() end),
        button({ modkey }, 3, function (c) c:mouse_resize() end)
    })
    -- New client may not receive focus
    -- if they're not focusable, so set border anyway.
    c.border_width = beautiful.border_width
    c.border_color = beautiful.border_normal
    client.focus = c

    -- Check if the application should be floating.
    local cls = c.class
    local inst = c.instance
    if config.floatapps[cls] then
        c.floating = config.floatapps[cls]
    elseif config.floatapps[inst] then
        c.floating = config.floatapps[inst]
    end

    -- Prevent new windows from becoming master
    awful.client.setslave(c)

    -- Resize hints
    c.honorsizehints = true
end

-- Hook function to execute when arranging the screen
-- (tag switch, new client, etc)
function hookArrange(screen)
    layouticon[screen].text = layout_symbols(awful.layout.get(screen))

    -- Give focus to the latest client in history if no window has focus
    -- or if the current window is a desktop or a dock one.
    if not client.focus then
        local c = awful.client.focus.history.get(screen, 0)
        if c then client.focus = c end
    end

    -- Mouse warping
    if config.warp_mouse then
        if client.focus then
            local c_c = client.focus:coords()
            local m_c = mouse.coords()

            if m_c.x < c_c.x or m_c.x >= c_c.x + c_c.width or
                m_c.y < c_c.y or m_c.y >= c_c.y + c_c.height then
                if table.maxn(m_c.buttons) == 0 then
                    mouse.coords({ x = c_c.x + 5, y = c_c.y + 5})
                end
            end
        end
    end
end

-- Timed hooks
function hookOneSecond()
    clockwidget.text = spacer..os.date(clockformat)..spacer
end

function hookTwoMinutes()
    os.execute(os.getenv("HOME").."/.gmail.py > /tmp/gmail-temp &")
end

-- Set up the hooks
awful.hooks.focus.register(hookFocus)
awful.hooks.unfocus.register(hookUnfocus)
awful.hooks.marked.register(hookMarked)
awful.hooks.unmarked.register(hookUnmarked)
awful.hooks.mouse_enter.register(hookMouseEnter)
awful.hooks.manage.register(hookManage)
awful.hooks.arrange.register(hookArrange)
awful.hooks.timer.register(1, hookOneSecond)
awful.hooks.timer.register(110, hookTwoMinutes)
-- }}}


```

---

### Post by deuce868 on 2008-10-15
Anyone tried out the package in Intrepid? I've installed awesome and I'm working on some of the config tweaks, but it doesn't seem like it's reading my .awesomerc on load. I can select the awesome session from gdm, it loads, but nothing I do to the config changes. 

I've tried just removing a tag to test if it's reading at all, but removing the 'nine' tag doesn't change a thing. 

Thanks for any tips/tricks.

---

### Post by Gigamo on 2008-10-16
What's the output of awesome -v?

If 3.0 or higher, the config is no longer ~/.awesomerc but ~/.config/awesome/rc.lua (example one in /etc/xdg/awesome/rc.lua).

Also it's lua configuration now.

---

### Post by urukrama on 2008-10-16
The [Intrepid version]("http://packages.ubuntu.com/intrepid/awesome") is 2.3.2, so it should read the awesomerc file.

---

### Post by deuce868 on 2008-10-16
> **Gigamo said:**
> What's the output of awesome -v?

If 3.0 or higher, the config is no longer ~/.awesomerc but ~/.config/awesome/rc.lua (example one in /etc/xdg/awesome/rc.lua).

Also it's lua configuration now.

Yea, it's 2.3.2. I've submitted a bug to the package and see if anything comes of it. I had hoped to just try it out a bit before deciding if it would be worth it to go through the additional work to setup a current version 3.

---

### Post by Maverick1712 on 2008-11-19
Hi All


Having a problem making libconfuse2.6. Not sure if this thread was dead or if this was related to Awesome so I posted here:

[http://ubuntuforums.org/showthread.php?t=986863](http://ubuntuforums.org/showthread.php?t=986863)

Any help is appreciated.

Cheers

---

### Post by chaitat on 2008-11-30
Hi guys,

I am using GRML Linux that comes with AWESOME 2.2-rc1 (Digital Love).

It is awesome except that I am having a small problem.

Whenever I change the focus to another window, I have to press "enter" before I can actually do anything with that window.  But sometimes, I don't have to.

Do you have any idea?

Thanks,

Chaitat

---

### Post by mali2297 on 2008-11-30
> **chaitat said:**
> Hi guys,

I am using GRML Linux that comes with AWESOME 2.2-rc1 (Digital Love).

It is awesome except that I am having a small problem.

Whenever I change the focus to another window, I have to press "enter" before I can actually do anything with that window.  But sometimes, I don't have to.

Do you have any idea?

Thanks,

Chaitat

Try adding
```

sloppy_focus_raise = true

```
in the *general* section. I have a later version of awesome, so I don't know if it will work.

---

### Post by chaitat on 2008-11-30
> **mali2297 said:**
> Try adding
```

sloppy_focus_raise = true

```
in the *general* section. I have a later version of awesome, so I don't know if it will work.

Thank you very much, Martin.

That option is there in the default .awesomerc generated by the system which simply implies that my awesome should support that. Unfortunately, it does not work.  I guess that option is for "rasing" the window if that window is behind some other windows but does not mean to make the window active and ready to type other command into it.

Can you confirm that you don't have the same problem as me?  Which version of awesome are you using?  I might give it a try.

Thanks,

Chaitat

---

### Post by mali2297 on 2008-11-30
I use awesome 2.3.4 and I haven't experienced the problem that you describe.

Generally, I avoid the release candidates and wait for the stable version. I still haven't upgraded to 3.0 though.

---

