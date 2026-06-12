---
title: "Zenity script with gksudo"
date: 2009-05-11
forum: Programming Talk
---

### Post by hobo14 on 2009-05-11
Hi all,

I'm trying to write a very simple gui script to force mount a drive for my girlfriend when she forgets to unmount a flash drive.

Something like this:

zenity --info --text="Mounting sdb1 to /media/tempdisc"
gksudo mount /dev/sdb1 /media/tempdisc -o force
if mountResult == "" zenity("mounted successfully")
else zenity(mountResult)

(haven't looked up how to do proper script for the if statement yet)

I'm having some problems with the first two lines:

- zenity windows always appear minimized in the panel, how do I get them to  appear unminimized on the desktop?

-the gksudo line won't run; gksudo thinks the -o option is for it, and it doesn't like it


Can anyone give me some tips?

---

### Post by hobo14 on 2009-05-11
Really? No-one? Am I in the wrong forum?

---

### Post by hobo14 on 2009-05-11
Deleted by hobo14.

---

### Post by kaibob on 2009-05-11
Post deleted by Kaibob

---

### Post by hobo14 on 2009-05-12
Bump.

Anyone? Help, please?

---

