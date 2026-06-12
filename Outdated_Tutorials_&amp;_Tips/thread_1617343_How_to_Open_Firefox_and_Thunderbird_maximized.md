---
title: "How to: Open Firefox and Thunderbird maximized"
date: 2010-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Crusty Old Fart on 2010-11-09
[B]
Application:[/B] Two simple shell scripts are provided. One of them applies to Firefox and the other to Thunderbird. Each will open its respective application in a maximized window, regardless of the size of the application's window when it was last closed.

**Requirements:** Most likely any variant of Linux running the Gnome desktop and having the following packages installed:

[LIST]
[*]wmctrl
[*]zenity
[/LIST]
**Skill level:** Minimal. Knowing how to create a launcher to run an application will result in achieving the maximum utility from these scripts.

**Presentation:** This post contains code blocks into which the source code for the scripts has been copied, as well as the two files as attachments.

**Function:** When invoked, these scripts will abort with a warning to the user if there are active processes already running for their respective applications. Each of them end by killing their own process rather than exiting, to prevent them from hanging when run in a terminal on systems where the RandR extension has been disabled by Xinerama.

**Source code for Firefox:** (attached as a file named ffoxmax.sh)
```

#!/bin/bash

####################################################
# This script opens Firefox in a maximized window. #
# The following packages are required:             #
#   zenity                                         #
#   wmctrl                                         #
####################################################
# Written by Crusty Old Fart - 11/8/10             #
####################################################

# ====================
# Variable assignment:
# ====================
APPNAME=firefox
CAPNAME=Firefox

# =======================================================
# Terminate script if the application is already running.
# =======================================================
if [ $(ps -ef | grep -ci $APPNAME) -gt 1 ]
then
 zenity --warning --title="Script Terminated" --text="$CAPNAME is already running."
 exit 0
fi

# ======================================
# Run the application in the background.
# ======================================
$APPNAME &

# ======================================================
# Allow the application time to establish its processes.
# ======================================================
while [ $(wmctrl -l | grep -ci $APPNAME) -lt 1 ]
do 
 sleep .2s
done

# ===============================================
# Calculate the pixel area of the opening window.
# ===============================================
x1=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $5}')
y1=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $6}')
z1=$[$x1 * $y1]

# ===========================
# Toggle window maximization.
# ===========================
wmctrl -r $APPNAME -b toggle,maximized_vert,maximized_horz

# ===============================================
# Calculate the pixel area of the toggled window.
# ===============================================
x2=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $5}')
y2=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $6}')
z2=$[$x2 * $y2]

# ============================================
# Toggle the window to maximum size if needed.
# ============================================
if [ $z2 -lt $z1 ]
then
 wmctrl -r $APPNAME -b toggle,maximized_vert,maximized_horz
fi

# ====================================================================
# Force script suicide to prevent hanging on missing RandR extension
# when Xinerama is enabled to extend desktop across multiple monitors.
# ====================================================================
kill $$


```**Source code for Thunderbird:** (attached as a file named tbirdmax.sh)
```

#!/bin/bash

########################################################
# This script opens Thunderbird in a maximized window. #
# The following packages are required:                 #
#   zenity                                             #
#   wmctrl                                             #
########################################################
# Written by Crusty Old Fart - 11/8/10                 #
########################################################

# ====================
# Variable assignment:
# ====================
APPNAME=thunderbird
CAPNAME=Thunderbird

# ========================================================
# Terminate script if the application is already running.
# ========================================================
if [ $(ps -ef | grep -ci $APPNAME) -gt 1 ]
then
 zenity --warning --title="Script Terminated" --text="$CAPNAME is already running."
 exit 0
fi

# ======================================
# Run the application in the background.
# ======================================
$APPNAME &

# ======================================================
# Allow the application time to establish its processes.
# ======================================================
while [ $(wmctrl -l | grep -ci $APPNAME) -lt 1 ]
do 
 sleep .2s
done

# ===============================================
# Calculate the pixel area of the opening window.
# ===============================================
x1=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $5}')
y1=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $6}')
z1=$[$x1 * $y1]

# ===========================
# Toggle window maximization.
# ===========================
wmctrl -r $APPNAME -b toggle,maximized_vert,maximized_horz

# ===============================================
# Calculate the pixel area of the toggled window.
# ===============================================
x2=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $5}')
y2=$(wmctrl -Gl | grep -i $APPNAME | awk '{print $6}')
z2=$[$x2 * $y2]

# ============================================
# Toggle the window to maximum size if needed.
# ============================================
if [ $z2 -lt $z1 ]
then
 wmctrl -r $APPNAME -b toggle,maximized_vert,maximized_horz
fi

# ====================================================================
# Force script suicide to prevent hanging on missing RandR extension
# when Xinerama is enabled to extend desktop across multiple monitors.
# ====================================================================
kill $$


```**Reversion:** These scripts do not alter your system in any way other than taking up the storage space where they have been saved on your hard drive. To completely reverse what you may have done as a result of reading this post, all that is needed is to delete the scripts provided and remove any launchers you may have created to run them. Beyond that, if you had to install either or both wmctrl and zenity, then uninstalling what you added will remove any trace that you've ever been here.

**Modification:** Feel free to modify the code as you wish, sell it, take credit for writing it, turn it in to your teacher as extra credit, print it out and feed it to your dog -- whatever.

---

