---
title: "How to backup everything from within Ubuntu"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by Skippy3E on 2012-05-13
I just installed 64-bit Ubuntu 12.04 using the Wubi installer from within Windows 7 64-bit, and want to be able to backup all my windows and ubuntu files from within ubuntu. I need everything backed-up, including my windows programs etc. and be able to recover everything relatively quickly if my computer dies. How can I do this, and are there any programs other than the default one you'd recommend?

Thanks,
Skippy

---

### Post by wilee-nilee on 2012-05-13
Full backups in a wubi are not practical in my opinion, I would back up home with grsync is all. Wubi is a file in windows.

A full installation in a partition of ubuntu, and windows can be cloned easily with the bootloader attached, a whole HD or by partitions I use this. A clone of windows with wubi though would retain both.

clonezilla.org

This does not exactly answer your questions so feel free to disregard. :)

---

### Post by coffeecat on 2012-05-13
If you want to backup your Windows applications, you'd also need to backup your Windows registry and I doubt there's a way of doing that from inside a wubi Ubuntu installation. I think your answer would be to use a Windows imaging application from within Windows. Since your Ubuntu installation is contained as a pseudo-partition in a single file in the Windows filesystem, that would get backed up in its entirety along with the rest.

Acronis TrueImage or Norton Ghost should be OK for this, or if you want something free (as in beer, not open source) then have a look at the free version of Macrium Reflect. I've used it myself and can recommend it. You create the image from a running Windows, which backups up everything, and if you need to restore the image to a new hard drive you simply boot from a live CD that you've previously created from Macrium.

Word of caution. That would only work to restore your system if you need to replace a failed hard drive. If the whole computer dies, then you have a problem. Restoring a Windows image to a completely different set of hardware will cause Windows to complain. At the very least it will require re-activation and if your Windows is a pre-installed OEM version, that would be against the MS EULA and you would get short shrift from the Microsoft support people.

---

### Post by Skippy3E on 2012-05-14
Thanks for you help :) I can see that it wouldn't be very practical and I don't like having my ubuntu installed through wubi, so would moving my ubuntu to a proper partition using this method: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) be a better option?
And if I did do that, what would I have to do from within ubuntu to backup all my windows and ubuntu files like I said before?Z

Thanks,
Jack

---

### Post by forrestcupp on 2012-05-14
> **Skippy3E said:**
> Thanks for you help :) I can see that it wouldn't be very practical and I don't like having my ubuntu installed through wubi, so would moving my ubuntu to a proper partition using this method: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) be a better option?
And if I did do that, what would I have to do from within ubuntu to backup all my windows and ubuntu files like I said before?Z

Thanks,
Jack

Yes, but you would want to back up all of your important files before you do that, just in case. :)

After you have a proper Ubuntu installation, your Windows partition will show up in the file system. Ubuntu can read your Windows drive, and you can access your files. So you could then use any Linux backup app to set it up to backup anything you want. Ubuntu comes with Deja-dup preinstalled. It's just called Backup in the menus. I use a different backup app called LuckyBackup. I like it better because it's a 1:1 backup that I can actually access the files from my external HD.

Also, if you had a real Ubuntu installation outside of Windows, it would be a lot safer to use something like Clonezilla than it would be from a Wubi installed Ubuntu. But no matter what, you'll want to copy all your important files over to an external or something, just in case you bork your system.

---

### Post by Mark Phelps on 2012-05-14
To, as you stated "recover everything quickly", at least in MS Windows, you do NOT want to do a file-based backup, regardless of what tool you use.

Windows apps use the registry, and file backup tools will not to a complete job of backing that up.

In addition, there are hidden files and directories that must be in place for Windows to boot and to run -- and once again, file-based backups will likely NOT see these.

What you need to do to be able to recovery MS Windows quickly is to do image backups of the Windows partition -- and that can be done for free, inside Windows, using Macrium Reflect.  Just go to their website, download and install the free version, and use it to make backups.  Also use the option to create and burn the Linux Boot CD.  That will allow you to boot from that to do Windows restores.

---

