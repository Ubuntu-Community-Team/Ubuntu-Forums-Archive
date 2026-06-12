---
title: "Advice before installing"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by applet3typod on 2014-05-06
Hey all, I'm not new, but I'm definitely rusty. Last time I used Ubuntu it was 10.something and I only set it up for basic internet tasks. 

So, I ask you, what should I do/get first? What are some must have applications? What reading/learning material do you suggest so I can get better aquainted? My only real desire for this machine is to be able to run my facebook groups, keep up on other social networks like twitter and pinterest, and play Hearthstone. My CPU and integrated laptop graphics can't handle anyting I'd really like to play, so how can I get the most out of this machine for me? (IE, someone not focused on business)

---

### Post by monkeybrain20122 on 2014-05-06
Social networking will work with no problem. As for heartstone, looks like you are in luck [http://appdb.winehq.org/objectManager.php?sClass=version&iId=28875](http://appdb.winehq.org/objectManager.php?sClass=version&iId=28875)

---

### Post by bobmoyer on 2014-05-07
Don't forget to install the restricted extras...

---

### Post by applet3typod on 2014-05-07
I remember Wine, but never got into it much. I'll definitely learn it now so I can set up my Hearthstone. As for restricted extras, not sure what language you're speaking, bobmoyer.

---

### Post by caver12 on 2014-05-07
Also there is Steam for Linux now. They are adding games al lthe time.

---

### Post by stalkingwolf on 2014-05-07
you will find the restricted etras in synaptic package manager.  i think its ubuntu restricted extras.  just putting restricted extras in the search will bring them up.

---

### Post by dmbNCSU on 2014-05-07
I would start to learn the command line interface (terminal).  It really is amazing how powerful a tool it is that has been around as long as personal computing.
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by Kurt_Alan on 2014-05-07
**[COLOR="#000000"][SIZE=5][/SIZE][/COLOR]**

Hi,

I keep this document in the cloud, a running list of quick installs and tweaks.  If I need to do a re-install, this list minimizes configuration time, particularly with command line installs.

These are my personal notes (edited). You can add or subtract.


If you mess up Upgrade Manager via CLI (dpkg), to fix broken packages:
sudo dpkg –configure -a
sudo apt-get install -f

****
Add PPA:
sudo add-apt-repository ppa:someppa/ppa

sudo apt-get update

Remove PPA:

sudo add-apt-repository --remove ppa:someppa/ppa

****
Y PPA Manager 0.9.9.2:  

sudo add-apt-repository ppa:webupd8team/y-ppa-manager

sudo apt-get update

sudo apt-get install y-ppa-manager  
****


Add ccsm:

sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

**Use advanced graphics features only on desktop (wobbly windows).
wiki.compiz.org
****
Google search: Things to do after install Ubuntu 14.04 . . . 
There will be a plethora of links.  Pick and choose.
****
Install multimedia codecs--
sudo apt-get install ubuntu-restricted-extras
NOTE: When you come to Agreement, scroll down, TAB to highlight OK, then Enter.
****

unity tweek tool--
sudo apt-get install unity-tweak-tool
****

Install classic menu indicator-- First, see Note below:

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator
****

THIS IS THE PREFERRED METHOD, IF AVAILABLE:
**Store: Install ClassicMenu Indicator (indicator applet to show the Gnome Classic Main Menu).
****

Remove keyboard indicator
The keyboard langauge is indicated on your panel. Why? If this annoys you you can remove it.
System Settings-> Text Entry and uncheck the Show current input source in the menu bar.
****
Add a nifty system load indicator--
sudo apt-get install indicator-multiload

****

****
Dropbox.  Synaptic.  Enable Dropbox/Nautilus.
Install.
dropbox -h   CLI choices
****

****
Add workspaces
Type “appearances” at the dash (or get there from system settings), click behavior, show workspaces.

To change horizontal and vertical numbers:

Substitute the number you want below after you copy/paste:
To change the number of rows, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ vsize 2 

To change the number of columns, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hsize 3 
****
Turn off third-party searches and Internet searches in Dash--
wget -O disable-searches.sh [http://drive.noobslab.com/scripts/disable-searches.sh](http://drive.noobslab.com/scripts/disable-searches.sh)
chmod +x disable-searches.sh;./disable-searches.sh;rm disable-searches.sh

****  
Synaptic: Add: dconf-editor
sudo dconf-editor
****
Keyboard shortcuts can be set by changing keybinding values with Configuration Editor. From terminal, navigate to org > gnome > desktop > wm > keybindings.

In place of dconf-editor you can also:

sudo gnome-control-center

****
screenlets: Old, broken, unsupported
None available for TT at this time (May, 2014). Try later but do NOT use screenlets.org).
****
Auto Start Up an Application   

Click the Dash Home icon (or tap Super), type 'Startup Applications' to search for the application and run it.
Click the "Add" button.
Name a program.
Click the "Browse" button and navigate to "Computer" > usr > bin, where programs are usually installed.
Select a program, click the "Open" button followed by the "Add" button.

The above program will then be listed in additional startup programs. Check if the program runs automatically by logging out.
****
Clean Up Old Crash Reports  
If your Ubuntu system always pops up a dialog saying "System program problem detected" each time you log in even though you've already reported the problem, you might need to clean up all old crash reports:

sudo rm /var/crash/* 
****


Also, I do not use the Home Folder for any data.  I re-create Home Folder in Dropbox.  This icon will go on the Desktop.  Here I also keep my various OS backups, including screenshots, this document, etc.

In the event of an OS crash or a lost/stolen computer, I re-access all my goodies from the cloud.  Then move through a rapid configuration from this document.

Also, go to the Store, installed Apps, and remove everything you don't need.

---

### Post by monkeybrain20122 on 2014-05-07
> **Kurt_Alan said:**
> 

Install classic menu indicator-- First, see Note below:

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator
****

THIS IS THE PREFERRED METHOD, IF AVAILABLE:
**Store: Install ClassicMenu Indicator (indicator applet to show the Gnome Classic Main Menu).
****


The preferred method is not to use the classic menu. If you use Unity there is no need for it. :) Also the classic menu is in the repo. There is no need for the ppa may be since 13.10(?)

> 
To change horizontal and vertical numbers:

Substitute the number you want below after you copy/paste:
To change the number of rows, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ vsize 2 

To change the number of columns, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hsize 3 
****


There is no more gsettings I think since they now use dconf. Also that long strings indicate the location of the settings in question within the menu structure of dconf-editor (used to be in gconf-editor, hence gsettings), but they change from release to release as they tend to modify things.A slightly better way is to use the dconf-editor gui, but the best way is to use CCSM. Instead of navigating through the maze of sub menus in dconf-editor, it is much easier to do it in the ccsm General > Desktop Size

> 
Turn off third-party searches and Internet searches in Dash--
wget -O disable-searches.sh [http://drive.noobslab.com/scripts/disable-searches.sh](http://drive.noobslab.com/scripts/disable-searches.sh)
chmod +x disable-searches.sh;./disable-searches.sh;rm disable-searches.sh


You don't need any third party script. Just go to system settings > security and privacy to press a button to turn off online search.

> Synaptic: Add: dconf-editor
sudo dconf-editor
****
Keyboard shortcuts can be set by changing keybinding values with  Configuration Editor. From terminal, navigate to org > gnome >  desktop > wm > keybindings.

In place of dconf-editor you can also:

sudo gnome-control-center



There is no need for 'sudo' (and undesirable to abuse sudo) for either doconf-editor or gnome-control center, also both have gui and there is no need to use the terminal to start them at all. I think the gnome-control-center is only for gnome-shell (I never installed it in Unity)


Finally there is one thing which is very handy but seldom mentioned. In  Nautilus go to Files > Preferences > Behaviour to check the box "add a delete command to bypass trash", the trash is the most stupid and useless feature, when I delete something I want it gone, not to be moved to a "hidden" directory where it sits and takes up space. There are similar options in other file managers. Also, I set executable text files to 'ask what to do" instead of "display". When you have a script you want to right click to run it, not to stare at the content. On the other hand, setting it to always execute is a bit dangerous, you may also want to edit it, so "ask what to do" is the most sensible option.

---

### Post by applet3typod on 2014-05-07
> **caver12 said:**
> Also there is Steam for Linux now. They are adding games al lthe time.

Would this run through Wine, or is it actually ported for Linux? I've never used steam, but 90% of what I do in life is play games. Go figure, my other 10% is spent running a health group and coaching on healthy living. lol.

I'll check out all the other info y'all posted. I like the idea of making a pre-designed backup so If I have to reinstall (or when I replace this tiny HDD I just had to put in) I can have most of my installed packets and settings right back in place. I worked for Apple for years, so I'm comfortable with a Max style OS. Because of this I'm running cairo dock and I have things like spaces and expose set up. I prefer the simplicity of Windows, but the first thing I always do when I install Ubuntu is make it a bit Mac-like. 

Linux seems to run almost exclusively on ones ability to use terminal, though I see there are many new features that work around this, like the app store, etc. I'm wondering, is there a guide that will explain file structure and basic OS navigation? I know exactly where to go for any system files or app data type things on mac and windows, but on here it's all abbreviations and I can't make heads or tails of it. I'd also love to know simple things like, when I close an app, is it closed or is there a process still running, etc. I need a visual guide book, or Trusty for dummies. lol

---

### Post by applet3typod on 2014-05-07
> **monkeybrain20122 said:**
> ...there is one thing which is very handy but seldom mentioned. In  Nautilus go to Files > Preferences > Behaviour to check the box "add a delete command to bypass trash", the trash is the most stupid and useless feature, when I delete something I want it gone, not to be moved to a "hidden" directory where it sits and takes up space.

That is exactly the kind of response I'm needing... things I wouldn't even think of, or know to ask about. Is Nautilus a pre-installed app? I'm not finding it, just wondering if it's something I need to grab from the software center.

---

### Post by monkeybrain20122 on 2014-05-07
> **applet3typod said:**
> Would this run through Wine, or is it actually ported for Linux? I've never used steam, but 90% of what I do in life is play games. Go figure, my other 10% is spent running a health group and coaching on healthy living. lol.


It is native port. I think you need to practice what you preach and spend less time on games. :)

---

### Post by monkeybrain20122 on 2014-05-07
> **applet3typod said:**
> That is exactly the kind of response I'm needing... things I wouldn't even think of, or know to ask about. Is Nautilus a pre-installed app? I'm not finding it, just wondering if it's something I need to grab from the software center.

Nautilus is the file manager, it is preinstalled. If you use other DE there are different file managers (thunar for xubuntu etc)

---

### Post by applet3typod on 2014-05-07
> **monkeybrain20122 said:**
> I think you need to practice what you preach and spend less time on games. :)

lol, quite. I guess losing 90 pounds from the couch spoiled me! I'm pretty active also though. Just not common for a gamer to be a health nut, it's quite the oxymoron. haha

---

### Post by Paulgirardin on 2014-05-07
> **applet3typod said:**
> Would this run through Wine, or is it actually ported for Linux? I've never used steam, but 90% of what I do in life is play games. Go figure, my other 10% is spent running a health group and coaching on healthy living. lol.

I'll check out all the other info y'all posted. I like the idea of making a pre-designed backup so If I have to reinstall (or when I replace this tiny HDD I just had to put in) I can have most of my installed packets and settings right back in place. I worked for Apple for years, so I'm comfortable with a Max style OS. Because of this I'm running cairo dock and I have things like spaces and expose set up. I prefer the simplicity of Windows, but the first thing I always do when I install Ubuntu is make it a bit Mac-like. 

Linux seems to run almost exclusively on ones ability to use terminal, though I see there are many new features that work around this, like the app store, etc. I'm wondering, is there a guide that will explain file structure and basic OS navigation? I know exactly where to go for any system files or app data type things on mac and windows, but on here it's all abbreviations and I can't make heads or tails of it. I'd also love to know simple things like, when I close an app, is it closed or is there a process still running, etc. I need a visual guide book, or Trusty for dummies. lol

You could be forgiven for thinking that you need to use the terminal,but it is possible to use Ubuntu without ever going near the terminal.It is just that giving terminal commands in this forum is quicker and more concise than describing how to do something via GUI.

Here's a guide to Linux file structure: [http://tuxradar.com/content/take-linux-filesystem-tour/#null](http://tuxradar.com/content/take-linux-filesystem-tour/#null)

---

### Post by dmbNCSU on 2014-05-07
> **Kurt_Alan said:**
> **[COLOR="#000000"][SIZE=5][/SIZE][/COLOR]**

Hi,

I keep this document in the cloud, a running list of quick installs and tweaks.  If I need to do a re-install, this list minimizes configuration time, particularly with command line installs.

These are my personal notes (edited). You can add or subtract.


If you mess up Upgrade Manager via CLI (dpkg), to fix broken packages:
sudo dpkg –configure -a
sudo apt-get install -f

.   .   .




This is awesome I'll definitely be using this myself

---

