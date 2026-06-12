---
title: "nautilus sidebar messed up"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-11-25
I am attaching a screenshot showing my nautilus sidebar. It has several documents and I can't remove any by right clicking. If I try to edit bookmarks only one documents shows on the edit list. How can I fix or wipe out sidebar and start fresh?

---

### Post by ajgreeny on 2012-11-25
You have forgotten the screenshot, and I don't understand exactly what your problem is.

EDIT:  OK, you have now added the screenshot, or for some reason it did not show a few minutes ago.

Have you got more bookmarks showing than are listed in the hidden .gtk-bookmarks file in your home?

---

### Post by cmcanulty on 2012-11-25
There is no gtk in my home and I do have hidden files shown. Look at the bottom of the screenshot where 3 Documents are I can't get rid of the extras, thanks

---

### Post by Morbius1 on 2012-11-25
Please post the output of the following command:
```
cat $HOME/.gtk-bookmarks
```If it comes back with a "file not found" kind of error what Operating System are you running?

If it's Ubuntu what version?

---

### Post by cmcanulty on 2012-11-25
Here is the results. I am running 12.04 classic I tried reinstalling nautilus and that did nothing

```
cmcanulty@HPTech:~$ cat $HOME/.gtk-bookmarks
file:///home/cmcanulty/Documents
file:///home/cmcanulty/Documents/BBC
file:///home/cmcanulty/Documents/Program%20Files/PGN%20&%20CB%20Files PGN & CB Files
file:///home/cmcanulty/Documents/New
file:///home/cmcanulty/Documents/Calibre Calibre
file:///home/cmcanulty/Documents/Ubuntu%20Fixes
file:///home/cmcanulty/Documents/PDF/Computers/Ubuntu Ubuntu
file:///home/cmcanulty/Documents/PDF/Computers/Linux Linux
file:///home/cmcanulty/Documents/iso's iso's
file:///home/cmcanulty/Documents/PDF PDF
file:///home/cmcanulty/Documents/Guitar Guitar
file:///home/cmcanulty/Documents/Linux%20Articles Linux Articles
file:///home/cmcanulty/Documents/Photos Photos
file:///home/cmcanulty/Documents/Sessions Sessions
file:///home/cmcanulty/Documents/Program%20Files
file:///home/cmcanulty/.themes
file:///home/cmcanulty/Documents/Carol's%20Library%20Files
file:///home/cmcanulty/.aMule/Incoming
x-nautilus-search://0/
cmcanulty@HPTech:~$ 
```

I was going to try purge nautilus but saw that would remove too much see below

```
cmcanulty@HPTech:~$ sudo apt-get remove --purge nautilus
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-backgrounds gnome-search-tool python-poster libgdict-common
  gnome-icon-theme-extras ttf-dustin libgdict-1.0-6 fonts-cantarell
  gnome-dictionary fonts-dustin python-nautilus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-core* nautilus* nautilus-image-manipulator* nautilus-sendto*
  nautilus-share* nautiluspatch* ubuntu-desktop*
0 upgraded, 0 newly installed, 7 to remove and 4 not upgraded.
After this operation, 3,296 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
cmcanulty@HPTech:~$
```

---

### Post by ajgreeny on 2012-11-25
I was going to suggest you removed the .gtk-bookmarks file from your home, but it is the standard, default bookmarks, ie, Documents, that seem to be showing the duplicates, not ones you have added, so I have to admit default.

It may still be worth purging nautilus and reinstalling everything along with it that it takes as well, which is not too many packages.  All the others that are removed will retain their configurations unless you purge the whole lot, so there should not be a big problem in that.

However, before doing that it may be worth trying ```
sudo dpkg-reconfigure nautilus
```

---

### Post by mc4man on 2012-11-25
If you want to start over then delete or rename ~/.gtk-bookmarks, then log out/in

If you don't want 3 "Documents" listings  in the "Computer" section then open 
~/.config/user-dirs.dirs in a text editor & return to normal, or post contents

Any other issues may be from using a non-standard install of nautilus - nautiluspatch, ect.

---

### Post by cmcanulty on 2013-01-12
that file you mentioned only lists the changes on the top folders which I can easily remove or add. It is the bottom section that has all the duplicates
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_PUBLICSHARE_DIR="$HOME/Desktop/Documents"
XDG_DOWNLOAD_DIR="$HOME/Desktop/Documents"
XDG_MUSIC_DIR="$HOME/Desktop/Documents"
XDG_VIDEOS_DIR="$HOME/Desktop/Documents"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Desktop/Documents"
XDG_PICTURES_DIR="$HOME/Documents/Photos"
```

Here is the screenshot

---

### Post by stinkeye on 2013-01-12
> **cmcanulty said:**
> that file you mentioned only lists the changes on the top folders which I can easily remove or add. It is the bottom section that has all the duplicates
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_PUBLICSHARE_DIR="$HOME/Desktop/Documents"
XDG_DOWNLOAD_DIR="$HOME/Desktop/Documents"
XDG_MUSIC_DIR="$HOME/Desktop/Documents"
XDG_VIDEOS_DIR="$HOME/Desktop/Documents"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Desktop/Documents"
XDG_PICTURES_DIR="$HOME/Documents/Photos"
```

Here is the screenshot
My contents of ~/.config/user-dirs.dirs 
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by mc4man on 2013-01-12
> **cmcanulty said:**
> that file you mentioned only lists the changes on the top folders which I can easily remove or add. It is the bottom section that has all the duplicates

No that file controls what's shown in the bottom (Computer) section.
You eliminated for whatever reason  "Documents" & as far as the other 4 built-in bookmarks replaced "Music", "Videos" & "Downloads" with /home/Desktop/Documents

Just fix as shown in prior post or delete the file & log out/in.

---

### Post by cmcanulty on 2013-01-13
That worked-I deleted the file and now the duplicate Documents are gone. However I would like to not have the bottom part videos, pictures, downloads,music at all. I tried deleting them from the file but they reappear. Is there a way to get rid of them for good as don't use them?

---

### Post by stinkeye on 2013-01-13
> **cmcanulty said:**
> That worked-I deleted the file and now the duplicate Documents are gone. However I would like to not have the bottom part videos, pictures, downloads,music at all. I tried deleting them from the file but they reappear. Is there a way to get rid of them for good as don't use them?

You need to stop /etc/xdg/user-dirs.conf from updating at login 
and overwriting your settings in ~/.config/user-dirs.dirs
Run...
```
gksudo gedit /etc/xdg/user-dirs.conf
```
and change
```
enabled=True
```
to
```
enabled=False
```


Then
```
gedit ~/.config/user-dirs.dirs
```
and comment out the folders you don't want shown.

---

### Post by cmcanulty on 2013-01-13
Hey that fixed it. This has been bothering me forever, thanks! See screenshot. They should make the bottom section the same as the top so it can be set up as needed.

---

