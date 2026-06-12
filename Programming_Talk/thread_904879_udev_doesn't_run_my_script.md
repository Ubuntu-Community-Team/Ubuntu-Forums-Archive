---
title: "udev doesn't run my script"
date: 2008-08-29
forum: Programming Talk
---

### Post by tinwelint on 2008-08-29
Hi I'm setting up a backup script as discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=558413]("http://ubuntuforums.org/showthread.php?t=558413").

I've written a script for doing backups with rdiff-backup, and want to do it automatically every time I plug in my external HD.

Everything seems to work except the execution of my script through an udev rule. This is my setup:

/etc/udev/rules.d/59-autobackup.rules
```

KERNEL=="sdc[0-9]*", SYSFS{serial}=="10000E0009C24E5E", RUN+="/usr/local/bin/test.sh"

```

I'm using a simple script just for testing and it works well from the terminal:

/usr/local/bin/test.sh
```

#!/bin/bash

X11User=`who | grep :0\) | cut -f 1 -d ' '` 
if [ -z "$X11User" ] ; then 
    exit 
fi

export DISPLAY=":0.0"
export HOME="/home/$X11User"

sudo -u $X11User zenity --info --title "Rdiff-backup" --text "Running!"  --height 100 --width 200

```

But running the udev-daemon in verbose mode and plugging my drive in gives this:

```

[14769] node_symlink: creating symlink '/dev/disk/by-label/aj-ext' to '../../sdc1'
[14769] run_program: '/usr/local/bin/test.sh'
[14769] run_program: '/usr/local/bin/test.sh' (stderr) 'This option is not available. Please see --help for all possible usages.'
[14769] run_program: '/usr/local/bin/test.sh' returned with status 255
[14769] pass_env_to_socket: passed 877 bytes to socket '/org/freedesktop/hal/udev_event', 

```

I really don't know what causes this.

---

### Post by jinksys on 2008-08-29
Does the script work if you change this line?

```

sudo -u $X11User zenity --info --title "Rdiff-backup" --text "Running!"  --height 100 --width 200

sudo -u $X11User zenity --info --title "Rdiff-backup" --text "Running\!"  --height 100 --width 200

```

Also, does the udev process have the rights to sudo to $X11User without a password?

---

### Post by mssever on 2008-08-29
Try calling [FONT=Courier New]set -x[/FONT] near the top of the script; that way you can see where the script is failing.

---

### Post by tinwelint on 2008-08-30
Ok, setting set -x gives:

```
[9078] node_symlink: creating symlink '/dev/disk/by-label/aj-ext' to '../../sdc1'
[9078] run_program: '/usr/local/bin/test.sh'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '++ who'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '++ grep ':0)''
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '++ cut -f 1 -d ' ''
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ X11User=aj'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ '[' -z aj ']''
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ export DISPLAY=:0.0'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ DISPLAY=:0.0'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ export HOME=/home/aj'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ HOME=/home/aj'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) '+ sudo -u aj zenity --info --title Rdiff-backup --text 'Running\!' --height 100 --width 200'
[9078] run_program: '/usr/local/bin/test.sh' (stderr) 'This option is not available. Please see --help for all possible usages.'
[9078] run_program: '/usr/local/bin/test.sh' returned with status 255

```

Don't really understand what this means either. Maybe the password is needed. How should I supply it in that case?

---

### Post by lswb on 2008-08-30
udev rules run scripots with root permission, they are not running on any X session or tty.

Try removing sudo from the lines beginning with zenity, and adding this option to the end of those lines:

--display=':0'

This will open the zenity popup on the 1st X session display. I'm pretty sure there is a way to designate the "active" display, should there be more than one X session running, but I don't know offhand how to do that. Something to do with "console owner" maybe.

---

### Post by tinwelint on 2008-08-30
using:
> **lswb said:**
> 
--display=':0'


gives me:
```

[9755] run_program: '/usr/local/bin/test.sh' (stderr) '+ zenity --info --title Rdiff-backup --text 'SKriptkör\!' --height 100 --width 200 --display=:0'
[9755] run_program: '/usr/local/bin/test.sh' (stderr) 'No protocol specified'
[9755] run_program: '/usr/local/bin/test.sh' (stderr) ''
[9755] run_program: '/usr/local/bin/test.sh' (stderr) '(zenity:9758): Gtk-WARNING **: cannot open display: :0'

```

Maybe the display has som other name? Don't have time to look into that right now though.

---

### Post by lswb on 2008-08-30
The leading single quote was left out of ':0' in your line.

---

### Post by tinwelint on 2008-08-30
Actually, it wasn't.
This is my script (in full):
```

#!/bin/bash
set -x

zenity --info --title "Rdiff-backup" --text "Running!"  --height 100 --width 200 --display=':0'

```

And this is the output:

```

[11329] node_symlink: creating symlink '/dev/disk/by-label/aj-ext' to '../../sdc1'
[11329] run_program: '/usr/local/bin/test.sh'
[11329] run_program: '/usr/local/bin/test.sh' (stderr) '+ zenity --info --title Rdiff-backup --text 'Running!' --height 100 --width 200 --display=:0'
[11329] run_program: '/usr/local/bin/test.sh' (stderr) 'No protocol specified'
[11329] run_program: '/usr/local/bin/test.sh' (stderr) ''
[11329] run_program: '/usr/local/bin/test.sh' (stderr) '(zenity:11332): Gtk-WARNING **: cannot open display: :0'
[11329] run_program: '/usr/local/bin/test.sh' returned with status 1

```

Is it treating the quotes in some strange way perhaps? I've tried both single (':0'), double(":0") and no (:0) quotes, always with the same result.

I'm going trekking in the scottish mountains and won't be able to investigate this further for two weeks.
Thanks for your help so far.

---

### Post by lswb on 2008-08-30
Man, that sounds like a great vacation!

I'm looking at the line you just posted and again, the error is lack of leading quote. You posted:
```

zenity --info --title Rdiff-backup --text 'Running!' --height 100 --width 200 --display=:0'   

```
that should be --display=':0'

---

### Post by lswb on 2008-08-30
I was looking into this problem some more because I thought it would be useful for some scripts on my own system. After playing around with zenity some, it appears to me that it will not display a popup on another user's desktop, even if run by root. I don't know if this is designed into zenity itself or the underlying libraries.

However, I found a program called dnotify, available in the repositories, that can be run by a user, no udev rules required. It can run a command whenever the contents of a specified directory change in a specified manner. There are some similar programs you can find by searching for keywords like "notify" in synaptic. A command could be put in your .profile or added to Main Menu/System/Preferences/Session/Startup

Something like

dnotify -M /path/to/directory -e scriptname &

or just put the zenity command directly in the place of "scriptname" above if that will suffice. The -M option tells dnotify to run the command if any files in the directory are modified, other options are for file renaming, removal, creation, etc.

---

