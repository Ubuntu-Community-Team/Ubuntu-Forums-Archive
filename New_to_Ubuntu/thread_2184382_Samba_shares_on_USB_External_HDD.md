---
title: "Samba shares on USB External HDD"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by newb85 on 2013-10-28
I have my Desktop machine doubling as a Samba server.  Some of the shares are media folders on a USB external HDD.  It works great...as long as the user the shares were set up under is actually logged in.  Otherwise, the drive isn't mounted to the user-specific location Samba is looking for it.

So here's the question: is there an easy way to have this external HDD mount to one non-user-specific location regardless of who is logged in?

---

### Post by newb85 on 2013-11-09
No one, really?  I'm a little surprised.  I don't feel like my goal here is that out-of-the-norm.

---

### Post by squakie on 2013-11-09
Yes - completely possible.  [This link ]("http://ubuntuforums.org/showthread.php?t=2171268")will show you how - and please ignore my ignorant replies in that thread - as noted in my last post there I found out the hard way I was wrong.

I currently have created a folder in /home called "xbmc", then I added the following in my /etc/fstab file:

UUID="3B426B086C5EFD27" /home/xbmc ntfs rw,uid=1000,gid=1000,fmask=002,dmask=002   0      0

You will need to subsitute the UUID for your drive (try "blkid" command - might need "sudo blkid").  Be sure to use the UUID, not dev path or anything like that.  Also update the mount point (the "/home/xbmc") to reflect where ever you are mounting your drive.

You can change ownershp, permissions, etc., as you need via the options on the mount command.

---

### Post by newb85 on 2013-11-10
Thanks for the reply.  I had suspected it would be something along those lines.  Before I charge in, though, I have a few questions.

As it is an external HDD, what will happen at boot-up if the drive is not connected?  As it is right now, I never disconnect it, but I could foresee reasons to.

Also, I frequently access the drive from the machine it's connected to when logged in as a user.  To maintain this, should I:
Make a group for accessing the HD.
Make that group the owner group for the drive's mount point.
Give read & write permissions to the group for the mount point.
Include any users in that group that I want to access the drive.

---

### Post by bab1 on 2013-11-10
> **newb85 said:**
> Thanks for the reply.  I had suspected it would be something along those lines.  Before I charge in, though, I have a few questions.

As it is an external HDD, what will happen at boot-up if the drive is not connected?  As it is right now, I never disconnect it, but I could foresee reasons to.

It will error and stop the mount process.  Use the **nobootwait** option in the fstab entry to overcome this.
> 

Also, I frequently access the drive from the machine it's connected to when logged in as a user.  To maintain this, should I:
Make a group for accessing the HD.
Make that group the owner group for the drive's mount point.
Give read & write permissions to the group for the mount point.
Include any users in that group that I want to access the drive.
Do you mean as a different user?  If the multiple users are going to access the data then a common group with all the users in it is the method.  The mount point is not where you add the ownership or the permissions.  You provide this using the options in the mount command if this is an NTFS partition.  That was part of the discussion in the link @squakie provided.

---

### Post by newb85 on 2013-11-11
I see. Thanks!

---

