---
title: "Howto: Optimize Xfce applications menu"
date: 2007-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by kahrn on 2007-09-04
**This script is a script which can optimize the application menu in Freedesktop.org compliant desktops (Tested in Gnome, XFCE and KDE)** - Read the rest of the post to learn more.

**How it works**
If you trawl around “/usr/share/applications/” and take a look at some of those files, you will notice that some of them have a lot of locale data which you probably do not need. It is possible to remove that locale data, and thus save a very small amount of hard disk space. I decided to write a script which can open each shortcut in a directory, and then remove all the locale data from each file in that directory. The end result is, on a standard Xubuntu system I can save almost 200kb of filespace just from removing the locale data from those shortcuts. It is also possible that the shortcuts will load faster on old machines as they don’t have to load as much data.. although that would be almost unnoticeable at best.

**How to remove**
If you want to remove all your locale data, I created a script using python to automate the process and remove it from all files in “/usr/share/applications/”. It can also create a backup automatically if you specify. Tested with KDE, XFCE and Gnome.

**The version as of this post is 0.3 and can be found at **[kahrn.pastebin.com/f662e0502]("http://kahrn.pastebin.com/f662e0502") or [code.tdlabs.co.uk/appentry-optimize/appentry-optimize-rel-0.3.py]("http://code.tdlabs.co.uk/appentry-optimize/appentry-optimize-rel-0.3.py")

**Rename it to appentry-optimize.py or something snazzy.**

**Configure locale:**
To configure the locale you need to open the script in a text editor and scroll down to the user definable variables area. By default, ordinary locale and en_GB are kept.

**Run it (WITHOUT BACKUP):**
```
sudo python appentry-optimize.py
```

**Alternatively, run it WITH backup:**
```
sudo python appentry-optimize.py -enable-backup
```

You can also configure options in the script itself to create backups or change the default directory, and to change the locale which is kept. These are all found in the user definable variables section.

**Program options**
> –enable-verbosity, -v    –    Enable verbose mode for more output.
–enable-backup, -b    –    Enable backup.
–help, -h    –    Display help.

**Feedback**
If the script has worked for you, I'd love to see how much filespace you saved and if it gave you a performance boost. If you find any bugs (which I'm sure you will) then feel free to tell me about them as I'd love to improve the script. You can find more information about the script at [http://kahrn.wordpress.com/2008/11/07/updated-appentry-optimize/]("http://kahrn.wordpress.com/2008/11/07/updated-appentry-optimize/")

---

