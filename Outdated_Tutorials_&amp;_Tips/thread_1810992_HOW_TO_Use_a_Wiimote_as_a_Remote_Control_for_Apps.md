---
title: "HOW TO: Use a Wiimote as a Remote Control for Apps"
date: 2011-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Mars11 on 2011-07-24
**Prerequisites:**
- A Wiimote
- Functional Bluetooth
- Ubuntu 11.04 Classic Desktop or Unity 2D (Problems with Unity 3D)

**1. Install wiican software.**
[*** New Instructions, updated for Natty, simpler]
- First install the Getdeb Repository PPA. [[COLOR="Blue"]http://www.getdeb.net/[/COLOR]]([COLOR="Blue"]http://www.getdeb.net/[/COLOR]) (Learn how to install applications from this web site by clicking [[COLOR="blue"]here[/COLOR]]("http://www.getdeb.net/updates/Ubuntu/11.04#how_to_install").)-

GUI:
- Open up the Ubuntu Software Center.
- Search for "wiican".
- Install it!

Terminal:
- Open up the Terminal. (Ctrl+Alt+T)
- Type ```
sudo apt-get update
```
- Then type ```
sudo apt-get install wiican
```

**2. Set up a udev rule so that any user can use wiican. (OPTIONAL)**
- From a terminal, ```
run sudo gedit /etc/udev/rules.d/76-wiican.rules
```
- Then copy in the following code:
```
KERNEL=="uinput", MODE:="0666"
```
- Save the file and reboot.

**3. Import and/or create Mappings.**
- Go to Applications > Accessories > Wiican or if using Unity 2D click the Ubuntu Icon and type "Wiican".
- A small Wiimote will appear in your panel. This means wiican is running.
- Right-click on the wiimote icon and selecte preferences.
- Uncheck the Mouse and Neverball boxes, unless you plan on using your Wiimote for those.

Make your own:
- Click the "new" button on the left.
- Type in "Rhythmbox" for the name, type and description. (OPTIONAL) 
- Copy the following into the mapping box.
```
Wiimote.A        = KEY_PLAYPAUSE
Wiimote.Up        = KEY_VOLUMEUP
Wiimote.Down    = KEY_VOLUMEDOWN
Wiimote.Left        = KEY_PREVIOUSSONG
Wiimote.Right    = KEY_NEXTSONG
Wiimote.Minus    = KEY_LEFT
Wiimote.Plus    = KEY_RIGHT
Wiimote.Home    = KEY_MUTE
Plugin.led.Led1    = 1
```
- Then click Save.

Import:
****UPDATED****
[[COLOR="Blue"]DVD Remote[/COLOR]]("http://dl.dropbox.com/u/16007317/Projects/DVD%20Remote.wii"):popcorn:
****UPDATED****
[[COLOR="blue"]Spotify Remote[/COLOR]]("http://dl.dropbox.com/u/16007317/Projects/Spotify%20Remote.wii"):guitar:

- Make sure that the ones you are going to use are checked.

**4. Connect your wiimote to wiican**
- Now left click on the wiimote icon. Choose the one use want to use.
- It will show you a message telling you to push the 1 and 2 buttons on your Wiimote, do so.
- The LEDs on your wiimote will flash for a bit, Wiican should connect to your wiimote, and then you should see the LEDs remain solid. You are now connected

**5. Set up GNOME so Wiican is started each time you login. (OPTIONAL)**
- Go to System > Preferences > Startup Applications.
- Click "Add".
- For the name put "Wiican", for the command put "wiican" (note the command must be in lowercase), for the description, put whatever you like. Click save.
- Make sure your new Wiican item is in the startup list and is checked. Click close.

Tada! That's it! Enjoy your new Wiimote power! If you want to make your own mappings, consult the following files:
- [[COLOR="Blue"][COLOR="blue"]Possible Actions[/COLOR][/COLOR]]("http://abstrakraft.org/cwiid/browser...ction_enum.txt"):
- [[COLOR="blue"]Possible Wiimote Inputs[/COLOR]]("http://abstrakraft.org/cwiid/browser/doc/wminput.list")

Enjoy!

**Most of this was taken from [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1713961&highlight=wiimote"). I just improved on it a little.**

---

