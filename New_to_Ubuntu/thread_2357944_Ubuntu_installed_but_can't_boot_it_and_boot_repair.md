---
title: "Ubuntu installed but can't boot it and boot repair didn't help"
date: 2017-04-07
forum: New to Ubuntu
---

### Post by ardydo on 2017-04-07
Hello!

I wanted to try linux for a long time and since I had some free time today and had been reading about it for some time, I decided to give it a go.

This is probably something easy to fix but I really have had no luck. I've installed ubuntu on my computer using ubuntu minimal and everything seemed okay but I just can't boot it. Apparently grub isn't working or something. I've tried boot-repair too but haven't had any luck. I've also tried searching all around for help about it but also had no luck and after a while I think that it would be better to just post the log of boot repair somewhere and see if someone is whiling to help me.

[http://paste.ubuntu.com/24336126/](http://paste.ubuntu.com/24336126/)

Sorry in advance if this is something easily solvable, but being new to anything linux related, I really couldn't find a way to fix it (I'm at it for 3 hours already). Any help will be greatly appreciated.

---

### Post by oldfred on 2017-04-07
What brand/model system?
And what video card/chip?

You are showing two ESP, sda2 & sda8. Your sda8 cannot be an ESP as it is ext4 formatted.
The ESP is the efi system partition and must be FAT32 with boot flag. Not other partition with gpt partitioning is to have boot flag. And grub does not use boot flag at all with either BIOS or UEFI installs.

You also show a bios_grub partition for BIOS boot. With UEFI boot you do not need that partition.

So remove boot flag from sda8. And rerun in UEFI mode Boot-Repair.
But you show old date on Boot-Repair. Better to use Ubuntu live installer and add Boot-Repair to it, so you have newest version.

Use second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ardydo on 2017-04-09
I'm using an "acer e1 572 6 br648" and the graphics card is an intel integrated cards.

I've tried running the boot-repair tool though the ubuntu USB boot (the same method I used to install it) and it gave me this [http://paste2.org/5ewmIPEm](http://paste2.org/5ewmIPEm). I don't really understand most of it but I can see it gave a lot of errors but more importantly, it didn't really change anything and bcdedit is saying it's not a valid command.

Some additional info.
sd1-3 I have no idea of what they are really. My guess is that they are some manufacturer stuff but I don't really know.
sd4 is the main windows partition and sd5 is another partition I've made to store misc data.
sd6 I also have no idea what it is. It was made after my misc partition? what?
sd7 is the bios boot that you said I didn't need so I should get rid of it?
sd8 and 9 are linux things.

I  don't really understand about UEFI and BIOS boot. The thing I know is  that I really can't boot anything else whitout turning EFI boot on the  BIOS because it won't let me turn off secure boot to choose anything  else.

I'm also tempted to just format everything and reinstall windows and them ubuntu to see how it works out but I'm kinda worried that I'll end up ruining everything (cuz notebook). Would I be able to just format (running gparted or something) sd6-9 and reinstall ubuntu safely?

---

### Post by oldfred on 2017-04-09
With Acer there is a unique requirement of setting UEFI supervisory password (never lose that or reset after configuration) and enable "trust" from within UEFI of Ubuntu/grub's .efi boot files.

Some older threads mention downgrading UEFI, but newer ones say newest works, so be sure to update UEFI to newest version from Acer.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by Paddy Landau on 2017-04-09
Welcome to the forums, ardydo.

Let's see if we can get your system up and running again without losing your Windows setup.

Before we go any further, do you have backups? Whenever you install a system, you can (as you unfortunately found out) get errors that potentially lose data. If you don't have any backups, what I suggest is this:
[LIST=1]
[*]Boot from your Live CD (or Live USB).
[*]Use the File Manager (it's called Nautilus) to locate your files on your Windows system. It looks as though you have two separate data partitions ("drives" in Windows-speak), which should be automatically available in your File Manager.
[*]Copy your data to a safe place, which would be an external USB drive if you have one.
[/LIST]
You can continue without making a backup, but of course there is always the chance of losing your data.

I shall have a good look at your pastebins to figure out what's happening on your system, and then I'll post again.

---

### Post by Paddy Landau on 2017-04-09
This will take more than one post to fix.

First: For clarification, here is your setup with a few comments.

[TABLE="class: outer_border, width: 100%, align: left"]
[TR]
[TD]**Partition**[/TD]
[TD]**Size (GiB)**[/TD]
[TD]**File system**[/TD]
[TD]**Purpose**[/TD]
[TD]**Comments**[/TD]
[/TR]
[TR]
[TD]sda1[/TD]
[TD]0.4[/TD]
[TD]NTFS[/TD]
[TD]Windows Recovery Environment[/TD]
[TD]For Windows[/TD]
[/TR]
[TR]
[TD]sda2[/TD]
[TD]0.3[/TD]
[TD]FAT32[/TD]
[TD]EFI System Partition[/TD]
[TD]For Secure Boot (aka UEFI)[/TD]
[/TR]
[TR]
[TD]sda3[/TD]
[TD]0.128[/TD]
[TD]FAT32[/TD]
[TD]MS Reserved Partition[/TD]
[TD]For Windows[/TD]
[/TR]
[TR]
[TD]sda4[/TD]
[TD]214[/TD]
[TD]NTFS[/TD]
[TD]Data Partition[/TD]
[TD]For Windows[/TD]
[/TR]
[TR]
[TD]sda5[/TD]
[TD]150[/TD]
[TD]NTFS[/TD]
[TD]Data Partition[/TD]
[TD]For Windows[/TD]
[/TR]
[TR]
[TD]sda6[/TD]
[TD]17[/TD]
[TD]NTFS[/TD]
[TD]Windows Recovery Environment[/TD]
[TD]For Windows[/TD]
[/TR]
[TR]
[TD]sda7[/TD]
[TD]0.001[/TD]
[TD]?[/TD]
[TD]BIOS Boot Partition[/TD]
[TD]Way too small, and seems corrupt[/TD]
[/TR]
[TR]
[TD]sda8[/TD]
[TD]80[/TD]
[TD]ext4[/TD]
[TD]EFI System Partition[/TD]
[TD]Invalid duplicate, and wrong format; probably intended to be Ubuntu[/TD]
[/TR]
[TR]
[TD]sda9[/TD]
[TD]4[/TD]
[TD]swap[/TD]
[TD]Swap partition[/TD]
[TD]Valid swap partition for Linux[/TD]
[/TR]
[/TABLE]

As you can see, Windows looks as though it is still in proper working order. However, there are two questions:
[LIST]
[*]Why are there two Windows data partitions ([FONT=lucida console]sda4[/FONT] and [FONT=lucida console]sda5[/FONT])? This might just be one of those things that some OEMs do, though why they do it is a complete mystery to me.
[*]Why are there two Windows Recovery Environments ([FONT=lucida console]sda1[/FONT] and [FONT=lucida console]sda6[/FONT])?
[/LIST]
I don't think that [FONT=lucida console]sda6[/FONT] is required, but for safety's sake, we should investigate further.

The Ubuntu installation, on the other hand, looks quite bizarre. A boot partition that is completely the wrong size; and Ubuntu itself (I think) that seems to be mislabelled as an ESP (EFI System Partition). The swap is the only thing that looks right!

Please would you:
[LIST=1]
[*]Boot from a Live CD (or Live USB, whichever one you have).
[*]Open a terminal (press [FONT=lucida console]Ctrl[/FONT]+[FONT=lucida console]Alt[/FONT]+[FONT=lucida console]T[/FONT]).
[*]Enter (that is, type and then press the [FONT=lucida console]Enter[/FONT] key) the following command, and post the response here. Don't worry about the occasional typo when giving me the response, because I only need a rough idea of what's there, but make sure that you type the command correctly. (If there is anything confidential in the output, just replace the confidential details with asterisks.) Notice that we use forward slashes instead of Windows-style backslashes.
```
sudo mount /dev/sda2 /mnt; ls /mnt; sudo umount /mnt
```
[*]Now use your up-arrow to display the command again; use your left-arrow to go to the digit 2; rub it out; and replace it with 4. So, this time you enter this command:
```
sudo mount /dev/sda4 /mnt; ls /mnt; sudo umount /mnt
```
You'll notice that it's exactly the same command except that it has [FONT=lucida console]sda4[/FONT] instead of [FONT=lucida console]sda2[/FONT]. Remember to post the results.
[*]Repeat with [FONT=lucida console]sda5[/FONT] and [FONT=lucida console]sda6[/FONT]. Don't bother about [FONT=lucida console]sda1[/FONT], [FONT=lucida console]sda3[/FONT], [FONT=lucida console]sda7[/FONT], [FONT=lucida console]sda8[/FONT] and [FONT=lucida console]sda9[/FONT].
[/LIST]
Once I get your responses, I'll have a better idea of how to proceed. I think that I already know, but I need to be sure that you don't mess up anything important.

---

### Post by ardydo on 2017-04-10
> **oldfred said:**
> With Acer there is a unique requirement of setting UEFI supervisory password (never lose that or reset after configuration) and enable "trust" from within UEFI of Ubuntu/grub's .efi boot files.

Some older threads mention downgrading UEFI, but newer ones say newest works, so be sure to update UEFI to newest version from Acer.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

Oh boy. I went through the first post and it worked like a charm! I had no idea acer notebooks needed some different thing and I'm really, really glad places like this forum exists where I can get help. Thank you very very much! I think that the post can be marked as solved (by me?) even thought I still have some doubts

> **Paddy Landau said:**
> 
[LIST]
[*]Why are there two Windows data partitions ([FONT=lucida console]sda4[/FONT] and [FONT=lucida console]sda5[/FONT])? This might just be one of those things that some OEMs do, though why they do it is a complete mystery to me. 
[*]Why are there two Windows Recovery Environments ([FONT=lucida console]sda1[/FONT] and [FONT=lucida console]sda6[/FONT])? 
[/LIST]
I don't think that [FONT=lucida console]sda6[/FONT] is required, but for safety's sake, we should investigate further.



I went ahead and did what you said. sd4 is the main windows installation and sda5 is a partition that I had created myself some time ago to store things and when mounted, displayed the files they should be displaying.

sda2 spits out only a file, BOOTSECT.BAK as seem [here]("https://www.dropbox.com/s/46lmj6u42j7jfhy/Screenshot%20from%202017-04-10%2013-55-02.png?dl=0")

sda6 on the other hand I can't really figure it out. [here ]("https://www.dropbox.com/s/xves06gagq4k4mn/Screenshot%20from%202017-04-10%2017-07-49.png?dl=0")is what it gave out

---

### Post by oldfred on 2017-04-10
Windows & vendor have a variety of partitions.
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 

With my Dell, when I made a Windows repair/recovery, it asked it I wanted to delete that partition.
And then when I made a Dell recovery flash drive, it asked it I wanted to remove that. 
Neither were large so I did not delete either, but since upgrade from Windows 8 to Windows 10, I doubt if either is worth anything unless I want to attempt to restore to as purchased.

---

### Post by Paddy Landau on 2017-04-10
> **ardydo said:**
> I went through the first post and it worked like a charm!
Does that mean that your system is working now?

> **ardydo said:**
> I had no idea acer notebooks needed some different thing…
OEMs often don't adhere to standards, unfortunately, which is a great pity.

> **ardydo said:**
> I'm really, really glad places like this forum exists where I can get help.
Yes, Ubuntu Forums is my favourite forum because of the friendliness and help.

> **ardydo said:**
> I went ahead and did what you said.
Ha ha — I see that I missed out a bit of the command! :redface: Fortunately, it wasn't an important part, but for completeness I've edited that post to put in the missing bit.

> **ardydo said:**
> sd4 is the main windows installation…
sda5 is a partition that I had created myself…
sda2 spits out only a file, BOOTSECT.BAK as seem [here]("https://www.dropbox.com/s/46lmj6u42j7jfhy/Screenshot%20from%202017-04-10%2013-55-02.png?dl=0")…
sda6 … [here ]("https://www.dropbox.com/s/xves06gagq4k4mn/Screenshot%20from%202017-04-10%2017-07-49.png?dl=0")is what it gave out
Excellent. That confirms what I thought about the system, except for sda5, which I now know what it is.

So, what I need to know now is this: Is your system working after oldfred's advice, or do you still need help? Please be specific if you need help.

---

