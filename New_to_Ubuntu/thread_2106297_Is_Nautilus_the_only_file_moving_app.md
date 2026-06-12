---
title: "Is Nautilus the only file moving app?"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Tarka Dal on 2013-01-18
Nautilus failed three times and has corrupted a few files while tring to transfer 3.6Gb of photo files.
Is there a better App than this?
Thanks for your help.

---

### Post by mcduck on 2013-01-18
It sounds unlikely that Nautilus would be the cause of the problem. It's very well tested, widely used and generally seen being as reliable file manager as one can be...

Where were you moving the files? What kind of device & filesystem, and if it was a removable device did you remember to unmount it correctly in the end? Any error messages?

(and yes, there are plenty of file managers available in the repositories. Like I said I doubt Nautilus was reason for your problems but if you want to try something with different features then thunar and pcmanfm would be pretty good ones, although both a bit less feature-rich than Nautilus is. And also keep in mind that if you use Gnome/Unity, the desktop itself is also managed by Nautilus...)

---

### Post by Tarka Dal on 2013-01-18
Thanks for your reply McDuck.
It's a clean install and one of my first transfers from my NAS. FAT 32. I have no idea why it would fail 3 times...
It's a mystery!:lolflag:

Is there a file transfer system like on windows Robocopy or something like this?
The thing is I don't want dropped or corrupted files...

---

### Post by lukeiamyourfather on 2013-01-18
It sounds like the network might be cutting out or there might be something that the filesystem won't allow (like special characters in the filenames, FAT is terrible in this regard). If you're on wireless try using a wired connection. If possible don't use FAT. Linux native filesystems are the best option like ext4.

---

### Post by The Cog on 2013-01-18
I have seen people complain before about failures when copying very large numbers of files with nautilus. I don't know whether nautilus really has a problem or whether it is just getting the blame when other things go wrong.

Either way, I personally feel uneasy when trying to copy thousands of files with the GUI. For large numbers of files, I always prefer to use the command line, cp or rsync. 

There are many file managers, [http://www.linuxlinks.com/article/20081224191928555/filemanagers.html](http://www.linuxlinks.com/article/20081224191928555/filemanagers.html) but I still prefer command line for big transfers.

---

### Post by dannyboy79 on 2013-01-18
grsync

---

### Post by mcduck on 2013-01-18
> **Tarka Dal said:**
> Thanks for your reply McDuck.
It's a clean install and one of my first transfers from my NAS. FAT 32. I have no idea why it would fail 3 times...
It's a mystery!:lolflag:

Is there a file transfer system like on windows Robocopy or something like this?
The thing is I don't want dropped or corrupted files...

Is it one file, or many? FAT has file size limit of 4GiB, and as programs tend to mix between using GB and GiB as the unit (and quite often refer to either one as GB!) the reported 3.6GB might in worst situation actually be pretty close to the limit...

I also agree with lukeiamyourfather about making sure it's not a network error. Especially if you are using a wireless connection.

And one more option would be keeping some system log open during the transfer, that way you should be able to catch some error messages when things start going wrong. There is a graphical log viewer included, but you can also juts pop open a terminal and run "tail -f /var/log/syslog" to monitor syslog..

---

### Post by helpee on 2013-01-18
If one of your devices has a fat32 format, you will be limited to copying any single file up to 4 GigaBytes. You could make a .rar out of your big file so that it's really a bunch of small files to the OS, and do it that way. I actually had to do that with a friend's fat32 usb stick just the other day, even though the stick was 16 GB in total size.

---

### Post by Tarka Dal on 2013-01-18
Thanks guys for the posts. Really appreciate it.
They are all photos of various sizes of around 1mb - 8mb. The problem usually occurs around two thirds the way through the GUI.
The NAS is fine but I cant convert it to anything else as it does not have NTFS available on it. It's an old banger in the scheme of things.

---

### Post by Tarka Dal on 2013-01-18
New problem:..
I want to use Grsync to sync my files from the NAS but, the NAS is not available too see in the window.
See Attached:[http://ubuntuforums.org/attachment.php?attachmentid=230263&stc=1&d=1358551159](http://ubuntuforums.org/attachment.php?attachmentid=230263&stc=1&d=1358551159)

---

