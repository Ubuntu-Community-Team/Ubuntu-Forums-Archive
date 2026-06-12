---
title: "How-to configure your network with scripts"
date: 2005-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by pjbgravely on 2005-11-08
I needed an easier way to change how my laptop connected to different networks. At home I use wireless with WPA encryption and static IP, but sometimes I need to use wired with static IP. When away I need to switch to open wireless with DHCP, and possibly wired with DHCP. I looked into the programs which can do this automatically but none seemed to fit my needs. The closest one was wifi-radar, but it didn't support my card running WPA  and since I already had a good working setup for WPA I decided that changing the configurations manually would be best. Doing this with the command line is slow, and dangerous if a command is forgotten. I have more than once locked up the laptop by trying to connect to an open AP without shutting off wpa_supplicant first.

  I started by copying my working config for wireless with WPA and static IP file in /etc/network.

sudo cp /etc/network/interfaces /etc/network/interfaces.home.wlan

I then used the network configuration GUI to setup 3 more configurations. It is important to test each configuration before continuing.

When I was done I had created 4 files with the following names:
interfaces.home.wlan
interfaces.roam.wlan
interfaces.home.lan
interfaces.roam.lan

Now to create the shell scripts. The scripts will copy the wanted configuration to /etc/network/interfaces, and restart the network.

I am giving examples of 2 of my scripts. The first one is to connect with WPA. Remember if you use different file names to substitute those in the scripts.

Open a shell and paste in:

gedit ~/.gnome2/nautilus-scripts/wireless_home

Copy this into the editor:

```

#!/bin/bash
gksudo 'cp /etc/network/interfaces.home.wlan /etc/network/interfaces'
gksudo '/etc/init.d/networking restart'

```

Save and then to make the file executable,

chmod +x ~/.gnome2/nautilus-scripts/wireless_home

In the second script you will notice that I killed wpa_supplicant. I did this on all the other scripts as well because of the lockup I mentioned earlier.

gedit ~/.gnome2/nautilus-scripts/wireless_roam

```

#!/bin/bash
gksudo 'killall -q wpa_supplicant'
gksudo 'cp /etc/network/interfaces.roam.wlan /etc/network/interfaces'
gksudo '/etc/init.d/ restart'

```

chmod +x ~/.gnome2/nautilus-scripts/wireless_roam

Now you are ready to test. 

cd ~/.gnome2/nautilus-scripts
./wireless_home

You will get a gksudo pop-up asking for your password. If you get any errors you will have to check your scripts for errors. Remember that you only will need your password once until it times out so you may not see the pop-ups while testing further. If no errors then,

gedit /etc/network/interfaces

Make sure that the file has been changed to what you want. If so test the rest and you are ready for showtime.

Right click on the desktop and select scripts and then the configuration you want. If you tested first your network should reconfigure perfectly and quickly.

Now I can quickly change between 4 different configurations. In the wireless roam mode I can use wifi-radar to connect. I also can use the Networking GUI to make changes, in all modes except wireless with WPA.

*Extra*
After finishing I realized that if the computer is booted up in a configuration that isn't available it takes a lot longer to boot. A fix for this would be to have the network configuration at boot be with no configured devices. I could do this with another script that I ran before I shut down but I thought it would be better if I had it done automatically.

***WARNING***
The following should only be done if you are skilled enough to recover from a command line if something goes wrong

First I created a new configuration file.

sudo gedit /etc/network/interfaces.no.network

Copy the following in.

```

# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback

```

Now create the script,

sudo gedit /etc/init.d/no_network

```

#!/bin/bash
cp /etc/network/interfaces.no.network /etc/network/interfaces

```

sudo chmod +x /etc/init.d/no_network

Test the script with,

sudo /etc/init.d/no_network

If the no network config is found in /etc/network/interfaces then the script works.


Now to make this script run only during shutdown or reboot make symbolic links to the shutdown /etc/rc0.d, and in reboot /etc/rc6.d

sudo ln -s /etc/init.d/no_network /etc/rc0.d/S20no_network 

sudo ln -s /etc/init.d/no_network /etc/rc6.d/S20no_network

Now for the final test change configuration and reboot then change and shutdown. If all goes well the no_network configuration will be there at boot. For me this worked perfectly the first time, and my computer boot much faster.Z

---

