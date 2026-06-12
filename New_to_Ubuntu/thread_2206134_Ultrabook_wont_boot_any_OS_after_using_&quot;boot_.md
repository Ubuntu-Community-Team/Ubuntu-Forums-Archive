---
title: "Ultrabook wont boot any OS after using &quot;boot repair&quot;"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-02-17
Hi,

I just installed 12.04 along side windows 8.1 on my ultrabook, installation went well as far as I can tell, but when i tried to boot the pc there was no GRUB menu and it booted directly into windows.

I ran Boot repair from the live USB of 12.04, I did the "recommended repair" and a message came up saying:

"buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI Flies]? (if any choice fails, please retry with the other)" 

the two options were "yes" and "no"

so first I pressed "no" and it said "boot successfully repaired" and asked me to note down the following URL incase it didn't work:
[http://paste.ubuntu.com/6950034/](http://paste.ubuntu.com/6950034/)

I then rebooted and the same problem occured, the pc booted straight into windows with no GRUB menu.

So as the program had advised, I booted back into the live USB and ran Boot repair again but this time when the same message about buggy kernel came up I pressed the "no"  option instead.

this time the URL I was asked to write down was:
[http://paste.ubuntu.com/6950090/](http://paste.ubuntu.com/6950090/)

when I rebooted the pc again there was no GRUB menu but this time after the toshiba logo popped up for a second the screen went black and in the top left it said:

"Insert system disk in drive.
Press any key when ready...."

I tried pressing any key but the same message kept popping up

the last thing I tried was running Boot repair again and this time pressing "No" like i did the first time, the URL that I was asked to write down this time was:
[http://paste.ubuntu.com/6950137/](http://paste.ubuntu.com/6950137/)

but again after rebooting the same message popped up:

"Insert system disk in drive.
Press any key when ready...."

Now I'm left with a £610 paperweight :(

please can someone kindly advise what I should do next?

Thanks in advance!

---

### Post by oldfred on 2014-02-17
Better to use 12.04.4 with the very new systems. But see Caution in link in my signature if you try re-installing. You cannot use any auto reinstall options.

Also the 'buggy' UEFI is for those UEFI systems that have modified UEFI to only boot Windows. Then Boot-Repair has to rename the Windows boot file and make grub/shim be the Windows file so it boots to grub menu. And then from grub menu you can boot the renamed Windows file. But then cannot boot Windows directly from UEFI.
Best not to rename unless confirmed that boot issue is not the buggy UEFI issue.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

You show some Intel SRT info, but that normally is an Ultrabook with a small SSD. And that either causes install issues or grub install issues.

Can you boot this entry? It will just say ubuntu in UEFI menu.

 Boot0003* ubuntu    HD(2,e1800,82000,1b495f04-b709-11e2-ad1d-ca2528ae576c)File(EFIubuntushimx64.efi)

You show the signed kernels and grub2's shim which are the versions with the Microsoft signing key to boot with secure boot on. But often better not to have secure boot on. 
Did you turn off fast boot or the always on hibernation in Windows? That can cause major issues with dual booting.

What brand & model paperweight is this? Some work well, some have issues but work arounds. 
A few will only boot Ubuntu in BIOS mode and Windows in UEFI mode.

And a couple of early UEFI configuration systems did become paperweights and had to be returned to vendor. It turned out to not just be a Linux issue as Windows also could convert system to paperweight.

---

### Post by LinuxVirgin2000 on 2014-02-17
Hi,

thank you so much for replying so quick! I appreciate it.

I should explain I am a newby at all this kind of stuff, I Don't fully understand everything. Could you very kindly explain to me in laymans terms what my next step would be to try and get windows back? 

with regards to the questions you asked:

I did try and look for a way to turn Intel SRT off but there was no GUI for it on my laptop for some reason so i couldn't turn it off,

sorry i don't know what you mean when you say "boot this entry"

i turned of "fast start up" in windows power options, but there was no option to turn off "Quick boot/ Fast boot" in my BIOS settings. there was something in the BIOS called intell rapid start tecnology (or something like that) which i disabled, and I also disabled "secure boot"

My paperweight/ultrabook is a toshiba satellite U920T-10Q

i'm downloading 12.04.4 now as we speak so that "next time" I can try installing with that instead, that is of coarse if there ever is a next time!

---

### Post by oldfred on 2014-02-17
Undo the rename that Boot-Repair did first.
Then you should be able to directly boot Windows from UEFI menu.
Try with both secure boot on and off.
And see if ubuntu entry works after you have undone the rename. Again with secure boot on or off.

I swear every user that posts has a different model. But some vendors are reasonalby consistent with similar models, just implementing added features. 

Some of these may have added suggestions. Some have found odd settings in UEFI/BIOS that do not seem related make a difference.

       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

    
This was a Dell but mentions a common Intel issue.
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

    
> Since these are Haswell systems, if you're running Ubuntu, you'll want to run Ubuntu 13.10--at least until Ubuntu 12.04.4 is released in January. Ubuntu 12.04.3  and 13.04 don't have support for the Haswell Intel Wireless chipset in  these systems. Depending on which configuration you have, you may need  to specify the nomodeset boot option if you're going with Ubuntu 12.04.3  or 13.04. 

 Running in legacy BIOS mode or in UEFI mode both work, but for  now you'll need to enable "Legacy Option ROM" in the BIOS if you're  running in UEFI mode because of the display's backlight. This is because  of an issue with the Intel i915 driver that currently affects several  systems from many vendors. If you don't enable this BIOS option, the  backlight will be stuck at the lowest setting in Linux.


---

### Post by LinuxVirgin2000 on 2014-02-17
Great thanks for the info,

How exactly do I go about undoing the re name? that's what I was trying to do when I ran boot repair again the 3rd time around and pressed "no" instead of "yes" but it didn't make a difference.

---

### Post by oldfred on 2014-02-17
To undo & to rename files to their original names, you just  need to tick the "Restore EFI backups" option of Boot-Repair.

Then see where we are.

---

### Post by SuperFreak on 2014-02-17
I had similar problems. I think Old Fred's advice should work and you will find "Restore EFI backups" in the advanced settings of Boot Repair I believe

---

### Post by LinuxVirgin2000 on 2014-02-17
YAY!!!!!

ok that worked, my paperweight now has windows again! so in other words its still useless:lolflag:

what should be my next step be to try and get the installed ubuntu to boot? should I remove the current install and replace it with 12.04.4? or will this not really help?

thanks so much for all the help so far :)

---

### Post by oldfred on 2014-02-17
There have been a lot of improvements in n13.10, 12.04.4 and a few really adventuresome folks even are using 14.04.
Is UEFI/BIOS the most current version, as vendors also are having to make many improvements also.

But if re-installing there is a bug where any of the auto install options may erase drive. Best to only use Something else and choose same /  (root) as new / and ext4 as format. Same if you had separate /home, but maybe NOT format if you had anything in it, and it should find existing swap.

Have you tried booting ubuntu entry from UEFI menu? You must have fast boot off in Windows and/or UEFI. 
And can try with secure boot on or off.
There is another bug with Windows 8.1 where grub will not boot it with secure boot on from grub menu. But UEFI menu should work.

---

### Post by LinuxVirgin2000 on 2014-02-19
Hi,

So I re installed ubuntu but this time i used the 12.04.4 iso. Installation went well  I think but still having the same problem, No GRUB menu just boots straight into windows, Obviously theres no point using the boot repair tool after what happened last time.

I had a look in the UEFI menu, there is no option to boot into ubuntu

What should I do next to try and get the GRUB menu to show up?

---

### Post by SuperFreak on 2014-02-19
What happens if you press the right shift button after post but before Ubuntu comes on?

will only work if  the value GRUB_HIDDEN_TIMEOUT in the file /etc/default/grub has to be set to a value greater than 0

---

### Post by oldfred on 2014-02-19
Do you have secure boot on, and installed Ubuntu without secure boot?
If secure boot is on, only secure boot systems will boot.
Did you install Ubuntu in UEFI mode?

You should have an ubuntu entry in UEFI.
 # from live CD and use efibootmgr
sudo efibootmgr -v


Some have to add the entry with Windows.
       UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by LinuxVirgin2000 on 2014-02-19
thanks for the replys!
@Superfreak i'm not sure what you mean?

@old fred
yes ubuntu was installed in efi mode,

secure boot is off
fast boot is off

Im afraid i dont understand the rest of the info you posted, could you explain in laymans terms what should be my next step?

Thankyou :)

---

### Post by oldfred on 2014-02-19
From live installer, does efibootmgr show an ubuntu entry?

And follow link for more detail as I have never edited a BCD. But you have to add an ubuntu entry to the Windows BCD.

---

### Post by LinuxVirgin2000 on 2014-02-19
Hi Oldfred

Just an update, Even though I said in the last post that i was not going to try boot repair due to the problems it caused the first time, I tried did just try it again now with the new 12.04.4 that i just installed and it actually worked! Thanks so much for all your help, your a star, could not have done it without your help!

---

