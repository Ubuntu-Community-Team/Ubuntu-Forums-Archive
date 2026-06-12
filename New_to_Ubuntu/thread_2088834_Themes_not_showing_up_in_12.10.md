---
title: "Themes not showing up in 12.10"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by greymaiden2 on 2012-11-27
I'm not an Ubuntu n00b, but I am a unity n00b, and I am really confused about how to install and change themes in unity.  I've downloaded and installed a GTK3 theme (swar-red) to both the usr/share/themes and the .themes folders, and it still isn't showing up in the appearances tab of Settings.  What gives?  I've searched these forums and haven't come up with much.  If I've missed a useful thread somewhere, please point me to it!

Also, come on ubuntu/cononical, Y U NO GIVE US NICE THEME MANAGER?
(I heard about myunity, but I also read that it's defunct for 12.10 for the time being)

---

### Post by qamelian on 2012-11-27
You need to install Gnome Tweak Tool from the Software Center. That will let you use additional themes.

---

### Post by greymaiden2 on 2012-11-27
Hrmmm.  Gnome tweak you say?  Is that similar or the same as Ubuntu Tweak?  I installed Ubuntu Tweak and it does give me access to additional themes, though I'm having some difficulty with the launcher's transparency settings, and also would still love to know why I can't install new themes so that they show up in the default Appearance pane.

---

### Post by Frogs Hair on 2012-11-27
Only the official default themes are applicable from appearance preferences which is a Gnome application.

install Downloaded Themes or icons in 11.10-12.04-12.10

Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  


Use only GTK 3.6 themes for 12.10, 3.4 for 12.04, and 3.2 themes for 11.10. Check this in the theme description at the download location. 

Download and fully extract the theme packages and hold the folders on the desktop until needed . 


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open  Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before themes are visible in Advanced Settings .

---

