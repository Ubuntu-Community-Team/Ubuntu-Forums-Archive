---
title: "trouble creating desktop icon from dash"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by fritjov on 2012-12-22
I have ubuntu 12.04.1 and when i drag an application icon from the dash onto my desktop, the new icon is an image of a paper with a lock over it, and when clicked a window pops up and says  "The application launcher "brasero.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe."  and only gives me the option to "cancel".... when i right click the icon and go to properties, it says owned by root and does not give me any permission options, they are greyed out.  what can I do to create a desktop full of working icons?

---

### Post by searchfgold6789 on 2012-12-22
It seems that there are some people out there who are suffering from this along with you. In 10.04, there was a [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/572918") for it. It seems that one easy way of fixing this ([Comment #13]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/572918/comments/13")) is to right click the file, select "Properties", go to the Permissions tab, and check "Allow executing file as program".


If that doesn't work, you can try the suggestion in [Comment #4]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/572918/comments/4").

Here is how you would do this:

[LIST=1]
[*]Open up a Terminal.
[*]Type in ```
cd ~/Desktop
``` and press Enter.
[*]Type in ```
sudo chmod ugo+rx *.desktop
``` and press Enter, type the root password, and press Enter again.
[/LIST]

---

### Post by fritjov on 2013-01-04
[LIST=1]
[*]Sorry it took so long to reply, that did work, kind of, sometimes, its a 50 50 chance that the problem remains, or that I will get a working icon when dragging out from the dash home.
[*] Sometimes if I try dragging out the same icon 2 or 3 times, and sending failed icons to the trash, I will get one working, however even then it is still has a little padlock icon over the desktop icon.  With the permissions options all still greyed out and owner listed as "root" literally, "root".
[*]Also, I don't know if this is strange, all of the icons, working or not, have shortcut symbols.  you know, the little curvy arrow from windows...... maybe this is all because I installed through ubuntus windows installer...  I don't understand how though, when I boot the netbook The BIOS pops up asking Windows 7 or Ubuntu, I guess BIOS, the black screen with white letters, arrow up arrow down, hit enter deal.
[/LIST]

---

### Post by El Tito on 2013-01-04
I believe the curvy arrow is ok, as you are creating shortcuts in your desktop, but I can't be sure 100% as I use KDE.
The black screen with the white letters is not the BIOS, it is the grub boot loader. It lets you choose which OS you would like to boot, amongst many other options like recovery.

---

