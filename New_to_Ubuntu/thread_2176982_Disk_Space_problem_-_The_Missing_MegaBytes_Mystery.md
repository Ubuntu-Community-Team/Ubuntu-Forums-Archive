---
title: "Disk Space problem - The Missing MegaBytes Mystery!"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by Crinkle on 2013-09-26
Hello there. Linux doesnt seem to be finding all my hard disk space. Whilst watching the Nvidia gfx drivers install/crawl across the empty progress bar, I decided to check, how much my installations of skype, blender (not yet working) and Nvidia took up.

To my suprise there is currently only 4.7GB free on the disk. It's a small partition, with the larger amount of the 480GB given over to its next door neighbour, the windows 7 installation. Windows 7 had reluctantly moved over and squeezed in a bit, earlier in the day, to make some room for Linux to come and inhabit. However, 25GB of space  was made for Linux, who has so little room it cant even afford to turn around!

Linux did a quick look in all its boxes and folders and files, and found, that only 3.4GB of files exist in its area, do there should be about 21.5 GB space to play in, but its not there!

Does anyone know where all that space might have gone?


Chapter 2: Non-installation
Ok so after the progress bar for nvidia drivers got to the end, the little window filled up with lots of characters and a lot of red highlighting of them, and it also told me it was corrupted. It turns out it was not installing, but opening the install file in a text editor called "gedit". Does anyone know how you are supposed to install the nvidia drivers? Someone said change the properties of the file to allow it to be run as an executable. I did this, but it still opens in the text editor (or tries to)

---

### Post by whitesmith on 2013-09-26
If you want to check available/used/free space on your various partitions, just bring up a terminal and type```
df -hT | egrep -i "file|^/"
``` This may reveal the location of the 'missing' storage. Others will have to comment on Nvidia's idiosyncrasies, of which there are several.

---

### Post by Impavidus on 2013-09-26
How did you install? Manual partitioning or did you simply select to install alongside? Is this a true dual boot or wubi? How did you make those free 25GB? Unallocated disk space of free space in a partition?

---

### Post by Crinkle on 2013-09-26
We'll all this just went horribly wrong! I used "partition magic" to split part ofthe Windows partition off to delete and make an empty bit of space for a extra Linux partition or something.

It said it had to do it on a fresh boot as the drive was in use, no problem! I thought! After reboot it got through the process quickly and restarted. Now loading from that hard disk results in:

ERROR: UNKNOWN FILESYSTEM.
GRUB RESCUE>

Looking at the drives from the CD, it appears to have done exactly what I asked, and something I didn't... It split the drive up as requested, but it turned the New partition into drive C!!!

On a scale of 0 to mumford, how f***** is my hard disk now? Is there anything I can do to try and get the partitions repaired so it all works? Or have I git to spend most of tomorrow in file recovery programs :(

---

