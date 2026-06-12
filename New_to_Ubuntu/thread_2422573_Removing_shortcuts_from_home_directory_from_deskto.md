---
title: "Removing shortcuts from home directory from desktop"
date: 2019-07-10
forum: New to Ubuntu
---

### Post by engrpeterjohn on 2019-07-10
Hi, 

I am new to Ubuntu. I just notice that are several short cuts on desktop of the folders which I am using originally from home directory. If I delete them from desktop they also delete from home directory. Is there any way to clean the desktop from such duplicates ?

---

### Post by CatKiller on 2019-07-10
It sounds like you've managed to have your desktop showing the contents of your home folder rather than ~/Desktop. There's a setting for it somewhere.

---

### Post by engrpeterjohn on 2019-07-10
Yes, I am wondering how to manage the desktop icons. At the moment the duplicates/short cuts of several home directory folders are there on the desktop. How to remove them ?

---

### Post by Impavidus on 2019-07-10
They aren't duplicates or shortcuts, they are the contents of your home directory. What's in your .config/user-dirs.dirs?```
cat ~/.config/user-dirs.dirs
```It must have an entry for XDG_DESKTOP_DIR. You can change it to "$HOME/Desktop" or whatever the name of your desktop directory is, or point it to some empty directory if you don't want to use it. Or you can change the setting of your desktop to choose what's shown there, but I'm on Xubuntu, not Ubuntu, so I can't give you the details.

---

### Post by engrpeterjohn on 2019-07-10
Hi, 

I don't understand what I need to do. Kindly explain bit more and share the command to run. Thanks.

---

### Post by CatKiller on 2019-07-10
> **engrpeterjohn said:**
> Hi, 

I don't understand what I need to do. Kindly explain bit more and share the command to run. Thanks.

Impavidus has already shown the command to run.

~/.config/user-dirs.dirs is just a text file. It lists the locations you want to use for directories for a specific function, like your desktop, or where you keep pictures, and so on. The cat command simply shows the contents of a file so that you can show us if there's anything weird with it. You can just open it in your text editor of choice, if you prefer. ~ means your home folder, and files that start with . are hidden by default. Ctrl-h will show/hide hidden files. 

I don't use Gnome either, and I'm writing from my phone anyway, so I can't check, but I think Gnome Tweak Tool has an option to change the entries in that file if it's not listed in the other options.

---

### Post by TheFu on 2019-07-10
I think engrpeterjohn is looking for some GUI tool.  Linux often uses simple text files to control configurations.  The way to edit those files is by using an "editor" - Not a word processor or fancy GUI tool, but a trivial, simple, text editor.  
```
$ cat ~/.config/user-dirs.dirs
```
using that command - copy/paste into a terminal.  At the top of the file, it explains how it works.
 
As for icons and how to change them, I suspect that is a theme thing for the default icons.  I know that programs can have a .desktop file which has a line to control the icon used, but I would need to search for the .desktop file for the specific program.  Sorta like the old .pif files from Windows 3.0 days.

---

### Post by engrpeterjohn on 2019-07-12
Hi, 

How to turn on the builtin speakers in Ubuntu ? I am new to this forum. Is it possible to upload the image of "sound settings" here ?

---

### Post by engrpeterjohn on 2019-07-12
Hi, I have installed Gnome Tweak Tool. I don't think this is helpful. Kindly let me know how to solve the problem ? The task is to remove the files and folders from home directory.

---

### Post by vanadium on 2019-07-12
Focus on a single question in one thread. If you have another question, simply open a new question.

Other posters instructed you to show us the contents of the file ~/.config/user-dirs.dirs. To that aim, open a command line terminal (search "Terminal" in the menu), copy and paste the command they provided, i.e. ```
cat ~/.config/user-dirs.dirs
``` and press the enter key. That will display the contents of that text file in the terminal under the command. Copy it by selecting the text and paste that text here.

Anyway, that file should look like:
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
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

It says that the folders "Desktop", "Documents", etc, should be treated as special files. We believe that currently, the line for Desktop in your case reads like: "XDG_DESKTOP_DIR="$HOME". In that case, your Desktop folder will at the same time be your home folder. That could have happened because you deleted your "Desktop" folder.

1) Recreate a "Desktop" folder in your home folder.
2) Edit the text file ~/.config/user-dirs.dirs to correct the line for "Desktop".

To find the text file, turn "Show hidden files" on in the file manager. You can do this simply by pressing Ctrl+h. The you will also see the hidden folders in your home folder. These are folders that start with a dot. Find .config, and in config, you will see the user-dirs.dirs file. Open that file in your editor to correct it.

After the correction, your Desktop will again show only the items that are present in the "Desktop" folder in your home folder.

---

### Post by deadflowr on 2019-07-12
What version of Ubuntu please?
Different releases handle files on the desktop differently.

---

### Post by engrpeterjohn on 2019-07-15
It is resolved. Thanks. How to accept answer in this forum ?

---

### Post by vanadium on 2019-07-15
Thanks for the feedback. How is it resolved? That will help future users like you.

---

### Post by Impavidus on 2019-07-15
Click Thread Tools -> Mark as solved.

Future users may want to know how you solved it, so could you descibe?

---

