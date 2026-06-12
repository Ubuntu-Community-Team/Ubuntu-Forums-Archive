---
title: "Installing ubuntu over a dualboot"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by blaz.kvas on 2014-03-24
Can I install ubuntu over elementary OS which is installed alongside windows 7 (dualboot). I would like to keep all windows 7 files. 
Can this be done simply by installing ubuntu on the partition that EOS is or can somebody please explain how to do it.

Thanks for your answers :D

---

### Post by Mark Phelps on 2014-03-24
While you probably CAN do that, we've been getting posts from folks who either reinstalled Ubuntu or simply upgraded it -- and it wiped out all their Windows partitions automatically in the process.

My suggest is that, BEFORE you do this, consider doing the following:
1) Download and install the free version of Macrium Reflect to Win7.
2) Use MR to make an image backup of Win7
3) Use the MR option to create a Linux Boot CD
4) Use the Win7 Backup feature to create and burn a Win Repair CD

With these, you will have the means to both repair Win7 and to restore it.

---

### Post by blaz.kvas on 2014-03-24
I already have all my files backed up on my external hard drive. And I can install a fresh windows with no problem. I was just hoping that there was a foolproof way of doing this since there is a lot of work to reinstall and transfer all the files. 
So is this ext hard drive backup ok or is it really necessary to do another backup?

Oh and will the dualboot "chooser" (the program where you choose which OS will you boot) stay?

---

### Post by ajgreeny on 2014-03-24
> **blaz.kvas said:**
> Can I install ubuntu over elementary OS which is installed alongside windows 7 (dualboot). I would like to keep all windows 7 files. 
Can this be done simply by installing ubuntu on the partition that EOS is or can somebody please explain how to do it.

Thanks for your answers :D
Depending on exactly what you mean by "Can I install ubuntu over elementary OS" the answer should be "Yes, you can" but it will depend on making sure you have backups of your personal files in elementary as well as windows.

If we assume you do have everything backed up, start the ubuntu install from DVD or USB and choose **"Something else"** when you get to the partitioning stage.  Don't choose any of the other options as they can be misleading and I have read several threads where windows has been wiped out and the whole disk used for the new install in spite of the writer believing that they had chosen to dual boot and out ubuntu alongside windows.

Having chosen the **Something else** option you will see a listing of all your current partitions and it should be easy to pick out the partition (or partitions) you used for elementary and point the installer to those same partitions in which you want ubuntu.  I realise that elementary is ubuntu based but I have no idea whether it is worth trying to install the new system over the old without formatting the partition during the install, which supposedly can work with ubuntu version upgrades; this is something I have no experience of, having always used clean installs as I feel it gives me a clean start, and I only use the LTS versions anyway, so it is necessary for me to reinstall or upgrade only once every two (or more) years.

PS:  Grub, or the "chooser" as you call it, will not actually stay on the machine, as ubuntu will overwrite the grub version that elementary put on disk and and replace it with its own version of grub.  You will however, still see the grub menu at boot and be able to choose to boot to ubuntu or windows.

---

### Post by oldfred on 2014-03-24
I think ajgreeny covered the issues. 
I will just add a couple of screen shots. I was installing a new version over an old version on my sdc drive, but I label partitions.

---

