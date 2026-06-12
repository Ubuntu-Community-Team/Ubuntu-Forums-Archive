---
title: "lost Network Manager applet in panel in Ubuntu 11.10"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by sievec on 2012-03-28
Hi, I am new to Ubuntu, started with version 11.10. My Network Manager changes between running alright or never. I fixed it (again) and it connects to wireless and wired connections but the small icon is now lost in the panel. I am using Unity and want to keep it. So switching to Gnome is not an option. How do I get the icon back? I couldn't find anything in the web that helped. Any help will be greatly appreciated.

---

### Post by ubume2 on 2012-03-28
A fairly new user of 11.10 here. 

You don't see the network icon, but are you connected to the internet?

Go to dash home (upper left) and click enter "system" in the search area, you'll see system settings. Click on that and click on network.  Check out the settings. Make sure that if you are wired that it is on, or if wireless make sure it is on. Reboot.

Hope it helps.  If you are not connecting to the internet, or losing the connection, there could be a conflict between the kernel and your ethernet or wireless driver.  I had that happen on 11.10 once.  I had to transition from 10.04 to 11.10 because I was having increased problems with the newer kernels on 10.04 (the pae kernels).
0055 utc

---

### Post by Krytarik on 2012-03-28
> **sievec said:**
> Hi, I am new to Ubuntu, started with version 11.10. My Network Manager changes between running alright or never. I fixed it (again) and it connects to wireless and wired connections but the small icon is now lost in the panel.
Make sure the package "network-manager-gnome" is installed; if this command indeed installs it, relogin thereafter:
```
sudo apt-get install network-manager-gnome
```
Also, make sure its corresponding item in "Startup Applications", "Network", is not disabled - even though that's not easily done in the first place.

Other than that, you can always run it directly from the Terminal to see if it outputs any error messages:
```
nm-applet
```
Regards.

---

### Post by sievec on 2012-03-29
Wow, I am impressed. Installing the networker-manger-gnome helped. After rebooting, it's back in the panel. However, I could only install it via the software center, the code above would only download half the package with some file missing and then apparently not installing it properly. So I guess there's still a (or many) bug(s) in my system. But I will address those in a different thread. Thanks a lot for the help

---

