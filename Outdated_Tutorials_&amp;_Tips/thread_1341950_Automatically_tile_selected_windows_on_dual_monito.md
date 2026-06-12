---
title: "Automatically tile selected windows on dual monitor setup"
date: 2009-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by wd5gnr on 2009-11-30
I had a monitor fail so I bought a new widescreen monitor. I liked it so well I bought another one just like it to replace the monitor that did not fail. So I went from 2 1280x1024s to 2 1600x900s. The 3200 pixel resolution screams for some way to divide the screen up reasonably. Yes I know about tiling window managers, but I just want some things tiled some time.

So... I wrote a script. It works best if you assign it to a global shortcut (I use Kubuntu, the Ubuntu instructions will have to wait for someone to supply them). The assumption is that you have two monitors side by side (and hopefully of the same resolution, for best effect). The script divides the total screen into 2 rows of 4 boxes. The top row is ABCD and the bottom row is EFGH. So your left screen is ABEF and the right screen is CDGH. You can also use 1 and 2 to refer to the screens (1 is on the left).

Steps:

[LIST=1]
[*]make sure you have the required other packages: sudo apt-get install zenity x11-utils wmctrl gawk
[*]Download the script (below)
[*]Place the script in /usr/bin:   sudo mv place-beta1.txt /usr/bin/place
[*]Make it executable:   sudo chmod +x /usr/bin/place
[*]For KDE 4.x (optional, see below)

[/LIST]

*NOTE: You may not want to put unpackaged software in /usr/bin. If you have /usr/local/bin on your PATH this may be a better choice. From a shell enter (without quotes): "echo $PATH" and see if you use /usr/local/bin among the colon-separated entries. If so, consider using that in both the mv and chmod commands above. The truth is, it doesn't really matter where you put it, as long as it is on your path. Me? I have a local bin directory ~/bin and I put it there (don't even need sudo in that case) but that's not standard, so if you want to do that you have to set your path in, for example, .bashrc. If you don't know why you care, don't worry. It will work find in /usr/bin. If you reinstall Ubuntu, you'll probably have to reinstall place anyway.*

Installing Global Shortcut in KDE 4.x (optional)
[LIST=1]
[*]Open System Settings, select Input Actions.
[*]Right click on left pane under "Preset Actions" in blank space and select New Group. 
[*]The name will look editable (and say New Group). Type over User Defined and press Enter. 
[*]Click the check box next to the name so it is checked. 
[*]Right click on User Defined and select New | Global Shortcut | Command/URL. You can type what you want in the comment tab (or nothing, its just to document what you are doing). 
[*]Click the Trigger tab. Click on the None button and then press the keys you want to use to place a window (suggest Win+Insert)
[*]Click the action tab. In the command box, enter (without quotes) "/usr/bin/place"
[*]Click Apply and close the window.
[/LIST]

I'm sure you can do the same thing in Gnome, but I don't have it installed to produce that detailed of instructions. 

If you did the global shortcut setup, you can press the key and you'll get a box reminding you that you have to click on a window. Press OK and then click on the window you want to move/size. Then a box will appear prompting you for the position. If you want the window in the top left enter A. If you want it to be across the top of your first monitor enter AB. If you want it all over your left screen, enter ABEF or just enter 1. 

This lets you pick any kind of layout you want (for example, BCFG will let the window span the center of your monitors). You can tile up to 8 windows or you can have some of them take 2 cells vertically or up to 4 cells across.

You can also use options to call place directly or customize how it works in the short cut. So you could press Alt+F2 and type (without quotes: "place" and press enter to run place. 

# Options (all optional)
# -w 10 - Set width trim to 10 
# -t 40 - Set height trim to 40
# -i 0x4942 - Use window ID instead of prompting for window
# -n 'mywin' - Identify window by title instead of prompting 
# Note: -n doesn't work well when 2 windows have same title!
# Note: Use -i -n or nothing but do not use -i and -n together
# -x 1600 - Override screen width to 1600
# -y 900 - Override screen height to 900
# -s ABEF - Use placer string and don't prompt
# -r - Do not raise window
# -q - Quiet (do not show intro dialog)

The "trim" is used when computing the "cell" size. If you make everything fit exactly the borders overlap. So the trim makes the window a little bit smaller than the actual computed cell size. The default is 40.

You might use -x and -y if you don't have same sized screens. At least on TwinView if you use, say, a 1024x768 next to a 1280x1024 screen it tells X you have 1304x1024 and you just have a dead band on the smaller monitor. So in a case like that you might try setting -x to 1304 and -y to 768, although the result won't be quite as nice. If there were demand, it would be possible to set x/y separate for each monitor, but I did not do that.

The -i, -n, and -s commands let you write scripts that do things (like move Thunderbird to CD). You can either make a new key shortcut with the options or put it in a script but that's outside the scope of this tutorial.

If you use Alt+F2 to launch place, the -s and -q options could be handy. For example:

place -q -s AB

Will just let you click on a window and then move it to the top half of your left monitor with no dialogs.

# TODO: Custom grid dialog to pick on a 4x2 grid
# I may do this with kdialog and/or pick zenity or kdialog depending on
# which has the best features for doing this.


Comments welcome. Patches even more so. I use KDE but since I get the sense that is the minority I used zenity instead of Kdialog (see comments for all the dependencies).

---

