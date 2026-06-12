---
title: "Grub command line on startup"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by josh82 on 2014-08-30
I've been running a dual boot, Windows 8 / Ubuntu 14.04 install for the past month or so, without any major problems until today. The battery died on me and my computer shut down, and instead of restarting back into the purple, Grub screen where I'd typically elect to run Ubuntu, it now runs right into Windows. First thing I checked was the BIOS, which apparently had no boot information for the Ubuntu installation anymore, because my only option was my Windows installation. I went ahead and booted into a LiveUSB version of Ubuntu, and from there I ran Boot Repair. 

[http://paste.ubuntu.com/8185006/](http://paste.ubuntu.com/8185006/)

Now when I boot, I'm able to see (& select) the Ubuntu options in my BIOS, but I go straight into the Grub command line (just Grub>, not Grub Recovery> FWIW). I ran ls -l & I'm getting a no known file system detected. I wish I would have written those results down because I can't seem to run ls -l anymore, just ls on its own for whatever reason :confused:. Hopefully the above log will provide some relevant information though and someone can provide some assistance without that information. 


If there's any additional information that'll help, please let me know. Thanks for reading & for any help!

---

### Post by yancek on 2014-08-30
The problems and suggestions for repair are at the bottom of the boot repair script you posted.  You seem to have a combination of mbr and efi since you have Grub installed to the mbr of sdb, the drive on which you have Ubuntu but you also have the necessary efi boot files on separate partition, sda1 for both windows and Ubuntu.  Unfortunately, that's the limit of my knowledge on efi booting.  There are a number of members here with more detailed knowledge who have resolved these problems for others so you can wait for someone else to post or try using the Search function at the top of the page to find a solution.

---

### Post by josh82 on 2014-08-30
Thanks for the input. I'm quite certain that I'm not the first one with this specific problem, but I just haven't found the right search string just yet. I've got to run right now, but I'll try and use your input to help guide me towards a solution later this evening, unless someone else comes along first. I don't really have much (almost any) dual boot experience, so this is admittedly a little foreign to me, and with about 9200 lines in the log file, quite frankly, I wasn't even quite sure what I was looking for / where to start. I was primarily looking at errors and warnings, but that seemed to be more or less a fruitless approach towards the solution.

---

### Post by yancek on 2014-08-30
UEFI booting made a lot of changes to the standard methods previously used to boot.  The pertinent information from boot repair is quoted below.  I've never used a uefi machine so can't help with that.

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

You may want to retry after activating the [Backup and rename Windows EFI files] option.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

=================== Default settings
Recommended-Repair
This setting would purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sdb1, using the following options: upgrade-grub       sdb5/usr, sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.


---

### Post by grahammechanical on 2014-08-30
What happens if you change the UEFI boot priority to boot into sdb? Do you get a Grub boot menu that offers both Windows and Ubuntu?

You are getting to a Grub boot menu. You can use recovery mode. It is under the Advanced Options sub-menu. There you can select Grub to update the Grub configuration files. Resume may load you to a desktop using a fall back open source video driver.

I think that you are not getting a Grub rescue prompt because you are actually getting a Linux command line prompt. Are there any error messages just prior to getting the prompt?

By the way, you should produce another Boot Repair log because Boot Repair may have changed the situation.

Regards.

---

### Post by josh82 on 2014-08-30
Looks like I've got it now. The quote below got me prodding around a bit:

> **yancek said:**
> UEFI booting made a lot of changes to the standard methods previously used to boot.  The pertinent information from boot repair is quoted below.  I've never used a uefi machine so can't help with that.

I don't recall making any changes regarding UEFI settings, but I may well have at one point or another last night. Anyways, all I ended up doing was disabling the UEFI and booting with Legacy instead and it worked like a charm. The log actually indicated that now that I look in line 734.

---

### Post by josh82 on 2014-08-30
Grahah - got this thing figured out but I figured I should reply anyways since you did take some time out to try and give me a hand, which I greatly appreciate.

> **grahammechanical said:**
> What happens if you change the UEFI boot priority to boot into sdb? Do you get a Grub boot menu that offers both Windows and Ubuntu?

I didn't get an SDB option per say, but I did get a Ubuntu option. Interestingly (to me at least), I was getting 2 Ubuntu options that were seemingly identical boot options. Neither worked FWIW.

> **grahammechanical said:**
> 
You are getting to a Grub boot menu. You can use recovery mode. It is under the Advanced Options sub-menu. There you can select Grub to update the Grub configuration files. Resume may load you to a desktop using a fall back open source video driver.

I was, before the problem started (and now that it's fixed), getting a Grub boot menu, where I'd be able to enter into recovery mode. However, all I was getting when it was in UEFI mode was a Grub prompt; nothing but a command line - and it didn't really even seem to allow me to do anything as only a select number of the commands seemed to work. It was having problems accessing something I suspect, but not familiar enough to identify that precisely. 

> **grahammechanical said:**
> 
Are there any error messages just prior to getting the prompt?

Yes and no - sometimes I'd see some mount errors flash across right before the prompt, but most starts it'd just go straight to the prompt. Odd to me, but whatever.

> **grahammechanical said:**
> 
By the way, you should produce another Boot Repair log because Boot Repair may have changed the situation.


I know that log wasn't created during the repair, but it was actually done just before I posted. I'm not sure if that's good practice or not. I actually had a log generated when the repair was actually made as well, but I just wanted to make sure I hadn't changed anything that might have affected the logs since then. 

Anyways, thanks for all your help!

Regards.

---

