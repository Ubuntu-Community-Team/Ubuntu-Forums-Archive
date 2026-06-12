---
title: "Mac-Like Meditations on the Unseen"
date: 2005-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by rcaskey on 2005-04-03
Do the following as root to hide all the existing directories in Filesystem, and replace them with more Maclike entries. Very limited usefulness, but it jogs the mind a bit.

Not a recommended way to use your computer.

Sincerely,
--Rob

ls / >> /.hidden
ln -s /home /Users
mkdir /System
mkdir /System/Configuration
ln -s /etc/ /System/Configuration
ln -s /var/log /System/Logs
ln -s /var/backups /System/Backup\ Files
mkdir /Library
mkdir /Library/Fonts
mkdir /
ln -s /usr/share/fonts/truetype /Library/Fonts

What are the files that Windows hides by default?

PS:

OS 10.3 Server has the following Darwin/OS X specific files/directories in it's /.hidden file.

automount
cores
Desktop DB
Desktop DF
Desktop Folder
mach
mach_kernel
mach.sym
private
Trash
VM Storage
Volumes

My /.hidden file has the following:

boot
cdrom
dev
etc
home
initrd
initrd.img
initrd.img.old
lib
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old

---

### Post by John Nowak on 2005-04-10
This is great... should've thought of this myself. Thanks!

Perhaps I will be able to make the OSX -> Linux transition yet... ;-)

---

### Post by Archangel_X19 on 2005-04-10
So is it a looks or an option change, before I go tweaking again.  I did the prelink and hard drive speed up tweak and couldn't get back into X-session.  I love to tweak but just wondering what category this falls into?

---

