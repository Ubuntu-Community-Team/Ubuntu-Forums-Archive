---
title: "Can Ubuntu be re-installed over an existing installation?"
date: 2017-11-18
forum: New to Ubuntu
---

### Post by sterator on 2017-11-18
the purpose would be to leave documents and hopefully settings in-place; you'd only re-install the system to the "pure" state, same as a nuke and pave.

can this be done?

---

### Post by deadflowr on 2017-11-18
Yes.
If you mean can you reinstall without wiping your Home folder and all your settings in place.
Then yes you can.
Simple method is to choose the option Something else when setting up the where to install Ubuntu in the installation page.
In here find the partition Ubuntu is currently installed on and select it with edit/change.
Then set the file system type, make sure it's the same as it currently is (Ubuntu defaults to ext4, you may need to scroll up in the listings to find it)
Then set / as the mountpoint ( / is the full file system, you will see other listings like /home or /var, ignore those and just set the / if that make sense)

The key though is DO NOT set or check the format option leave that unchecked.
Formatting would overwrite the whole partition, but not formatting only overwrites system files but leaves the files already in the home folder alone.

Second key is you must re-use the same username (s); not sure about same password, but I would simply try reusing the old one and simply change that after the reinstall if need be.
(unless you are trying to reinstall because you think you maybe hacked, in which case nuke everything, don't use this method and start from scratch and rely upon external backups)

This process does take a bit longer to do than a regular install as the installer will burp a lot of warnings about files already existing in home, but you can ignore those. I did.

I've done this twice, out of curiosity, and both times worked as expected.
But I have plenty of nets (erm backups) to fall onto, so for me a failure wasn't going to be a problem.

I would suggest you set up backups, too.

More reading on reinstalling here:
[https://help.ubuntu.com/community/UbuntuReinstallation]("https://help.ubuntu.com/community/UbuntuReinstallation")

Hope it helps

---

### Post by photonxp on 2017-11-18
If one has multiple partitions for the system, then Ubuntu would use system file /etc/fstab to record how to mount these partitions.

Reinstall would rewrite old files such as system file /etc/fstab, so the information needed for mounting the partitions would be lost, so the re-installation would not be proper.

If someone wants to keep the /etc/fstab same as before, the partitions have to be reassigned as before during the installation. That probably means choosing "Something else" for the "Install Type" during installation so the partitions could be assigned as before. 

If Ubuntu could read the /etc/fstab, keep its data, and restore it during the installation, it would be one step closer to a re-installation as required. That might be true someday.

---

### Post by sterator on 2017-11-18
Thank you..good advice, and thanks for the tips/caveats.

---

### Post by sterator on 2017-11-18
Thank you!

---

### Post by DuckHook on 2017-11-18
> **photonxp said:**
> …If Ubuntu could read the /etc/fstab, keep its data, and restore it during the installation, it would be one step closer to a re-installation as required. That might be true someday.
Although it might be a nice-to-have, this would have its dangers. The use of "something else" during the install process is very powerful and allows a person to play around with partitions, which means that partition UUIDs would be changed. For one thing, the swap partition is almost always re-initialized with a different UUID. Inheriting the old fstab would break the system with such partitions.

@sterator

I learned a lot from *deadflowr* and will try out his method on one of my old laptops. But for new users, his caveats need to be taken seriously and this method approached with caution. If one is very comfortable with Linux/'buntu, this shortcut is incredible, but one needs to have a decent understanding of what is going on under the hood.

---

