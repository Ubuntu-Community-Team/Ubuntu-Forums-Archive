---
title: "Update from update manager to Gusty?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-06-17
If I update from the update manager to Gusty Gibbon (7.10) will I loose any of my files or programs?

---

### Post by cotcot on 2008-06-17
The idea of an upgrade is not to loose your files or programs. Nevertheless please back up your files before upgrade. You have to do this anyway, also when you do not upgrade.

---

### Post by redfox1160 on 2008-06-17
> **cotcot said:**
> The idea of an upgrade is not to loose your files or programs. Nevertheless please back up your files before upgrade. You have to do this anyway, also when you do not upgrade.

So when I go to update, it will automatically backup my files?

---

### Post by avtolle on 2008-06-17
If you have any third-party applications installed, you will lose them IIRC. Backups should always be done when upgrading, whether via the upgrade manager or by fresh installation.

---

### Post by Dzenhax on 2008-06-17
I've upgraded with each new release from DD through HH.  Generally you don't loose much, but a word of warning is that when you are asked if you want to keep your custom files or replace them, pick keep.

The first time when I didn't have much experience with it, I chose replace, thinking I was getting something newer, or cleaning up my poor configurations.  The result was that I had to reconfigure everything.

That was a good experience too, since I needed OS practice, but I don't recommend it.

---

### Post by redfox1160 on 2008-06-17
> **Dzenhax said:**
> I've upgraded with each new release from DD through HH.  Generally you don't loose much, but a word of warning is that when you are asked if you want to keep your custom files or replace them, pick keep.

The first time when I didn't have much experience with it, I chose replace, thinking I was getting something newer, or cleaning up my poor configurations.  The result was that I had to reconfigure everything.

That was a good experience too, since I needed OS practice, but I don't recommend it.

Do I need to download a program to back up my files?

---

### Post by Captain_Riker on 2008-06-17
Hello there,

First: No. You will not loose your data. Nor will an update delete/remove/overwrite your data. It will not (except maybe for third party Software) alter your settings, i.e. Firefox settings.

No, the update manager will not Backup your Data. This should be done manually. Use an external Harddrive, for instance, to save your data(simply copy it). Here is why:

As I said, the update will not delete your files or overwrite your Settings. It might happen though, that certain software will be removed, out of incompatibility. In 98% of all packages these are Packages that you as a regular user might mot ebven been aware of an can easily be removed.

But updating your System could end up in an corrupted  System. I.e. a Hardware incompatibility with the Kernel. Your Data is still there, but you (please do not take offense in this ) as a Desktop User might not be able to retrieve the data via rescue tools and command line.

But don't be afraid. ;-)

Just Backup your Data to be sure and then go on . . . it will certainly work like a charm . . . :D

---

### Post by redfox1160 on 2008-06-17
> **Captain_Riker said:**
> Hello there,

First: No. You will not loose your data. Nor will an update delete/remove/overwrite your data. It will not (except maybe for third party Software) alter your settings, i.e. Firefox settings.

No, the update manager will not Backup your Data. This should be done manually. Use an external Harddrive, for instance, to save your data(simply copy it). Here is why:

As I said, the update will not delete your files or overwrite your Settings. It might happen though, that certain software will be removed, out of incompatibility. In 98% of all packages these are Packages that you as a regular user might mot ebven been aware of an can easily be removed.

But updating your System could end up in an corrupted  System. I.e. a Hardware incompatibility with the Kernel. Your Data is still there, but you (please do not take offense in this ) as a Desktop User might not be able to retrieve the data via rescue tools and command line.

But don't be afraid. ;-)

Just Backup your Data to be sure and then go on . . . it will certainly work like a charm . . . :D

thanks

---

### Post by gameryoshi600 on 2008-06-17
If you upgrade from the update manager (which is called a dist. Upgrade) it will keep your settings but clean up some applications that the new ones included replace, etc. I recommend you back up your files first just in case even though it will keep them.

---

### Post by Dzenhax on 2008-06-21
> **redfox1160 said:**
> Do I need to download a program to back up my files?

Sorry to answer so late.  The easist way to backup your files is just to copy them to an external hard drive.  If you are worried about making an exact copy of the system in case it totally crashes, still use the external hard drive.

You'll get a hundred answers about the best way to backup your hard drive, but I've found the easiest for me is to boot up with the live CD and run the command dd in a terminal.

That will take reading the man page for dd. Other backup solutions can be found here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Hope that helps.

---

