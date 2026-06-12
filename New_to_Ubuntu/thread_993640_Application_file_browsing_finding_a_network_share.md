---
title: "Application file browsing finding a network share?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-11-25
Hello, thanks to the fine people of this forum, I have been working on sharing a 500GB hard drive across a mixed Windows-linux network using Samba on a Kubuntu server.

However, I have a less difficult question - how do I get this network share to show up in the file browser for applications on my Ubuntu machine?  For instance, I am using MusicBrainz on my Ubuntu machine and I want to add files/folders from the server.  Unfortunately it only checks the local machine, and I don't know where to find the mount point for the network share.

If you can tell me what path I should check for this (it isn't found in the shortcut that was created), I would appreciate it.

Thanks!

~Nix

---

### Post by Peter09 on 2008-11-26
You will have to create a mount point for these shares on your local drive. These mount point appear as a local folder to your applications, when the folder is opened the contents of the share are shown.

This thread provides more details.

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)
[http://ph.ubuntuforums.com/showthread.php?t=887518](http://ph.ubuntuforums.com/showthread.php?t=887518)

---

### Post by Nixie Pixel on 2008-11-27
Thank you, I followed the instructions and was able to mount the drive to a mount point on my Ubuntu machine.

Unfortunately I can't create/edit files on the server, I can only view them.  Even though I have the share set up to allow create/edit/modify permissions.

What could be going wrong?

Thanks!

---

