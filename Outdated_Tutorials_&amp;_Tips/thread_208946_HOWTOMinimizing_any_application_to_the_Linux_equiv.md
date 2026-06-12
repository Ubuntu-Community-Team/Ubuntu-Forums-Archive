---
title: "HOWTO:Minimizing any application to the Linux equivalent of the system tray."
date: 2006-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Bossieman on 2006-07-04
I will use Swiftfox as an example for this guide but any application should work in a similar way.
It works well with Gnome,  KDE,  XFCE 4*, Fluxbox* and WindowMaker*

*no drag 'n drop support .

Usally when I boot up my laptop I start Swiftfox after the boot has finished. I found a way to launch Swiftfox in the background and put an icon in the systemtray instead of the old shortcut icon in the panel. The difference is marginal, a little longer nautilus start time and the Swiftfox icon is on the right side of the taskbar instead of the left. 
So after the boot I have an icon next to the gaim/skype icons (Or whatever you have) in the systemtray and when I click the icon it works just as the gaim or skype icons in the system tray. 
When I close the Swiftfox window it will minimize back to the system tray.
Lets start:
Copy and paste the following into a teminal window.
> 
sudo gedit /etc/apt/sources.list

For Ubuntu Dapper add the following lines in the file :
> 
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

For Ubuntu Breezy add the following lines in the file :
> 
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) breezy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

Save the changes and exit gedit, then enter this command in the terminal:
> 
sudo apt-get update

Now enter this in the terminal:
> 
sudo apt-get install alltray

Now rightclick on the desktop and choose create document and choose emty file
Name the file 
> 
.startme

If you want the file to not be hidden just name it startme
Open up the file and enter the following:
> 
alltray /opt/swiftfox/swiftfox &

/opt/swiftfox/swiftfox can be something else on your system, make sure you put the right path to application you want to use.
Save the file, make it executable and move the file to some directory, I use my homedirectory. If you use KDE move the file to /home/USERNAME/.kde/Autostart
> 
cd /home/USERNAME/Desktop

> 
sudo chmod +x .startme

> 
mv .startme /home/USERNAME/


Now, if you use KDE do the following:
Go to "Session Manager" in "Control Center"; Select "Restore manually saved session" or "Start with empty session"

If you use Gnome do the following:
Go to: "System->Preferences->Sessions"
In Tab "Startup Programs" add this script to "Additional startup programs", just wright down the path to the file, should be /home/USRNAME/.startme
In Tab "Session options" disable "Automatically save changes to session"

Logout, login and it should work!
If you want to run an application that doesnt have a systemtray icon add the following to the script after "alltray applicationname"
> 
-i /path-to-icon.png &

Example that i use
> 
alltray nautilus --no-desktop -i /usr/share/pixmaps/gnome-home.png &

That puts the home folder in the systemtray and gives me a very fast way to access the homefolder.

---

