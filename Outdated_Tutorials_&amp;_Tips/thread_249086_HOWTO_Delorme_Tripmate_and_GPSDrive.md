---
title: "HOWTO: Delorme Tripmate and GPSDrive"
date: 2006-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by amp_man on 2006-09-02
For starters, I've tried to make this as complete as possible but still keep it concise, since documentation on this GPS is fairly scare, and what little documentation there is is usually based on HAM radio usage. So, having little experience with GPS and serial ports, this has taken me literally months (off and on) to figure out. I'm writing this in the hope that some other linux user (Ubuntu or not) will find it helpful, and if you do, please let me know.

The Delorme Tripmate is an older NMEA-compatible serial port GPS from Delorme, that is now available fairly cheap from places like eBay (~$50 USD, mine was $10 at a yard sale). However, trying to use programs like GPSd and GPSDrive right out of the box results in failure (timeout from GPS). Since this GPS doesn't have a power switch, it requires the string "ASTRAL" to be sent to it before it will start broadcasting coordinates. If that helps you, great! Otherwise, if you're like me and have no idea what to do now, read on:

Starting from the _very_ beginning, get gpsdrive. I've never gotten this to work with GPSd, if anyone can tell me how, it'd be awesome, but IMO, gpsdrive is the only usable linux GPS client anyways:
```
$ sudo apt-get install gpsdrive 
```
Now, run gpsdrive (not as root)
```
$ gpsdrive
```
Click the preferences button and then the "Settings 2" tab, and you should see a box that looks something like this:
[img]http://ubuntuforums.org/attachment.php?attachmentid=15182&stc=1&d=1157176358[/img]
Notice the check box for **"Use serial conn."** is checked, and **Baudrate** is set to 4800, you will need to mimic these settings. If you're interested in the others, read the gpsdrive manpages, but don't check them off, especially not the GARMIN or Earthmate settings. **Interface** should be set to your serial port interface; /dev/ttyS0 is usually the first serial port, or /dev/ttyUSB0 for most USB-to-serial adapters (like mine). If you don't know where your GPS is connected to (ie what serial port), scroll down to the bottom, first entry in the "Side Notes" section. Once you've got that set, it's time to see it in action. First, head outside, GPS doesn't work very well inside, even near windows. I'm writing this from my car, with the Tripmate on the dash, and getting decent (but not great) signal.

```
For serial:
$ sudo echo "ASTRAL" >> /dev/ttyS0 && gpsdrive
or for USB:
$ sudo echo "ASTRAL" >> /dev/ttyUSB0 && gpsdrive
```

From what I can find, the Tripmate has a timeout for the ASTRAL string, if a program doesn't open a connection to it, it will revert back to sleep mode very quickly, so I reccomend running it as a single string. Also, if you're still a somewhat of a noob like me, notice that only the "echo" command is being run with root privileges, gpsdrive should not be (and will warn you if you do).

For my USB connection, I made this (really!) simple script:
```
#!/bin/bash
if [ -e "/dev/ttyUSB0" ]; then
        gksudo echo "ASTRAL" >> /dev/ttyUSB0 
        gpsdrive
else
        echo "GPS is not connected!"
fi
```

This basically checks if the GPS (WARNING: or any USB communication device, like a usb modem or cell phone) is connected, and if it is, sends the string and starts gpsdrive, otherwise it exits. If you want to use this, copy it into a text file, save it, and then run "$ chmod +x <file>". I then put it in /usr/bin, and created a link on my panel to it. Gnome even has an icon, "gpsicon.ico" in /usr/share/pixmaps.

** Using GPSDrive: The Basics **

This is by no means a full tutorial, just enough to get you started. By default, GPSDrive will open with a map of some area of Germany. Once the "Not enough satellites in view" message at the bottom disappears (this will take several minutes the first time, and about a minute each time after), move the slider at the left to get to a world map, and if you live in the US, it will probably show your location as being somewhere in outer space. DON'T PANIC!. Click the "Download Map" button, and then select a scale of 2000000. This should download a fairly large (state-size) map around your GPS's current coordinates. From there, you can download higher detailed maps of your location, and use the "Pos. Mode" to move the map focus and get maps of other areas. You can also set waypoints using CTRL-click, and map out trip routes. From here, you're on your own!

**Known Problems:**
GPSDrive at times doesn't like to close when using a direct serial connection (ie not using gpsd), at least with this GPS. Closing with the close button on the top bar will result in Gnome complaining about it not exiting and a Force Quit option, and using the Quit button will hang. The best option is using the close button at the top, and then selecting Force Quit.

When closing and reopening GPSDrive, the Tripmate will sometimes stay in sleep mode. I have no idea why, it just does. Just close and reopen gpsdrive (with the astral string or your script) a few times, and it should eventually work.

***Side Notes***
Some other Tripmate-related things I found out while researching that don't apply to me, but might help other users.

"Finding" your GPS:
Figuring out which serial port your GPS is connected to sometimes isn't as easy as it sounds. Ubuntu automatically sets up /dev/ttyS0 as your first serial port, /dev/ttyS1 as the second, etc. But some hardware manufacturers do odd things and the first physical serial port isn't necessarily the first hardware one. If GPSdrive still reports it can't find your GPS after following the guide, use the ASTRAL to your advantage. ASTRAL is being constantly sent out by the GPS, so with 
```
$ cat /dev/ttyS0
```
you should be able to see the ASTRAL string (use CTRL+C to exit). If not, try ttyS1, 2, and 3. If you still don't get an ASTRAL, check your batteries, or else it be that your unit has been modded (see below), your serial port is disabled in the BIOS, or your Tripmate is just plain dead.
If you know how to work with serial ports, you could probably create a script or program that checks for the "ASTRAL" string incoming on a serial port (the Tripmate broadcasts this constantly while in sleep mode), but that's beyond me.

Alternative power options: 
The Tripmate, like many GPS's, eats batteries. [here](http://www.shotton.com/gps/tripmate_cable.html) is a tutorial to create a power adapter to plug into your cigarrette lighter, or [here](http://www.bevhoward.com/TripMate.htm) you can find info on supplying power from your laptops keyboard/mouse connector. Personally, I have a lighter adapter from a PSP ($1 on clearance at walmart, supplies 5v, 2A) connected directly to the wires from the battery terminal.

Hardware mod:
This mod removes the necessity for the "ASTRAL" string to be sent to the GPS by routing the ASTRAL sent by the GPS while in sleep mode back to itself, so it's essentially on any time there's power. If this sounds like your cup of tea, and you've got a steady hand with a sodiering iron, check it out [here](http://wes.johnston.net/aprs/tripmate.htm)

---

### Post by t182s on 2007-10-03
what repositories are you using?

---

### Post by amp_man on 2007-10-03
Last time I used it I was using the normal Feisty repos, I've since updated to Gutsy beta and don't have a use for it at the moment.

And since this thread has already been bumped, I might as well mention that I only own a Tripmate, not an Earthmate. I've been getting a few emails/pms lately about this, and TBH I don't know jack about the Earthmate, other than it's USB and very different from the Tripmate. The info in this HOWTO will NOT carry over to the Earthmate.

---

### Post by tgalati4 on 2007-10-04
I've had good luck compiling from an SVN snapshot of gpsdrive.  Gpsd seems to work with the snapshot that I used.  I use a USGlobalSat BU-353 USB GPS.  I was able to get 7 instances of gpsdrive sharing one GPS device and run it for 4 days.  No memory leaks--and stable--100% CPU load.

I modified it to play mp3's when you get to within 35 meters of a defined waypoint.

---

### Post by ckamas on 2008-12-10
To get gpsd to work, you have to set the baud rate to 4800 first.  I also force gpsd to keep the TripMate alive with the -n command.

try:
$ stty -F /dev/ttyS0 4800; echo "ASTRAL" >> /dev/ttyS0; gpsd /dev/ttyS0 -n

when I run the gpsd with the debug turned on I get:

gpsd: launching (Version 2.36)
gpsd: listening on port gpsd
gpsd: Unable to start ntpshm.  gpsd must run as root.
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 1000
gpsd: running with effective user ID 1000
gpsd: opening GPS data source at '/dev/ttyS0'
gpsd: speed 4800, 8N1
gpsd: => GPS: $PASHQ,RID*28\x0d

Good luck
Chuck

---

