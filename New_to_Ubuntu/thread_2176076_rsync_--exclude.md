---
title: "rsync --exclude?"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by lance bermudez on 2013-09-22
How do I exclude these folder and files?

rsync -vaP --delete --exclude="/home/lance/.cache" --exclude='/home/lance/.gnome2_private' --exclude='/home/lance/.local/share/Trash' --exclude='/home/lance/.mplayer' --exclude='/home/lance/.thumbnails' --exclude='/home/lance/.VirtualBox' --exclude='/home/lance/Downloads' --exclude='/home/lance/dwhelper' --exclude='/home/lance/linux/download' --exclude='/home/lance/VirtualBox*VMs' /home/lance/ /media/lance/TOSHIBA*EXT/fedora19backup/localhome

---

### Post by Lars Noodén on 2013-09-22
First, do your practice while using the **-n** or **--dry-run** option so you see what you get before making your move.  That is especially important when using --delete.

---

### Post by oldfred on 2013-09-22
The minute it becomes more than one or two entries it is easier to use a separate file.

rsync -aurvlP --exclude-from=[COLOR=#ff0000]mybackup_excludes.lst[/COLOR] /home /mnt/backup

# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
/home/*/.wine
home/*/.macromedia

---

