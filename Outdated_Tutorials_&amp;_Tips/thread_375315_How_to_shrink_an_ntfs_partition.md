---
title: "How to shrink an ntfs partition"
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by AllBuntu on 2007-03-03
I have not seen a start-to-finish description of shrinking ntfs, so here is one

a. you need an Ubuntu desktop cd that you can boot from
b. a too big ntfs partition
c. an idea how much data is on that partition, and what size it should become
it could be good to backup using dd, partimage or ntfsclone before you start

   1. Boot from Ubuntu desktop CD
   2. Gnome > Applications > Accessories > Terminal
   3. sudo bash # get the # as the end of your prompt indicating root powers
   4. ntfsresize /dev/hda1 -s 26G # pick a value less than your final partition size, but large enough to hold your Windows data, size is bytes or suffixed by k, M, G, /dev/hda1 is the partition your are resizing. Don't live on the edge, have a GB or so of margin
   5. Gnome > System > Quit > Restart
   6. Boot Windows for automatic chkdsk # this verified disk integrity
   7. Windows restarts by itself, launch Windows then immediately restart to Ubuntu # this enables the journal
   8. Boot from Ubuntu desktop CD
   9. Gnome > Applications > Accessories > Terminal
  10. sudo bash # get the # as the end of your prompt indicating root powers
  11. fdisk -u /dev/hda # -u indicates block sizes, /dev/hda is the device where your partition resides
         1. p # note your partition's boot (* for yes or no), start (large number, typically 63), and id (small hex number, typically 7)
         2. d, 1 # delete your partition (this is the number corresponding to your partition 1 for hda1)
         3. n, p, <same start>, desired last sector # re-create partition starting at same block but slightly smaller
         4. t, 1, <same id, 7> # put back your partition identifier
         5. w # write partition table to disk and quit
  12. # now the hard disk has a different partition table than what kernel is using, so we want to reboot right away, if you stick around here, it will get weird
  13. Boot from Ubuntu desktop CD
  14. Gnome > Applications > Accessories > Terminal
  15. sudo bash # get the # as the end of your prompt indicating root powers
  16. fdisk -ul # list and verify that your partition data looks ok
  17. ntfsresize /dev/hda1 # adjust to the size of the partition
  18. Boot Windows for automatic chkdsk # this verified disk integrity
  19. Windows restarts by itself, launch Windows # this enables the journal


Very easy,

Harald Rudell

---

### Post by Mudskipper on 2009-09-28
> **AllBuntu said:**
> Very easy
 
lol!

---

