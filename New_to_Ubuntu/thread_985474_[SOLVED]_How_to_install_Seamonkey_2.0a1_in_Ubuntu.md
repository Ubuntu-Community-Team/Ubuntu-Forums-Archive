---
title: "[SOLVED] How to install Seamonkey 2.0a1 in Ubuntu"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-11-17
In Synaptics all there is for Seamonkey is version 1.1.12. But...I'm wanting to get the latest alpha build, 2.0a1 installed. As I was using this in Windows, and I love it. It has a Firefox like add on manager to it.

So, there isn't a .deb package that I can find anywhere of 2.0a1, and I have never have much luck with installing .tar's. So would someone be kind enough to let me know or walk me through on how to install this in Ubuntu 8.10?

Thank you for any help.

---

### Post by spiderbatdad on 2008-11-17
You will have to read the instructions for the tar. If it uses standard build..../configure, make, sudo make install...You can run sudo "check install, if you install checkinstall first, from synaptic. This will build it as a deb and add it to your synaptic package manager for easy removal.

Also check out the seamonkey irc channel on freenode for on line assistance.

---

### Post by h8uthemost on 2008-11-17
Wow, I have no idea what you said. I forgot to mention I'm still pretty new to Linux, and a noob to Terminal.

But thank you though. I'll see where the instruction for that tar are.

---

### Post by spiderbatdad on 2008-11-17
right click on the tar file and select "extract here" then enter the folder and look for a readme or install file. Maybe provide a link to the package you downloaded?

---

### Post by aysiu on 2008-11-17
**Step 1**
Close all instances of Seamonkey (or Firefox or Iceweasel). Since the next step will require you to copy and paste commands, you may want to copy these to an open text file before you close your web browser. Believe me, you do *not* want to retype these commands. Copy and paste is the way to go.

**Step 2**
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cp -R ~/.mozilla ~/.mozilla.backup
wget -c http://mozilla.mirror.rafal.ca/seamonkey/releases/2.0a1/seamonkey-2.0a1.en-US.linux-i686.tar.bz2
sudo tar -jxvf seamonkey*.tar.bz2 -C /opt
sudo mv /opt/seamonkey/plugins /opt/seamonkey/plugins.old
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/seamonkey/plugins
sudo dpkg-divert --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey
sudo ln -s /opt/seamonkey/seamonkey /usr/bin/seamonkey
``` **Step 3**
That's it. Now the command *seamonkey* will launch the alpha build and the command *seamonkey.ubuntu* should launc the old repositories versio of Seamonkey.

**Terminal Commands Translation**
*cp -R ~/.mozilla ~/.mozilla.backup*

Copy recursively all the Seamonkey preferences (bookmarks, saved passwords, etc.)

*wget -c [http://mozilla.mirror.rafal.ca/seamonkey/releases/2.0a1/seamonkey-2.0a1.en-US.linux-i686.tar.bz2](http://mozilla.mirror.rafal.ca/seamonkey/releases/2.0a1/seamonkey-2.0a1.en-US.linux-i686.tar.bz2)*

Fetch the Seamonkey compressed file off the web.

*sudo tar -jxvf seamonkey*.tar.bz2 -C /opt*

Extract the compressed archive to the /opt directory.

*sudo mv /opt/seamonkey/plugins /opt/seamonkey/plugins.old*

Rename the plugins folder of the new Seamonkey.

*sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/seamonkey/plugins*

Link the real Ubuntu plugins folder to the Seamonkey plugins folder.

*sudo dpkg-divert --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey*

Divert the normal Seamonkey launcher to be a different name.

*sudo ln -s /opt/seamonkey/seamonkey /usr/bin/seamonkey*

Link the new Seamonkey launcher to the old Seamonkey command

---

### Post by Moop on 2008-11-17
You can get seamonkey 2.0 from this ppa.[https://launchpad.net/~fta/+archive]("https://launchpad.net/%7Efta/+archive") Follow the directions for adding it to your sources list ( System-Administration-Software Sources) and then you can get it from Synaptic. 

After you install Seamonkey you might want to uncheck the ppa in your Software Sources so you won't be prompted to upgrade everything else in the ppa although I've never had a problem with anything there.

---

### Post by aysiu on 2008-11-17
I didn't know about that repository. That's great to know, Moop.

In this particular instance, I might still suggest the old-fashioned method (the one I posted), since Seamonkey is still alpha (not beta). It may be good to be able to fall back easily to the stable 1.* release.

---

### Post by h8uthemost on 2008-11-17
Sweetness! Thank you Moop for that site! I didn't see any instructions on how to actually add it to the repos, so I just downloaded the .deb. And I now have 2.0a2 installed.

aysiu I tried your method, and Seamonkey appeared to install in Terminal, but only 1.1.12 would pop. Now the newer alpha one. So I'm not sure what I did wrong.

And thank you again spiderbatdad for the help.

I appreciate it you guys.

---

