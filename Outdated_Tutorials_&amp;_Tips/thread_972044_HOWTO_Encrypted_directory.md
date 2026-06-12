---
title: "HOWTO: Encrypted directory"
date: 2008-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lettas on 2008-11-05
Open source way to safely encrypt a directory without consuming unnecessary resources? EncFS is the way to go if you're not afraid to use console. If you are, this guide is for you.

First we need to access FUSE. If you don't have it, install it and add yourself into FUSE group. You will need zenity for the icons. Both are bundled in 8.10 and 8.04.
```

sudo apt-get install encfs
encfs ~/.encrypted ~/Protected
```

This code installs EncFS, creates an encrypted directory into your home directory and later mounts it to ~/Protected. EncFS will ask you permission to create those two directorys and the level of encryption to be used. Default is fine if no intelligence agency have interest to open your files. For password, use normal and capital letters and numbers, preferably more than eight.

```
gksudo gedit /usr/local/bin/salaus
```

Add next lines to the empty file 
[INDENT]
#!/bin/bash
while(true)
do
zenity --notification --text="Open your encrypted files by clicking here" --window-icon=/usr/share/icons/gnome/scalable/actions/gtk-open.svg
nautilus ~/Protected && gnome-terminal -x encfs ~/.encrypted ~/Protected
zenity --notification --text="Lock your encrypted files by clicking here" --window-icon=/usr/share/icons/gnome/scalable/actions/lock.svg
fusermount -u -z ~/Protected
done[/INDENT]

Lastly, to be able to run the created script:

```
sudo chmod +x /usr/local/bin/salaus
```

You may now try how it runs. Press F2 and enter
```
salaus
```

If it works the way you want, add it to System > Preference > Session > Startup programs

I have had this configuration for last 6 months, no problems occured yet. Since EncFS makes a separate encryption for all the files, physical damage to the disc isn't as fatal as in some encryption systems. Use this guide carefully and keep backup of your files. I am not held responsible for any data loss.

---

