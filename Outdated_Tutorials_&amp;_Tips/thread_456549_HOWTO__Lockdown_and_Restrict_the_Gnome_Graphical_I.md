---
title: "HOWTO:  Lockdown and Restrict the Gnome Graphical Interface"
date: 2007-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by JetSirus on 2007-05-27
**Tested with Ubuntu 7.04 Feisty Fawn 32bit Desktop Edition**

This guide will explain how to lock down the Gnome graphical user interface and desktop to prevent non-administrators from making unauthorized changes.  

**What you will need:**
[LIST]
[*]Ubuntu with Gnome (default)
[*]Gnome Configuration Editor (standard)
[*]Preferably at least two accounts (one locked and one unrestricted)
[/LIST]
**NOTE:**  This can be done with one account, but it is recommended that you have at least two.  One account that is unrestricted (usually the main one made when installing Ubuntu) and one that is locked and restricted.  That way if anything goes wrong you can easily reboot the system and log into the unrestricted account.

**Step 1: ** Press ALT+F2 to open the run program dialog.
**Step 2:**  Type "gconf-editor" minus the quotes and click run.  This will run the Gnome Configuration Editor,
**Step 3:**  In the left pane click the arrow next to "apps".
**Step 4: ** In the sublist under "apps" click the arrow next to "panel".  You may need to scroll down to see it.
**Step 5:**  Click on "global" in the sublist under "panel".  
**Step 6:**  In the right pane there are four items of note.  
[LIST]
[*]Checking "disable_force_quit" will prevent the users ability to *forcibly* close a panel applet.
[*]Checking "disable_lock_screen" will prevent the user from display the screen saver and password protecting the screen.
[*]Checking "disable_log_out" will prevent the user from logging out of, shutting down, or restarting the computer.
[*]Checking "locked_down" will prevent the user from making any changes to the panels.
[/LIST]
**Step 7:**  In the left pane click the arrow next to "desktop".
**Step 8:**  In the sublist under "desktop" click the arrow next to "gnome".
**Step 9:**  In the sublist under "gnome" click on "lockdown".
**Step 10:**  In the right pane there are six items of note.
[LIST]
[*]Checking "disable_command_line" will restrict the users ability to access the terminal.  This also disable the "Run Program" dialog.
[*]Checking "disable_lock_screen" will prevent the user from locking the screen.
[*]Checking "disable_printing" will prevent the user from printing things to the attacted printer.
[*]Checking "disable_print_setup" will prevent access to all "Print Setup" dialogs.
[*]Checking "disable_save_to_disk" will prevent the user from saving thing to the hard drive.
[*]Checking "disable_user_switching" will prevent the user from switching to another account while the current session is active.
[/LIST]
**[COLOR="Red"]WARNING:[/COLOR] Disable the command line with caution.  You will need to reboot into another account to reopen the Gnome Configuration Editor easily. ** 

Simply reverse the following steps to undo any of the changes.

---

### Post by makan on 2007-06-05
i have tried to enable "disable_save_to_disk" for one account but it still can create any file in it's home directory... :(

how to set it correctly?

---

### Post by JetSirus on 2007-06-05
All that does is disable the "right-click" save as or save option.  It is still possible to write to the user home directory.  What you can do is change the permissions of the users home directory to read only, but that is out of the scope of this tutorial.

---

