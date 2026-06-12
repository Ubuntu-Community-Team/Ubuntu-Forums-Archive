---
title: "Where is my &quot;Program Files&quot; directory?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Rebelli0us on 2008-07-03
Firefox is prompting me to select an application to play a media file. I want to point to VLC media player as the default application, but I have no clue how Linux keeps apps. Are they all in one place? What does a Linux executable look like in the file browser? I know VLC is installed, so I did a file search for VLC.. nothing. VLC in the apps menu doesn't have "properties", I figured "launcher" is the equivalent of windoz shortcut? Help!

---

### Post by dje on 2008-07-03
point it to:
```
/usr/bin/vlc
```

hope that helps,
dje

---

### Post by Pjotr123 on 2008-07-03
Simple explanation:
[http://ubuntutip.googlepages.com/filesystem](http://ubuntutip.googlepages.com/filesystem)

---

### Post by nothingspecial on 2008-07-03
Read this - 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

About 1/2 of the way down it explains how to make vlc your default media player.

---

### Post by ibuclaw on 2008-07-03
If you are looking for an app, use the **which** or **whereis** command to search for it.

ie:
```
which vlc
```
```
whereis vlc
```
The difference between the two is that "whereis" will also search the /usr/lib and /usr/share folders for the app data folders. "which" just finds the executable.

Regards
Iain

---

