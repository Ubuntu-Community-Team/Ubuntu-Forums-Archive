---
title: "Uninstalled Ubuntu 11.10 now Windows XP Pro won't boot!"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Future Warthog on 2012-04-11
[COLOR=Red][SIZE=4][B]HELP!!!!!!
[SIZE=2][COLOR=Black]I recently uninstalled Ubuntu 11.10 by deleting the extended partition, and now Windows XP Professional won't boot!!!!
Someone PLEASE HELP ME!!

[/COLOR][/SIZE][/B][/SIZE][/COLOR]

---

### Post by muteXe on 2012-04-11
what actually happens?

---

### Post by Future Warthog on 2012-04-11
> Error: Partition not found
GRUB RESCUE>
That came up after I booted, It wasn't a GUI, just text.

---

### Post by muteXe on 2012-04-11
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Future Warthog on 2012-04-11
Ok, this works, but I don't have the XP install disk.
Gulp.

---

### Post by anewguy on 2012-04-11
This is a common mistake in the sequence of uninstalling ubuntu.


Here are some steps that will cure this:

(1) Reinstall Ubuntu

(2) Reboot and go into Windows

(3) go to [www.downloads.com](www.downloads.com), or just search the net, and grab the free program mbrfix

(4) while still in Windows, run mbrfix.  You'll need to check the html document that comes with it for the exact syntax as I am on Linux so I don't have access to it right now.

(5) step 4 has modified the MBR so only Windows will boot now.

(6) boot the LiveCD

(7) go to disk utility

(8) remove the ubuntu partitions

(9) reboot - it will be Windows

(10) depending on your version of Windows, you can either use Windows itself or a utility to reclaim the unused space that used to be the ubuntu partitions

Now, for others reading this:

When you installed ubuntu, the MBR was changed such that it tries to load the boot information from your Ubuntu partition. If you dual-boot, that is where the boot menu comes from.  By simply removing the ubuntu partitions, it cannot find that anymore, so it cannot load any OS.  There are many, many posts on this forum and elsewhere for the proper way to do this.  One of the simplest is the above mentioned mbrfix - just steps 3 and 4 above.  Just download it and run it in Windows, and the ubuntu menu no longer shows - you just boot straight to Windows.  It will be up to you what you want to do to reclaim the space used by the ubuntu partitions.  Steps 6 through 10 above are just 1 way.  Please search the forum and/or the net for how to properly remove ubuntu and go back to Windows before you attempt it.

Dave ;)

---

### Post by oldfred on 2012-04-11
If you have a Ubuntu liveCD you do not have to reinstall.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Or you can download this into the Ubuntu liveCD or download as a liveCD.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by anewguy on 2012-04-12
Hey, didn't know you could actually do that off the LiveCD!  You see, considering synaptic isn't installed by default in 11.10, I assumed it wouldn't be there in a session using the LiveCD - hence one would have to edit the sources list manually.  Nice to know - thanks!!

Dave ;)

---

### Post by Future Warthog on 2012-04-12
So, you can install programs while on a live CD?

---

### Post by oldfred on 2012-04-12
I have not booted 11.10 liveCD except to install. You may have to also install synaptic
sudo apt-get install synaptic

Yes you can install to liveCD, but the disadvantage is every time you reboot you have to redown load & reinstall. And you may have to have enough RAM memory or swap, so a lot of larger apps may cause issues.

You can add persistence if using a USB flash drive, that allows you to save your data, but applications are only saved as as the download and I think you are in effect reinstalling each time. With persistence you cannot update system as it still is the liveCD on a USB.

---

