---
title: "Major Ubuntu 20.04 File Folders Problem"
date: 2022-12-19
forum: New to Ubuntu
---

### Post by bhubunt on 2022-12-19
Hi All,
Today, I dragged my entire Download, Pictures and Video Folders from my laptop to an external hard drive. But in the process of doing so, something seems to have gone wrong, as the layout of my Ubuntu 20.04 window completely changed. This annoys me to no end, as I do not know how this happened nor how I can fix it to restore the old layout. Since I could not find any help on any Ubuntu forum, I am hoping someone here will have a solution. 

I'm attaching a screenshot and will describe what seems to have happened: as I dragged the three folders to the external hard drive they somehow got stuck between the "trash icon" and "other locations" as you can see in the attached screenshot. What is the status of this slot, this in-between space, btw? 

But more importantly: what do I do to get those 3 folders back in the row of folders, underneath Desktop and Documents and above Trash?

Why did this happen when I dragged them to the hard drive? I have done this dragging many times before but never had an issue like this.

Another weird thing: screenshots I take now no longer end up in the Pictures Folder, as you can see in the screenshot, but outside the Picture and any other folders.

Thanks a million for helping me out.

---

### Post by MAFoElffen on 2022-12-19
Please post the contents of file ~/.config/gtk-3.0/bookmarks, /etc/xdg/user-dirs.defaults, and ~/config/user-dirs.dirs ...

---

### Post by bhubunt on 2022-12-20
> **MAFoElffen said:**
> Please post the contents of file ~/.config/gk3/bookmarks, /etc/xdg/user-dirs.defaults, and ~/config/user-dirs.dirs ...

Hi, 
What's the best way to find the contents of these files? I just installed "locate" using the terminal but would appreciate help using the right command line to locate the contents of these files. 
Thanks.

---

### Post by tea for one on 2022-12-20
The first location, unfortunately, has a typo error (gk3 should be gtk-3.0)
However, try this via a terminal:-
```
nano .config/gtk-3.0/bookmarks
```

Use a similar instruction in the terminal to find the other two files requested.

---

### Post by Morbius1 on 2022-12-20
```
cat .config/gtk-3.0/bookmarks
```
```
cat .config/user-dirs.dirs
```
```
cat /etc/xdg/user-dirs.defaults
```

---

### Post by bhubunt on 2022-12-20
Thanks for the code lines.

Here is what I get for 
cat .config/gtk-3.0/bookmarks
file:///home/[my name]/Downloads 
Plus the same format for the 4 other file folders. These are links and when I click on them the file folder opens.



For [COLOR=#000000][FONT=&quot]cat .config/user-dirs.dirs[/FONT][/COLOR]
This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

Quick question in between: why does it say Publicshare? I do not have a server nor do I log in to a server nor do I wish to share my home folder with anyone. I just have a desktop with Ubuntu 20.04 on it. I don't code, so I have not made changes since installing Desktop Ubuntu 20.04 LTS on my Lenovo Thinkpad laptop.

cat /etc/xdg/user-dirs.defaults

# Default settings for user directories# The values are relative pathnames from the home directory and
# will be translated on a per-path-element basis into the users locale
DESKTOP=Desktop
DOWNLOAD=Downloads
TEMPLATES=Templates
PUBLICSHARE=Public
DOCUMENTS=Documents
MUSIC=Music
PICTURES=Pictures
VIDEOS=Videos
# Another alternative is:
#MUSIC=Documents/Music
#PICTURES=Documents/Pictures
#VIDEOS=Documents/Videos


That's it.

---

### Post by bhubunt on 2022-12-23
> **Morbius1 said:**
> ```
cat .config/gtk-3.0/bookmarks
```
```
cat .config/user-dirs.dirs
```
```
cat /etc/xdg/user-dirs.defaults
```

Hi  -- 
I posted the results using the code commands I got from you all, but I have a feeling the results are  not what you were looking for. Do I need to enter different command lines? 
Thanks for letting me know.

---

