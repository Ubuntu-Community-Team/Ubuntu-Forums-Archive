---
title: "Reinstalling 20.04"
date: 2020-12-02
forum: New to Ubuntu
---

### Post by terraclast on 2020-12-02
I recently deleted the Ubuntu 20.04 partition from my Win 10 dual boot at a techie friend's suggestion due to not being able to figure out or research out how to install rtl8812au-5.1.5 driver for a Brostrend ac3 WLAN.  I messed up by doing this because I was momentarily stuck in grub. I figured out how to work around it and am back in Windows.  When I first posed that question in the forum I was told I should have asked the community about the install and made my issues worse.  

Well, now I would like to reinstall 20.04 and the original install's bootloader is still on the comp (I have to boot windows through UEFI), and I was wondering if it is safe to just do a normal reinstall from the flash drive or if there is anything I should be aware of and cautious about, like if I should remove the bootloader.  

If I should remove grub, any help would be appreciated seeing that google searches put me in the above mess to begin with. 

I have a couple months with 18.04 in a VM, and no problems there with what I was using it for, but this is the first experience I have with any sort of "permanent" Linux install and I'm realizing the stakes are a fair bit higher.  I'm having to learn a lot more and dive a lot deeper and I'm 100% okay with that.  

Any help would be greatly appreciated.  Thank you in advance.

---

### Post by yancek on 2020-12-03
Dual booting Ubuntu with windows 10 in UEFI mode is explained in detail at the link below, the official Ubuntu documentation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you originally installed Ubuntu in UEFI mode, are you referring to the boot entry in the UEFI BIOS you see on boot?  That can be removed using efibootmgr from Ubuntu.  Will likely be overwritten on the new install of Ubuntu.

---

### Post by terraclast on 2020-12-03
Yes, I am referring to the boot image in the UEFI. I don’t currently have access to Ubuntu because it needs to be reinstalled. I’m wondering if what you said will happen or if bad things can come of reinstalling without removing the boot image first.

---

### Post by CelticWarrior on 2020-12-03
[B]Nothing bad will come out of reinstalling with or without the previous bootloader still residing in the ESP (EFI System Partition).
[/B]
Understanding UEFI, its features, requirements and boot process is something you must make friends with. The link above is a good starting point. A few additional notes about details that may not be as clear as they should in the aforementioned link and specifically from the perspective of a dual- or multi-boot configuration:
[LIST]
[*]Bootloaders are saved/installed in the ESP (EFI System Partition), a small FAT32 formatted partition typically at the beginning of the boot drive with the highest priority (the Ubuntu installer will use a preexisting ESP or, in its absence, create one of ~512MB, more than enough for dozens of concurrently installed OSes)
[*]Properly installed bootloaders in the ESP boot their respective OSes regardless of their system/main partitions residing in the same physical drive or any other.
[*]The ESP in not, typically, user accessible. That space is reserved, forget about it.
[*]"Orphaned" bootloaders do NOT need to be cleaned. Its presence changes nothing, they just don't and can't work if the partition they're pointing to no longer exists. That said, a cleanup is usually recommend as this avoids users' confusion and knowing that usually they have the same exact name ("Ubuntu" and "Ubuntu" should be the result in your case after reinstalling Ubuntu without removing the previous bootloader; the practical implication is one works, the other doesn't)
[*]The boot order is ALWAYS selected in the UEFI settings > Boot menu. Do NOT confuse this with the old, BIOS based, method of selecting drives. Now you have two settings to account for: In one hand you need to assure the drive containing the ESP has the highest priority (this is one settings) and then which OS to actually boot from when more than one is installed (this is a different setting). The second selection is only possible when the first setting is correct and firmware can read from the ESP.
[*]Regardless of the amount of physical drives, systems typically have only one ESP and only one is needed. Some people prefer - and I must stress this isn't a requirement but a very personal preference - to have ESPs also in other drives and copy the contents of the main  one to the others. The only practical advantage of this configuration is the ability to boot at least one or some of the OSes in case of drive failure affecting the ESP in use. In any case NEVER try to put two ESPs in the same physical drive.
[*]The great advantage of UEFI vs old BIOS boot processes is the possibility of booting any installed OS independently at any time (something you already discovered by yourself; with the old BIOS you wouldn't have had any other choice than to boot Windows media and then "repair" the MBR, reinstalling the Windows bootloader instead of Grub
[*]Specifically when dual-booting Windows and Ubuntu we select "Ubuntu" (actually Grub) as the bootloader in UEFI settings > Boot because Grub can, obviously, boot Ubuntu (its main purpose) but also chainload to the Windows bootloader to boot Windows, and allows such selection from a convenient boot menu
[/LIST]

[B]In conclusion, just reinstall. Cleaning up the old bootloader isn't important but you can do that later.
[/B]
Then, not mentioned in this thread, but I already know that you'll probably need a manually installed driver for WiFi, DO NOT INSTALL ANY DRIVER FROM A CD OR DOWNLOADED FROM A RANDOM WEBSITE! Most of the WiFi chipsets are already supported but not all work OOTB and need proprietary drivers that aren't distributed with the Ubuntu installation media. A small subset of those will need drivers obtained from third-party sources but most can be easily installed via Additional Drivers from the Ubuntu repositories (an alternative temporary internet connection is required. The ones that need drivers from elsewhere usually can be installed with a few commands and yes, also for this cases an alternative internet connection makes it really easy; not having one makes it very hard even for some experienced users let alone newbies.

---

### Post by terraclast on 2020-12-04
After rereading the UEFI link yancek posted above and I suppose I was still confused because there wasn't anything directly addressing a second install on the same HDD. 
I really don't mean to one off as petulant or anything, and if I did I apologize. 
Your additional notes make things as clear as day and I can't think you both enough for the information and the clairity on the topic. 
CelticWarrior, you're absolutely right about my next step being working out the driver install. I have a feeling I'll be learning quite a bit about repositories. I look forward to that. One question I have is how to know how safe a non-standard repository is. In any event, it looks like I'll have to get my hands on a nice long eithernet cable. 
Seriously, thank you both.

---

### Post by tea for one on 2020-12-04
@CelticWarrior

I linked your comments in post 4 to [https://ubuntuforums.org/showthread.php?t=2454668](https://ubuntuforums.org/showthread.php?t=2454668)

I hope that you don't mind ;)

---

### Post by TheFu on 2020-12-04
Why bother running dual boot?  Just keep running inside a virtual machine.  VMs can be tuned to provide over 90% of native performance for almost all workloads that aren't GUI-centric.  I don't have any dual-boot systems. Switched to running other OSes inside a VM around 2007 and never looked back.

I run between 10 and 20 VMs daily, all day, all night, 24/7.  I do shutdown Windows VMs to make image backups of that (there don't seem to be any good Windows backup tools), but my normal 20.04 desktop, running inside a VM:
```
$ uptime
 12:07:37 up 16 days, 13:38,
```

What do you want to do with 20.04?

---

### Post by terraclast on 2020-12-05
I've been having trouble getting VM software to work in Windows, which I think is a product of not looking around in UEFI enough, the HP Z440 really should have more than enough of everything to run a VM or several.  Also, I generally would prefer to have my home OS, so to speak, be Ubuntu or Linux more generally.  However, having an instance of Windows 10 to tool around in is useful.  I've started going back to school for InfoSec due to the pandemic and the lock down it's placed on my prior career and at the current moment I'm using this box as a learning tool with the intention of using it as my home workstation when that time comes.

---

### Post by TheFu on 2020-12-05
I've found HP laptops usually lock down the BIOS access more than I like and often don't follow UEFI standards. In in short, I avoid HP after being personally burned AND after seeing all the issues that people have in our annual Linux "install-fests".  Sometimes, the more expensive laptops don't have the locked down settings, but for laptops under about $450 from vendors like Acer and HP, we see lots of those with BIOS settings needed for virtualization blocked.

I'm at a stage in my career where Win10 will likely never be needed again. If I do need it at work, they will have a remote desktop that I can access.  I haven't personally used any version of Windows since Win7. But for someone just starting out, you'll probably need to hold your nose, agree to the EULA (which is pretty nasty), and move forward.  Or you can use the 90-day trial Win10 and just reinstall as needed. This has the added benefit that you won't end up with too much crap in your Windows install, since you'll either get tired of reinstalling stuff or come up with a more automated method so it isn't nearly so painful.  On Win7, I ended up using ninite packages to patch non-MSFT stuff every week. I vaguely recall that other teams had created something similar.

Some day, MSFT will finally decide to make a solution that comes close to APT for 3rd party patching, updates, installs, but I won't hold my breath.  By the time that actually happens, we'll all be using wrist-top computers which securely connect to video, keyboards, mice, and networks with a quick confirmation when we sit at a desk.  Already, we have desktop computers about the size of a deck of cards that meets the needs for 80% of office workers. Soon, those devices will be on our wrists. with 10G wireless connections for all peripherals.  The changes in the next 10 yrs will be amazing. Just think how wifi changed LAN computing.  That is going to happen with wireless USB soon.

---

### Post by terraclast on 2020-12-05
WIRELESS USB!?!? WUT??? For some weird reason that makes me giddy.  

This particular box is a desktop.  Though, I'm sure it's not really different from the laptops you're talking about.  And yeah, not super stoked to be giving MS so much free reign over my info, but they are, at least currently, the main focus of what I'm learning in my A+ core 2 class.  I'd love to just stick to Linux and OSX.

---

