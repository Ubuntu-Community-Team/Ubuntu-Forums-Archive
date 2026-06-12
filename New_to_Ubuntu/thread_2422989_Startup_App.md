---
title: "Startup App"
date: 2019-07-16
forum: New to Ubuntu
---

### Post by billy3xs on 2019-07-16
Ok I can't get Spotify to open with Startup App. It worked before and I've gotten Firefox to start.
Spotify starts in Terminal with just typing Spotify.

Also I see I can't find the system files like an exe for Spotify. I'm new, duh, coming from Win 7. So using "Files" all I get is Home and can't figure how to navigate to /bin/ or user, etc. I was looking for the file to execute Spotify start, to enter into the Startup App command window.

billy2xs@billy2xs-W150ER:~$ spotify
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"

and Spotify starts...

thankyou for your time!
bill
 no matches in "Check if already posted"

---

### Post by dino99 on 2019-07-16
two seconds finding that howto [https://howtoubuntu.org/how-to-install-spotify-in-ubuntu](https://howtoubuntu.org/how-to-install-spotify-in-ubuntu)  :P

---

### Post by CatKiller on 2019-07-16
For future reference, if you want to know where the file is that gets run when you execute a command, you can use **which**:
```
which spotify
```

Linux doesn't use anything like .exe files. A file's type is determined by what's actually in it, not its name, and whether it is executable is determined by whether it has the executable permission for a particular user.

The filesystem is a tree that starts at /. Your home folder would be in one of the branches of that tree, at somewhere like /home/billy/.

---

### Post by billy3xs on 2019-07-16
Dino99, One minute trying the link! 
Um, I have Spotify installed and I don't see that the link answers the OP question.  &#128526;

---

### Post by billy3xs on 2019-07-16
[QUOTE=CatKiller;13873367]For future reference, if you want to know where the file is that gets run when you execute a command, you can use **which**:
```
which spotify
```

billy2xs@billy2xs-W150ER:~$ which spotify
/snap/bin/spotify

Also reloaded Spotify and Startup App in Synaptic. But no joy.

---

### Post by CatKiller on 2019-07-16
So what you've got there is a [snap](https://itsfoss.com/use-snap-packages-ubuntu-16-04/). I've never used them myself. But now you know what to put in your startup launcher.

---

### Post by again? on 2019-07-16
Another way is to copy the snap launcher to the users autostart directory @ **~/.config/autostart**
Firstly remove/disable your current entry in start up applications.

Check the snap desktop file name...
(as mentioned previously, because it's a snap application the .desktop file is in a 
different location than most other launchers which are in /usr/share/applications)
```
ls /var/lib/snapd/desktop/applications
```
eg
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls /var/lib/snapd/desktop/applications**
gnome-calculator_gnome-calculator.desktop  mimeinfo.cache
gnome-characters_gnome-characters.desktop  snap-store_snap-store.desktop
gnome-logs_gnome-logs.desktop              [COLOR="#FF0000"]spotify_spotify.desktop[/COLOR]

```

Then copy over the system snap launcher to the user autostart directory.
```
cp /var/lib/snapd/desktop/applications/[COLOR="#FF0000"]spotify_spotify.desktop[/COLOR] ~/.config/autostart/
```

Additionally you can add a startup delay by then editing the copied file...
```
gedit ~/.config/autostart/spotify_spotify.desktop
```

...and adding this line to the end....
```
X-GNOME-Autostart-Delay=15
```
Delay is in seconds...your choice how long.

Log out/in.

---

### Post by billy3xs on 2019-07-17
Thanks Guber2 it worked great! and  fun too...
I see even mahjong is Snapped.
Dang before posting this I changed the post to solved and lost my reply.
Anyway I'll file these commands for future start up editing!
thanks, Bill

---

### Post by again? on 2019-07-17
No problem....being new to linux... you can use the manual pages to lookup commands.
eg 
```
man cp
```
or online... [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
Also nice tutorial here... [https://ryanstutorials.net/linuxtutorial/](https://ryanstutorials.net/linuxtutorial/)

---

### Post by torresailyna on 2019-07-19
Hello. I am happy to read your problem was solved. Good day everyone

---

