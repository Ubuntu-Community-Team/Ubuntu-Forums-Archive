---
title: "Menu bars top and bottom dissapeared...arrgh!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Pasdesignal on 2008-07-25
I have been running my first Ubuntu system for 6 months now as a 'media server' for my house.

For some reason the two window bars at the top and bottom of my desktop have suddenly dissapeared. I have no idea why, I havent installed anything new recently.

Anyhow, I have searched the forums and tried this in the terminal:

**gnome-session-remove gnome-panel **

but only get this in reponse:

**error: could not connect to the session manager**

I can't easily navigate my computer without the two menu bars, as I am still heavily dependent on the GUI.

Any suggestions appreciated.

---

### Post by RobbyemCee on 2008-07-25
Try resetting the GNOME Desktop to it's default settings.

Here's a really good tutorial on how to do that.
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

-RobbyemCee

---

### Post by SunnyRabbiera on 2008-07-25
They are called panels by the way.

---

### Post by Pasdesignal on 2008-07-25
Thank-you both for your replies.

I have followed the link and used the howto suggested. No luck yet, but am working my way through the responses at the bottom of the howto.

---

### Post by iaculallad on 2008-07-25
On your terminal (Alt+F2 -> and input "gnome-terminal" w/o quote):

```
sudo gconftool-2 --shutdwon
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

```

---

### Post by Pasdesignal on 2008-07-25
Thanks, tried it and no progress. Still no panels. Everything else seems to be fine. I run a vnc server from the ubuntu machine and a samba server and these are both running as per normal.
(except the vnc client has no panels either of course!)

---

### Post by bumanie on 2008-07-25
Try > sudo apt-get  --reinstall ubuntu-desktopthen > sudo apt-get update

---

### Post by Pasdesignal on 2008-07-25
Invalid operation ubuntu-desktop

---

### Post by Pasdesignal on 2008-07-25
Ok, I have made good progress and if anyone wants to know how I did it - I used this thread:

[http://ubuntuforums.org/showthread.php?t=649290](http://ubuntuforums.org/showthread.php?t=649290)

Then worked my way to normality from there. 

Came up with some gnome-applet problems on the way, removed gnome-applet and reinstalled it and this semmed to have worked.

---

### Post by animusFL on 2008-09-01
> **iaculallad said:**
> On your terminal (Alt+F2 -> and input "gnome-terminal" w/o quote):

```
sudo gconftool-2 --shutdwon
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

```

Thanks iaculallad! My panels mis-behaved after hooking an external
display to my laptop. Removing the panel directory and a killall
gnome-panel reset to defaults. I will write this tip down as I'm 
always using the external display to watch DVDs, videos, etc.

---

