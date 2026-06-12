---
title: "HOWTO: Compiz-Fusion from GIT to Ubuntu Gutsy --- The Easy Way"
date: 2008-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by mlapaglia on 2008-03-24
I've read through a bunch of posts on how to get compiz-fusion from git. I've found the easiest way is through two seperate scripts. These two scripts do absolutely eveything for the user (except restart your x session after installation.)

**_Part One:_**
Uninstall anything related to compiz first through synaptic. open up the manager and search for compiz, and uninstall anything and everything that appears.

Download bp-compiz.tar.gz. Double click the file and pull the script out onto your desktop to extract it. Open up a terminal and type:

```
cd Desktop 
```
then
```
Sudo chmod 775 bp-compiz
```

to set the user rights neccesary for a proper install, and then

```
Sudo bash bp-compiz
```

and you should be presented with a few selection choices.

Select "0. Install..."
Select "0. GNOME"    ------ or KDE if that is the enviorment you are using
Select "0. Git (developer's repository with latest source, unstable)"
Select "0. Use (apt-get build-dep compiz)"

and now the configuration part is done. You should now be looking at a 1-16 choice menu. We are going to install choices 2, 3, and 4, but nothing else. This script will get libx11 running with xcb, and the required dependencies to run the Git version of compiz.

Select "2. Install Required Dependencies (git-core automake ...)"
let that install, then hit enter once it is finished.
Select "3. Install Compiz' Dependencies"
and hit enter once it is done.
Select "4. Install libX11 with xcb support (required for git)"
and hit enter once you are done.

After these steps are completed press

```
CTRL C
```

This will pull you out of the script and back to the regular terminal.

**_Part Two:_**

ElemonGW is currently supporting an excellently customizable script for installing compiz-fusion from the git, but it doesn't do dependencies or the xcb stuff yet. You should check out his website after this tutorial to see what you can really do with his script, but I've put together a GNOME and KDE version that will get a novice off the ground for now.

Download the second (or third) script that belongs to you (either Gnome or KDE) and extract is just as before.

go back to your teminal and type in 

```
cd git4cf
``` - but hit the tab button before you hit enter, which will fill out the rest of the name for you.

now

```
sudo python git4cf.py -i compiz 
```

then

```
sudo python git4cf.py -i bcop
```

then

```
sudo python git4cf.py -i libcompizconfig
```

then

```
sudo python git4cf.py -i compizconfig-python
```

and lastly

```
sudo python git4cf.py -i all
```

The first 4 parts need to be done in order because they depend on each other, and the script currently does not install them in the correct order for you. and after that you can install the rest of the parts automatically.

Now add compiz-fusion to your startup sessions.

Click System > Prefrences > Sessions

Then Click "+ Add"
and add the following
```
Name: Compiz-Fusion
Command: fusion-icon
Comment: Desktop Effects
```

and click OK.
Now log out and back in.

You should see a new icon in your task tray.

Right Click on the icon > Select Window Manager > Compiz

and you should then be running compiz. You can mess around with all the settings, after a few months of testing I've found it to be extremely stable. To get to the desktop customization options simpy right click the icon and click "Settings Manager" which will give you everything you should need to make compiz-fusion just the way you like it.

**_Part Three:_**
To update compiz-fusion to the latest and greatest Git issue the following command inside the git4cf-automator-(gnome or kde) folder:

```
sudo python git4cf.py -u all
```

and your computer will download and install the updated parts as needed.
if it says a specific component is up to date, then you can be assured you are using the most bleeding edge compiz-fusion has to offer.


For some reason the bulletproof dependency script installs a lot of KDE files (even for gnome users), so if you are using gnome and don't like the KDE files, and aren't using any programs using KDE (like amarok, etc) use

```
sudo apt-get remove konqueror
```
then
```
sudo apt-get autoremove
```

If you want to uninstall compiz-fusion, simply run the two scripts again and select the uninstall options. for the second script simply issue a 

```
sudo python git4cf.py -r all
```
and then do the same for the dependency script.

**_Troubleshooting:_**
Sometimes compiz-fusion complained about libcompizconfig not being installed, even though the script did. I believe this is because the components in Git are all updated at different times by different people, and the newer versions of the files don't see each other properly until they are all updated. You can install libcompizconfig from synaptic if all else fails, but normally waiting a day or two and seems to fix the issue.

The first script came from [http://forum.compiz-fusion.org/showthread.php?t=3960](http://forum.compiz-fusion.org/showthread.php?t=3960)

and the second one from [http://elemongw.exofire.net/projects/linux-section/git4cf-automator/](http://elemongw.exofire.net/projects/linux-section/git4cf-automator/) ( i just configured it for KDE and Gnome myself to spare some time) Elemongw's script is pretty robust. All of the modules are stored in py config files that you can custom make very easily, allowing you to install extra plugins that aren't included by default. He is actively developing his script and is very helpful when it comes to troubleshooting or additional features.

I take no credit for either of the scripts, I just found an easy way to install and keep compiz-fusion up to date.

---

### Post by the guitarist on 2008-07-04
hi there ...i tried to install using the script but when i try the 3rd option it gives me a fail msg ?!....what should i do

---

