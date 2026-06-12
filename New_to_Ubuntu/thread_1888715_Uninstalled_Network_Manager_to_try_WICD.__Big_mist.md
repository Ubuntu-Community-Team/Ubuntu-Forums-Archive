---
title: "Uninstalled Network Manager to try WICD.  Big mistake."
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Mesquiter on 2011-11-29
My Wifi connection with Ubuntu 10.10 kept dropping out so I decided to try another Wifi manager and installed WICD?  It seemed to work fine so I uninstalled my "Network Manager" to use only the WICD.  Big mistake.  WICD was working because of the network manager. Now, the WICD won't connect at all no matter how I configure it.  I have no Internet access and can't re-install "Network Manager."  How do I get "Network Manager" back without a complete re-install of the system?

---

### Post by bluexrider on 2011-11-29
Go to the machine that needs the the network manager re-installed. Open synaptic and search for the program ie: NETWORK-MANAGER. Highlight it as you would to install it then under FILE dropdown to Generate Package Download Script and save it to a thumbdrive.

Then you can use the thumbdrive on another machine to get the package and install it.


OR

use your live CD and under software sources add the CD to the source list and install it from there.

---

### Post by fantab on 2011-11-29
> **Mesquiter said:**
> My Wifi connection with Ubuntu 10.10 kept dropping out so I decided to try another Wifi manager and installed WICD?  It seemed to work fine so I uninstalled my "Network Manager" to use only the WICD.  Big mistake.  WICD was working because of the network manager. Now, the WICD won't connect at all no matter how I configure it.  I have no Internet access and can't re-install "Network Manager."  How do I get "Network Manager" back without a complete re-install of the system?

Try recovering it from archive.. Run the following command in the Terminal:

```
sudo dpkg -i /var/cache/apt/archives/network-manager_*.deb
```

---

### Post by Mesquiter on 2011-11-30
BLUEXRIDER ~

I tried your first suggestion and got confused as to the files and what I was suppose to do with them.  Tried the second with my Meerkat 10.10 install disk and it failed.  Tried again with a live Linx 10.04 DVD and transferred two packages to my hard drive "network-manager" and "network-manager-gnome"  I restarted the computer and in a terminal typed:  sudo apt-get install network-manager  then at the prompt:  sudo apt-get install network-manager-gnome.   Shut down and restarted my computer and voila! my "Network Manager" icon was there and already connected to the net.  Thanks for your help.  It's greatly appreciated.  You saved me hours of copying files and reinstalling.

---

### Post by Mesquiter on 2011-11-30
Fantab~

Thanks for your suggestion as well; except, I got messages: error processing:  cannot access archive:  no such file or directory: errors were encountered while processing.  I must have really erased the files.  I've spent hours on my own reading and pouring over posts on the net and finally you folks came through with some excellent suggestions.  Thanks again.

---

### Post by bluexrider on 2011-11-30
Glad to help

---

