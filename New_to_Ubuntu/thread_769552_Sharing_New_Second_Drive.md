---
title: "Sharing New Second Drive"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by dshehane on 2008-04-26
First, I am new to Linux and Ubuntu.  And I have tried to read and do all the tips given on the other posts with issues like mine - not getting read/write access to a newly installed drive.  Then every time I think I have it, it doesn't work and I get "access denied".

The problem seems to be that every time I get all the permissions set up right, mount the new drive, and then share it, root takes all the permissions back and makes the drive/directory 'read only'.  When I use sudo chown or other sudo commands to try take ownership back or change permissions, the response says "operation is not allowed" or "cannot change owner", etc....

Last month I had no problem with another second drive, but I ran out of space and needed a larger drive.  I now have spent several days trying everything I read on this and other forums, with no luck.  I have moved the mounting point from /media to /home/username to see if that would help.  I mount and dismount.  I redo the partion..  I really get irritated that "root" takes ownership (like another thread in this forum) and will not allow me to take it back!

The disk (SDB)is a terabyte with one big partition formatted in FAT32 (SDB1).  I am using it as a NAS for backups from my other Windows computers.  Samba seems to be working fine, as I can go to the disk and open files I put there from the Ubuntu side, but cannot create or modify any files from the windows side.  A normal Samba share on the Primary Ubuntu hard drive (SDA) drive mounted at home/username/documents/shared works just fine.  I just cannot keep ownership and my permission settings on the new drive as soon as I share it.

Any hints out there? Again, I am a novice...maybe I am overlooking something simple here.

---

### Post by nicedude on 2008-04-26
Did you set it up in your fstab file to automount when you boot?

---

### Post by dshehane on 2008-04-26
Nope...I was going to do that after everything checked out - I didn't think you needed to do that immediately.  As soon as I share the directory, the permissions go away, so I never get to the automount part....

---

### Post by dshehane on 2008-04-27
Hmm...not getting too much feedback here, so, after trying several different things, I went back to the same thing I did with the prior drive. First, I reformmated it overnight to ntfs.  This morning, I popped the drive back in the ubuntu box and booted.  Everything happened automatically, the drive mounted by itself (I had installed the ntfs configuration utility for the first drive I installed).  All I had to do was to create a shared directory on the newly added drive and it appeared with RW permissions on both my windows xp and windows Vista boxes.  Backups are humming along nicely and everything is working fine.

It is interesting in retrospect to ponder - why, using all the tools and advice posted on the forums, could I not configure the drive using command line, sudo nautilus, gpart, etc.  I feel bad that I did not learn how to solve the problem except by avoiding the issue.  I will still watch and try to learn.

---

