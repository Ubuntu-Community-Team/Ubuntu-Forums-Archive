---
title: "Task bar malfunction"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by psundar on 2008-10-08
Hi,

I was trying to install a plugin for eclipse, the system got hung in between. When I restarted my windows and then the virtual machine, the following problems were faced:
1. The desktop is not fully visible, it is cut at the top. 
2. The "Applications" menu icon at the menu bar is gone
3. File explorer is open by default and I cannot move/resize (happens with all window). I can perform all operations within the window.
4. Im not seeing the windows at the task bar
5. The "show desktop" is not working

I tried restarting the machine, reinstall the vmplayer. I recently upgraded to vm player 2.5 and so tried downgrading to 2.4 too. Can anyone help?

Regards,
Pratibha

---

### Post by bumanie on 2008-10-08
Open terminal and put in code > sudo apt-get install xubuntu-desktopThis should reinstall the desktop back to how it was before.

---

### Post by scavenger2008 on 2008-10-08
1. First, rename the ~/.config directory (it's hidden) to something like .confbak . **This will nuke all your settings, so you'll need to set up things like panels and wallpapers again.**
2. Reboot.
3. If it didn't work, try to re-install (sudo apt-get remove xubuntu-desktop then sudo apt-get install xubuntu-desktop) your desktop.

Good luck! :)

Sc@venger

---

### Post by psundar on 2008-10-08
Hi,

I tried both. didnt work

Regards,
ps

---

