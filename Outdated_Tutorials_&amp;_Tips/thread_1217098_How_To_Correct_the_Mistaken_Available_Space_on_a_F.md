---
title: "How To: Correct the Mistaken Available Space on a Flash Drive"
date: 2009-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-07-19
Hello, everyone. :-)  [COLOR="Red"][B]This tutorial is for GNOME.  Easy to translate for other DEs/WNs, however.
[/B][/COLOR]
**For a long time, after deleting a large amount of data from a flash drive or MP3 player, I would see something like the attached image.**

[B]
Where I have an 8.0 GB Flash drive with no files, but also no space.[/B]  

The simple "#-o" solutions are as follows:
1. [COLOR="Red"]Ctrl+H[/COLOR] to view hidden files, and delete all of them.
2. [COLOR="Red"]Empty your desktop trash, and also your root trash.[/COLOR] 

**But sometimes, like in my example, there are absolutely no files on the drive, or in any trash bin.**  

[COLOR="Red"]This problem remained a constant annoyance, bother, and mystery for me until just recently.[/COLOR] 

**Here's how I fixed it. :-)**

**[SIZE="3"]Step 1[/SIZE]**
Follow System --> Administration --> System Monitor --> File Systems.  [COLOR="Red"]Take note of your flash drive.[/COLOR]  In my case it was /dev/sdb1.

**[SIZE="3"]Step 2[/SIZE]**
Follow Applications --> Accessories --> Terminal and run the following command, [COLOR="Red"]replacing /dev/sdb1 with the name of your flash drive.[/COLOR]
```
sudo dosfsck -rV /dev/sdb1
```

**[SIZE="3"]Step 3[/SIZE]**
Press 1 to "backup to original" if this is an option.
then,
Press 2, for "Correct," followed by a "y" to confirm.

[B][SIZE="3"]Step 4[/SIZE]
Unmount, then remount your flash drive, [COLOR="Blue"]and all should be well![/COLOR][/B] :-)

---

