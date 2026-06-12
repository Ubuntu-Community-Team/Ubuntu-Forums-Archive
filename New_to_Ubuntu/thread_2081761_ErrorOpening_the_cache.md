---
title: "Error:Opening the cache"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by Ghostedmind on 2012-11-07
Recently installed ubuntu 12.4 on my laptop (which ive been having issues with to begin with. The most recentprogram installedwas the "gnome-tweak-tool" after i rebooted i recieved an error on the top right:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error: Opening the cache (E:Read error - read (5:Input/output Input/output error),E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmetdependencies"

Being newer to ubuntu i dont know the terminal commands to find the info. The only things i can get to open is the terminal and the main settings page. Nothing inside the settings page will open though.

---

### Post by Bashing-om on 2012-11-07
Ghostedmind; Hi ! Welcome to the forum .

To see what is wrong -> let's start with the terminal code:
```
sudo apt-get -f install
``` to attempt to repair broken packages. 

The use of "sudo" enables administrative authority and requires your password, will get no response to the screen when entering your password (security reasons).

If errors are generated please post them back (copy/paste ->code tag (#)[top of post].
 Possibly a corrupt data base file at fault and may take further actions to resolve.
[INDENT][INDENT]Try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Ghostedmind on 2012-11-07
Thank you for the help, but I've got it working well now. so far no more issues.

Thank you again for the help

---

### Post by Bashing-om on 2012-11-07
Ghostedmind;

Glad you got it sorted out,
please enumerate your resolution for others seeking a solution and mark this thread as "solved" to aid all.
[INDENT][INDENT]Happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

