---
title: "How to modify the 'System Monitor' ?"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by Innernet on 2014-11-19
Hi.
There is a way to bring the program lines on screen and edit minor things as text, dimension, position of the GUI; but cannot remember how/where it is done.
It is to change some 'cosmetics' of the utility program but not its functionality.
Can you help with wording for an unskilled tweaker, please ?

---

### Post by DarkSapphire on 2014-11-22
You actually go into the system monitor application, and the settings are right there. :)

---

### Post by coldcritter64 on 2014-11-22
> **Dane917 said:**
> You actually go into the system monitor application, and the settings are right there. :)

For anyone in this section "New to Ubuntu", it pays to state exactly where. In this case, the Edit menu > Preferences, will bring up a window with interface settings. 

Also with system monitor some setting up user preferences can be set in the "View" menu. Whether or not to show just "active" processes, or "all" processes, or "user" processes. Also in the view menu is a setting to show process "dependencies".

@ OP, short answer, look in the "Edit > Preferences" and "View" menus to set up system settings to your preferences.

However,
> dimension, position of the GUI; Can't usually be controlled from within system monitor. There may be ways to control such with more advanced usage of Compiz settings (not sure in newer releases, I used to do so up to 12.04). 

Or there is also a window matching daemon called devilspie, its frontend is called gdevilspie. With it you can create window rules, including in this quoted example window "geometry" settings (dimension and position of the GUI). Both devilspie (the daemon) and gdevilspie are in the Ubuntu repositories and should be available in the Software Center for easy installation. Though in my opinion it is a bit more advanced and may not suit all beginners, be aware, it can take quite a bit of effort to learn its usage. 

Good luck, coldcritter64.

---

### Post by timrseattle on 2014-11-23
Regarding the window placement, I was able to get System Monitor to open in a specific workspace, at a specific placement, using compizconfig-settings-manager installed on my 14.04 LTS 32-bit via Software Center on my Dell Inspiron 1720 with screen res of 1440x900.

Before I try to explain the steps I took, a few disclaimers and excuses: I have been a Linux user for less than a week, and this is my first post to any forum. Ever. So please be nice :)  I will try to remember that this forum is for beginners like me, but my terminology and assumptions will probably be all wrong. And also, it will be WAY to long to read.

While going through this, remember the shortcut to keyboard shortcuts -- press and hold the "Super" key, which in my case has the MS Windows logo on it. The key combos I needed during my playing around with window placement were:
<Super>+S  to show the workspaces, then choose the one I want with either the mouse or the arrow keys
<Alt>+<Tab> to make sure I was focused on the System Monitor window when it got lost off-screen
<Alt>+<Spacebar> . then "M" then arrow keys to move that off-screen window back into view


[LIST]
[*]Enable workspaces: 
[*=1]System Settings, then double-click Appearance, then choose the Behavior tab, and check the option to Enable-workspaces) 
[*]Install compizconfig-settings-manager: 
[*=1]Ubuntu Software Center, then copy/paste **[FONT=system]compizconfig-settings-manager[/FONT]** into search box. 
[*=1]Highlight the compizconfig application and choose Install. 
[*]Set the System Monitor window placement: 
[*=1]Open the System Monitor application and place it somewhere on your workspace - you will need to click on it later so don't let the next steps overlap it entirely. 
[*=1]Open CompizConfig from the launcher, and, in the Window Management section, make sure "Place Windows" has the checkbox checked. Open "Place Windows" with a single click 
[*=1]Choose the tab labeled "Fixed Window Placement". In the section "Windows with fixed positions" click "New". A dialogue box named "Edit" will pop up. 
[*=1]Clck the green "+" icon and another dialogue box named "Edit Match" will pop up; Change the "Type" to the "Window Name" drop-down choice. 
[/LIST]
[INDENT]
[/INDENT]
[INDENT]LOOK! a picture!
[/INDENT]
[CENTER][INDENT]**CompizConfig / Window Management**
[/INDENT]

[IMG]http://i1122.photobucket.com/albums/l538/Colleen98103/CompizConfig1.png[/IMG]
[/CENTER]
[INDENT]
[/INDENT]

[LIST]
[*=1] Click the "Grab" button. The mouse pointer will change to a cross-hatch. Click anywhere on the previously-opened System Monitor window, and the field should be filled in with the window name: **name=gnome-system-monitor** . If so, click the "Add" button. 
[*=1]Change the x-position and y-position fields to something, perhaps 500 each. You can edit this later to place it where you want it. (This is where I lost my System Monitor window, as the default placement was way off-screen) 
[*=1] Click Close. The last of the dialogue boxes should be gone now. If you have any extra half-finished entries due to trial and error, you can remove them with a right click-delete 
[*]Choose which of the four workspaces you want it to open into (I wanted mine in the bottom-left one) 
[*=1]Back in the compizconfig screen, in the section named "Windows with fixed viewport", go through the same steps (add, window name, grab) and change the x and y positions, in my case x=1 and y=2 for the bottom-left workspace. 
[/LIST]

If you read this far, GOOD LUCK!

---

### Post by coldcritter64 on 2014-11-23
> **timrseattle said:**
> ....

Thanks for posting that timrseattle, I am not on a compiz desktop at the moment. 
That's basically what I was remembering using. Welcome, nice 1st post :smile: . Cheers, coldcritter64.

@ OP I'm pretty sure they were the settings I was referring to in my 1st post, and should be easier to use than gdevilspie ...
> There may be ways to control such with more advanced usage of Compiz settings
Good Luck. coldcritter64

---

### Post by DarkSapphire on 2015-03-17
Yea, my bad coldcritter64.  I got to be more descriptive.

---

