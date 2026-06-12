---
title: "Slave harddrive does not appear on desktop."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by meteora184 on 2008-08-27
ok well here's a simple question again haha.
I have a 8.4gb slave drive that works and is mounted in media.
however, for some reason when i updated to ubuntu studio the drive no longer shows up on my desktop. I would like it to be there haha. There is probably a simple solution, but I have little knowledge on linux or ubuntu for that matter.

---

### Post by bumanie on 2008-08-27
You will need to add it to /etc/fstab. Please supply the name of the drive and the filesystem format it is formatted with. 
However, if it is ntfs you can use ntfs-3g and ntfsconfiguration tool to add it to /etc/fstab.> sudo apt-get install ntfs-3g> sudo apt-get install ntfs-configThen fill out the GUI found under Applications --> System Tools --> ntfs configuration tool.
If not ntfs, supply as per first sentence and also the output of>  cat /etc/fstab

---

### Post by phidia on 2008-08-27
Is it showing and automounted in Places (from your top panel)?
There's a guide [here]("http://ubuntuforums.org/showthread.php?t=802699&highlight=drive+mounting") for mounting drives NTFS and other filesystems.

---

### Post by meteora184 on 2008-08-27
it is fat32 anhd it is already mounted it is already shown under "computer:///"
all i want to do is add it to my desktop
Edit: sorry the name is "slave" haha so original.

---

### Post by phidia on 2008-08-27
Just right click your desktop choose "create launcher"
In the first category in the window that opens select "Location", give it a name and I think you can figure out the rest-just select the actual directory location (you can just use the browse button). Hope that helps.

---

