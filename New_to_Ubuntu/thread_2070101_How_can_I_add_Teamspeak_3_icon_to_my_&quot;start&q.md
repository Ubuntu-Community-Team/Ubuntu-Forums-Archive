---
title: "How can I add Teamspeak 3 icon to my &quot;start&quot; menu"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Darkhaund on 2012-10-12
any ideas or way do do this?
I dislike to have to go to hte folder to run the program etc.

---

### Post by BrandonIngalls on 2012-10-13
Well the method I would use is as follows...

Create a new shortcut on your desktop(Copy all of this and paste it into a terminal then hit enter)
```
cat << _DONE > ~/Desktop/Teamspeak\ 3.desktop
[Desktop Entry]
Name=Help
Comment=Get help with Unity
OnlyShowIn=GNOME;Unity;
Exec=/bin/false
Icon=/usr/share/pixmaps/firefox.png
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;GTK;Core;Documentation;Utility;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=Yelp
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.4.1
MimeType=x-scheme-handler/ghelp;x-scheme-handler/help;x-scheme-handler/info;x-scheme-handler/man;
X-Ubuntu-Gettext-Domain=yelp
Name[en_US]=Teamspeak 3
_DONE
```Right click on the new launcher and click properties, Edit the logo by clicking on it and for the command box type out the full path to the application...
/home/username/TeamspeakPath/Teamspeak

Test that launcher to make sure it works by opening it, and if it does work continue with this next part...
```
 chmod 755 ~/Desktop/Teamspeak\ 3.desktop
sudo chown root: ~/Desktop/Teamspeak\ 3.desktop
sudo mv  ~/Desktop/Teamspeak\ 3.desktop /usr/share/applications/
```You should now be able to open Teamspeak through Unity.

Also as a side note I just copied the insides of the yelp shortcut -- just ignore that.

---

### Post by Darkhaund on 2012-10-22
But i have lubuntu NOT unity.. what can i do? i would apprciate help

---

### Post by Darkhaund on 2012-10-22
I have managed to make a "shortcut" of the teamspeak application
But it will NOT allow me to place it anywhere on the "apps" section nor on the desktop

this is what my file looks and it is currently in my documents folder etc

[Desktop Entry]
Type=Application
Icon=/home/darkhaund/Apps/TeamSpeak3-Client-linux_x86/tslogo.jpeg
Name=Teampeak 3
Comment=TS3 Client
Categories=Internet
Exec=/home/darkhaund/Apps/TeamSpeak3-Client-linux_x86/ts3client_linux_x86 %U
StartupNotify=true
Terminal=false

I want to place this shortcut or my TS application with the other "internet" apps such as firefox, thunderbird etc

Thanks in advance

---

### Post by Darkhaund on 2012-10-24
i need to bump this since I dont want to make a new post

i need help for the LUBUNTU interface not gnome nor unity

i would appreciate assitance

---

### Post by mike555 on 2012-10-24
You may need to install a menu editor like ; [http://lxmed.sourceforge.net/](http://lxmed.sourceforge.net/)

---

### Post by Darkhaund on 2012-10-24
Thank you for your kind reply, I will check that link once Iget home on my laptop

---

### Post by Radio3 on 2013-05-26
Not sure if this works on Ubuntu But I did make an icon on desktop for Fedora It might at least give you an idea how to do it on Ubuntu if it does not work the way I describe. Bare with me I have been using Linux for 1 day now.  To start with after unpacking the TS program to were ever you choose to do it open the folder. go to the icon labeled "ts3client_linux_x86". Right click it and go to properties.  Click the permissions tab make sure "Allow executing file as a program" is checked and close window.  Now again right click the "ts3client_linu_x86" icon and this time click "Make link". The new link should be highlighted right click it  and click "Cut".  Close the file manager window and on desktop right click anywhere empty and choose paste.  Now to make it look right, right click the link and go to properties. In properties window click the image of the icon and a new window should popup to change the icon appearance. Navigate through the left file tree to find your teamspeak folder. open it and there should be "ts3_icon.png" at the bottom of the list click it and click open. Then click in the name Box and rename it TS3 or TeamSpeak 3 how ever you like. now click close.  Now double click the Link you created and it should open TeamSpeak.   Hope this helps Good luck.

---

### Post by monkeybrain2012 on 2013-05-26
You have to make your .desktop file executable (right click, choose Properties > Permission) and then place the file in .local/share/applications. 
.local is a hidden folder in your home, open the file manager and choose view hidden files to see it. You can drag and drop the .desktop file there.

Edited: Opps, just noticed that it is an old thread.

---

