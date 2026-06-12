---
title: "Wubi to Full Version"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by Treyonator56 on 2011-12-04
I am not really sure if this is noobish anymore, but I installed Ubuntu via Wubi and I need to make it the full version. I have tried doing it the right way but it seems there is a broken link on the site. I have read other guides so I know it's possible, but they don't make that much sense. Can anyone please help me repartition my Netbook and do what ever else is needed? Any help will be appreciated. =)

---

### Post by Frogs Hair on 2011-12-04
Some information about your computer may be helpful because computers coming from the factory have different partition setups at times . Since you are asking about partitions you must want to dual boot with Windows . Is that correct or do you want to replace Windows ?

I know you have read some guides , but here is a link that describes moving a Wubi installation to its own partition . The Wubi mega thread is another good resource .

[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by Treyonator56 on 2011-12-04
Emachines Acer
1 gig memory
Intel atom processor
160 gb hard drive 
Windows 7 starter 
...And a 3 cell Li-ion Battery =)

I want to dual boot so I can easily switch back to windows when needed.

---

### Post by Frogs Hair on 2011-12-04
If you want to move a Wubi installation to a partition use the method at the first link because it is best explained there . 

If want to hide the Windows option in the boot loader , that is a different question . As you probably know the max space you can give a Wubi installation is 30 Gb unless you move it to a partition .

---

### Post by Frogs Hair on 2011-12-04
Another option is to increase the size of the Wubi disc with the following method and continue to use it as you are now . [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by mastablasta on 2011-12-04
wouldn't it be easier to simply backup your /home, uninstall wubi, create empty disk partition (as big as you want to reserve fo linux) and make a full install there?

---

### Post by Treyonator56 on 2011-12-04
I am trying to perform the dual boot partition and it seems the Windows 7 partition is too large. How do I fix this? I have included a picture to show you what I am talking about. Do I decrease the reserved space?

---

### Post by Treyonator56 on 2011-12-04
> **mastablasta said:**
> wouldn't it be easier to simply backup your /home, uninstall wubi, create empty disk partition (as big as you want to reserve fo linux) and make a full install there?

I failed to mention that I can not back up my files. I do not have an external hard drive and my Netbook does not have a disk drive. Sorry for the double post.

---

### Post by cryptotheslow on 2011-12-04
Use the disk management tool within Windows 7 itself to shrink sda3. Do not use any Linux based tools to do it - Win7 has a habit of getting annoyed if you mess around with its filesystem externally.

Once resized - reboot into Win7 3 or 4 times to ensure it is completely happy - it may run some filesystem checks and corrections during this.

Then you will be able to use the Ubuntu LiveCD / LiveUSB to install into the now empty space on the drive (use the side-by-side or alongside option). This should create a new sda4 as an extended partition with sda5 as a logical partition within it for the / partition and sda6 as swap.

Once that is done - you should be able to boot back into your Wubi installation, mount the new sda5 and copy what you need from the Wubi install to a convenient place on your new side-by-side install. Once you are happy you have everything you need in the new install you can uninstall Wubi from within Win7.

Good luck :)

---

### Post by Frogs Hair on 2011-12-04
You can shrink the size of the Windows partition from Windows disk management , try looking at the partitions from there . I'm not clear if you are still trying to move a Wubi installation or preform a dual boot . If you can get USB storage I would suggest making backups that way .

---

### Post by cryptotheslow on 2011-12-04
Yep - just to add to my above - I wouldn't want to attempt any of that without backing up at least my most crucial files. Even if it were just to something like Dropbox in the absence of a USB stick or external drive.

---

### Post by Treyonator56 on 2011-12-04
Okay. I know what to do now but it is late. I will attempt to do this tomorrow and tell you guys how it goes. =) Originally, I wanted to install the full version of Ubuntu. Now I want to dual boot them just in case I need Windows for something that Ubuntu can not do or lacks in quality.

---

### Post by Frogs Hair on 2011-12-04
Here is a link to one guide and there are many more available . [http://www.muktware.com/man/2684](http://www.muktware.com/man/2684)

---

### Post by Treyonator56 on 2011-12-05
I am having some problems with this. I had to restore my whole Hard Drive because something went wrong...=S Should I just stick with Wubi this time?

---

