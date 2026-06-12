---
title: "Can't find mirrored disks"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by ReverendMo on 2014-03-04
I am a new ubuntu user. 

I have successfully installed ubuntu on my ssd drive, along side Win 8.1. 

I have two 1TB drives mirrored in Win 8.1 that I use for a data drive. Having lost data in the past I figured a mirror was a relatively inexpensive way to prevent data loss. 

When I go into disks and look at the drives, disks shows me two 1TB drives. Is there any way I can use these in Ubuntu as I do in Win 8.1? 

Thanks for reading.

---

### Post by centaurusa on 2014-03-04
What you are doing with the "mirrored disks" isn't totally clear.  I would imagine that you are using one as a data disk and the second as a backup (a mirror) of the first.  If this is the case, you can certainly continue in this manner in Ubuntu, although you will (probably) need to use different software under Linux than that used under Windows.   It all depends how you are establishing the mirror feature.  Is this a manual, one-time copy or an automatic, continuous-copying process? 

 If you make the backup manually, there are a number of options.  For example, something like FreeFileSync ([http://linuxnorth.wordpress.com/2011/11/29/file-and-folder-synchronization/](http://linuxnorth.wordpress.com/2011/11/29/file-and-folder-synchronization/)) could be used under both operating systems to maintain the second drive as a mirror of the first.   Another option I like is Back in Time ([http://linuxnorth.wordpress.com/2012/09/08/going-further-back-in-time/](http://linuxnorth.wordpress.com/2012/09/08/going-further-back-in-time/)) which can create incremental backups. 

If you run a "shadow copy" system, then something like Quick Shadow ([http://opcug.ca/public/Reviews/Me&MyShadow.htm](http://opcug.ca/public/Reviews/Me&MyShadow.htm)) under Windows can be complemented by something like inosync ([http://linuxnorth.wordpress.com/2011/02/19/real-time-backup/](http://linuxnorth.wordpress.com/2011/02/19/real-time-backup/)) in Linux.

---

### Post by ReverendMo on 2014-03-04
Well, I set the mirror up using the built in disk management tools in Win8.1. Both disks display as one 1tb drive with a single drive letter. I would think it would be detrimental to write to one of the drives outside of windows.

---

