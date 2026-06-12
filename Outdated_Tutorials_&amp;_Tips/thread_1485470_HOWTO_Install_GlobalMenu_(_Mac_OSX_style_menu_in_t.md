---
title: "HOWTO: Install GlobalMenu ( Mac OSX style menu in top panel) and change text colour"
date: 2010-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by formaldehyde_spoon on 2010-05-16
This thread is **not** for support on GlobalMenu, or a place to offer ideas/complaints/whatever.  
Do all that stuff in this thread: [http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868) 

This little howto just tells you how to install and change the text colour of GlobalMenu, without searching through almost 3000 posts in the other thread ;).

 Global Menu is the menu style you see in OSX.  
The menu bar is always at the top of the screen, instead of being attached to each window.
It saves space and makes it easier to quickly hit the menu with your mouse.

**_1.) Install from the repositories:_**
```
 sudo add-apt-repository ppa:globalmenu-team/ppa
sudo apt-get update
sudo apt-get install gnome-globalmenu

```**_2.) Put it on a panel:_**
 - right click on a panel, select Add To Panel
 - choose Global Menu Applet from the list
 - logout, and back in again


**_3.) Change the text colour:_** 
GlobalMenu's text is determined by your desktop theme. If you want to change it do the following:
 - add this code to ~/.gtk-2.0 
(note: ''~'' is your home directory, and to be able to see .gtk-2.0 there you'll need to press ctrl-h or select View -> Show Hidden Files)
```
  style "menu_item"
 {
   fg[NORMAL] = "#000000"
 }
widget_class "**"				style "menu_item"
  style "menubar"
 {
   fg[NORMAL] = "#FFFFFF"
 }
widget_class "**" 				style "menubar"

``` #FFFFFF is white, and is the colour that will be used for ''File Edit View...''
#000000 is black, and is what will be used in the drop down menus, eg. ''New Open Close Save...''

Change the colours to whatever you want.  Just use 6 characters, where each character is one of ''0123456789ABCDEF''
The first pair of characters is for red, the second for green, and the third for blue.

Note: this will also change the menu clour in Firefox (which is not compatible with GlobalMenu) so you may want to change your firefox theme to suit (Tools -> Addons -> Themes in Firefox) 

Thanks to Ayoli [http://ubuntuforums.org/member.php?u=122327](http://ubuntuforums.org/member.php?u=122327)
for showing me how to do this :D
If anyone finds this helpful please thank him, not me.

---

