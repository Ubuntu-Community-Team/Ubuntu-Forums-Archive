---
title: "How do I make MPlayer my default DVD player?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by crjackson on 2008-06-28
How do I make MPlayer movie player my default DVD player?  It doesn't appear in the nautilus media options.  Totem and xine are the only things there.

In it's preferences I have to change /dev/dvd to /media/cdrom0  is that normal?  Otherwise it won't open up a dvd movie.

---

### Post by silkstone on 2008-06-28
I believe that you have to do this, although please backup the file first in case it doesn't work!

gksudo gedit /etc/gnome/defaults.list

Look for entries starting with **x-content/video**, and change **totem.desktop** to **mplayer.desktop**.

Then, go to Places > Computer > Edit > Preferences > Media > DVD Video and make sure mplayer is selected.

I know that works for making vlc the default player (changing to vlc.desktop) but I haven't tried it for mplayer.

---

### Post by crjackson on 2008-06-28
> **silkstone said:**
> I believe that you have to do this, although please backup the file first in case it doesn't work!

gksudo gedit /etc/gnome/defaults.list

Look for entries starting with **x-content/video**, and change **totem.desktop** to **mplayer.desktop**.

Then, go to Places > Computer > Edit > Preferences > Media > DVD Video and make sure mplayer is selected.

I know that works for making vlc the default player (changing to vlc.desktop) but I haven't tried it for mplayer.

Thanks.  That actually made it launch mplayer but it gets an error and refuses to play the DVD's.  Changing it back allows the program to play movies but it won't launch automatically.

Thanks again.

---

### Post by mc4man on 2008-06-28
> How do I make MPlayer movie player my default DVD player Mplayer (gmplayer) is not suited to being run from as autoplay for dvds. There is a chance smplayer could be set up as a default (autorun) player in hardy. It would require some experimentation which could lead to a borked install. The first issue is the launcher command (default %f). Based on testing in gutsy, for autoplay to succeed it would need to be %m. This also resolves the problem of smplayer being tied to one device if you have 2 drives. The downside is it will take 12-15 sec. for smplayer to locate and start playback of the disk after opening. It would be nice if the default dvd device was dynamically changed based on last device to call it but i don't think it would help with the delay.

 In hardy the only way to change the autoplay launch command is to edit it from the apps menu (from what I see).. You would need to see if this affects smplayer adversely in other areas. (other than the 12 sec. delay opening dvds)(at least on my system)
If running smplayer from %m is acceptable then you may try adding it in defaults.list and see what happens. (smplayer.desktop must be in /usr/share/applications) 
 Note that editing the same line multiple times in defaults.list can cause some unintended consquences which may or may not be fixed by editing in mimeapps.lists.(which may cause other problems)

I may set up a fresh install on a tester next week to see  about the delay, if that can't be resolved the whole thing is a moot point. (or just leave comm. at %f in which case smplayer will open but you'll need to click play - good for the device set in preferences only)
> 
I have to change /dev/dvd to /media/cdrom0 is that normal
It doesn't really matter as long as it's a mountpoint or symlink associated with the device. Odds are your drive is /dev/dvd1
If you only have 1 drive or have two and want to switch that drive to /dev/dvd , ect. that's easily done

---

### Post by crjackson on 2008-06-29
> **mc4man said:**
> 
It doesn't really matter as long as it's a mountpoint or symlink associated with the device. Odds are your drive is /dev/dvd1
If you only have 1 drive or have two and want to switch that drive to /dev/dvd , ect. that's easily done

I don't know exactly what a symlink is, but changing the line to /dev/dvd1 works fine.

---

### Post by mc4man on 2008-06-29
basically your dvd drive is given several links to the device. Some apps default to a dev link to access the device. For instance mplayer defaults to /dev/dvd. When you only have 1 dvd drive it usually gets links of /dev/dvd, /dev/cdrom, /dev/cdrw ect. linking to the device scd0 which mounts at /media/cdrom0. 
In a couple of scenarios while your drive is scd0 mounting at /media/cdrom0 it gets links that are 1 up (/dev/dvd1, ect.)(even some times with 2 drives)
It can either be adjusted back to /dev/dvd, ect. or left as is - making changes in your apps as needed like you did for mplayer.
running
```
sudo lshw -C disk
``` will show you some of the logical names (links) of your drive

---

