---
title: "Changing login screen in Kubuntu via Command Line"
date: 2008-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by PeonDevelopments on 2008-07-23
**[SIZE="4"]This is a tutorial directed at new users for changing their login screen in kde.[/SIZE]**
*Version 1.11*

I use Kubuntu 7.10, KDE v3.5.8.
This tutorial may not work for KDE 4.0 and above.

**IMPORTANT NOTES**
If you are attempting to change your login screen via System Settings -> Advanced Tab -> Login Manager, it may not work correctly.


**Bug #1:** Entering password for Administrator Mode does nothing. 
**Solution:**
```
sudo kcontrol
```
Go to System Administration -> Login Manager

**Bug #2:** After changing login screen wallpaper, image does not appear.
**Solution:** Each Login screen wallpaper must have a .desktop file along with the image file. See below.
(Changing just the background colour does work since it does not involve an image file.)

**Change Login Screen Wallpaper Tutorial:**
I have an image called KDE.png that I want to display as background for the login screen.

[COLOR="Navy"]**Step 1:** Copy the file to the system folder. (Assuming you are in the folder with your image file)[/COLOR]
Open up a terminal window ( Konsole, XTerm, Yakuake, etc.) and type in the following code:
```
sudo cp KDE.png /usr/share/wallpapers/
```
[B]
[COLOR="navy"]Step 2:[/B] Create a .desktop file for your image. Creating this file allows kcontrol to recognize your image file and consequently load it.[/COLOR]
```
sudo kate /usr/share/wallpapers/KDE.png.desktop
```
(Yes, the filename should be your image file + ".desktop" and you will need to use sudo in order to write to the system folder)
[B]
[COLOR="navy"]Step 3:[/B] Enter in the image details. All you really need to put in it:[/COLOR]

[FONT="Courier New"][Wallpaper]
Encoding=UTF-8
File=KDE.png
Name=KDE Login Image[/FONT]

Now save the file.

[COLOR="navy"]**Step 4:** Write to the configuration file
(This step may be optional; Go to System Settings and Login Manager. You should be able to choose your login wallpaper from the list now. If you cannot edit the settings in Administrator Mode, continue to the next step.)[/COLOR]

On my machine, it's located in 
/usr/share/kubuntu-default-settings/kde-profile/default/share/config

Time to edit the file. Keep in mind that this is a system configuration file and a typo may crash your system or mess up the display. You may want to make a backup file by entering
```
cd /usr/share/kubuntu-default-settings/kde-profile/default/share/config/
```
```
sudo cp kdesktoprc kdesktoprc.bak

```

Now open up the file:

```
sudo kate /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdesktoprc
```

Change the option that looks like:

**Wallpaper= ...**

and enter in the address to your image file and save.
[B]
Wallpaper=/usr/share/wallpapers/KDE.png[/B]


Voila. You are done.
If you go back into kcontrol, you should see that not only is your file selected, but the name you gave it in the .desktop file also shows. If not, selecting it should finally work.

To change the login screen background to the original, either overwrite the file with the backup or change the Wallpaper= option. Confirm it in the Login Manager.

---

