---
title: "desktop and login screen"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by vagelism on 2011-10-25
HEllo to all!
I just made an upgrade to the new version of ubuntu 11.10 (I think).
I want my clasic old login screen and the old desktop with the programs etc on the top....!!! 
Any help?
Keep it simple please!
Thank you!

---

### Post by candtalan on 2011-10-25
It is going to be useful to know which version you are using for sure. If you were recently using 11.04 in the Classic session then I have some bad news, the Classic session is not available in 11.10 - there may be ways to get a classic look, perhaps others can help here?

You could stay with 11.04 for a while longer, it will be supported until 2012, October. Or you could use Xubuntu which has a much more classic arrangement. Or again, you could use 10.04.3 (LTS) which will be supported until 2013 April. 10.04.3 has the classic arrangement anyway.

---

### Post by cryptotheslow on 2011-10-25
Please do verify that you have actually upgraded to 11.10 as candtalan suggests.

You can verify by opening a Terminal window and entering:

```
cat /etc/lsb-release
```


If you are on 11.10 then other users have had some success getting that GNOME2 look and feel back by using gnome-session-fallback


Shamelessy plagarised from another's (ajgreeny) post:

*Here is the info that may help you, courtesy of **bob-linux-user**, a  forum member.  I have used these recommendations on my test  installation of 11.10, but changed a few of the theme choices, and it is  as near as I can get to the old classic-gnome desktop.*

 	> 

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

Thanks to ajgreeny and bob-linux-user.

I've not tried the above myself but it is reported as mostly successful.

Good luck!

---

