---
title: "trying to make a script that mounts drives on bootup.. not working the way I want it."
date: 2007-04-25
forum: Programming Talk
---

### Post by billdotson on 2007-04-25
Hello, I am trying to make a bash script that automatically mounts my WIndows partition, copies all my savegames and then unmounts it but I have having issues, the Windows partition won't mount if the command is in the script.  It will however mount w/ the same command if I just run it in the terminal.  Details below:

mount /dev/sda1 /media/Windows -t ntfs -o nls=utf8,umask=0222

cp -ubpR /media/Windows/Program\ Files/Activision/Rome\ -\ Total\ War/saves /media/Ext3_1/rome_saves

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Mozilla/Firefox/Profiles/iL70wrj5.default /media/Ext3_1/firefox_backup

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Thunderbird/Profiles/hln64ls5.default /media/Ext3_1/thunderbird_backup

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Opera/Opera/profile /media/Ext3_1

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/My\ Documents/My\ Games/Company\ of\ Heroes/Savegames /media/Ext3_1/coh_saves

cp -ubp -t /media/Ext3_1/swat4_campaign /media/Windows/Program\ Files/Sierra/SWAT\ 4/Content/System/Campaign.ini
cp -ubpR /media/Windows/Program\ Files/Activision/Rome\ -\ Total\ War/saves /media/Ext3_1/rome_saves
cp -ubpR /media/Windows/Documents\ and\ Settings/All\ Users/Documents/STALKER-SHOC/savedgames /media/Ext3_1/STALKER_saves

cp -ubpR /media/Windows/Documents\ and\ Settings/All\ Users/Documents/Monolith\ Productions/FEAR/Save/Profile000/SinglePlayer /media/Ext3_1/FEAR_saves
umount /media/Windows

This script is executable, it's owner and group is root:root and it is in the /bin .
When I run it as sudo Win_filebackup (the name of the script) I get this:

```

bill@bill:/$ sudo Win_filebackup
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

cp: cannot stat `/media/Windows/Program Files/Activision/Rome - Total War/saves': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/Bill/Application Data/Mozilla/Firefox/Profiles/iL70wrj5.default': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/Bill/Application Data/Thunderbird/Profiles/hln64ls5.default': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/Bill/Application Data/Opera/Opera/profile': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/Bill/My Documents/My Games/Company of Heroes/Savegames': No such file or directory
cp: cannot stat `/media/Windows/Program Files/Sierra/SWAT 4/Content/System/Campaign.ini': No such file or directory
cp: cannot stat `/media/Windows/Program Files/Activision/Rome - Total War/saves': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/All Users/Documents/STALKER-SHOC/savedgames': No such file or directory
cp: cannot stat `/media/Windows/Documents and Settings/All Users/Documents/Monolith Productions/FEAR/Save/Profile000/SinglePlayer': No such file or directory
umount: /media/Windows: not mounted

```

I know the rest of this (everything under dmesg | tail   or so  is because the partition didn't mount, but if I type 

```

mount /dev/sda1 /media/Windows -t ntfs -o nls=utf8,umask=0222

```

(the same thing in the script) in the terminal the partition mounts fine.  Does anyone understand what is going on here?

---

### Post by billdotson on 2007-04-25
I fixed it by adding a commented line between the mount command and the beginning on the cp commands.  But why did I have to do that?

---

