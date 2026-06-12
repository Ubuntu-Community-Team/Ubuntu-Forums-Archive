---
title: "linux mint -not as impressed as i was-videos in browser issues"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-25
Well my enthuasism has waned somewhat, although it may have been my fault I still like the look of it, but after reading about someone who couldn't play videos at atom films, well just the first bit played. I decided to try myself, and had no luck. But I was using "no script",and although I allowed scripts for atom films, I didn't notice until later that there were other media sites that also needed acess to java.
But before noticing that, i decided to edit preferances in firefox to open flash files with movie player.
Now, up to now, i had been able to open youtube videos. Now I couldn't
even open them. using sudo apt, i have been installing and uninstalling 
adobe flash player and flash player non free with no sucess. The problem is that in prefences applications shockwave fliles are configured to play with movie player. I see an option to choose other, but no mention of
flash player in particular. So maybe I just need to point shockwave towards where flashplayer is located.
Actually should there be a preferance for flv files and swf files, or are they the same thing, I only see an option for shockwave files, but not flv files. Wheras in opera, i only see one for video flv files. 
Now, i did try installing adobe flash player by downloading from
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)
when that didn't work, i opened a terminal and typed
apt remove adobe-flashplugin
anyway it's already removed, but i did it again, 
and here is terminal output+output for installing flash player non free
martin@martin-desktop ~ $ apt remove adobe-flashplugin
[sudo] password for martin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kcontrol kdebase-data kdebase-bin-kde3 kicker cryptsetup kdebase-kio-plugins
  kfind kdebase-bin localechooser-data libdbus-qt-1-1c2 kdesktop
  xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 286 not upgraded.
martin@martin-desktop ~ $ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
martin@martin-desktop ~ $ apt install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
martin@martin-desktop ~ $ apt install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done


flashplugin-nonfree is already the newest version.





The following packages were automatically installed and are no longer required:
  kdebase-data libdbus-qt-1-1c2 xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.


0 upgraded, 0 newly installed, 0 to remove and 286 not upgraded.
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 
martin@martin-desktop ~ $ 

Now, i'll have to post about that are you root question
but i removed most of the pacages i was asked to using pacage manager.
anyway time for a shutdown and reboot to see if i've made things 
better worse or the same
M

---

### Post by binbash on 2008-11-25
dude give the commands with SUDO, there is nothing wrong here except you forgot sudos.Why are you blaming Linux Mint?

---

### Post by irish66 on 2008-11-25
Well, first i thought i had made a hames of it, as mint was loading very slowly. I rebooted, and everything okay.
Well the only changes I've noticed that I now have an older version of firefox, but still asked to get latest version of of flashplayer.
I've also lost my addons, but not the addons.
i see in pacage manager that adobe flash plugin is not installed, but flashplugin non free is.
So this I'm gonna use pacage manager, and uninstall that first
okay i'll close down firefox again.

 
How do you I'm not a girl :)
Anyway i said up at the top, that it might be my fault.
As for using the sudo command, well i did use it before when installing, uninstallimg adobe flash and flashplayer non free before, when same output

Hmm, i uninstalled firefox 2 with intention of installing firefox 3. but now can't install either by way of pacage manager or sudo apt, I'm in opera now.
actually it seems i can't install anything.
okay it looks install anything
M

---

### Post by irish66 on 2008-11-25
okay, in linux mint, live cd now with intention of uninstalling and reinstalling Mint . I can watch youtube vids now, but still nothing at atom films.
okay, complete reinstallation did the trick, still can't watch anything  at atom films though
M

---

