---
title: "Deleted Documents Folder"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by llmunro on 2014-07-25
Hi Forum,

Somehow in the middle of setting up a new laptop and transferring files, etc., I accidentally deleted the Documents folder on the new laptop (oops!).  I made a new Documents folder in my home folder and fortunately had a backup of all of my data, so all seems to be well.  Is there anything that I need to do to the Documents folder I made so that it behaves as the Documents folder that comes with a fresh Ubuntu install?

Thanks much for helping newbies!

Best,
Lisa

---

### Post by Dennis N on 2014-07-25
The original Documents folder that was deleted is probably in the Trash, and unless you emptied the Trash is still there. The original Documents folder could have a special Documents folder icon you may want to use (mine does), and the replacement you created may not. So, you may want to delete your replacement folder, and restore the original from the Trash.

---

### Post by llmunro on 2014-07-25
Thanks!  I'll check! :)

---

### Post by sameermw on 2014-07-25
Icons are located in ```
/usr/share/icons
``` or in your home  ```
~/.icons
```

or you can edit ```
~/.config/user-dirs.dirs
``` and it's look like this unless you edit it.

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

Backup your ```
$HOME/.config/user-dirs.dirs
``` and delete the original one.
and then run "xdg-user-dirs-update" 

That's all.

And also you can reset your home folders (Documets/Download and ...) using ```
Ubuntu-Tweak
```

[ATTACH=CONFIG]255033[/ATTACH]

---

### Post by llmunro on 2014-07-25
Thanks for the suggestions!  I realized that the Documents folder wasn't showing up in Nautilus under Places.  So I followed your instructions and managed to get it back in the right place, icon and all!  Thanks also for the Ubuntu Tweak tip.  I'll be installing it shortly!

---

### Post by sameermw on 2014-07-26
**I use this ppa to install Ubuntu-Tweak in Ubuntu/Linux Mint **

```
[TABLE]
[TR]
[TD]sudo add-apt-repository ppa:tualatrix/ppa
[/TD]
[/TR]
[TR]
[TD]sudo apt-get update
[/TD]
[/TR]
[TR]
[TD]sudo apt-get install ubuntu-tweak
[/TD]
[/TR]
[/TABLE]

```

---

