---
title: "[SOLVED] Problem with grub/menu.lst"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by OldGrey on 2008-09-28
Hi

I installed Startup Manager and used it to limit the no of kernels showing in grub. That worked fine. However when, for reasons I won't bore you with, I reset the option to show all the kernels and later to limit the kernels to 1 again, the last action did not work and all the kernels remained visible. 

I completely removed Startup Manager and tried edting menu.lst directly 

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

and changed #howmany=all to #howmany=1. However all the kernels still show.

Any ideas please.

---

### Post by bobnutfield on 2008-09-28
Editing manually will not remove the kernel entries.  You must remove the ones you do not want by deleting the entries.  But you will also want to delete the kernels from your /boot directory with apt-get or from the Synaptic Package Manager.  But, BE CAREFUL WHEN EDITING MENU.LST.  If you make an error and delete the kernel entry you want to keep (or any part of it), you may render your system unbootable.  You might also consider keeping at least two kernels.  One you know is bootable satisfactory, as well as the latest.  This is just in case the latest becomes inoperaable for some reason, you will still have a bootable kernel.

---

### Post by gnuvistawouldbecool on 2008-09-28
I don't consider myself an expert on grub bot options, but I have messed around with it a reasonable amount, and would in your position comment out the ones you don't want shown with the #.  Similarly in your example the number shown line seems to be commented out, and as such doesn't actually count as existing to grub at bootup.

---

### Post by caljohnsmith on 2008-09-28
OldGrey, after you change it to "howmany=1", I believe all you need to do is run:
```
sudo update-grub
```
And it will update your menu.lst so it only has one Ubuntu entry. Or you could do like gnuvistawouldbecool recommended and just comment-out the entries manually by putting a pound sign # in front of them.

---

### Post by OldGrey on 2008-09-28
Thanks everyone for your advice

gnuvistawouldbecool - commenting out the titles worked for me.

I tried your idea caljohnsmith, but for some reason that did not seem to work, though I was given a series of options and I might have chosen the wrong one.

I also took on bobnutfield's advice and kept 2 kernels

---

