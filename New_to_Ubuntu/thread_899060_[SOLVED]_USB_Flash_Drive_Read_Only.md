---
title: "[SOLVED] USB Flash Drive Read Only"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Spooky5 on 2008-08-23
Earlier this evening, I copied some files to a 16 GB flash drive. When I was done, I right clicked on the desktop icon and selected unmount. A dialog box which said it was safe to remove popped up. So I removed it. A little while later I plugged it back in to recopy a file I had changed. Only one the video podcast folder and my bookmark back-up is displayed on the drive. Yet, it says there are 8 files with 12.1 GB of the 16 being free. It won't let me do anything with it cause it says it is read-only.

How do I get full access back? :confused:

---

### Post by Loaded.len on 2008-08-24
My key has a physical switch on it to set it to read-only mode.  This has caused me grief a few times because it's always the last thing I think to check.  Does your key have that?

---

### Post by Spooky5 on 2008-08-24
No, it doesn't have any switches.

---

### Post by Patb on 2008-08-24
Spooky, did you try rebooting?  

The reason for the behaviour may possibly be explained by your fstab setup and folder permissions which is a long subject. If you want to go into it, you might [start here]("http://ubuntuforums.org/showthread.php?&t=283131"). 

Cheers, Pat

---

### Post by etnlIcarus on 2008-08-24
Try restarting the whole PC and see if it's more agreeable again.

Also a possibility that the data on the drive is corrupted. I've had linux suddenly go read-only on drives when there was something wrong with them. Might be worth trying to reformat the flashdrive with gparted in super user mode.

---

### Post by seagullplayer77 on 2008-08-24
You might also try right-clicking the drive to make sure that it did indeed mount again. I've had situations where the drive would pop up and you could read data, but Ubuntu never actually mounted the drive so you couldn't write to it. I believe there's a read-only option under "Properties" if you right-click the media. Good luck!

---

### Post by Spooky5 on 2008-08-24
> **etnlIcarus said:**
> Try restarting the whole PC and see if it's more agreeable again.

Also a possibility that the data on the drive is corrupted. I've had linux suddenly go read-only on drives when there was something wrong with them. Might be worth trying to reformat the flashdrive with gparted in super user mode.

I think that's what happened. I plugged it into my windows machine and tried to open the bookmark file. It said it was corrupted. I reformatted and it's working beautifully now. I've recopied the files, unmounted and plugged it back in. All of the files are still there. :)

Thanks, everyone!

---

### Post by itsdarklikehell on 2009-10-15
i have the same prob, but on a 500 gig usb hd, ive tried to change the permissions on ubuntu and with my freenas server witch both came up with the same error and i am not willing to repartition the whole damn thing cos it is gonna cost me a sh1tlo@d of time and bandwith to get all of my data back, so is there another option to fix this like fsck or scandisk to correct the possebly lost/corrupt data?? and how do i get to know witch file is corrupted? pls mail me [EMAIL="bauke.molenaar@gmail.com"]mailto:bauke.molenaar@gmail.com[/EMAIL]__[EMAIL="//bauke.molenaar@gmail.com"][/EMAIL]

---

### Post by az on 2009-10-15
> **itsdarklikehell said:**
> i have the same prob, but on a 500 gig usb hd, ive tried to change the permissions on ubuntu and with my freenas server witch both came up with the same error and i am not willing to repartition the whole damn thing cos it is gonna cost me a sh1tlo@d of time and bandwith to get all of my data back, so is there another option to fix this like fsck or scandisk to correct the possebly lost/corrupt data?? and how do i get to know witch file is corrupted? pls mail me [EMAIL="bauke.molenaar@gmail.com"]mailto:bauke.molenaar@gmail.com[/EMAIL]__[EMAIL="//bauke.molenaar@gmail.com"][/EMAIL]

Are you able to read your files?

---

### Post by itsdarklikehell on 2009-10-15
read yes, write no! 
ill post the errormessage i get (if i get it again) lateron, cos im running fsck so i cant mount my drive atm.
thnx for the fast reply m8!

---

### Post by itsdarklikehell on 2009-10-15
TQ so much people! 
seems fsck kinda fixxed it.. mayb it was a corrupted file/block..

U rock!:guitar:

---

### Post by Glace on 2010-11-03
For me to fix my read only usb drive:
[LIST]
[*]mount your usb drive
[*]open gparted (must be root)
[*]find you're drive in the menu (try different selections in the top right if you can't see it)
[*]right click -> unmount
[*]it loaded for a while then next time I mounted it it was like normal
[/LIST]

---

### Post by csk1103 on 2013-02-03
> **etnlIcarus said:**
> Try restarting the whole PC and see if it's more agreeable again.

Also a possibility that the data on the drive is corrupted. I've had linux suddenly go read-only on drives when there was something wrong with them. Might be worth trying to reformat the flashdrive with gparted in super user mode.
I solved the problem by rebooting. Thank you.

---

### Post by oldos2er on 2013-02-03
Closed, please don't bump old threads.

---

