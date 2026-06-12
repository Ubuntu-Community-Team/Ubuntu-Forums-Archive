---
title: "ubuntu media files, not being seen in xp"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-07-27
I have a small problem, when i burnt avi in ubuntu using k3b or brasero, xp cant see them, in ubuntu it see the file! Why is this?

And how can i fix it?

---

### Post by billgoldberg on 2008-07-27
Do you mean you can't see the file in explorer.exe or winxp can't play the file?

---

### Post by Bucky Ball on 2008-07-27
Hi Bill!

Yea, Ibizatunes. If you are in windoze and you have your ubuntu information stored on ext3 formatted drives, you won't see the files, or the ext3 partition even, if that is what you mean. You are going to need to drop them onto a fat32 or ntfs partition, which windoze will see (read). 

Good luck.

---

### Post by billgoldberg on 2008-07-27
Hi bucky :p

I'm going by the presumption you can't read your cd burned in ubuntu on your winxp install using explorer.exe

Well, did you burn the file correct?

In windows you could try this and see if it works:

[http://www.download.com/Free-CD-Ripper/3000-2140_4-10212165.html](http://www.download.com/Free-CD-Ripper/3000-2140_4-10212165.html)

You are going to give more info.

---

### Post by bobbob1016 on 2008-07-27
Did you burn the files on the same computer you are playing them on?  As in dual-booting XP and Ubuntu?  Does the XP machine have a burner?  It could be that you aren't "finalizing" the disc, an unfinalized disc can only be read by a burner.  There should be a "finalize" option somewhere.

---

### Post by ibizatunes on 2008-07-27
I know the ext3 wont be able to be seen in windoze, i burn cd off so i can watch them in windows because ubuntu doesnt display correct on my LCD..... (I cant the correct resolution)

In windows it doesnt see that the data is on the cd that i have burnt, i will check to see if they have been finalized, but i have set it up to do this....

---

### Post by ibizatunes on 2008-07-27
worked it out, sh**y windows has a 16 letter limit on and my file names are to long... that is why it wouldnt play!!

---

### Post by billgoldberg on 2008-07-27
> **ibizatunes said:**
> worked it out, sh**y windows has a 16 letter limit on and my file names are to long... that is why it wouldnt play!!

Really?

Haha.

If your resolution isn't correct, install your graphic card or change the resolution in /etc/X11/xorg.conf

Or

If the computers are in the same network (both connected to the router) you can set up ssh.

Instructions: [ubuntu]("http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/"), [windows]("http://pigtail.net/LRP/printsrv/cygwin-sshd.html")

This won't work if it's dual boot.

If you dual boot, you can read your Ubuntu partition from within windows using [this]("http://www.fs-driver.org/") program (for ext2 and 3).

These options will save you time and money.

---

### Post by Bucky Ball on 2008-07-27
Ibizatunes! ha! Typical. It ain't called Windoze for nothing, cos that sort of thing just puts you to sleep, especially after grovelling around for hours trying to find a fix. Good one!

---

### Post by JillSwift on 2008-07-27
If you burn a CD with a Joliette file system extension it gives Windoze (and other OSs) 103 characters per file name.

---

### Post by Bucky Ball on 2008-07-29
Interesting info, there JillSwift. Ta. But mostly thanks for the link in your signature, good idea to pass that info on. Cheers.

---

