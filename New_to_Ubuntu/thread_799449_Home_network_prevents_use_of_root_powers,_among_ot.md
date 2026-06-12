---
title: "Home network prevents use of root powers, among other things."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Janus%TheDoorman on 2008-05-19
I've been using Ubuntu for a number of months now, but I'm not sure where else to put this thread.

I've just come home from college, and after helping to setup my family's wireless network - Linksys WRT54G, WPA Personal Security, I noticed a new issues, the most prominent being the one in the title.

Whenever I'm connected to the home network, anything and everything that requires root permissions stops cold. sudo in the terminal, a GUI prompt for my root password, just running things like Synaptic, none of it works. As soon as I hop off the network, things run smooth.

Secondly, and I think this might have something to do with it, filesharing on the network is... difficult at best. The computer connected to the actual router is running Windows Vista, and if I try to access the music or documents on my laptop, which is running Hardy Heron, I get errors about not having permission to access those files.

I used 'sudo nautilus' to set the files/folders as shareable, but after closing nautilus, it seems as if the permissions didn't "stick", so to speak. I've set up Samba properly, as far as I can tell, but that is a possible source of error.

Lastly, the network connection doesn't seem to work at all if I set it to manual configuration through the Network Manager applet and feed the SSID and WPA Key in through that way. For whatever reason, when I go back and check the settings, the key is a great many more characters long than what I entered when I first set it up.

In summary:

-Home network is run though a Linksys WRT54G connected to a PC running Windows Vista
-When my laptop running Ubuntu 8.04 is connected to said network, processes requiring root privileges fail
-File sharing permissions are not being set properly, possibly because 'sudo nautilus' command is improper
-Manual configuration connection to the network fails, possibly because of WPA key issue

Thank you in advance for your help

---

### Post by Janus%TheDoorman on 2008-05-19
Bump

---

