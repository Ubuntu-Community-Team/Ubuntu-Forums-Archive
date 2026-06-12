---
title: "How to add &quot;downloads&quot; folder back to menu?"
date: 2022-08-29
forum: New to Ubuntu
---

### Post by jonfisher on 2022-08-29
Ubuntu 22.04 lts

How to add "downloads" folder/option back to menu (in "files" folder) ?
 
It use to be under "documents" as attached screenshot from my other computer....

---

### Post by ajgreeny on 2022-08-30
I don't use nautilus (files) as I am using Xubuntu, but I suspect you simply need to add a bookmark in files and it should show again.

---

### Post by vanadium on 2022-08-30
Open the configuration file ~/.config/user-dirs.dirs and correct the line for Downloads to read 'XDG_DOWNLOAD_DIR="$HOME/Downloads"'

(Correction: .config rather than config. Thanks to Impavidus for pointing this out)

---

### Post by Impavidus on 2022-08-30
That must be the file ~/.config/user-dirs.dirs. Mind the dot in .config; it's a [s]file[/s] directory normally hidden by the tools.

---

### Post by jonfisher on 2022-09-01
ok guys.  I'm in need of a little help to locate/open the file "~/.config/user-dirs.dir"

---

### Post by Impavidus on 2022-09-01
When opening it in a GUI program, you may have to show hidden files before you can navigate there. Otherwise, there's the terminal:```
nano ~/.config/user-dirs.dirs
```
I use nano here because that's installed on every variant of Ubuntu; you may use another text editor if you prefer.

---

### Post by deadflowr on 2022-09-01
Check the file name.

---

### Post by ajgreeny on 2022-09-01
It's **user-dirs.dirs** which may be why you couldn't find it.

Use Ctrl+H to see hidden files and folders in your file manager.

---

### Post by jonfisher on 2022-09-01
I have "show hidden files./directories on

ok, let's try you guys showing me this way to navigate to the directory

from the files folder, i click "other locations", then i CLICKed "computer", then I clicked, "usr" folder

in other words

other locations>computer>usr

I know I'm going to the wrong place, but if you could type to me in that manner how to navigate to the proper location (using the gui), then I'm sure I can get to the right place to locate this file (please)

---

### Post by Impavidus on 2022-09-02
It's in your home directory. In the GUI, go to home, show hidden files, go to .config, look for user-dirs.dirs.

~ and $HOME are both short for your home directory.

---

### Post by ActionParsnip on 2022-09-02
Don't you just drag it over?

---

### Post by ajgreeny on 2022-09-03
> **ActionParsnip said:**
> Don't you just drag it over?
No idea with nautilus (files) but that is what I do in thunar, Xubuntu being my choice of the DE versions.
This is the same in many ways as simply adding to bookmarks, as I said in post #2.

---

### Post by jonfisher on 2022-09-21
> **Impavidus said:**
> It's in your home directory. In the GUI, go to home, show hidden files, go to .config, look for user-dirs.dirs.

~ and $HOME are both short for your home directory.

ok thanks you

So, should I change line #9 to read "'XDG_DOWNLOAD_DIR="$HOME/Downloads"'

[then save]


Tried to screenshot it, but basically looks like below and of course I'm referring to changing line #9

#1 This file is written by xdg-user-dirs-update
#2 If you want to change or add directories, just edit the line you're
#3 interested in. All local changes will be retained on the next run.
#4 Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
#5 homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
#6 absolute path. No other format is supported.
# 7
8XDG_DESKTOP_DIR="$HOME/Desktop"
9XDG_DOWNLOAD_DIR="$HOME/"
10XDG_TEMPLATES_DIR="$HOME/"
11XDG_PUBLICSHARE_DIR="$HOME/"
12XDG_DOCUMENTS_DIR="$HOME/Documents"
13XDG_MUSIC_DIR="$HOME/Music"
14XDG_PICTURES_DIR="$HOME/Pictures"
15XDG_VIDEOS_DIR="$HOME/Videos"

---

### Post by Impavidus on 2022-09-22
> **jonfisher said:**
> 
So, should I change line #9 to read "'XDG_DOWNLOAD_DIR="$HOME/Downloads"'


Yes.

BTW, make sure the directory actually exists.

---

### Post by jonfisher on 2022-09-22
ok, I did it, but no success yet.  I assume the directory is there, as it can be seen on the right here.

---

### Post by jonfisher on 2022-09-22
Also, here's another screenshot

---

### Post by jonfisher on 2022-09-24
Upon reboot, it works!

Thanks everyone for your help!  Marking this thread as solved...

---

