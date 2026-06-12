---
title: "i can't mount my external HD :*("
date: 2008-08-22
forum: New to Ubuntu
---

### Post by medioxcore on 2008-08-22
okay, so in trying to use my external today, i got an error message saying something about ubuntu not being able to mount the HD for some reason or another.  it showed up in my computer, but i could not access it.

i tried looking in various places for help and i found plenty of answers, but they were all just code with no explanation.  i am still VERY new to ubuntu (this is my first day) and i assume im supposed to place this code in the terminal?  but i'm not sure and don't want to just go plugging away on a guess.

thank you!

---

### Post by tuxulin on 2008-08-22
what are the error messages ?

T

---

### Post by Elfy on 2008-08-22
First welcome to the forum.

It would help if you were able to give us the message that you got - right click to eject/unmount first just in case, then plug it in again.

I think the error will appear in a small box - you can do a screenshot of it - take screenshot in accessories - post that here if it is too long to type out :)

---

### Post by roscal on 2008-08-22
Well, first off,.. 
How is the external formatted?
Is it new? 
Does it have data on it?

In my own limited experience, external HD
have automatically mounted with a Fat 32 (but read only) or EXT 3 filesystem (read/write).

you might have to format the disc

---

### Post by k3lt01 on 2008-08-22
1. If you have a Windows machine hook the external HDD to it.
2. wait for it to show up and be sure you can get into it.
3. Then shut down the external HDD's Windows Explorer screen while not removing the HDD.
4. Right click the HDD icon on the main Windows screen, this should bring up a selection list, click on "safely remove hardware" and wait for Windows to tell you it is safe to remove the HDD.
5. hook it up to your Ubuntu machine and tell me what happens.

The above list is based on my experience with my Seagate External HDD when I first bought it and when I forget to "safely remove" it if its used on a windows machine.

---

### Post by k3lt01 on 2008-08-22
> **roscal said:**
> In my own limited experience, external HD
have automatically mounted with a Fat 32 (but read only) or EXT 3 filesystem (read/write).

you might have to format the disc I think you will find most if not all new external HDDs are formatted already and have manufacturers software installed on it. Not only that but the majority are formatted as NTFS.

---

### Post by medioxcore on 2008-08-22
thank you for the welcoming :)

i can get a screenshot, but i am in windows right now, i'll have to reboot.  i was trying to avoid that because i can't get any music to my ubuntu partition because of this HD problem and i am really feeling this radiohead album right now.  ha.

i'm not sure if the HD is ntfs or fat32, how can i check?
it's probably 7 or 8 months old
and it has all of my media and a few programs backed up on it.

be back in a bit...rebooting.

---

### Post by medioxcore on 2008-08-22
heres the screenshot

[IMG]http://a748.ac-images.myspacecdn.com/images01/21/l_bcf152306fd7440d4e20e25da6eb6393.png[/IMG]

god...after working in windows for a couple hours, it's so nice to come back to this.  if photoshop put out a linux version...i would never use windows again.

---

### Post by Rolcol on 2008-08-22
Oh!  That's a simple fix (but it requires going through the command line).  Just follow the command it gives you in that error window: ```
sudo mount -t ntfs-3g -o force /dev/sdb1 /media/My\ Book
```

This error occurs when you remove the hard drive in windows without safely removing it.  It can get annoying if you do it often.

---

### Post by medioxcore on 2008-08-22
i got this message

"$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/my book: No such file or directory
johnnyfresh@johnnyfresh-laptop:~$ sudo mount -t ntfs-3g -o force /dev/sdb1 /media/my\ book"

so i figured i would try and find the right path and try it again, but when i opened my computer, i decided to try and open my external once more...and it opened.  lol.  i don't know what happened, but it's working now.  thank you!

---

### Post by medioxcore on 2008-08-22
oops.

accidental double post.  sorry :/

---

### Post by Rolcol on 2008-08-22
> **medioxcore said:**
> [B]"$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.[/B]
[I]fuse: failed to access mountpoint /media/my book: No such file or directory
johnnyfresh@johnnyfresh-laptop:~$ sudo mount -t ntfs-3g -o force /dev/sdb1 /media/my\ book"[/I]

so i figured i would try and find the right path and try it again, but when i opened my computer, i decided to try and open my external once more...and it opened.  lol.  i don't know what happened, but it's working now.  thank you!

The reason it mounted this time is because the logfile was reset.  It didn't mount because the folder "my book" didn't exist.

---

