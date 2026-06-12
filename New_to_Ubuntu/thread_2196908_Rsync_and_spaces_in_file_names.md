---
title: "Rsync and spaces in file names"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by christophererose on 2014-01-01
Hi
I am having problems using rsync to back up the data files held on my server.
The plan was to use rsync to create a back up on an external hard drive.
I understand that rsync can not deal with spaces in file names easily and have searched all over but it looks like i am failing to understand what I need to do.
The rsync command i am running is
rsync -av --delete /media/Music/ /media/usb0/Music
but this just hangs.
I have understand about quotes around paths that contain spaces but my problem lies in the fact that its the file names within the directories that contain spaces?
How do i get rsync to do this?

Any help much appreciated.
Thanks
Chris

---

### Post by TheFu on 2014-01-01
If you let rsync determine the file names to be sync'd, as it appears you are doing above, then there isn't any issue provided special files (pipes, devices, etc) or illegal file/directory name characters aren't hit.  Spaces are handled properly, of this I am certain.

The target file system type can be an issue too (NTFS?) if it doesn't support the same filename characters.  As an example, don't use ':' in any filename on NTFS.  There are other characters that work for some file systems and not others too.  Music tends to have odd characters in the titles .... then there is that guy from the 80s .... formerly known as .... great music, terrible names which screw up computer files.

If you turn up the verbosity and log the output, I'm positive that the exact filename causing the issue will become known.  Try
```
rsync -avz --stats --progress  --delete /media/Music/* /media/usb0/Music/ | tee /tmp/log.rsync.music
```
Sorry for the slight change in the source/target. I just wanted to be certain we get exactly what we want and this is the way I do it.  If you don't see the problem file on the screen, check the logfile.

BTW, rsync is fantastic for mirrors of files, especially media files, but not-so-good for OS, Apps, and personal data that changes.  For those sorts of files, I like rdiff-backup ESPECIALLY if you are already using rsync. The command is almost the same.

Is the target file system UTF8 character compatible?  The character encoding _could_ be an issue too, but that is less of an issue these days.  Looking at the mount commands used for each should be helpful, though if the system "automagically" mounts these file systems ... don't know how to figure out which character encoding is being used. There must be a setting under /etc .... er ... somewhere?
So, if this stuff doesn't help, can you please verify and check the source and target file systems?  Let us know.

---

### Post by SeijiSensei on 2014-01-01
Rsync has no problems with filenames that include embedded spaces on backups if both filesystems are ext[234].  As TheFu mentions, backups of an ext4 system to an NTFS filesystem can run into problems because the latter doesn't support the same filesystem primitives as Linux expects.

I also agree that you should use the source specification /media/Music/* rather than just /media/Music.  I recommend using the "-n" switch ("rsync -avn") while experimenting.  You'll see the list of files that will be transferred, but the transfer itself will not take place.

---

### Post by cmcanulty on 2014-01-01
I use grsync a GUI for rsync and it works fine with spaces in names, it is in synaptic and the software center

---

### Post by christophererose on 2014-01-02
Hi
Thanks for the responses.
The increased verbosity has shown another problem! I am only getting transfer speeds of 50kbs? I should be getting way more than this surely?
The external drive is formatted to NTFS, i am beginning to think that this could be part of the problem?

Chris

---

### Post by TheFu on 2014-01-02
Speed - USB2, FUSE drivers?  What are your mount options?  What do the log files say?

NTFS allowed filenames are different from Linux file system allowed filenames. Here's a quick reference (probably NOT complete):  [https://en.wikipedia.org/wiki/Filename#Comparison_of_filename_limitations](https://en.wikipedia.org/wiki/Filename#Comparison_of_filename_limitations)

Turns out this is extremely complex. The best recommendation that I've seen is to reuse a Perl CPAN module for this.  The Perl guys are crazy-careful about following specs AND testing.  OTOH, the high-level illegal characters are probably enough to help you fix the media filenames and directory names.

BTW, using NTFS for data backups **is smart **if these files need to be shared with non-Linux systems. However, it does cause issues for Linux system/HOME backups unless the backup solution that maintains user/group/permissions AND ACLs outside the file system is deployed.

---

