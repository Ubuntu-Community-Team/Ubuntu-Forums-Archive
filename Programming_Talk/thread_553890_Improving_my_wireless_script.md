---
title: "Improving my wireless script"
date: 2007-09-18
forum: Programming Talk
---

### Post by MattAd on 2007-09-18
Okay, so I've been working little by little on a script that will connect me to available wireless networks on my laptop. What I have so far is good enough, and works, but I'd like to improve upon it and add more functionality.

Here's what I have so far:

```

#!/bin/bash

# setwlan.sh
# this script sets an essid for a wireless network I can connect to.
# This version has had a GUI added to it with Zenity.
# check 'man zenity' for zenity options.

E_NOESSID=65			# Error code if script is passed
				# without an ESSID name.

wlan_essid=`zenity --entry --text="Enter the name of the Network you want to connect to."` # Prompt for ESSID
	

if [ -z $wlan_essid ]
then
  zenity --error --text="You didn't enter a network name!"
  exit $E_NOESSID
fi

echo "Clearing out old network connection..."
sudo ifdown wlan0			# Close any old connections
echo "Setting ESSID..."
sudo iwconfig wlan0 essid $wlan_essid		# set the network name
echo "Network set!"
echo "Restarting network..."
sudo ifup wlan0			# Connect to the new network
echo "Done!"

exit

```

Here's my laundry list of what I'd like to add:
[LIST]
[*]Being able to select a wireless network from a list of which ones are available. Right now, I have to know what network I'm connecting to, to do so.
[*]I'd like to have this as a program, instead of just a script. What programming language would be ideal for that?
[*]I'd like to improve upon the GUI, specifically to have the terminal output in its own window, so that if I call this program something something other than a terminal window, I'll still get feedback as to if it connected or not.
[/LIST]

I'd like to hear everyone's thoughts and input. Thanks!

---

### Post by moephan on 2007-09-18
Here are some suggestings:

1. Use "sudo iwlist scanning" to get a list of available connection points. Parse the output and create a list from that.
2. Python
3. Design your GUI using Glade and implement it in Python and you'll have an honest to goodness Ubuntu app.

My $.02, HTH

Cheers, Rick

---

