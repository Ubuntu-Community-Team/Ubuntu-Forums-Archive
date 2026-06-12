---
title: "home folder moved"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-09-18
Somehow my home folder got moved to the desktop and I can't seem to move it back to /home/cmcanulty even when I try it in sudo nautilus. I want to get it back where it should be.

---

### Post by Lisiano on 2011-09-18
I'm a bit lost. Did you somehow move everything in /home into /home/cmcanulty/Desktop ? Or just the contents of your /home/cmcanulty to ~/Desktop?

---

### Post by cmcanulty on 2011-09-18
I didn't move anything but suddenly my cmcanulty (myu home folder) is on the desktop and when I look in/Homne/cmcanulty it shows location is desktop. Also I can't rt click and move it or copy it these options are greyed out,to home very weird.

---

### Post by Lisiano on 2011-09-18
Could you post the output of```
ls -lha /home
``` I suspect your home folder symbolic linked to your Desktop.

---

### Post by Frogs Hair on 2011-09-18
This can happen if the home icon on the left pane of Nautilus is merged with the desktop icon . This action usually displays a question prompt asking if you are sure you want to do it . Do as Lisiano suggests .

---

### Post by cmcanulty on 2011-09-18
```
cmcanulty@HP:~$ ls -lha /home
total 40K
drwxr-xr-x   5 root      root      4.0K 2010-10-07 05:15 .
drwxrwxr-x  24 cmcanulty cmcanulty 4.0K 2011-08-02 11:53 ..
drwxr-xr-x 177 cmcanulty cmcanulty  12K 2011-09-18 09:01 cmcanulty
drwxr-xr-x   2 librarian librarian 4.0K 2011-03-06 19:11 librarian
drwx------   2 root      root       16K 2011-03-06 17:02 lost+found
cmcanulty@HP:~$ 
```

---

### Post by Lisiano on 2011-09-18
Hmm. Your home folder is not linked. Good. Do a ```
ls -lha ~/
``` and just post the line that has Desktop in it. Maybe that is symlinked to your /home

---

### Post by Krytarik on 2011-09-18
Make sure the content of your "~/.config/user-dirs.dirs" looks like this:
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
```And that the key "/apps/nautilus/preferences/desktop_is_home_dir" is disabled in "gconf-editor".

Then relogin.

Hope it works!

---

### Post by cmcanulty on 2011-09-18
```
cmcanulty@HP:~$ ~/.config/user-dirs.dirs
bash: /home/cmcanulty/.config/user-dirs.dirs: Permission denied
cmcanulty@HP:~$ 


```
and the gconfig looks correct

---

### Post by Lisiano on 2011-09-18
```
ls -lha ~/.config/user-dirs.dirs
```Should look like this
```
drwxr-xr-x 177 **cmcanulty cmcanulty**  12K 2011-09-18 09:01 cmcanulty
```If it says user-dirs.dirs is root or someone else, ```
sudo chown -R cmcanulty:cmcanulty ~/.config/user-dirs.dirs
```
then try opening it again using Gedit or nano
```
gedit ~/.config/user-dirs.dirs
```

---

### Post by cmcanulty on 2011-09-18
OK 
```
cmcanulty@HP:~$ sudo chown -R cmcanulty:cmcanulty ~/.config/user-dirs.dirs
cmcanulty@HP:~$ gedit ~/.config/user-dirs.dirs

```
and
```

XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="$HOME/"

```

---

### Post by Lisiano on 2011-09-18
> **Krytarik said:**
> ```
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

Set it up as Krytarik said.

---

### Post by cmcanulty on 2011-09-18
OK I changed it to look like yours and restarted and the home folder is still on the desktop and not a link to it properties show it is located on the desktop. I tried a screenshot of the properties but it disappears when I click the screenshot button.Another weird thing when I open the desktop folder it doesn't show up. Also when I restarted some of the changes didn't save evn though I said save.
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_MUSIC_DIR="$HOME/Music"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="$HOME/Pictures"
```

---

### Post by Krytarik on 2011-09-18
First, re-check the content of "user-dirs.dirs" and the state of the Gconf key.

Then, also make sure your "~/.gtk-bookmarks" looks like this, reg. the concerning directories (possibly you have more - and need more - entries there, if you didn't remove some directories like I did):
```
file:///home/cmcanulty/Documents Documents
file:///home/cmcanulty/Music Music
file:///home/cmcanulty/Pictures Pictures
file:///home/cmcanulty/Videos Videos
file:///home/cmcanulty/Downloads Downloads

```Another not so irrelevant fact I've noticed is that owner of the parent directory of "home", "/" - the system root directory -, is you, while "home" itself is owned by root. How come? Is this an external home directory? If so, may it be that the drive it is located on is not ready in time? Even if so, the system root directory should still be owned by root!

---

### Post by cmcanulty on 2011-09-19
Here are the commands again. No I didn't change home at all this just started 2 days ago. I had years ago deleted the downloads, videos, and some other folders as I don't use them but that never caused a problem before. I have a separate partition for home and I haven't changed any root things or any ownership of home.
```
cmcanulty@HP:~$ ~/.config/user-dirs.dirs
bash: /home/cmcanulty/.config/user-dirs.dirs: Permission denied
cmcanulty@HP:~$ ls -lha ~/.config/user-dirs.dirs
-rw------- 1 cmcanulty cmcanulty 598 2011-09-19 08:02 /home/cmcanulty/.config/user-dirs.dirs
cmcanulty@HP:~
```
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="$HOME/"
```

I also tried the below command to try and repair the ownership issues you mentioned and got this which has never happened before
```
cmcanulty@HP:~$ gksudo nautilus

(nautilus:11163): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

---

