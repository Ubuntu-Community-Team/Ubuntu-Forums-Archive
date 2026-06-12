---
title: "[SOLVED] How to set up a dual-boot"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-21
My boyfriend wants Ubuntu (whoo!!)

But, he wants to keep his data on windows and be able to use photoshop on windows.

SO I said: "Dual Boot!"
And he said: "Alright, let's do it tonight!"
And I said: "Sure!... If I knew how to set up a dual boot. ;_;"

So! How do I set up a dual boot without formatting the data of the second OS?

---

### Post by Dark_Stang on 2008-07-21
You can install Ubuntu through windows using Wubi. I'd give that a shot as it's probably the easiest way to do it. (to be honest i'm very partial to using the partitioner built onto the live cd, however i imagine wubi is more friendly for newbies)

---

### Post by iaculallad on 2008-07-21
> **projecthikari said:**
> My boyfriend wants Ubuntu (whoo!!)

But, he wants to keep his data on windows and be able to use photoshop on windows.

SO I said: "Dual Boot!"
And he said: "Alright, let's do it tonight!"
And I said: "Sure!... If I knew how to set up a dual boot. ;_;"

So! How do I set up a dual boot without formatting the data of the second OS?

Here, try to read Ubuntu Community's Dual Booting [page]("https://help.ubuntu.com/community/WindowsDualBoot").

---

### Post by projecthikari on 2008-07-21
> **Dark_Stang said:**
> You can install Ubuntu through windows using Wubi. I'd give that a shot as it's probably the easiest way to do it. (to be honest i'm very partial to using the partitioner built onto the live cd, however i imagine wubi is more friendly for newbies)

I cant get on the internet on his computer currently... :[

---

### Post by projecthikari on 2008-07-21
> **iaculallad said:**
> Here, try to read Ubuntu Community's Dual Booting [page]("https://help.ubuntu.com/community/WindowsDualBoot").

(sorry, two posts. :[)

thanks for this! :KS

---

### Post by Dark_Stang on 2008-07-21
You don't have to go online on his machine. You just need to be able to get the iso and burn it to a disc somehow. However I would suggest going online asap to get any drivers/extras you may need.

---

### Post by Niniel on 2008-07-21
So this wubi is now good enough to be used by the general public?
I remember a while ago somebody tried that and totally trashed his Windows installation.
Setting up dual boot with the Ubuntu CD was very easy though, so I'd recommend that. The advantage is that you can also re-partition your hd - just shrink the NTFS partition and give Ubuntu the free space. Piece of cake (do a manual install) :).

Oh, and Photoshop installs/runs well under Ubuntu+Wine, at least version 6 does.

---

### Post by projecthikari on 2008-07-21
> **Niniel said:**
> So this wubi is now good enough to be used by the general public?
I remember a while ago somebody tried that and totally trashed his Windows installation.
Setting up dual boot with the Ubuntu CD was very easy though, so I'd recommend that. The advantage is that you can also re-partition your hd - just shrink the NTFS partition and give Ubuntu the free space. Piece of cake (do a manual install) :).

Oh, and Photoshop installs/runs well under Ubuntu+Wine, at least version 6 does.

We always use the most updated photoshop. XD;

---

### Post by mb-editor on 2008-07-21
I've done this now on a few PCs, so even though I'm (relatively) new to Ubuntu, I think I can help...

First, download the ISO and burn it to a CD - you can do this while in Windows.

Next, change the boot sequence in the BIOS to boot with the CD first.

Bung the CD in and restart the PC.  You get the live CD desktop in Ubuntu.

If you've only one single disk (no partition), it would be best to let Ubuntu automatically decide to split that drive for the install.

Alternately, start by going to System -> Administration -> Partition Editor.  Resize or delete an existing partition to create unallocated space (would be a good idea to back up first, or of course, to empty out a partition to be deleted!) 

Get back to the live desktop and double-click 'install'.  When the partition manager starts up, ask it to use the 'largest unallocated space'.

Once Ubuntu installs, it will include Windows in the GRUB, so at the next restart, you can choose to launch either OS.  Voila, you have dual boot!!

Of course, if you're need to photoshop, there's always GIMP that comes pre-installed in Ubuntu.  For more power, there's GIMPshop...

---

