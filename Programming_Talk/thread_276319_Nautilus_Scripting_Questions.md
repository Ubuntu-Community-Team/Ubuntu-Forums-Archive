---
title: "Nautilus Scripting Questions"
date: 2006-10-12
forum: Programming Talk
---

### Post by fatsheep on 2006-10-12
I think I did a pretty bad job of explaining my problem in the last topic so I'll try again:

Nautilus scripts get passed three parameters that are of use to me: $NAUTILUS_SCRIPTS_SELECTED_URIS, $NAUTILUS_SCRIPTS_SELECTED_FILE_PATHS, and $NAUTILUS_SCRIPT_CURRENT_URI.  

The names of the variables should explain what they are but if not, I made a nautilus script that simply displays the value of these variables.  When I right click on a file named "Clear Trash" on my desktop and run the script, here are the values for these variables:

**$NAUTILUS_SCRIPTS_SELECTED_URIS** = file://home/ubuntu/Desktop/Clear%20Trash
**$NAUTILUS_SCRIPTS_SELECTED_FILE_PATHS** = /home/ubuntu/Desktop/Clear Trash
**$NAUTILUS_SCRIPT_CURRENT_URI** = file:///home/ubuntu/Desktop

Now here's the goal of my script: to execute Clear Trash with root permissions.  I've tried the "sudo $NAUTILUS_SCRIPTS_SELECTED_URIS" and "sudo NAUTILUS_SCRIPTS_SELECTED_FILE_PATHS" commands.  Neither works.  HOWEVER, I have another script with the command "gksudo gedit $
NAUTILUS_SCRIPTS_SELECTED_URIS" and it works flawlessly.  

If 

> gksudo gedit file://home/ubuntu/Desktop/Clear%20Trash

opens the file "Clear Trash" in gedit with root permissions then why does the commmand

> sudo file://home/ubuntu/Desktop/Clear%20Trash

return the error

> sudo: file://home/ubuntu/Desktop/Clear%20Trash: command not found

**???** :confused:

---

### Post by po0f on 2006-10-12
fatsheep,

Does the script have execute permission?  Obviously you can read from and write to it, but can you execute it?  Right-click on the script and check it's permissions.

---

### Post by fatsheep on 2006-10-13
Yes the file is executable.  If it were not then it wouldn't even show up in the scripts menu under nautilus.

---

