---
title: "HOWTO: autohide GIMP dock windows using gnome panel"
date: 2008-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by knarf on 2008-07-07
Want to use the GIMP without having those docks clutter up your screen? Here's how you can have the GIMP's controls swallowed in a pair of autohidden Gnome panels so you have the whole screen available for the current document instead of wasting a third of it on controls. It also makes those controls available when you want them without having to hunt for them. When you quit the GIMP the panels will be removed, to be recreated on the next invocation of the GIMP...

Prerequisites: GIMP, Gnome, gnome-swallow-applet (*from universe repo*)

**How it works**

The Gnome panel can be configured through gconf. The way to do this from the command line is by using gconftool-2. This works but it is exceedingly tedious, except for those who relish in having to type in endless repetitive strings of redundant data. A helper script which can make this work slightly less tedious is attached to this posting.

To swallow X windows in the Gnome panel you can use the gnome-swallow applet. This applet can be installed from universe (sudo apt-get install gnome-swallow-applet). This applet works as stated but it can be a bit cranky - it sometimes refuses to find the windows which it is supposed to swallow, even though they are plainly visible. In other cases it does seem to swallow the window (it disappears from the desktop) but it does not appear in the panel. In such cases it is best to simply restart the applet and the application to be swallowed.

The gnome-swallow applet recognizes windows by their X window titles. The GIMP always uses the same window title for the toolbox window ('GIMP') but it changes the titles of other dock windows according to their contents. This means that my script has to be tailored to your GIMP configuration OR your GIMP configuration has to be tailored to my script... The GIMP stores the dock configuration in the ~/.gimp-(version)/sessionrc file so for reference a copy of my sessionrc is attached to this posting. Do note that sessionrc contains absolute window coordinates so it is dependent on screen resolution. As my T23 has a 1024x768 screen you may not want to use this file on your 1900x1200 screen... let alone on anything with a lower resolution than 1024x768...

**About *gnome-panel-config.sh***

The gnome-panel-config.sh script can be used for modifiying the Gnome panel from the command line or from scripts. It makes it slightly less tedious to create/delete panels, applets and objects without mousing through the maze of cascaded menus. To start applets you still have to produce the required amount of bonobo-related mumbo-gumbo though. See the start_gnome.sh script for examples of how to use this script.

**Yes, I want it!**

So if you really want to try this it is probably best to first configure the GIMP to display the docks as you want them (one or two windows, to your personal preference) or to follow the instructions in the next post regarding the alternative sessionrc file. If you use two dock windows you need to change the window title for the second dock in the script to reflect the title of your second dock window. The script is configured for my way of using the GIMP, with the toolbox and tool options in a dock on the left hand side (X window title: GIMP) and a second window with the layers/channels/paths & brushes/patterns/gradients/palettes/fonts (X window title: Layers, Channels, Paths, Undo | Fonts, Palettes, Gradients, Patterns, Brushes). I created that window by taking the first two ´standard' docks and dragging the contents of the second in the bottom frame of the first. Make the windows full-height and minimum usable width as they will appear with the same size in the panels and can not be resized once swallowed.

When you have...
[LIST]
[*]configured everything like it should and installed gnome-swallow-applet (from universe)
[*]copied the scripts somewhere in your path (I suggest ~/bin)
[*]tailored the *start_gimp.sh* script to your needs, mainly by changing the "*right_dock_title*" window name variable on line 10 OR by changing your GIMP configuration to suit the default window name, you might want to edit the panel sizes as well
[/LIST]
...it is time to try whether it works for you. Start the *start_gimp.sh* script and hold your breath. If everything goes according to plan you will be greeted by the GIMP splash screen. After 10 seconds (this delay can be configured by editing the script, see *sleep* after the *gimp* incovation) two Gnome panels will open on the left and right hand side. GIMP will finish starting, the two dock windows will appear. These should be swallowed by the panels, which should autohide. If it works you can now use GIMP as usual, with the whole screen there for your editing pleasure. Mouse to the left/right hand side of the screen to use the docks. If it does not work... 
[LIST]
[*]gnome-panel-config -P gimp_left -P gimp_right -A gimp_swallow_left -A gimp_swallow_right (this removes the created panels and applets)
[*]kill any remaining GIMP bits (killall gimp)
[/LIST]
...and try again. If it still does not work you'd better check why it doesn't. It _WorksForMe_ after all... You might have made a mistake editing the script, you might have misspelled the second dock window name, etc. Questions or comments? Post 'm here... Someone might answer...

---

### Post by knarf on 2008-07-07
The mentioned sessionrc file is attached to this post because the initial post already had 5 attachments (there is a limit of 5 attached files per post). To use this file simply copy it to your current gimp preferences directory (~/.gimp-(version)) and start the *start_gimp.sh* script with the *--session* parameter set. If you have more than one ~/.gimp-(version) directory just copy it to the highest numbered one (.gimp-2.4 on Hardy).

Don't forget to copy the file without the .txt extension or it won't work [1]

```

cp sessionrc.swallowed.txt ~/.gimp-2.4/sessionrc.swallowed
start_gimp.sh --session swallowed

```

[SIZE="1"]([1] the .txt extension is needed to get this forum to accept the file as an attachment... silly, as it does a file(1) check on the attached files anyway so there is no need for such counterproductive three_letter_extension Windowsisms...)[/SIZE]

---

### Post by knarf on 2008-10-02
Here's an updated version for Gimp 2.6. The only relevant changes are the names of the windows to be swallowed:

Gimp 2.4:
 # dock window titles
left_dock_title='GIMP'
right_dock_title='Layers, Channels, Paths, Undo | Fonts, Palettes, Gradients, Patterns, Brushes'

Gimp 2.6
 # dock window titles
left_dock_title='Toolbox'
right_dock_title='Layers, Channels, Paths, Undo - Fonts, Palettes, Gradients, Patterns, Brushes'

There is also a small change in the gnome-panel-config helper script (removed superfluous 'brackets' function).

Attached to this posting are the start_gimp.sh and gnome-panel-config.sh scripts (with '.sh' extension to get this site to accept the files as attachments…) as well as the 'sessionrc.swallowed' Gimp session resource file. You'll have to copy the 'sessionrc.swallowed.txt' file to '~/.gimp-2.6/sessionrc.swallowed' (and yes, the '.txt' extension had to be added to get this silly site to accept the file as a valid attachment, tsk tsk tsk…). Copy the scripts to some directory in your $PATH and make them executable (using chmod +x name_of_script.sh).

If the script fails to capture both toolbox windows you can try to close the Gimp and restart the script, or increase the timeout value ('sleep 10' in start_gimp.sh).

Gimp 2.6 is not in the official repo yet by the way...

---

### Post by XsXPo8o on 2008-10-02
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

