---
title: "Set CPU speed &amp; touch support lacking after upgrading to 12.04"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by onthefence on 2012-06-21
I just upgraded my Lenovo x61t Tablet from version 10 to 12.04. So far two things I can't figure out:

1. CPU speed control - I used to have a menu bar item that alowed me to change the CPU speed, but it disappeared and I can't find it.

2. I also had a method of calibrating the touch capabilities but that method doesn't seem to work on 12.04. The stylus works perfect out of the box, but the finger touch input works incorrectly. It does respond but only moves the pointer very slowly while continually left-clicking at the same time. Anyone know how to set it up properly? Do you think it could be because I upgraded rather than doing a clean install?

Thanks

---

### Post by Dlambert on 2012-06-21
> **onthefence said:**
> I just upgraded my Lenovo x61t Tablet from version 10 to 12.04. So far two things I can't figure out:

1. CPU speed control - I used to have a menu bar item that alowed me to change the CPU speed, but it disappeared and I can't find it.

2. I also had a method of calibrating the touch capabilities but that method doesn't seem to work on 12.04. The stylus works perfect out of the box, but the finger touch input works incorrectly. It does respond but only moves the pointer very slowly while continually left-clicking at the same time. Anyone know how to set it up properly? Do you think it could be because I upgraded rather than doing a clean install?

Thanks

The cpu control should be automatic. Anyways the reason it's "not there" is because ubuntu 10.10/.04 used Gnome 2. Unity is brand new for you and uses Gnome 3.


Update to add cpu control: >      39     down vote   
                  **[[B]CPUFreq**]("https://launchpad.net/indicator-cpufreq")[/B]

  **Category:** *System Information*
  [IMG]http://i.stack.imgur.com/fdeBk.png[/IMG]
  If you have a laptop or Netbook and want to be able to cool down that  chip that's burning your hand and save some battery power this will be  useful.
  ppa:artfwo/ppa and install package indicator-cpufreq
 
                [link]("http://askubuntu.com/a/37997")[improve this answer]("http://askubuntu.com/posts/37997/edit")
          


---

### Post by philinux on 2012-06-21
ppa not required. indicator-cpufreq in ubuntu repos. Either install via synaptic software-center or command line.

> apt-cache policy indicator-cpufreq
indicator-cpufreq:
  Installed: (none)
  Candidate: 0.1.4-0ubuntu2


---

### Post by onthefence on 2012-06-21
Thanks to you both. OK, so I've got indicator-cpufreq installed but is there a way to set it up so it's always on the menu bar? I don't want to have to run the command each time I want to use it and keep the terminal open. Forgive me, but even after years of using Ubuntu, I am still a newb.

I have no idea what the difference between Gnome2 and Gnome3 are, but I am seeing many things that have changed from v10. It feels much more Mac-like. Especially the system prefs, dock. In Gnome2, it was much more "intuitive" to customize the menu bars. Why doesn't right-click do anything anymore? I'm so used to contextual menus. 

Is there still a way to customize which items appear on the menu bar?

---

### Post by Favux on 2012-06-21
> UNITY TRAY WHITELIST
Starting with  Ubuntu's Natty Narwhal (11.04) and the introduction of the Unity Desktop a whitelist for application icons in the System tray was added.  In order for Magick Rotation's icon to show you now need to add the key value 'magick-rotation' to the key systray-whitelist located at com.canonical.Unity.Panel.  Otherwise the Magick Rotation icon will not appear in the System tray.  The preferred way is to use gsettings from the command line.  First determine the list of applications whose icons are already whitelisted with:
    gsettings get com.canonical.Unity.Panel systray-whitelist
In the gsettings enable command add the magick-rotation-extension to the list of currently installed applications like so:
    gsettings set com.canonical.Unity.Panel systray-whitelist "['app1', 'app2', 'app3', 'magick-rotation']"
To remove Magick Rotation from the whitelist just delete the 'magick-rotation' key value from the list and run the gsettings set command again.  Then run the gsettings get command to verify it was removed.

Another option would be to use the dconf-editor, if installed, by running in a terminal:
    dconf-editor
and manually adding the 'magick-rotation' key value to the list in the systray-whitelist key.

NOTE:  In Precise (12.04) the key systray-whitelist appears at a new location in dconf-editor:  desktop.unity.panel.  However the old location is what gsettings uses.
From philinux you'd use indicator-cpufreq instead of magick-rotation.

It sounds like touch may not be on the linux wacom X driver.  What is the output of:
```
xinput list
```
run in a terminal?

---

### Post by onthefence on 2012-06-23
So update on the indicator-cpufreq, apparently I just needed to reboot because when I did, the applet automatically appeared on its own in the menu bar (same as systray?).

@Dlambert
Here is the output:
```
user@user:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]

```

---

### Post by onthefence on 2012-06-23
For the archives, this guy seems to be working on touch support for this tablet but so far hasn't fixed the touch issue I have.

[http://indexoutofboundsexception.wordpress.com/2012/05/01/installing-ubuntu-12-04-on-a-lenovo-thinkpad-x61t/](http://indexoutofboundsexception.wordpress.com/2012/05/01/installing-ubuntu-12-04-on-a-lenovo-thinkpad-x61t/)

---

### Post by Favux on 2012-06-23
Well the X Server does see your touch and it does appear to be on the Wacom X driver because we see stylus, eraser, and touch appended to the device name in **xinput list**.   But to be sure about the touch what is the output of?
```
xinput list-props "Serial Wacom Tablet touch"
```

For automatic rotation you can use Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

