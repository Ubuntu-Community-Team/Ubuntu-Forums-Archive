---
title: "[SOLVED] Stuffed up my system, slightly(I hope). Hardy heron"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by ceaser_salad on 2008-10-23
Hi

Last night I was trying to write an image to a dvd. The image was in .mdf format, so I went to synaptic and downloaded fuse-something. But couldnt find it once on my system(I'm guessing its command line only?). 
So the hunt continued, and I downloaded mdf2iso. that too seemed to vanish into the depths of system files.
Then I found Acetoneiso2, which seemed really nice, but would only let me use it as a root user.
I hate having to do that. If I'm the registered user of this pc, I should be able to use a program, without resorting to black magic and incantations.

Which brings me back to my call for help. Somehow, while sacrificing birds eggs, and shoving lavender into my Psu, something went wrong:-I 

The first time I typed in 'gksudo nautilus' I put an extra 'l' in by mistake. Then I typed it in correctly and nothing happened. Before when I typed that command, the root-user explorer would pop up, and I could look at what ever file were normally hidden from view, or write protected.
This time nothing:-(
So I hunted some more, and found that I could run a program as a root from the terminal. So I typed 'gksudo' and ran 'Acetoneiso2'. That worked, and I was able to convert the file to iso, and put it into media/cd rom for writing.
The trouble was, I still couldnt see home folder, file system etc as a root. So  I kept typing 'gksudo nautilus' until I started getting 'segmentation fault' errors. 
Then all of a sudden folders and files on my desktop became unreadable '...nautilus..desktop..no program to run this file...' It was late, I cant remember it all.
Then I did something even sillier, looking for help on nautilus, I found something on 'how to make hidden folders visible', ah ha I thought, now I might find that iso, and be able to write the dvd. So I type ctrl+H, and poof, all the folders on my desktop vanished! 

Now for some reason I've got the contents of my home folder on the desktop.

If any of this makes sense, please help. And If you're asking yourself, how and why? I have a cold, and I'm on a lot of medication, which reinforces my 'never back down until you succeed' mentality.

Thanks

---

### Post by philinux on 2008-10-23
Have you rebooted?

---

### Post by ceaser_salad on 2008-10-23
Yes, no difference.

---

### Post by philinux on 2008-10-23
Lets have a look what you did

```
cat /home/**yourusername**/.bash_history | tail -50
```

---

### Post by ceaser_salad on 2008-10-23
Activating blush mode: Heres the whole sad story.
 

emile@emile:~$ cat /home/emile/.bash_history | tail -50
sudo chmod 666 /dev/ttyUSB0
regedit
env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x winetricks
sh winetricks gdiplus
env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Cen
emile@emile:~$ env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
regedit
env WINEPREFIX="/home/emile/.wine" wine "C:\Garmin\Training Center.exe"
sudo gpsbabel
-w
w
r
gpsbabel -w -i garmin -f /dev/ttyS1 -o gpx -F test_wpt.gpx
gpsbabel -w -i garmin -f /dev/ttyS0 -o gpx -F test_wpt.gpx
sudo gpsbabel
gpsbabel -w -i garmin -f /dev/ttyS0 -o gpx -F test_wpt.gpx
b
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
mount Armada 2.mdf /mountpath -t iso9660 -o loop
gksudo nautilus
mount file.mdf /mountpath -t iso9660 -o loop
mount Armada 2.mdf /mountpath -t iso9660 -o loop
mount Armada 2.mdf /media/cdrom0 -t iso9660 -o loop
gksudo nautillus
gksudo nautilus
acetoneiso
gksudo nautilus
gksudo
brasero
nautilus
reboot
sudo nautilus
gksudo brasero
gksudo brasero disc burning
gksudo 
sudo cp <armada.iso> <desktop>
sudo cp armada.iso desktop
gksudo cp armada.iso desktop
sudo -s
gksudo
gksudo nautilus
emile@emile:~$

---

### Post by philinux on 2008-10-23
Well you aint done nothing bad as far as I can see.

If you can open places>home folder then edit> prefs untick show hidden files if it's ticked will set it back to default behaviour.

---

### Post by ceaser_salad on 2008-10-23
The 'show hidden folders' box wasn't ticked. So I ticked and un-ticked it, the rebooted, still nothing.
The funny thing was, that when I used that ctrl+H command, I didnt see anything extra, and the stuff on my desktop just disappeared. I'd like remove the home folder contents from the desktop, and put my old folders(wherever they are) back there. 

Could I have caused some trouble as a root, that the history didn't show?

---

### Post by philinux on 2008-10-23
Does places and your home folder look/work ok. Is nautilus working ok.

Take a screenshot of your desktop.

---

### Post by ceaser_salad on 2008-10-23
Ok, found my desktop folders. I found it while saving the screen shot. I do remember telling that acetoneiso2 program, that I wanted the iso saved in desktop. I must have made a new folder?

---

### Post by philinux on 2008-10-23
Yep your desktop is displaying your home folder contents plus the iso.

---

### Post by ceaser_salad on 2008-10-23
Another screenshot.

---

### Post by philinux on 2008-10-23
From the terminal run 
gconf-editor
and browse to /apps/nautilus/preferences/. 
There should be an option there called desktop_is_home_dir.

If it's ticked then untick it.

---

### Post by ceaser_salad on 2008-10-23
And if its unticked?

---

### Post by philinux on 2008-10-23
Then we'll have to think again. :)

---

### Post by ceaser_salad on 2008-10-23
Luddite+linux= trouble.

---

### Post by ceaser_salad on 2008-10-23
I experimented with deleting this mysterious 'desktop' folder. I cut and pasted the contents to the home folder and hit del. No problems. Then I took a screenshot, and instead of having the fake desktop folder as a save option, my user folder is there. When I try and select the true desktop, it jumps back and selects the user again:confused:

---

### Post by ceaser_salad on 2008-10-24
bump

---

### Post by ceaser_salad on 2008-10-25
help

---

### Post by ceaser_salad on 2008-10-26
bump

---

### Post by ceaser_salad on 2008-10-27
Anybody?

---

### Post by klytu on 2008-10-27
> **ceaser_salad said:**
> Anybody?

OK, I'll take a shot. Please post 3 screenshots: one of your current Desktop, one of your home folder, and one of the Desktop folder within your home folder.

---

### Post by ceaser_salad on 2008-10-27
Thanks. Here you go.

---

### Post by klytu on 2008-10-27
> **ceaser_salad said:**
> Thanks. Here you go.

OK. Try typing this in a terminal console: ```
gconf-editor
```Then navigate to apps>nautilus>preferences In the right-hand window, confirm that the box next to desktop_is_home_dir is checked. Then, uncheck it. 

Once this is completed, let me know what's on your desktop.

---

### Post by ceaser_salad on 2008-10-27
No luck, the box was unchecked.

---

### Post by dracayr on 2008-10-27
in a terminal, execute:

```
gedit ~/.config/user-dirs.dirs
```

look for this entry: XDG_DESKTOP_DIR. Change it to this:XDG_DESKTOP_DIR="$HOME/Desktop". Save, log off and login again.

dracayr

---

### Post by ceaser_salad on 2008-10-27
Yay! That did it. Thanks guys!!!
SOLVED

---

### Post by klytu on 2008-10-27
Glad you solved your issue!

---

