---
title: "Odd file copying problem"
date: 2017-07-11
forum: New to Ubuntu
---

### Post by crip720 on 2017-07-11
I copied my /home/video to an external hard drive a couple months ago.  I went to use videostream the other day, only to find that it would not play one video, tried another one, and had the same error, also tried vlc and it would not play either.  I guess the file is corupted.  This is the original file in my home.  I then tried to play the copied file in the external drive, it seems to play well.  Question can copying a file corrupt the original file, but the copy is fine?  I copied with the right click option, the complete /home/ video folder(I get the wording right).  I am on Ubuntu 16.04.  These files are not that important, just this seems to be odd, would think that the copy would get corrupted, not the original.  Thank you if you have any ideas.

---

### Post by deadflowr on 2017-07-12
Also possible that the original's hard drive ( or the original's file system) got a corruption between the time you made the copies and when you tried playing the originals.
Perhaps some diagnostics are in order:
Hard drive checking here
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html]("https://help.ubuntu.com/stable/ubuntu-help/disk-check.html")
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

File System Checking here
[https://help.ubuntu.com/community/FilesystemTroubleshooting]("https://help.ubuntu.com/community/FilesystemTroubleshooting")

---

### Post by crip720 on 2017-07-12
During last boot, partition comes up clean and drive tests okay.

---

### Post by HermanAB on 2017-07-12
Anyhoo, when copying large amounts of data, you should use rsync, since it ensures that the files are copied correctly.  This is also a good example of why btrfs and zfs are good.

---

