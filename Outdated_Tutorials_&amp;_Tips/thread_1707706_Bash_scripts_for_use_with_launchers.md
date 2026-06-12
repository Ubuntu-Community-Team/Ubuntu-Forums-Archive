---
title: "Bash scripts for use with launchers"
date: 2011-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by lyleunderwood on 2011-03-15
So I'm kind of crazy. I love launchers like Synapse (and ALT+F2) because I hate taking my hands away from the keyboard. I also have a really big clunky keyboard with no media keys (Model M :)) but I want to quickly control my media. My quick and ugly solution to this is to write shell scripts for invocation within Synapse. I thought somebody else might find these cool. They're very simple and only required some research to put together.

Also, I can't guarantee these will work with your system because they sort of assume you have a very simple basic setup.

The first one changes volume, and I call it vol.

This requires amixer which is in the package alsa-utils, **sudo apt-get install alsa-utils**
```
#!/bin/bash

amixer set Master $1
```amixer accepts values in a couple of useful formats, such as:

Set volume to 20%
vol 20%

Increase volume by 5
vol 5+

Decrease volume by 10
vol 10-

Nice. If master is not the correct control for your system (though it probably will be), figure it out! (hint: alsamixer scontrols)

I use Grooveshark to stream music, it's a flash based player that runs in a browser (there's also a desktop AIR version and an amazing Android app). I wanted to pause / resume Grooveshark without having to alt+tab to it or something, and I knew that Grooveshark responded to the spacebar event to pause / resume, so I cooked up the following script. I call it groove-pause.

This requires xdotool, **sudo apt-get install xdotool**
```
#!/bin/bash

win=`xdotool getwindowfocus`
xdotool search --name Grooveshark windowfocus type " "
xdotool windowfocus $win
```There is probably a better way to achieve this, xdotool is pretty powerful. Basically it gets the window ID of the currently focused window with the first line. It then looks for a window with "Grooveshark" in the title, focuses it, and sends it a space. Then it focuses back on the original window with the final line. This could probably be a single line of xdotool, but I didn't want to figure that out. 

**NOTE:** For this to work the tab that Grooveshark is in must be front and center! I generally keep Grooveshark in its own window, so that's no trouble for me.

This script is great because it's so easy to modify it to work with something else.

[B]INSTALLING
[/B]For anybody who doesn't know, you want to put these in ~/bin (if it doesn't exist, create it) and make them executable (chmod +x ~/bin/vol)

Just figured I would put these here on the off chance somebody else would have to repeat my research! If you've got different ideas about how to achieve these or similar things from Synapse or other launchers I'll be very intrigued.

Also, for all I know there may very well already be a Synapse plugin for volume, but I didn't bother to look because this was so simple. I really should, but I like using this type of stuff to learn more about bash.

---

