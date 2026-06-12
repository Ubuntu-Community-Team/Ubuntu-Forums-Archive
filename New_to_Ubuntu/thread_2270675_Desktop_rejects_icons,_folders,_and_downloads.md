---
title: "Desktop rejects icons, folders, and downloads"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by Olecoot68 on 2015-03-24
Greetings Forum,
Desire to learn Lubuntu but can't get out of the gate.  The Desktop has no icons or apps. to select.  When I try to drag folders to Desktop, they will not stay there.
I can open folders but can't activate them.  I can access internet but can't save anything to desk.  I have scanned Forum for similar thread but found only a migraine.  I was able to complete the, "first ten things to do after installing Lubuntu" and would like to continue with Linux so I can forget that other OS for good.
Any help would be appreciated as long as we take small steps to begin with.

---

### Post by Rex Bouwense on 2015-03-24
Hello Olecoot68.  Frustrated?  Well we are here to help.  First what does your desktop look like?  A standard install should have nothing on the desktop and what is called the LXPanel on the bottom.  In the bottom left hand corner of your screen on the panel there should be a blue square with a white circle in the middle of it.  Inside of the circle is a bird.  I know but that is what it is supposed to be.  That is your main menu.  When you click it the menu displays.  Each item on the menu has a sub-menu where the application shortcuts reside.  A left click will of course open the application and a right click will enable you to add a shortcut to the desktop if you choose Add to Desktop.
Now if you look at the LXPanel you will see a few icons (quick launch icons) and a couple of gey boxes.  Those grey boxes are different workspaces.  The default install comes with two.  You can adjust that to any number of workspaces that you want.  You can change things by using the applications Customize Look and Feel, Desktop Preferences, and Openbox Configuration Manager.  All three are under Preferences.  That should get you started.

By the way the first ten things to do after installing Lubuntu is merely someone's opinion.  You may not need or want to do them.

---

### Post by Olecoot68 on 2015-03-24
Thanks Rex,
My Desktop is the Lubuntu default when booted up with the request for login.  I have changed wallpapers a couple times so can change desktop properties.  When I right click I do not get an option for new folders.  When I went to the menu I was able to left click and select sub-menus but when I tried to place them on the desktop, nothing happened.  Nothing is seen on either of 2 workspaces, not even the trashcan.  I believe I had that at first but not now. If I am in an open box session how do I change when I do not have the menu in top right corner?  Folders in the file manager do not execute with one, two clicks but open with right click.  Hope this is not too comfusing.

---

### Post by CantankRus on 2015-03-25
Sounds like you're in the openbox session where no panel is started by default.
At the login screen, click on the cog icon at the top right and choose the Lubuntu session then login.
This will now be the default session.

Some info for you.....
Both sessions use openbox as the window manager but in the "openbox session" you have to edit ~/.config/openbox/autostart 
to start up applications like a panel and a file manager to control the desktop.
eg my ~/.config/openbox/autostart which starts a tint2 panel, the plank dock and conky as a sysmonitor. 
```
## Openbox autostart
## ====================
## Note*: some programs, such as 'nm-applet' are run via XDG auto-start.
## Run '/usr/lib/openbox/openbox-xdg-autostart --list' to list any
## XDG autostarted programs.

## GNOME PolicyKit and Keyring -needed for admin authentication and google-chrome password saving.
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &

## Set pcmanfm to draw wallpaper
# pcmanfm --desktop &

## draw wallpaper with nitrogen
nitrogen --restore &

## start up a panel
#lxpanel &
tint2 &

## start conky
conky -p 5 -c /home/glen/conky/configs/openbox-panel.conkyrc &
#conky -p 5 -c /home/glen/conky/configs/gmail-conkyrc &

## Start up power management
#xfce4-power-manager &

## Start the Clipboard manager after 3 seconds wait
(sleep 3s && glipper) &

## start volume manager after 15 seconds
(sleep 15s && volumeicon) &

## Turn on Numlock at start-up
#numlockx on &

## Start Composite manager
#xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &
compton &

## simple dock
plank &

```
[ATTACH=CONFIG]260892[/ATTACH]


Whereas, the **Lubuntu session** autostarts the lxpanel, pcmanfm and various other applications.

When in the Lubuntu session use Desktop Preferences in the **Panel menu > preferences** to control how the desktop behaves.

---

