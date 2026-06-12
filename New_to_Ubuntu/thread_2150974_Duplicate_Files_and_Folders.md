---
title: "Duplicate Files and Folders"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by nogidapogi on 2013-06-02
Hi noob here

My problem is my files and folders in Home/my_user are also in Desktop. When I delete one file in desktop that file will also deleted in my Home/my_user directory automatically, some sort of a mirroring or something. How do I remove the files and folders from Desktop without harming my original files and folders from my Home/my_user directory?

TIA ;)

---

### Post by MidnightGrey on 2013-06-03
Did you accidently rename your "Desktop" folder, "my_user" by any chance?? Otherwise i'm not sure how your files are being mirrored. can you open a terminal (Ctrl-Alt-T) and then cd into your desktop (something like $ cd ~/Desktop/) and then type "$ ls -l" and tell me what the output is.

---

### Post by steeldriver on 2013-06-03
It sounds like your XDG_DESKTOP_DIR got set to $HOME instead of $HOME/Desktop - you can check by opening a terminal and typing

```
cat ~/.config/user-dirs.dirs
```

---

### Post by slickymaster on 2013-06-03
> **nogidapogi said:**
> Hi noob here

My problem is my files and folders in Home/my_user are also in Desktop. When I delete one file in desktop that file will also deleted in my Home/my_user directory automatically, some sort of a mirroring or something. How do I remove the files and folders from Desktop without harming my original files and folders from my Home/my_user directory?

TIA ;)
Hi, nogidapogi. Welcome to the forum.

I think your issue is related to[ xdg-user-dirs]("http://www.freedesktop.org/wiki/Software/xdg-user-dirs/"), which is a tool to help manage "well known" user directories like the desktop folder and the music folder. It also handles localization (i.e. translation) of the filenames.

What you can do is to edit **/etc/xdg/user-dirs.conf** file by changing the line that reads 'enable=True' to 'enable=False' as shown below:```
# This controls the behaviour of xdg-user-dirs-update which is run on user login
# You can also have per-user config in ~/.config/user-dirs.conf, or specify
# the XDG_CONFIG_HOME and/or XDG_CONFIG_DIRS to override this

# enabled=True
enabled=False

# This sets the filename encoding to use. You can specify an explicit
# encoding, or "locale" which means the encoding of the users locale
# will be used

filename_encoding=UTF-8
```Log out and back in again to see if it made any difference.

---

### Post by nogidapogi on 2013-06-03
> **steeldriver said:**
> It sounds like your XDG_DESKTOP_DIR got set to $HOME instead of $HOME/Desktop - you can check by opening a terminal and typing

```
cat ~/.config/user-dirs.dirs
```


Here is the output:



> XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

How could I change it to Desktop?

---

### Post by nogidapogi on 2013-06-03
> **slickymaster said:**
> Hi, nogidapogi. Welcome to the forum.

I think your issue is related to[ xdg-user-dirs]("http://www.freedesktop.org/wiki/Software/xdg-user-dirs/"), which is a tool to help manage "well known" user directories like the desktop folder and the music folder. It also handles localization (i.e. translation) of the filenames.

What you can do is to edit **/etc/xdg/user-dirs.conf** file by changing the line that reads 'enable=True' to 'enable=False' as shown below:```
# This controls the behaviour of xdg-user-dirs-update which is run on user login
# You can also have per-user config in ~/.config/user-dirs.conf, or specify
# the XDG_CONFIG_HOME and/or XDG_CONFIG_DIRS to override this

# enabled=True
enabled=False

# This sets the filename encoding to use. You can specify an explicit
# encoding, or "locale" which means the encoding of the users locale
# will be used

filename_encoding=UTF-8
```Log out and back in again to see if it made any difference.

Hi slickymaster thank you for the help. I followed your instructions but still no luck, the folders and files are still in Desktop. ;)

---

### Post by VirginiaDrifter on 2013-06-04
Here is mine:

 # This file is written by xdg-user-dirs-update# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
**[COLOR=#ff0000]XDG_DESKTOP_DIR="$HOME/Desktop"[/COLOR]**
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/.Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"


And here is yours;



**[COLOR=#ff0000]*XDG_DESKTOP_DIR="$HOME/"*[/COLOR]**
[COLOR=#000000]*XDG_DOWNLOAD_DIR="$HOME/Downloads"*[/COLOR]
[COLOR=#000000]*XDG_TEMPLATES_DIR="$HOME/Templates"*[/COLOR]
[COLOR=#000000]*XDG_PUBLICSHARE_DIR="$HOME/Public"*[/COLOR]
[COLOR=#000000]*XDG_DOCUMENTS_DIR="$HOME/Documents"*[/COLOR]
[COLOR=#000000]*XDG_MUSIC_DIR="$HOME/Music"*[/COLOR]
[COLOR=#000000]*XDG_PICTURES_DIR="$HOME/Pictures"*[/COLOR]
[COLOR=#000000][I]XDG_VIDEOS_DIR="$HOME/Videos"
[/I][/COLOR]
Looks like your missing the desktop designation.

---

### Post by steeldriver on 2013-06-04
Yes just edit the file - you can either 'show hidden files' in the file manager (shortcut is Ctrl-h) and navigate to the file and double-click to open it in a text editor, or

```
gedit ~/.config/user-dirs.dirs
```

When you've corrected it, save and exit

---

### Post by slickymaster on 2013-06-04
> **nogidapogi said:**
> Hi slickymaster thank you for the help. I followed your instructions but still no luck, the folders and files are still in Desktop. ;)

Ok, rollback that file to its prior state, so to make the Enable value to true:```
# This controls the behaviour of xdg-user-dirs-update which is run on user login
# You can also have per-user config in ~/.config/user-dirs.conf, or specify
# the XDG_CONFIG_HOME and/or XDG_CONFIG_DIRS to override this
#

enabled=True

# This sets the filename encoding to use. You can specify an explicit
# encoding, or "locale" which means the encoding of the users locale
# will be used
filename_encoding=UTF-8
```
And afterwards, edit the value for XDG_DESKTOP_DIR parameter from "$HOME/" to **"$HOME/Desktop"**, in your **~/.config/user-dirs.dirs** file 
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

