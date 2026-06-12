---
title: "Program's exact name"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by czgirb on 2013-03-22
How can I know a program/application exact name?
**For example:** Previously, I think that **Ubuntu Tweak** is the program/application exact name. But later I found that **ubuntu-tweak** is the exact name.

Cos lately I found that my **U-Splitter** is not works properly. It begins to unable to join a file.
Previously I un-install the apps from **Ubuntu Software Center** and re-install it ... but all give a same result.
So, I suspect that the problem may caused from the configuration itself. So I wish to try:
> 
sudo apt-get purge usplitter *usplitter

But I'm not sure that my command is right.
Please guide me ...

The apps that I wish to uninstall is not only **U-Slitter** ... **Beatbox**, **Cairo** also.

---

### Post by schragge on 2013-03-22
See [thread=2124743]this thread[/thread].
Basically, what I came up with in that thread was
```

sudo apt-get install dctrl-tools
sed -nrs '/^\[Desktop Entry\]/,/^\[/{s/^(Name|Exec)=/\1: /p};${z;p}' /usr/share/applications/*.desktop|sort-dctrl -kName|tbl-dctrl -cName:30 -cExec:43|more

```
This will give you names of executables. They are not necessarily the same as package names. To find out the name of the package that installs an executable, try
```
dpkg -S `which [COLOR=blue]executable[/COLOR]`
``` where [COLOR=blue]executable[/COLOR] is the name you'll find with the long sed command above.

BTW, it's *u-splitter*: ```
sudo apt-get purge u-splitter
```

And what do you exactly mean with Beatbox and Cairo? The search for Cairo on apps.ubuntu.com gives me [92 results]("https://apps.ubuntu.com/cat/search/?q=Cairo"), while the search for Beatbox gives none. The only mention of BeatBox I can find is an MDA plugin for LV2 (no idea what these abbreviations mean) in the package [mda-lv2]("http://packages.ubuntu.com/precise/mda-lv2"): ```
apt-cache search beatbox
```

---

### Post by Frogs Hair on 2013-03-22
The purge command doesn't delete the profile folder _usually_ located home/hidden folders. ```
sudo apt-get remove --purge package-name
```

---

### Post by schragge on 2013-03-22
Neither *apt-get remove --purge* does. In fact, it does the same as *apt-get purge*

---

### Post by |{urse on 2013-03-22
Also try 

apt-cache search whateveryouthinktheprogramisnamedhere

Then look for the actual name in the results.

---

### Post by czgirb on 2013-03-22
> **schragge said:**
> 
... what do you exactly mean with Beatbox and Cairo?


Cairo ... is Cairo Dock
[http://glx-dock.org/](http://glx-dock.org/)

Beatbox is a Music Player
[http://www.omgubuntu.co.uk/2012/05/beatbox-music-player-sees-new-release-on-ubuntu](http://www.omgubuntu.co.uk/2012/05/beatbox-music-player-sees-new-release-on-ubuntu)
[http://www.noobslab.com/2012/05/install-beatbox-player-in-ubuntu-1204.html](http://www.noobslab.com/2012/05/install-beatbox-player-in-ubuntu-1204.html)

---

### Post by oldos2er on 2013-03-22
> **czgirb said:**
> How can I know a program/application exact name?
**For example:** Previously, I think that **Ubuntu Tweak** is the program/application exact name. But later I found that **ubuntu-tweak** is the exact name.

Something like ```
apropos tweak
``` would probably work, but I don't have Ubuntu Tweak installed to test it.

---

### Post by schragge on 2013-03-22
> **czgirb said:**
> Cairo ... is Cairo Dock
…
Beatbox is a Music Player
 Aha. So, to uninstall Cairo Dock, try
```

sudo apt-get purge ^cairo-dock

```
To uninstall BeatBox, try
```

sudo apt-get purge beatbox
sudo apt-get autoremove

``` The second command should uninstall dependencies of BeatBox like *libgranite* and *libsqlheavy*. After that you also may want to disable *ppa:sgringwe/beatbox* in your Software Sources.
 
To find out these bits of information, I searched for cairo on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and for bitbox on [https://launchpad.net/](https://launchpad.net/) (as it was clear that BitBox is not an official Ubuntu package, but part of a PPA).

---

