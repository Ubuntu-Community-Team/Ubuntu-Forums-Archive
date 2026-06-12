---
title: "Unable to change folder permissions"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-14
Hi Guys,

I wrote a nice script to move photos from my camera into a directory and then upload that directory to the web server.
The script makes the directory for the photos on an external hard drive.

I thought everything was cool and I was so proud of myself until I noticed that the pictures wouldn't show up after adding them in Joomla.

I suspect the reason is that the directory that is uploaded is not 755.

Now here is the **WEIRD** part.

Below is a screenshot of a directory I made on the external hard drive:

[IMG]https://dl.dropboxusercontent.com/u/23115609/perm.png[/IMG]

I made this directory by right clicking and choosing Create New Folder.
No matter what I do, I can not change the permissions.
As soon as I change something, it reverts to what you see in the screen shot.

Any ideas??

---

### Post by dave0109 on 2013-04-14
This external drive - which format is it?  If it's FAT or NTFS, then it won't support UNIX style permissions, and when mounted the files will dynamically be assigned the owner of your user, and the permissions will be as you see.  You can't change them because the underlying format doesn't understand the request.

You will either need to change the permissions on the remote server after uploading the directory, or you'll need to put the directory somewhere under your $HOME area, which should be ext3 or ext4 format and therefore have proper permission support.

---

### Post by GrouchyGaijin on 2013-04-14
> **dave0109 said:**
> This external drive - which format is it?  If it's FAT or NTFS, then it won't support UNIX style permissions, and when mounted the files will dynamically be assigned the owner of your user, and the permissions will be as you see.  You can't change them because the underlying format doesn't understand the request.

You will either need to change the permissions on the remote server after uploading the directory, or you'll need to put the directory somewhere under your $HOME area, which should be ext3 or ext4 format and therefore have proper permission support.

NTFS is the format.  Well, that explains a lot!
I'll use my home directory.

Thank you for the quick reply!

---

