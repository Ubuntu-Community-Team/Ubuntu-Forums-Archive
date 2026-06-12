---
title: "Script to remove sensitive information on your computer"
date: 2007-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by bigfox on 2007-08-30
I have created a script to remove sensitive information such as caches and trash using the wipe program to securely delete the files.

the program 'wipe' must be installed in order for this script to work

```
sudo apt-get install wipe
```

So far, the script only works with gnome and firefox caches.  if anybody has any suggestions on other directories or files that should also be wiped, please comment in this thread and I will add it and post a final script in this thread.

Also, this script is geared for Ubuntu (K,X) so I don't know what it would do with other distros.

```
# Privacy cleaning script
# Requires program 'wipe' to be installed.



# Thumbnails and recently open files list
echo "Wiping Gnome thumbnails, recently used lists and Trash."
cd ~
wipe -r -f .thumbnails
wipe -r -f .recently-used
wipe -r -f .recently-used.xbel

# Trash
wipe -r -f .Trash/*

# External Trash such as on thumb drives
# uses a quick wipe so it doesn't flog flash drives as badly.
echo "Wiping Trash files on external drives."
wipe -r -f -q /media/*/.Trash*

# Search Indexes
echo "Wiping Beagle search index."
wipe -r -f .beagle

# GIMP
echo "Wiping recently used documents in any version of Gimp."
cd ~
wipe -r -f .gimp*/documents

# Firefox
echo "Wiping Mozilla history, cookies and cache."
cd ~
wipe -r -f .mozilla/firefox/*.default/Cache
cd ~
wipe -r -f .mozilla/firefox/*.default/history.dat
cd ~
wipe -r -f .mozilla/firefox/*.default/formhistory.dat
cd ~
wipe -r -f .mozilla/firefox/*.default/cookies.txt

```

Eventually, I want to make it into a script that runs on shutdown or logout or something.

---

### Post by userundefine on 2007-08-31
You might want to preface all dirs with ~ or something... running this in the wrong directory could be bad news.

---

### Post by SteveHoffmanUK on 2007-08-31
Message deleted

---

### Post by simplyw00x on 2007-09-01
Deleting your beagle cache often is a great way to fritter away CPU time...

---

