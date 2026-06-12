---
title: "How to block the update manager (to keep GNOME 2.X)"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by Guillaumeb on 2011-10-25
hello, 

As i would like to get back to ubuntu 11.04 with GNOME 2 I was wondering how I should proceed to avoid downloading GNOME 3 thru the update manager. Once all set up, what can I desactivate to avoid the update manager to prompt me to install the newest version of GNOME ?

thanks

---

### Post by cryptotheslow on 2011-10-25
If you have already upgraded distribution from 11.04 to 11.10 I don't think there is a particularly easy way to roll back as an awful lot of components are upgraded with the GNOME 2 to 3 move.

Probably simplest to backup your personal files / settings etc. and clean install 11.04 again. Although you could ~try~ installing 11.04 over the top of 11.10 by making sure to choose the option _**not**_ to format the partition. I have a feeling that would end up with a kludgy hybrid mess though. Once back in 11.04 proper there is an option in Update Manager not to show distribution upgrades.

Before going that route you may want to have a look on these forums for threads that go into using "Gnome fallback session" on 11.10. It seems some people have had quite good success getting that to work to provide a somewhat GNOME2-ish feel on 11.10. Not tried it myself so can't really comment further.

---

### Post by cryptotheslow on 2011-10-25
Excuse the double-post - but just shamelessly plagarised this from another's thread in the "Desktop Environment" forum....

[I]Here is the info that may help you, courtesy of **bob-linux-user**, a  forum member.

[/I] 	> 

 	 	 		 			 				The Gnome that is available on Ubuntu 11.10 is I find a good  alternative to Unity and as far as I can see it looks and feels like  classic gnome. The instructions below let you use a panel, get rid of  the diabolical overlay scrollbars and put the window controls back at  top right.This is what I did:

Install ubuntu 11.10 in normal way
In a terminal type
sudo apt-get install synaptic
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0
sudo apt-get install gnome-session-fallback
sudo apt-get install gconf-editor
sudo apt-get install gnome-tweak-tool
log out and log back in gnome classic
In a terminal type
gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to
:minimize,maximize,close
Alt right click on panel at top.
-Set orientation to bottom and size to 36
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
sudo apt-get install ubuntustudio-theme
sudo apt-get install ubuntustudio-icon-theme
sudo apt-get install human-theme
sudo gnome-tweak-tool
Set Theme:Icon theme to Ubuntu Studio
Set GTK+ theme to Raleigh
Set window theme to human 			 		


I cannot attest to it's veracity! But best of luck!

---

