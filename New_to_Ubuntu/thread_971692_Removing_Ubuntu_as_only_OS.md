---
title: "Removing Ubuntu as only OS"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by tomduffy1984 on 2008-11-05
I have installed Ubuntu on my brand new laptop and it is the only OS.  When the options were given to me i choose not to create a small partition to keep Ubuntu on.  Instead i guess the whole HD is still one partition.  

I now want to remove Ubuntu but all the current advice seems to be on removing Ubunutu as a part of a dual boot system.  I have been trying to install crystal XP by booting directly from CD but it gets so far and then comes up with a warning which says:

"A problem has been detected and windows has been shuit down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer.  If this screen appears again follow thsese steps:  

Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check you hard drive to make sure it properly configured and terminated.  Run CHKDSK /F to check for hard drive corruption, and then restart your computer."  Then it give me a few hex numbers which i assume are memory addresses.  

So basically what i need is a way to either install windows or get rid of Ubuntu I think?

Please help!

---

### Post by Cypher on 2008-11-05
If you want to remove Ubuntu and replace it with XP, then the procedure is to simply boot up the XP CD and delete all existing partitions on the HD and have the XP installation create new partitions and install XP for you.

Now, you should most likely use the XP CD that came with your laptop. Possibly a restore CD or something. Generic XP CD's should work, but if there is any unique hardware that isn't supported on the standard XP CD, the restore CD you got with the laptop should have the right support.

If the laptop originally came with XP/Vista when you bought it and since you are attempting to return to it, your best bet is to contact the manufacturer of the laptop and they'll be able to quickly get you back into Windows..

---

### Post by Bölvaður on 2008-11-05
If you then want to go dual boot, you should either do what the guy above me said and then install ubuntu on a new partition or you could do this.

make new partition with ntfs file system on it
install windows on it
get and burn grub super disk
boot up with the grub super disk to repair grub, as windows will "destroy it" (not really, it will just owerwrite mbr)

---

### Post by tomduffy1984 on 2008-11-05
yes but my windows xp CD doesn't have a reformatt partitions option or maybe it does but the error comes up before that option is given to me.  My laptop came as a blank box.  Literally nothing installed on it.

---

### Post by CatKiller on 2008-11-05
Personally, I think that your XP cd has problems.

But it's simple enough to get your hard drive back with nothing on so that you just create the partitions as part of the XP install. Boot up your Ubuntu cd. Go to System -> Partition Editor. Wait a bit as it reads the layout of your hard drive. Delete the partitions and hit apply. Reboot. It will eject the Ubuntu cd. Put the XP cd in.

---

### Post by tomduffy1984 on 2008-11-08
Xp Disc works fine have tried it on another laptop.  Removed ubuntu by deleting the partition (although there was a little bit of the HD that i couldn't alter) and then the same error message came up when i next tried to install XP.  

So, it would appear that the problem is specific to my laptop.  What i am not sure about now is if this error is coming about as a result of installing Ubuntu badly initially?

---

### Post by niccholaspage on 2008-11-08
I think this is a problem with your laptop, Not Ubuntu...

---

### Post by CatKiller on 2008-11-08
> **tomduffy1984 said:**
> (although there was a little bit of the HD that i couldn't alter)

This, combined with the fact that XP was complaining about your hard drive smells like a faulty hard drive to me. Read/write errors could have been either the hard drive or the cd, but this seems to point the finger at the hard drive.

You can probably get a utility from the website of the manufacturer of your hard drive that will check for errors, and try to fix them. There will probably be a suite of tests and a "low-level" format option.

---

