---
title: "Having trouble mounting a slave drive..."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Splitshine on 2008-10-21
Ok so I've got an 80g slave drive connected as a slave, however, attempting to open the media through the file browser gives me the message box:

Unable to Mount Location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

What I want to do is: get a few gig of files from the slave and move them to the master, and then format it. However, I can't seem to get those files..

Please help a newb!

EDIT: I'm on Ubuntu 8.04.1 - Hardy Heron (if that helps at all)

---

### Post by wolfen69 on 2008-10-21
i always take the easy way out and use my puppy linux live cd. it can mount anything.

---

### Post by Splitshine on 2008-10-21
Is there another way to do it? Even just getting the files from the drive? Cause your option (although a perfectly valid and good one!) involves having to download the .iso for the live cd and that could take a good while..

---

### Post by wolfen69 on 2008-10-21
> **Splitshine said:**
> Is there another way to do it? Even just getting the files from the drive? Cause your option (although a perfectly valid and good one!) involves having to download the .iso for the live cd and that could take a good while..

it's only 94mb. [http://www.puppylinux.org/downloads](http://www.puppylinux.org/downloads) plus, it's a great disc for your "toolbox".

---

### Post by Splitshine on 2008-10-21
Oh, awesome. Now.. Forgive me for being completely stupid, but which file am I looking to get and how do I then use it to mount the slave drive in ubuntu?

EDIT: Is the LiveCD for Ubuntu the one that I download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ?? If so I've got that lying around somewhere... Would I be able to use that to mount the slave drive?

---

### Post by wolfen69 on 2008-10-21
> **Splitshine said:**
> Oh, awesome. Now.. Forgive me for being completely stupid, but which file am I looking to get and how do I then use it to mount the slave drive in ubuntu?

EDIT: Is the LiveCD for Ubuntu the one that I download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ?? If so I've got that lying around somewhere... Would I be able to use that to mount the slave drive?

you would want puppy 4.1

you can always try the ubuntu live cd. can't hurt.

---

### Post by Splitshine on 2008-10-21
Ok I'll try the Ubuntu LiveCD first. So I shove the CD in, get to the install menu, etc, and then what?

---

### Post by Splitshine on 2008-10-21
Anyone able to help? Bit out of my depth here..

---

### Post by ajgreeny on 2008-10-21
Why not try the Disk Mounter applet in your panel.  Just right click in an empty space in one or other panel and go to "Add to Panel" and choose Disk Mounter.  Then click in the appropriate icon for the disk and select "Mount *diskname*"  I use it all the time as I don't like to mount my other partitions when Ubuntu boots; I like to keep things separate.

---

### Post by Splitshine on 2008-10-21
The drive unfortunately remains not mounted. As a result I'm going back to the original plan of getting the files I want off the drive and formatting it.

A little search of the forums has turned up Testdisk and Photorec. Does anyone have either, a little guide on how I would copy a folder from the slave disk to the master disk using one of these programs, or a link to a guide?

Thanks for your input Ajgreeny.

---

### Post by wolfen69 on 2008-10-21
if you use the puppy cd i mentioned, you will see all drives on the desktop. just click them to mount them, then copy and paste from one drive to another. easy.

---

### Post by tagabukid on 2008-10-21
> **Splitshine said:**
> The drive unfortunately remains not mounted. As a result I'm going back to the original plan of getting the files I want off the drive and formatting it.

A little search of the forums has turned up Testdisk and Photorec. Does anyone have either, a little guide on how I would copy a folder from the slave disk to the master disk using one of these programs, or a link to a guide?

Thanks for your input Ajgreeny.

you can try [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

