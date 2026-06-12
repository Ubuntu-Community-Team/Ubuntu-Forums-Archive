---
title: "Installation of Ubuntu 14.04 fails"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by la.khan on 2014-06-21
Hi all,

I have Dell Inspiron 1525 with Win XP SP3 and I am trying to have a dual boot OS with Win XP & Ubuntu Linux 14.04. I am a newbie with Linux and need help with UL14.04 installation.

I have downloaded ubuntu-14.04-desktop-i386.iso from [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/) and burnt onto a DVD. I inserted this DVD in my CD/DVD drive, change the boot sequence priority to CD/DVD drive (instead of internal HDD), save my settings, exit setup,the machine tries to access the CD/DVD drive and then Win XP starts up. Any idea why Ubuntu doesn't begin installation? What am I missing? Do I need to open the ISO file using 7Zip appln & burn the contents on to a DVD and then use this new DVD to boot up my laptop for Ubuntu installation?

Since my laptop doesn't begin installation, I let it boot into Win XP, used 7Zip appln to browse the contents of ubuntu-14.04-desktop-i386.iso file. I see that this has wubi.exe (Windows based Ubuntu installer). I copy the ISO file from the DVD to my HDD, open the ISO file to double click wubi.exe (as per [http://www.techsupportalert.com/content/easy-way-install-ubuntu-within-windows.htm](http://www.techsupportalert.com/content/easy-way-install-ubuntu-within-windows.htm)). I see Ubuntu starts installation and then fails as it is unable to find a folder.

---------------------------
Ubuntu Installer
---------------------------
An error occurred:

No such file or directory

For more information, please see the log file: c:\docume~1\support\locals~1\temp\wubi-14.04-rev286.log
---------------------------
OK   
---------------------------

When I click OK, installation terminates. I looked at the above log file and I see the following:

06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-21 17:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-21 17:34 DEBUG  TaskList: ## Finished create_dir_structure
06-21 17:34 DEBUG  TaskList: ## Running uncompress_target_dir...
06-21 17:34 DEBUG  TaskList: ## Finished uncompress_target_dir
06-21 17:34 DEBUG  TaskList: ## Running create_uninstaller...
06-21 17:34 DEBUG  WindowsBackend: Copying uninstaller C:\DOCUME~1\Support\LOCALS~1\Temp\7zO30B.tmp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-21 17:34 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\Support\\LOCALS~1\\Temp\\7zO30B.tmp\\wubi.exe'

Hardware configuration: Dell Inspiron 1525; Intel Core 2 Duo; T5800 @ 2 GHz; 150GB HDD; 3 GB RAM
OS: Win XP SP3; 32 bit

Please let me know if you need any more info. Any help regarding this is greatly appreciated.

**Note: Sorry for the long post but should this go in the Absolute Beginner Talk forum or the Installation & Upgrades forum?**

---

### Post by Rob Sayer on 2014-06-21
Don't ... do not ... use wubi.  It's been deprecated for some time.  There's lots of info here on this issue, and I don't know why it's there.

Did you do an md5sum checksum on the downloaded iso live CD file?

---

### Post by jdeca57 on 2014-06-21
You most probably burned the iso file as a file to the dvd. That's not the way to go, if you burn it correctly the content of the iso is on the dvd, not an iso file you can look into. It's not difficult to correct, search for xp burn iso and you'll find plenty of explanations.

---

### Post by la.khan on 2014-06-21
> **jdeca57 said:**
> You most probably burned the iso file as a file to the dvd. That's not the way to go, if you burn it correctly the content of the iso is on the dvd, not an iso file you can look into. It's not difficult to correct, search for xp burn iso and you'll find plenty of explanations.

jdeca57,

Yes, I burnt the downloaded ISO file as is to a DVD. As per my understanding, you suggest I need to use an ISO burner (for ex. [http://www.freeisoburner.com](http://www.freeisoburner.com)) to open up the ISO file and burn all folders and/or files to another DVD. This new DVD should be used to boot & install UL 14.04. Did I get you correctly?

Let me try that & get back to you in a few hours :)

---

### Post by Impavidus on 2014-06-21
1: Don't use wubi. It's no longer supported.

2: Burn the iso as an image, not as a file. Afterwards you'll see a bunch of files when you look at the iso, not a single iso file. Every decent dvd burn application has an option to burn an iso as a disk image.

3: Don't unpack the iso file to burn the individual files inside either. The contents will look the same, but the boot code will be lost.

4: Your processor supports 64 bit. With 3GiB memory it doesn't matter too much whether you install 32 or 64 bit Ubuntu. 64 bit is a little faster, but also uses more memory, so you can do slightly less with the same memory.

5: Before installation, use Windows tools to shrink the Windows partition.

---

### Post by la.khan on 2014-06-22
Hi all,

As jdeca57 suggested, I burnt the downloaded ISO file to a DVD using FreeISOBurner. I used this DVD to boot my laptop and UL14.04 installed in 30-40 mins. I now have my laptop with dual boot OS WinXP & UL14.04.

Thanks to users Rob Sayer, jdeca57, Impavidus for your suggestions :)

---

