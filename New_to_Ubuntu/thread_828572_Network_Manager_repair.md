---
title: "Network Manager repair"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Eltern on 2008-06-13
I've been steadily increasing by Linux-fu over the past few years, but last week I really got myself in over my head, and now I'm in a bit of a jam. 

Short story:
I uninstalled the default GNOME network manager, and now I don't know how to connect to the internet (if I still have the necessary programs). So, instructions on how to get connected to a wireless connection from the command line would be great. 

Long story:
I was trying to connect to a WPA2 protected wireless network, and saw that the default program I used for connecting to wireless networks didn't have WPA2 as an encryption option. So I searched for wpa2 in the repositories, saw kwlan supported it, and installed it. Unfortunately, it seems the installation of kwlan uninstalled the previous network manager, which was very unexpected. Kwlan was/is a supreme hassle to work with, and in short order I unknowingly selected an option which hid many of its tools, including (as far as I can tell) the option to unhide them. So, that was a bust, and I no longer know how to connect to a wireless or wired connection. I'd love to know what I did wrong, but at the moment I'm most concerned about regaining the ability to easily connect to the internet from the GUI.

Thanks!

---

### Post by sam_delta on 2008-06-13
for the default network manager ```
sudo apt-get install network-manager network-manager-gnome
```

for wicd (another very good network manager) ```
sudo apt-get install wicd
``` i belive that wicd will appear under applications>internet

sam

---

### Post by Eltern on 2008-06-14
I would understand how to do that (I'm not quite -that- new :)), however, I can't get connected to the internet. Therefore, no connecting to the repos to get network-manager. Thanks for the help, but the problem remains.

---

### Post by sam_delta on 2008-06-14
try inserting ubuntu cd into your drive and type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install network-manager network-manager-gnome
``` they'll install from the CD,, you might also download the .deb packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), copy them and run them on the affected computer

sam

---

### Post by Eltern on 2008-06-14
Already tried that, and here's what happens: 

apt-get cdrom add works fine.

apt-get update
cries that it can no longer see the servers for the repositories.
(Could not resolve 'ubuntu.cs.utah.edu')
Finds the cdrom fine
Cries that it can't fetch from the servers
Then the message "W: Some index files failed to download, they have been ignored, or old ones used instead."

apt-get install network-manager network-manager-gnome
"Package network-manager is not available, but is referred to by another package. This may mean the package is missing, has been obsoleted, or is only available from another source."

I had previously unchecked the online repositories from the repos list in Synaptic. Checking them back in does not change the above behavior. It seems possible the the errors produced in apt-get update are preventing the update from properly identifying the CD's packages, but I'm just guessing :)

Thanks!

---

### Post by PmDematagoda on 2008-06-14
Well, you are on the internet from somewhere, so why don't you try getting the packages from Ubuntu Packages? To make things simple the network-manager packages can be obtained [here]("http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=hardy&section=all").

---

### Post by Eltern on 2008-06-14
That's a good solution, thanks! If anyone has a notion of what was going wrong with apt-get update, feel free to post so the rest of us learn.

---

### Post by sam_delta on 2008-06-14
duno what happened, might sound $tupid, but was it a 8.04 disk?

sam

---

