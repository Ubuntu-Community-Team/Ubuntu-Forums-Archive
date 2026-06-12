---
title: "Script creates a mime for actionscript on gnome"
date: 2008-10-15
forum: Programming Talk
---

### Post by fatblueduck on 2008-10-15
I wrote a script for actionscript syntax highlighting and it would be great if it would save someone else some time. If you are using an editor that uses gtksourceview (mono develop, gedit, anjuta), this script will enable your editor to automatically open actionscript files and apply correct syntax highlighting to them.

The script wraps files that [Julien Castelain]("http://www.punkscum.org/blog/?p=23") created, but the script corrects the setup for Ubuntu (Julien's setup did not work with Ubuntu) and it automates the setup for Hardy Heron.

Here's the script: [add_flash_mime.sh]("http://www.bumblehead.com/arb_files/add_flash_mime.sh") download it and, from a terminal, run 'sudo bash /path/to/script/add_flash_mime.sh'. Restart your desktop and you're ready to go!

---

### Post by geirha on 2008-10-16
Messing around in /usr/share is something only the package system should do imo, so I wouldn't recommend it if you want to keep the system "clean". Rather do it in ~/.local/share for each user instead, then you won't need to use sudo either.

---

