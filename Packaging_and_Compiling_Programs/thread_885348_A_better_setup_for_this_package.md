---
title: "A better setup for this package?"
date: 2008-08-10
forum: Packaging and Compiling Programs
---

### Post by Igtenio on 2008-08-10
I'm working on a package to install a certain set of configuration files for IceWM, Thunar, and SLiM. I'm making a remix of Ubuntu, and one of the install options is a light-weight environment called RimeIce(Each install option has its' own little name :P).

Anyway, the package currently works, but I'm not sure if it's working optimally. I'm not too worried about actual speed or size on the disk; after all, it's just text files and a single background.

But I'm curious as to whether this's the best method to go about it. The major reason I ask is because of the changes to slim.conf; I can't overwrite the file directly, so I've been forced to have the postinst script backup the current file, and then create a new one in its' place. The backup is then restored in the prerm script.

When I tried just having a slim.conf file, it said it couldn't overwrite the existing one when I went to install. Hence the script solution.

Here's the current setup. If it's important, this's intended to be installed on a command-line system with the following packages; xorg, icewm, menu, slim, thunar, dillo, leafpad, gtk2-engines-murrine, xfce4-icon-theme

The directory setup is standard for .debs. I'm not listing the whole thing, frankly. :P If you need it, go ahead and tell me, but I'm certain enough that it's right to not feel that it needs to be posted.

This's the control file. I know it's not that great, but I'm working more on making it actually work at the moment then making sure all of the optional lines are filled in.

```

Package: RimeIce
Priority: optional
Section: Miscellaneous - Graphical
Maintainer: Igtenio <Snip>
Architecture: all
Version: 0.1
Pre-Depends: icewm, slim, thunar, gtk2-engines-murrine, xfce4-icon-theme
Description: The Iggybuntu defaults for RimeIce.


```

postinst;

```

#!/bin/sh

### Copy the settings to every home directory.
cp -r /etc/skel/.icewm ~/.icewm
cp -r /etc/skel/.icewm /root/.icewm
cp /etc/skel/.gtkrc-2.0 ~/.gtkrc-2.0
cp /etc/skel/.gtkrc-2.0 /root/.gtkrc-2.0

### Backup the slim.conf file
mv /etc/slim.conf /etc/slim.conf.bak

### Make new slim.conf
cat > /etc/slim.conf << "EOF"
# Path, X server and arguments (if needed)
# Note: -xauth $authfile is automatically appended
default_path        ./:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
default_xserver     /usr/X11R6/bin/X
xserver_arguments   -dpi 100 -nolisten tcp

# Commands for halt, login, etc.
halt_cmd            /sbin/shutdown -h now
reboot_cmd          /sbin/shutdown -r now
console_cmd         /usr/X11R6/bin/xterm -C -fg white -bg black +sb -T "Console login" -e /bin/sh -c "/bin/cat /etc/issue; exec /bin/login"
#suspend_cmd        /usr/sbin/suspend

# Full path to the xauth binary
xauth_path         /usr/X11R6/bin/xauth 

# Xauth file for server
authfile           /var/run/slim.auth


# Activate numlock when slim starts. Valid values: on|off
# numlock             on

# Hide the mouse cursor (note: does not work with some WMs).
# Valid values: true|false
# hidecursor          false

# This command is executed after a succesful login.
# you can place the %session and %theme variables
# to handle launching of specific commands in .xinitrc
# depending of chosen session and slim theme
#
# NOTE: if your system does not have bash you need
# to adjust the command according to your preferred shell,
# i.e. for freebsd use:
# login_cmd           exec /bin/sh - ~/.xsession %session
login_cmd           exec /bin/bash -login /etc/X11/Xsession %session

# Commands executed when starting and exiting a session.
# They can be used for registering a X11 session with
# sessreg. You can use the %user variable
#
# sessionstart_cmd	some command
# sessionstop_cmd	some command

# Start in daemon mode. Valid values: yes | no
# Note that this can overridden by the command line
# option "-d"
# daemon	yes

# Available sessions (first one is the default).
# The current chosen session name is replaced in the login_cmd
# above, so your login command can handle different sessions.
# see the xinitrc.sample file shipped with slim sources
sessions            icewm,xfce4-session,openbox,wmaker,blackbox

# Executed when pressing F11 (requires imagemagick)
screenshot_cmd      scrot /tmp/slim.png

# welcome message. Available variables: %host, %domain
welcome_msg         Welcome to %host

# shutdown / reboot messages
shutdown_msg       The system is halting...
reboot_msg         The system is rebooting...

# default user, leave blank or remove this line
# for avoid pre-loading the username.
#default_user        simone

# current theme, use comma separated list to specify a set to 
# randomly choose from
current_theme       rimeice

# Lock file
lockfile            /var/run/slim.lock

# Log file
logfile             /var/log/slim.log


EOF

```

prerm;

```

#!/bin/sh

### Remove the settings from all of the home directories
rm -r ~/.icewm
rm -r /root/.icewm
rm ~/.gtkrc-2.0
rm /root/.gtkrc-2.0

### Remove the modified slim.conf
rm /etc/slim.conf

### Restore the backup
mv /etc/slim.conf.bak /etc/slim.conf

```

---

