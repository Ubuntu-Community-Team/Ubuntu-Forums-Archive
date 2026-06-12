---
title: "CD read only?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by tqprvn on 2008-08-18
Hi all

I just put in a CD full of photos - everything on it is coming up as read only.  I cannot copy and paste them - I have to burn a bunch of CDs duplicating this, any advice appreciated!

Matt

---

### Post by Ripfox on 2008-08-18
Hmm, have you tried > gksu nautilus in a terminal then navigating to the photos from there? Sounds like a permission problem...do other cds work and move data fine? Sometimes I have noticed things I create while in windows won't give up the proper permissions when inserted into a ubuntu machine (namely usb devices)

---

### Post by mcduck on 2008-08-18
The normal file system used on CD's _is_ read-only. You need to use a burning program to burn the disks, and files can't be added or changed once burnt to the disk.

If you want packet writing you'll need to install it yourself. Here's a how-to I found, seems to be rather old but might still work: [http://ubuntuforums.org/showthread.php?t=129093]("http://ubuntuforums.org/showthread.php?t=129093")

Also, when moved from the CD to your own machine the files will keep their permissions, which means that they will stay read-only until you change their permissions. (you do _not_ need root permissions to do this, you are still the owner of those files). Sama kind of problems can happen when kopying files from Windows file systems, as they are not able to understand the kind of file ownerships & permissions used in Linux.

---

### Post by nicedude on 2008-08-18
All CD's are read only ( unless rewritable ) so you cannot write anydata to them once they are burned. But you should be able to say make a new folder on your desktop and then copy the pictures from the CD to the directory and do whatever you want ( like rearrange and then burn them to a new CD ). Once you figure this out and burn them to a CD you can just keep making copies of the CD to have more copies :-)

So in short copy should be YES and pasting to the CD should be NO

If this does not help then I will try to help further.

---

### Post by tqprvn on 2008-09-16
ugh - here we go again.

Sorry - let me clarify that.  

I am not trying to copy on to the cd, I mean when I copy the photos from the CD on to my hard drive, they remain read only.  This is annoying, as there are over 100 of them, and so I have to manually open them and do a 'save as', meaning I have two of everything, and have spent a bunch of time on it.

On a couple of previous occassions (notably when I started the thread), it has been even worse - it won't let me copy files FROM the cd to my hard disk, telling me I do not have permission.

Understand it is a permissions thing, I just don't know how to batch-reset the permissions for them all so that I can work with them.

---

### Post by Mornedhel on 2008-09-16
When in the folder containing the files :

chmod 644 *.jpg (replacing .jpg by whatever the correct extension is) resets the permissions to rw-r--r-- (read/write for you, read-only for everyone else except root)

See the man page for chmod with "man chmod".

---

### Post by stalkingwolf on 2008-09-16
If you copy all your pictures to a single folder, then when you are done
right click the folder, select properties , then permissions, change the
permissions to how you want them.  Then at the bottom click apply to enclosed files.  That should do it all at one fell swoop.

---

### Post by alienexplorers on 2008-09-16
Copy the files to a directory on your disk that is not used by anything else and then select all and right click and select properties -> Permissions.  Change the top on under your name to read/write.

---

