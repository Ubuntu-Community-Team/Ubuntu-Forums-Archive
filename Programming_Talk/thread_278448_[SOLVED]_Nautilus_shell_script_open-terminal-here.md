---
title: "[SOLVED] Nautilus shell script: open-terminal-here"
date: 2006-10-16
forum: Programming Talk
---

### Post by bswilson on 2006-10-16
I've found the nautilus scripts installed by *Automatix* to be very helpful.  But I started missing a few functions that I felt maybe could help others.

When I was a Windows user, I used one of Microsoft's Power Toys called *'Open command prompt here'*, that could be invoked from an explorer window.  So I wrote a quick and dirty script to do the same with the Terminal from within nautilus. 

Just save this as **~/.gnome2/nautilus-scripts/open-terminal-here**, and issue a **chmod 755** command on it to make it executable.

```
#!/bin/bash
# Opens a terminal window wherever you are.
gnome-terminal --working-directory $NAUTILUS_SCRIPT_CURRENT_URI
```

---

### Post by skymt on 2006-10-16
Or, just install [nautilus-open-terminal](http://packages.ubuntu.com/dapper/gnome/nautilus-open-terminal). ;)

---

### Post by bswilson on 2006-10-16
I stand properly chastised.  :rolleyes:

---

### Post by sbfisher on 2006-10-20
Um, I'm obviously a newbie, but that would be nice since I'm faster at pointing at folders than typing them (even with the autocomplete).

So where does this option show up. <snip>

installed the open package terminal and assuming it will show up somewhere after a reboot or something.

---

### Post by utnubuk on 2010-08-24
> **sbfisher said:**
> Um, I'm obviously a newbie, but that would be nice since I'm faster at pointing at folders than typing them (even with the autocomplete).

So where does this option show up. <snip>

installed the open package terminal and assuming it will show up somewhere after a reboot or something.

I'll erect this thread from the dead, because the way dolphin does it was confusing me to see how it's done in nautilus and I had the same problem as sbfisher

After installing nautilus-open-terminal, if you right click any folder (not file) and look for "open in terminal" in the list. Voilá, a terminal with the path of the folder you clicked on will open. 

In Dolphin it's possible to visually integrate a terminal into the file manager as a split window view, apparantly this is neither possible nor planned for implementation in the future for nautilus.

But personally I can live with the offered solution in nautilus, as I chronically mistype the path or put / at wrong places.

---

### Post by tednix on 2011-02-28
I found this thread while doing research on running shell scripts under Nautilus.

Two points that need clarification:
1) Nautilus-open-terminal is available through the Ubuntu Software Center.
2) As suggested by sbfisher I could not find the open in terminal option when right clicking a folder until I had rebooted my system after installation.

---

### Post by take-kun on 2011-06-16
Instead of restarting the whole system, you may do the following from a terminal:

nautilus -q

It will also work to make the option available.

---

### Post by AbsolutIggy on 2011-06-17
I wrote something similar to what bswilson has, but simpler and has a slightly different behaviour

```

#!/bin/sh

gnome-terminal

```

The difference to nautilus-open-terminal is that this opens a terminal with the folder you are currently looking at in nautilus, not in the one you select - meaning you can click any file in a folder and run this script, you will still get a terminal in the current working directory

---

### Post by ankushdharkar on 2011-08-04
u missed out on " = "

---

### Post by ankushdharkar on 2011-08-04
I believe it should be

#!/bin/bash
# Opens a terminal window wherever you are.
gnome-terminal --working-directory = $NAUTILUS_SCRIPT_CURRENT_URI

this one works :)

---

### Post by hakermania on 2011-08-05
or  simply install [nautilus elementary]("http://www.webupd8.org/2011/03/install-nautilus-elementary-2322-in.html") :O

---

### Post by stoian on 2011-09-20
or, see here for another good version:

[http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

which basically says this:

Create file as follows using gedit text editor:

```

$ gedit "~/.gnome2/nautilus-scripts/Open Terminal Here"

```

Append shell script code:

```

#!/bin/bash
# From Chris Picton
# Replaces a Script by Martin Enlund
# Modified to work with spaces in path by Christophe Combelles
 
# This script either opens in the current directory,
# or in the selected directory
 
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi
 
gnome-terminal --working-directory="$dir"

```

Make it executable:

```
$ chmod +x "~/.gnome2/nautilus-scripts/Open Terminal Here"
```

Note that - in order for the new script to show up in the right-click menu - you might have to re-login, reboot, or:

```
sudo killall nautilus
```

---

### Post by buzink on 2011-12-30
The solution of AbsolutIggy worked best for me. It shows the behavior I expect: just opens a terminal in the current working directory, which ever file or directory (or nothing) is selected. It's also the most simple solution, requiring only one word of 'code'.


> **AbsolutIggy said:**
> I wrote something similar to what bswilson has, but simpler and has a slightly different behaviour

```

#!/bin/sh

gnome-terminal

```

The difference to nautilus-open-terminal is that this opens a terminal with the folder you are currently looking at in nautilus, not in the one you select - meaning you can click any file in a folder and run this script, you will still get a terminal in the current working directory

---

