---
title: "Will Ubuntu 12.04 LTS work on Dell Studio 1537?"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by thphwh on 2012-09-02
I will accuire a Dell Studio 1537 laptop in a few days and I was wondering will Ubuntu work on it? I have never tried Ubuntu before, though I'm sure I know how to install and completely delete Vista.

Thanks,
Thphwh

---

### Post by Sidewinder1 on 2012-09-02
I don't see why not. That said, I haven't used that particular model but, ubuntu seems to work well on most Dells.

Side

---

### Post by thphwh on 2012-09-02
Thank You. Also if I use a USB stick to install, can I then use it to store files?

---

### Post by NikTh on 2012-09-02
Hello , 
you can try it and see if working OK , with you hardware. 

Boot in Vista and : 

Grab the .iso from here : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Grab unetbootin from here : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Grab a usb flash drive at least 2GB and check the install procedure here: [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)

When installation finish , boot from Usb and choose the first option "Default"  

See if Ubuntu works well. 
A general rule is " If works well in live session it will works well after installing it" 

Thanks

---

### Post by Bodsda on 2012-09-02
> **thphwh said:**
> Thank You. Also if I use a USB stick to install, can I then use it to store files?

Absolutely. After you use the USB stick to perform the install, you don't need to keep it. Just reformat the USB stick and your good to go.

I personally wouldn't delete Vista, especially as Dell rarely include the install media. Just dual boot.

HTH,
Bodsda

---

### Post by thphwh on 2012-09-02
But how much space would Vista use?

---

### Post by NikTh on 2012-09-03
> **thphwh said:**
> But how much space would Vista use?

If you choose to install Ubuntu Alongside Windows , then you will see than Ubuntu automatically will resize the disk. So you will have no problem.

If you want to shrink more the space that Vista will use , you have also this option. 

I suggest (for the first time) to leave the automatic installer to do the things. 

Thanks

---

### Post by thphwh on 2012-09-04
I've burnt the .ISO onto the disk and it went correctly. What will Ubuntu do to the existing system when I try it, not install it. Does it write anything into the disk. Will there be any remnants on the disk from Ubuntu?

Thanks,
Thphwh

---

### Post by Sidewinder1 on 2012-09-04
> **thphwh said:**
> I've burnt the .ISO onto the disk and it went correctly. What will Ubuntu do to the existing system when I try it, not install it. Does it write anything into the disk. Will there be any remnants on the disk from Ubuntu?

Thanks,
Thphwh

No, there shouldn't be anything (of consequence) if you just "Try Ubuntu." If you do decide to install (dual boot, NOT wubi), alongside windows, especially if you're planning on shrinking the NTFS partition, I would strongly suggest that from the windows environment you defragment the C:\ drive, at least twice prior to running the installation.
The following page contains a plethora of information but beware; some of those pages can be a bit confusing as to real dual-boot versus wubi. Wubi is an install
_*within*_ the windows environment and does not require any ext3 or ext4 formatting of partitions. WUBI is definitely NOT recommended, at least by me; with all due respect to the developers of course.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I would highly recommend reading that entire site and after that going back to the install page that I've linked above. 
Good luck and as an aside, that's the site/pages that I used, back in 2007 to install and dual boot.

HTH,
Side

---

### Post by newb85 on 2012-09-04
> **Sidewinder1 said:**
> No, there shouldn't be anything (of consequence) if you just "Try Ubuntu." If you do decide to install (dual boot, NOT wubi), alongside windows, especially if you're planning on shrinking the NTFS partition, I would strongly suggest that from the windows environment you defragment the C:\ drive, at least twice prior to running the installation.
The following page contains a plethora of information but beware; some of those pages can be a bit confusing as to real dual-boot versus wubi. Wubi is an install
_*within*_ the windows environment and does not require any ext3 or ext4 formatting of partitions. WUBI is definitely NOT recommended, at least by me; with all due respect to the developers of course.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I would highly recommend reading that entire site and after that going back to the install page that I've linked above. 
Good luck and as an aside, that's the site/pages that I used, back in 2007 to install and dual boot.

HTH,
Side

+1 to all that.

If you are new to Ubuntu, you will probably find yourself wanting to run Windows for something every now and then.

The wubi installer makes your Ubuntu system a slave to your Windows system.  If, down the road, you do want to remove Windows, it will cause problems.  If your Windows system fails, it could take the Ubuntu system down with it.  And, of course, Ubuntu would have to use Windows' NTFS (a sub-optimal 13-year-old file system requiring defragmentation) instead of EXT4 (a 2-year-old file system that doesn't require defragmentation).

Psychocats' pages can be a great reference.

---

### Post by Sidewinder1 on 2012-09-04
Well, I didn't want to list the problems with wubi; too time consuming.
Another great resource is the #ubuntu channel on Freenode via IRC. You'll need an IRC client; might I suggest X-Chat, for that?
BTW, newb85, I love Sir Winnie's quote!

Side

---

