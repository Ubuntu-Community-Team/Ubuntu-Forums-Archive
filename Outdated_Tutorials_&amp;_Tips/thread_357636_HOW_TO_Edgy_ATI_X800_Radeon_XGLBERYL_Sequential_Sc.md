---
title: "HOW TO: Edgy ATI X800 Radeon XGL/BERYL Sequential Script"
date: 2007-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Profusion on 2007-02-09
[COLOR="Black"]**[SIZE="4"]This is a sequential setup designed for anyone with an ATI Radeon Series graphics card and wants to use XGL with BERYL on a fresh EDGY install![/SIZE]**[/COLOR]

[SIZE="3"]Download the script file and follow the on screen guide.[/SIZE]

[SIZE="3"]**How does this script work?**[/SIZE]

[SIZE="3"]Since this is my first time making a linux script =), I could not completely automate the setup but is still worth the effort to use. This script will download all nessasary packages, and install your ATI driver for you. 

It will not add the nessasary lines for you, but I have executed each step to open the needed config files to be edited. Once you edit the file save and close it, it will move to the next step. 

Please let me know how it works for you, if you know how to beter this setup script please do so and show me your changes. Hope this works as well as it did for me on a fresh install of Edgy.[/SIZE]

**Shall we begin?**

Download and save the script on your Desktop.
Execute it by typing in your terminal: 

> sudo sh ./ssfuxba.sh

**Add these to lines at the bottom of your sources.list**

Step 1.
> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Step 2. 
**Unmark your universe and multi-universe repositories! **

**Save** and **close** the window.

Step 3.
**Add these lines at the bottom of your xorg.conf file:**

> Section "Extensions"
        Option  "Composite" "0"
EndSection

**Save** and **close** the window.

Step 4. 
**Add the line "fglrx" in your restricted modules.**

> DISABLED_MODULES="fglrx"

**Save** and **close** the window.

Step 5.
**Add the line in the script for XGL to load on the startup:**

> #!/bin/sh
# Start up Xgl and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start GNOME
exec gnome-session

**Save** and **close** the window.


**[SIZE="4"]Your system will now force a reboot unless you ctrl-c to stop it, come back to complete the final steps!![/SIZE]**

**Final Step!**

[SIZE="4"]Add beryl-manager in your startup:
add "**beryl-manager**" in startup programs (System -> Preferences -> Sessions).
Also, should add "**gnome-settings-daemon**" in startup programs too (following the beryl entry").

Also to stop the slow animation effect when loading your browser:

run in termial gconf-editor 

sudo gconf-editor

under apps>panel>default_setup>global>enable_animations uncheck it.[/SIZE]

Done!

Let me know how it went!

Peace!

---

### Post by themilstead on 2007-02-18
Hmm...I tried this three times with a x800 on a fresh install of Edgy. When I reboot and login, the system hangs for awhile trying to boot the desktop, until I'm thrown back to the login screen where I have no choice but to manually select Gnome as my interface. I also noticed that there were a couple of errors during the execution of the script. All I can recall at the moment is that the module-assistance package failed to install...not sure how important that is, though.

:confused: Any ideas to help me solve this? I'd really like to see your script work; it'd be a great alternative to the sometimes messy tutorials.

---

