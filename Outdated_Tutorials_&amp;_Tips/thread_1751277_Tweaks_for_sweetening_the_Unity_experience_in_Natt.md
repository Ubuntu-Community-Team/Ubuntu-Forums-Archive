---
title: "Tweaks for sweetening the Unity experience in Natty Narwhal"
date: 2011-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by chandra on 2011-05-06
There has been considerable exchange of opinion about the Unity interface on Natty Narwhal, both pro and con. I chronicle below my experiences with both, on a clean install of Natty on an AMD64 desktop in case it helps others.

**1. Natty installation**

Previously I used to manually partition my disk and mount not only the root and home partitions, but also some others during installation from the desktop ISO. The new installation GUI for manual partitioning does not allow user-specified mount points, but rather only standard ones like /opt etc., selectable from a menu. Whether this is a feature or a bug, it means that one needs to edit /etc/fstab after installation to mount the other partitions on non-standard mount points, at a somewhat small price of inconvenience. Apart from this exception, the installation went off flawlessly and much smoother than for Maverick or previous releases.

**2. Resizing icons on Unity Launcher**

The most persistent complaint about Unity that I have read is that the Launcher icons are too large on the desktop. There is valuable advice at:

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

which shows how to reduce the size of the icons in Launcher, i.e., the "panel' at the left. The steps are summarized below for convenience:

(a) ```
sudo apt-get install compizconfig-settings-manager
```

(b) Type Alt-F2 and "ccsm" in the textbox and click on the icon that appears in the first row.

(c) On the GUI:

 Desktop -> Ubuntu Unity Plugin -> Experimental -> Lauuncher icon size

I set mine to 32 pixels, which is the currently available minimum.

**3. Removing mounted media from Launcher**

There is useful advice at:

[http://www.tendenciadigital.com.ar/english/linux-open-source/how-to-remove-mounted-drives-from-the-ubuntu-unity-launcher.html](http://www.tendenciadigital.com.ar/english/linux-open-source/how-to-remove-mounted-drives-from-the-ubuntu-unity-launcher.html)

and

[http://goneme.com/?p=1553](http://goneme.com/?p=1553)

on how to prevent mounted media from hogging scarce space on the Launcher.

The steps are again summarized below:

(a) ```
sudo apt-get install dconf-tools
```

(b) Type Alt-F2 and "dconf-editor"

(c) On the GUI:

desktop -> unity -> devices

Select "Never"

**4. Customizing date and time**

First ensure that your language settings are correct by clicking on the icon at the top right panel with "On/Off" symbol and choose as follows:

System Settings -> System -> Language Support -> Regional Formats

and ensure that the date and time display are correct for your region.

Then look at what date and time the clock applet shows. On my system, unfortunately, the clock applet shows "month-day" rather than "day-month" as specified by my regional formats settings. I suspect that this might be generally true. If so, it is probably a bug that the locale-specific formats for date and time do not seem to be reflected in the date and time display in the clock applet.

The steps to set this right are:

(a) Type Alt-F2 and "dconf-editor" into the text box.

(b) On the panel that appears, navigate so:

com -> canonical -> indicator -> datetime

"custom-time-format" is at the top on the right panel and may be set by typing. I set mine to "%a %d %b %H:%M".

Then scroll down to "time-format" and select "custom".

You should now have a date and time display that you are comfortable with.

**5. Dash**

I did not have to use the Dash that appears on clicking on the Ubuntu icon at the top left except to bring up applications which I would then move to the Launcher to populate it. Even though the Dash has extremely large icons for a desktop PC, because it gets out of the way fast, I did not mind it or find any need to spend time to customize it in any way.

**6. Systray applications**

If an application like a wallpaper changer or an alarm clock does not appear on the "systray", you need to do this:

(a) Type Alt-F2 and "dconf-editor" into the text box.

(b) On the panel that appears, navigate so:

desktop -> unity -> panel

Edit the "systray-whitelist" entry to accommodate your panel applet that did not show up. You might need to reboot to see the change; I have not tested that.

**7. Switching workspaces**

Switching workspaces has attracted criticism because of the extra mouse clicks necessary. This is usually stated to be one click on the Workspace Switcher icon and a double click on the workspace one wishes to switch to in the "expo" graphic. However, one may reduce this to two mouse clicks, as explained in this quote:

> Left-click on the launcher = start expose mode.
Right-click on a workspace = switch to workspace.

from this post:

[http://ubuntuforums.org/showpost.php?p=10635653&postcount=7](http://ubuntuforums.org/showpost.php?p=10635653&postcount=7)

See also my comments in 8(c) below.

**8. Using the Unity interface**

My overall experience and opinion on Unity is positive. I think that Shuttleworth and his team at Canonical have used certain usage guidelines to design Unity. Once one realizes this, and is in sync with that thinking, the experience with Unity on Natty is a refreshingly efficient one.

What I have written below is simply my own inference based on playing with the interface: I am not privy to the thinking of the developers.

There are these major points:

(a) The Panel at the top has been pressed into service to also function as a "Universal Menu Bar" when a window is maximized. The disappearance of the familiar Menu Bar for firefox or gnome-terminal or gedit or thunderbird might at first be disconcerting. Yet, if the mouse goes to the Panel, it appears automagically. I think this decoupling of Menu Bar from application window was made to use the unused horizontal real estate on the Panel, especially during window maximization. In the process, some *vertical* space is also saved, to wit, the height of the Panel (or Menu Bar on application windows).

(b) I was at first unsure how to spawn a second tab or terminal from a gnome-terminal until I hovered my mouse over the Panel and the menu items appeared automagically. The interesting thing was that if two terminals were open, the extra tab got added only to the most recently active terminal. This is actually quite dandy! You can also use F10 to reveal the first panel menu and thereafter navigate with arrow keys.

(c) As long as the application window touches the Panel, one can move from one workspace to another *simply by clicking on the Launcher icon for the target application.* I noticed that this happens with two scenarios:

(i) if the application window is maximized, and the application window "docks(?)" into the Panel and loses its separate identity; or

(ii) if the application window is not maximized, but its edge is contiguous with the Panel.

In these circumstances, clicking on the relevant icon to move across workspaces is actually more efficient in Unity than was possible in Ubuntu Classic; one then circumvents the process explained above in (7). 

(d) The only persistent gripe I have read about is that the Launcher could not be customized to be on the right rather than on the left as at present. However, I did come across some setting that allowed the Launcher to be placed anywhere, but since I cannot find it again from the maze of configuration settings behind which it is hidden, I might be wholly mistaken on this. [Edit: please see [http://ubuntuforums.org/showpost.php?p=10810655&postcount=13](http://ubuntuforums.org/showpost.php?p=10810655&postcount=13) and [http://ubuntuforums.org/showpost.php?p=10810868&postcount=14](http://ubuntuforums.org/showpost.php?p=10810868&postcount=14) in this thread for more on this. At present, the edge from which Launcher appears does not seem to be customizable, and I do not recommend trying to do so.]

**9. Last Word**

All in all, my experience with Unity has been refreshingly different, perhaps even effervescent, like a fizzy lime drink. It is fun! Use it. If you find it getting in the way, surf the Web and find out how others have customized it to remove any sources of minor irritation. I, for one, think Unity is a step in the right direction and IIRC, it is on the pathway to a non-X graphical display subsystem. I hope Unity gets more polished, without ever sacrificing customization, during its evolution. It is that very power to customize that makes Linux and Ubuntu so attractive.

Enjoy!

---

### Post by beegary on 2011-05-09
> **chandra said:**
> **1. Natty installation**
 
Previously I used to manually partition my disk and mount not only the root and home partitions, but also some others during installation from the desktop ISO. The new installation GUI for manual partitioning does not allow user-specified mount points, but rather only standard ones like /opt etc., selectable from a menu. Whether this is a feature or a bug, it means that one needs to edit /etc/fstab after installation to mount the other partitions on non-standard mount points, at a somewhat small price of inconvenience. Apart from this exception, the installation went off flawlessly and much smoother than for Maverick or previous releases.
 !
 
thank you for the very useful post. I will try out a few of your tips.
regarding the first point, I struggled with this allot too but found a workaround.....
the installer would not let me type a custom mount point in, but what it will allow is for you to right click and paste. So I clicked on the network icon and types the required mount point in one of the add-wireless fields, right click copy (I wanted /bee_media), cancel out of that then paste it int he mount point.
I hope this helps others (I had no problem with this during the alpha release)

---

### Post by geazzy on 2011-05-10
great tutorial :D

---

### Post by meborc on 2011-05-10
It is good to have this kind of compiled knowledge here in the tutorial section

Be sure to update this post with new findings and tips! :)

---

### Post by rahilm on 2011-05-10
[http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/)

[http://www.omgubuntu.co.uk/2011/04/become-a-natty-power-user-in-no-time-using-this-unit-keyboard-shortcuts-wallpaper/](http://www.omgubuntu.co.uk/2011/04/become-a-natty-power-user-in-no-time-using-this-unit-keyboard-shortcuts-wallpaper/)

---

### Post by geazzy on 2011-05-10
> **rahilm said:**
> [http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/)

[http://www.omgubuntu.co.uk/2011/04/become-a-natty-power-user-in-no-time-using-this-unit-keyboard-shortcuts-wallpaper/](http://www.omgubuntu.co.uk/2011/04/become-a-natty-power-user-in-no-time-using-this-unit-keyboard-shortcuts-wallpaper/)

thanks :D

---

### Post by chandra on 2011-05-11
> **meborc said:**
> Be sure to update this post with new findings and tips! :)

I just came across this "list of lists" and thought I should share it here:

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

HTH

---

### Post by chandra on 2011-05-11
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

---

### Post by mtantawy on 2011-05-11
Thank you so much for these awesome tweaks, i wonder if you can help with integrating Thunderbird in the messaging menu?

I know there are a lot of posts but all are buggy and some are out-dated

---

### Post by chandra on 2011-05-12
> **mtantawy said:**
> i wonder if you can help with integrating Thunderbird in the messaging menu?

I know there are a lot of posts but all are buggy and some are out-dated

I am afraid that I have no experience with this. However, a quick search has shown that the primary development along these lines is by Ruben Verweij:

[https://launchpad.net/~ruben-verweij](https://launchpad.net/~ruben-verweij)

If you have not already done so, please also see:

[http://www.webupd8.org/2010/12/integrate-thunderbird-in-ubuntu.html](http://www.webupd8.org/2010/12/integrate-thunderbird-in-ubuntu.html)

and try```
sudo add-apt-repository ppa:ruben-verweij/thunderbird-indicator
sudo apt-get update
sudo apt-get install xul-ext-indicator
sudo apt-get install libnotify-bin
```bearing in mind that this is neither official nor supported.

Alternatively, there is this addon from Mozilla Labs themselves:

[https://mozillalabs.com/messaging/messaging-menu/](https://mozillalabs.com/messaging/messaging-menu/)

where they state> This is an experimental extension, and a work in progress. The extension currently only works with Thunderbird 3.3 and higher, running on Ubuntu Natty Narwhal. There are a number of shortcomings and known bugs with this version:

I am sorry not to be able to assist more, and hope that you get some pointers from these links.

---

### Post by chandra on 2011-05-13
There is also a cornucopia of indicator applets that may be installed at:

[http://askubuntu.com/questions/30334/list-of-application-indicators?s=1ccf7c8a-221e-4d01-bfa9-4939370ecfd3](http://askubuntu.com/questions/30334/list-of-application-indicators?s=1ccf7c8a-221e-4d01-bfa9-4939370ecfd3)

in case you are so inclined.

---

### Post by ubume2 on 2011-05-13
Great guide. 
Becoming a lover of Unity!.

Now all I need to do is remove "orphaned" apps in the Launcher Applications

---

### Post by Duncan Williams on 2011-05-13
You mentioned in the opening post re/ moving the launcher from left, I think the setting is here in CCSM. (reveal mode)

[IMG]http://files.myopera.com/DuncanWilliams/usercss/Screenshot.png[/IMG]

---

### Post by chandra on 2011-05-13
> **Duncan Williams said:**
> You mentioned in the opening post re/ moving the launcher from left, I think the setting is here in CCSM. (reveal mode)

Thank you Duncan Williams: that is precisely what I was referring to in my original post.

However, when I tried it out now, I find that the choice from "Left" to "Right" does not make any difference, even after a reboot. Launcher still shows up on the left edge.

So, I suspect that this setting might be for future use. Moreover, when I tried "Bottom" instead of "Left", a dialog popped up about a conflict with existing settings for something else. Given that Unity is still new, I did not want to press my luck by changing defaults I did not understand.

In sum, *perhaps* Launcher might be revealed from another edge in future, but it does seem to be from the left for now regardless of this setting. Moreover, choosing some other option than "Left" could upset other default settings, and possibly mess up the whole interface, not making it worth the experiment.

---

### Post by chandra on 2011-05-13
These links

[http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html)

and

[http://g33q.co.za/2011/05/02/ubuntu-unity-a-new-direction-no-one-expected-also-custom-launchers/](http://g33q.co.za/2011/05/02/ubuntu-unity-a-new-direction-no-one-expected-also-custom-launchers/)

help one personalize Launcher by customizing it.

---

### Post by wojox on 2011-05-13
Cool thread. If I had seen it earlier I would have posted here instead of a new thread. :)

[HOWTO: Create a quick launch for Firefox in Unity.]("http://ubuntuforums.org/showthread.php?t=1756050")

---

### Post by chandra on 2011-05-13
There is an interesting test given at 

[https://wiki.edubuntu.org/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.edubuntu.org/DemystifyingUnityGraphicsHardwareRequirements)

to find out if your graphics card is supported by Unity. It is

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by chandra on 2011-05-13
> **wojox said:**
> Cool thread. If I had seen it earlier I would have posted here instead of a new thread. :)

[HOWTO: Create a quick launch for Firefox in Unity.]("http://ubuntuforums.org/showthread.php?t=1756050")

Thanks wojox. :)

---

### Post by Duncan Williams on 2011-05-14
press the windows key on keyboard, type 2-4 letters of app or file/folder.
theres the app/file/folder icon staring right at you.

---

### Post by wojox on 2011-05-15
Here's a good one: [List of custom Launchers & Quicklists for Unity]("http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity/")

---

### Post by Duncan Williams on 2011-05-15
was having slow speed on my internet. (using my pre-paid mobile as a modem for 3g internet) so anywaze, it was annoying me, only getting like 10 - 40 k. So I put my mobile in a shiny steel saucepan and bang... it went upto 100 - 200 k.

---

### Post by Duncan Williams on 2011-05-17
If you are getting jerky responses from your browser,videos, mp3's etc. 
Try `unity 2D'
(install from software center)
It's much smoother and quicker on older machines and older graphics. 
and stops the jerks.

---

