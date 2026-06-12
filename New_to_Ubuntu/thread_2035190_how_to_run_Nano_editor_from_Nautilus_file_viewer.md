---
title: "how to run Nano editor from Nautilus file viewer"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by ronewolf on 2012-07-30
Well, the 'standard' Ubuntu text editor gEdit has a [bug]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1021720") that prevents it from opening some (many?) files and, IMHO, gEdit has gotten too complex for its own good anyway. However, there is a simple terminal-based editor, Nano, that is part of the Ubuntu distribution that seems to be a good alternative for simple file viewing and editing. However starting a terminal session and then launching Nano, remembering to use the preferred options, is a pain, so I wrote a simple shell script to launch Nano on files selected in the Nautilus file viewer and thought to share it with y'all.

To 'install' this script, use gEdit (or whatever you like) to put the script below in your scripts folder (usually .gnome2/nautilus-scripts/ in your home directory), and call it nanoEdit (or whatever you like really). Then give the file execute permission (easily done by right-clicking the file, selecting properities, permission tab, checking allow execute). 

Now when right clicking selected files, a scripts option should be visible, select the nanoEdit script. A terminal session will come up with the selected file opened for editing in Nano. If you selected more than one file, then the next file will be available for editing when the 1st terminal session is closed, etc.

```
#
# run the simple editor Nano on files selected in Nautilus
# use backup (-B), smooth scrolling (-S), enable mouse (-m),
# and don't add line feeds for long lines (-w) options

for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
   gnome-terminal -x nano -B -S -m -w -- "$FILENAME"
done

```

---

### Post by ajgreeny on 2012-07-30
The alternative and possibly slightly simpler way is to use the "Open with" from a right-click of a .txt file, click on"Other Application" and choose "Custom command", then enter the same **gnome-terminal -x nano -B -S -m -w** command in that box without the $FILENAME variable.

A right click will then offer you the simple option to open the file in gnome-terminal -nano, though only for a txt file, whereas I assume your way will allow any file to be opened in nano.

---

