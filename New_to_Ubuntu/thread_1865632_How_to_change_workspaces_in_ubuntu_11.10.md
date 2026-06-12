---
title: "How to change workspaces in ubuntu 11.10?"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by meadhikari on 2011-10-20
Probably the silliest question everasked BUT am a beginner in the Absolute Beginner Talk Section. :D


When I click on the workspaces in the doc, it divides the screen into 4 parts with my desktop in the first quadrant but how to change the workspace? When I tried clicking on the other quadrants of the screen nothing happens.

Thanks

---

### Post by ubupirate on 2011-10-20
I find that setting up keyboard shortcuts for the workspaces works much better than clicking (even though I am on 10.04, I did try 11.10 for awhile).

I've setup ALT+1, ALT+2, ALT+3 and ALT+4 for Workspaces 1,2,3,4 accordingly (as an example of what I use, you may find something else more efficient).

---

### Post by meadhikari on 2011-10-20
and How could one do that?
What must be the command so as to make Alt+1 switch to workspace one and so on?

---

### Post by ubupirate on 2011-10-20
> **meadhikari said:**
> and How could one do that?
What must be the command so as to make Alt+1 switch to workspace one and so on?

System Settings > Keyboard > Shortcuts

Find the listings with "Switch to workspace x", and click the area where it says "disabled" (workspace shortcuts are disabled by default), then enter your new shortcut combination.

---

### Post by meadhikari on 2011-10-20
There is not the Switch to Workspace on the Keyboard shortcut menu in 11.10 or I can not find it :(

---

### Post by Harry.k on 2011-10-20
hover your cursor over the icon and use the scroll wheel to switch the workspace

---

### Post by Paqman on 2011-10-20
> **meadhikari said:**
> When I tried clicking on the other quadrants of the screen nothing happens.


Tried double-clicking?

---

### Post by meadhikari on 2011-10-20
but moving my scroll wheel when the mouse is over the "workspaces" icons moves the dock up and down :(

am I not understanding what you are saying or what?

---

### Post by meadhikari on 2011-10-20
> **Paqman said:**
> Tried double-clicking?
Double clicking the quadrant is not helping either :(

Am I having some sort of error(ALT+TAB is just simple and not fancy at all for me)

---

### Post by Harry.k on 2011-10-20
> **Paqman said:**
> Tried double-clicking?

Of course. I guess i've been spoilt too much by kde to think of it.

---

### Post by Harry.k on 2011-10-20
Try reinstalling the unity user interface with synaptic. Maybe it is corrupted.

---

### Post by meadhikari on 2011-10-20
> **Harry.k said:**
> Try reinstalling the unity user interface with synaptic. Maybe it is corrupted.
How would I go that?
sudo apt-get install ?

---

### Post by philinux on 2011-10-20
> **meadhikari said:**
> Double clicking the quadrant is not helping either :(

Am I having some sort of error(ALT+TAB is just simple and not fancy at all for me)

Bit weird but you have to right click the quadrant you want.

This might help with any other problems.
 [http://ubuntuforums.org/showthread.php?t=1742326](http://ubuntuforums.org/showthread.php?t=1742326)

---

### Post by meadhikari on 2011-10-20
Right, Left, Scroll, Double click nothing works I think I have a currupt unity. How would I reinstall it?

---

### Post by meadhikari on 2011-10-20
```
sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version.
unity set to manually installed.

```

IS the "set to manually installed" some sort of problem or the cause of the error that I am having?

---

### Post by The Bright Side on 2011-10-20
Hey meadhikari,

welcome to Ubuntu, glad you made the switch. Expect to be frustrated with it for a bit until you figure out all the tricks, fixes and workarounds. Once you have the hang of it, you'll love it.

You can switch between workspaces using CTRL-ALT-Arrow Keys.

However, it is odd indeed that you cannot move between workspaces by clicking on them in the overview. I seem to remember that working just swell in the Unity interface in 11.04 (I moved to the Gnome Shell interface in 11.10).

"Synaptic" is a package manager, similar to the "Software Centre", but less fancy and more functional. It was the standard package manager Ubuntu was using before the introduction of the SWC, and remains the preferred manager for many users.

You can install it from the Software Center.

---

### Post by Harry.k on 2011-10-20
run the synaptic package manager. Search for it using the search bar of unity. In the package manager, search for unity. Mark all unity related installed packages(indicated with a green box) for reinstallation. Do this only if u think your unity is corrupted.

---

### Post by The Bright Side on 2011-10-20
> **meadhikari said:**
> IS the "set to manually installed" some sort of problem or the cause of the error that I am having?

Afaik, Synaptic will allow you to reinstall Unity from its GUI. Once you have Synaptic open, search for "Unity", then right-click on the icon to its left (should be a green box, because it is installed). You will get a menu, and one of the options should be "mark for reinstallation" or similar.

I may be wrong though, I'm at work atm and away from my Ubuntu machine, so I can't verify.

---

### Post by meadhikari on 2011-10-20
> **The Bright Side said:**
> Hey meadhikari,

welcome to Ubuntu, glad you made the switch. Expect to be frustrated with it for a bit until you figure out all the tricks, fixes and workarounds. Once you have the hang of it, you'll love it.

You can switch between workspaces using CTRL-ALT-Arrow Keys.

However, it is odd indeed that you cannot move between workspaces by clicking on them in the overview. I seem to remember that working just swell in the Unity interface in 11.04 (I moved to the Gnome Shell interface in 11.10).

"Synaptic" is a package manager, similar to the "Software Centre", but less fancy and more functional. It was the standard package manager Ubuntu was using before the introduction of the SWC, and remains the preferred manager for many users.

You can install it from the Software Center.

Thanks for your message.

But still that "CTRL-ALT-Arrow Keys" is not working either. :(
The switching of workspaces used to be very easy in the past using the mouse but I can not figure out that now.

First I thought I did not know How to do it, now it seems I am having error any way to fix this. I tried installing unity but it says its already in its latest form.

---

### Post by meadhikari on 2011-10-20
I installed Synaptic.
When I tried launching it, the synaptic screen flashes for a second and I get this in the terminal
```
(synaptic:29494): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:29494): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:29494): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(synaptic:29494): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
terminate called after throwing an instance of 'std::out_of_range'

```

---

### Post by The Bright Side on 2011-10-20
Okay, that's just weird. I would agree with the others here that your Unity is fried somehow. You can install Gnome Shell, then log into that, uninstall Unity, reboot, reinstall Unity.

Never hurts to have both user interfaces installed on your system anyway, they're both really cool (when they work). Though that's just my opinion :-)

Is your Ubuntu 11.10 install a fresh one, or did you upgrade from something else? As in, did you format your PC completely, then install Ubuntu 11.10?

If so, it may be worth just reformatting. Worst case, you'll lose an hour or two. Happens to me, too, when a new Ubuntu comes out - I usually install it once, tinker around with it until it's broken, then install it again and treat it nicely :-)

---

### Post by Harry.k on 2011-10-20
i recommend ditching unity and using kde or gnome. Its just a wee bit bloated and clunky

---

### Post by meadhikari on 2011-10-20
The Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
disappeared after i installed gtk2-engines-pixbuf 
but 

terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
is still shown and synaptic behaves the same way

---

### Post by philinux on 2011-10-20
Try this in a terminal.

unity --reset

---

### Post by meadhikari on 2011-10-20
> **The Bright Side said:**
> 

Is your Ubuntu 11.10 install a fresh one, or did you upgrade from something else? As in, did you format your PC completely, then install Ubuntu 11.10?


I upgraded from 11.04

> **The Bright Side said:**
> 
If so, it may be worth just reformatting. Worst case, you'll lose an hour or two. Happens to me, too, when a new Ubuntu comes out - I usually install it once, tinker around with it until it's broken, then install it again and treat it nicely :-)

Formatting is not a option for me right now. :(
and formatting most be the wrost case scenario. There must really be some option :)

---

### Post by meadhikari on 2011-10-20
> **Harry.k said:**
> i recommend ditching unity and using kde or gnome. Its just a wee bit bloated and clunky
Thinking exactly the same I installed GNOME 3 but did not liked it either, now I think I will swictch to Classic.

---

### Post by meadhikari on 2011-10-20
> **philinux said:**
> Try this in a terminal.

unity --reset

I did and the output is below if it helps solving the problem.

```
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Processing upgrade com.canonical.unity.unity.01.upgrade
profile: unity
number: 1
domain: com.canonical.unity
Initializing session options...done
Initializing staticswitcher options...done
Initializing snap options...done
Initializing core options...done
Initializing fade options...done
Initializing mousepoll options...done
Initializing ezoom options...done
Initializing wall options...done
Initializing bailer options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing compiztoolbox options...done
Initializing workarounds options...done
Initializing unityshell options...done
Initializing opengl options...done
Initializing gtkloader options...done
Initializing decor options...done
Initializing scale options...done
Initializing detection options...done
Initializing vpswitch options...done
Initializing expo options...done
Initializing grid options...done
Initializing regex options...done
Initializing move options...done
Initializing unitymtgrabhandles options...done
Initializing composite options...done
Initializing imgpng options...done
Initializing resize options...done
Initializing place options...done
Removed 0 items from active_plugins
Overriding value alt_tab_timeout
Completed upgrade com.canonical.unity.unity.01.upgrade
Processing upgrade com.canonical.unity.unity.02.upgrade
profile: unity
number: 2
domain: com.canonical.unity
Overriding value x_offset
Overriding value y_offset
Overriding value distance
Overriding value vp_distance
Overriding value vp_brightness
Overriding value vp_saturation
Overriding value reflection
Completed upgrade com.canonical.unity.unity.02.upgrade
compiz (expo) - Warn: failed to bind image to texture

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(compiz:32092): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed
WARN  2011-10-20 21:20:31 unity.bghash BGHash.cpp:390 Passed in a bad pixbuf, defaulting colour
WARN  2011-10-20 21:20:31 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1360x768

Couldn't find a perfect decorator match; trying all decorators
Starting unity-window-decorator
DEBUG 2011-10-20 21:20:34 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1360 h=768
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "main_menu_key"
Setting Update "run_command_terminal_key"
Setting Update "run_key"
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-20 21:21:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-20 21:21:33 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-20 21:21:33 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory


```

---

### Post by meadhikari on 2011-10-20
BTW CTRL+ALT+ARROW works after 
unity -reset

Thanks to the community for your time.
The single best thing of me using ubuntu is the community of helpful people who help me in any problem encountered :)

---

### Post by The Bright Side on 2011-10-20
unity --reset doesn't do it?

Apart from that, I'm outta ideas for now. Generally, though, for the long run, I highly recommend formatting when new releases come out. It's a great way to have a fresh desktop every half year. Dump your home directory on an external hard drive, install new Ubuntu and then copy it back.

I was completely pissed off by both Unity and Gnome Shell when I first installed 11.04, so much so that I went back to 10.10 on my desktop PC. But a couple months later, I put 11.04 back on my laptop and started really enjoying Unity. You need to get used to them, but then they are pretty cool.

EDIT: aah! Here we go. Glad it's working now!

---

### Post by Harry.k on 2011-10-20
> **The Bright Side said:**
> unity --reset doesn't do it?

Apart from that, I'm outta ideas for now. Generally, though, for the long run, I highly recommend formatting when new releases come out. It's a great way to have a fresh desktop every half year. Dump your home directory on an external hard drive, install new Ubuntu and then copy it back.

I was completely pissed off by both Unity and Gnome Shell when I first installed 11.04, so much so that I went back to 10.10 on my desktop PC. But a couple months later, I put 11.04 back on my laptop and started really enjoying Unity. You need to get used to them, but then they are pretty cool.

EDIT: aah! Here we go. Glad it's working now!

Unity is best enjoyed on a netbook. On a pc, xfce or kde or gnome are better

---

### Post by Harry.k on 2011-10-20
> **meadhikari said:**
> BTW CTRL+ALT+ARROW works after 
unity -reset

Thanks to the community for your time.
The single best thing of me using ubuntu is the community of helpful people who help me in any problem encountered :)

True! Mycrowshaft wind'uhs users never get the quality of support we get. I'm glad i dumped wind'uhs

---

### Post by Goldquestllc on 2012-04-03
> **meadhikari said:**
> Probably the silliest question everasked BUT am a beginner in the Absolute Beginner Talk Section. :D


When I click on the workspaces in the doc, it divides the screen into 4 parts with my desktop in the first quadrant but how to change the workspace? When I tried clicking on the other quadrants of the screen nothing happens.

Thanks


If you haven't figured it out (or for anyone having the same problem), this is what I do.

After having our 1st program open, click the workspaces icon to the left, and the 4 panels opens. DOUBLE click on any other pane, and it will open (half way), then DOUBLE click again.  You will see your full desktop again.  (NOTE) the program you have in pane 1 you will see a small check mark along side the icon on the left that means that program is still open).  Now that you have the SECOND pane (desktop) up, click any other program.  Now click again on the workspaces icon to the left and you will see your programs in 2 panes.  To open one or the other, you have to DOUBLE CLICK TWICE, once to view, and once to activate.  Switch back and forth with the workspaces icon on the left.

---

### Post by cshowardjohnson on 2012-05-16
the person saying to go to keyboard shortcuts was close but they moved it's location in 11.10

to to the icon in the top right corner of the screen.
select "system settings..."
search for keyboard, click on it.
select the shortcuts tab.
under navigation are the "switch to workspace" shortcuts.

good luck.

---

### Post by cshowardjohnson on 2012-05-16
One other thing, you can switch workspaces by using CTRL + ALT and one of the arrow buttons (up down left right) to move to that workspace respecitively.

To move the active window to that workspace include the SHIFT key in that combonation

example: 

to move the current window to the right workspace press CTRL+ALT+SHIFT+Right arrow

Have fun.

---

