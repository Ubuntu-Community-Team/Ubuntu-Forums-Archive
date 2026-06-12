---
title: "Separating ascii text from binary data in image file"
date: 2008-07-29
forum: Programming Talk
---

### Post by Redsandro on 2008-07-29
Not sure if this is the right forum, but here goes:

I have a 40 gig image of my broken harddrive, and I like to get all my ascii data back. I tried getting a specific article back with grep, but it didn't work. [SIZE="1"]([http://ubuntuforums.org/showthread.php?t=831055](http://ubuntuforums.org/showthread.php?t=831055))[/SIZE]

Is there a smart chain of commands or pherhaps a little script that can strip the ascii data from the binary data on the drive image, and save those as text files if they are bigger than say 1k?

Or can one point me in the right direction to think for making my own script?

---

### Post by LaRoza on 2008-07-29
> **Redsandro said:**
> Not sure if this is the right forum, but here goes:

I have a 40 gig image of my broken harddrive, and I like to get all my ascii data back. I tried getting a specific article back with grep, but it didn't work. [SIZE="1"]([http://ubuntuforums.org/showthread.php?t=831055](http://ubuntuforums.org/showthread.php?t=831055))[/SIZE]

Is there a smart chain of commands or pherhaps a little script that can strip the ascii data from the binary data on the drive image, and save those as text files if they are bigger than say 1k?

Or can one point me in the right direction to think for making my own script?

"strings" will list all the ascii data

You can pipe these results into something else.

---

### Post by dwhitney67 on 2008-07-29
What kind of image do you have?  Is it an ISO image?

If it is an ISO image, try to mount it:
```
$ sudo mount -o loop <ISO image> <mount point>
```
where the <ISO image> is the name of the image file (e.g. image.iso) and <mount point> is the path to some directory where you want the image mounted (note, the directory must exist!)

If the mount succeeds, then you should be able to navigate to the directory where you have mounted the image, and hopefully everything in your HDD image will be accessible.

When you are done, unmount the image:
```
$ sudo umount <mount point>
```

---

### Post by dribeas on 2008-07-30
> **dwhitney67 said:**
> 
If it is an ISO image, try to mount it:
```
$ sudo mount -o loop <ISO image> <mount point>
```
where the <ISO image> is the name of the image file (e.g. image.iso) and <mount point> is the path to some directory where you want the image mounted (note, the directory must exist!)


If the image is not corrupted, then that will work even if it is not an ISO image. mount should detect the filesystem type. If the filesystem was corrupted, then it may fail to mount and/or show invalid data. There are some tricks on what you can do depending on the filesystem type, some utilities that can recover broken filesystems... but that depends on the type.

   David

---

