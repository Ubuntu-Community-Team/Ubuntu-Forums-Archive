---
title: "No GRUB access after win10 update"
date: 2018-01-15
forum: New to Ubuntu
---

### Post by jonatanlv on 2018-01-15
Hi all,

I have a laptop with both windows 10 and linux (Ubuntu 16).

I use grub to enter one or the other. From time to time, windows makes an update and I lose access to the grub menu. In these cases I run boot-repair and averything gets to normal. But this time it didn't work and I don't know what to do after that. I only used recommended repair.

This is the report from boot-repair:
[http://paste.ubuntu.com/26380466/](http://paste.ubuntu.com/26380466/)

Thank you,

---

### Post by oldfred on 2018-01-15
I believe UEFI specification may allow more than one ESP - efi system partition, we have not seen any system that supports that. You can have two configured, but have to move boot flag back & forth so only one is active at a time.
You have two ESPs.sda2 & sda6.

Remove boot flag from sda6.
Partition sda6 does show Ubuntu boot files, but so does sda2. 
Your fstab was updated from UUID of sda2 to UUID of sda6 to mount the ESP. Not sure why system would ever do that. And your UEFI boot entry changed from using GUID of sda2 to GUID of sda6.
Did you create a second ESP and reinstall grub?

After you remove boot flag from sda6, use Boot-Repair's advanced mode to totally uninstall & reinstall grub. Be sure to boot live installer in UEFI boot mode.

You also should houseclean some of the older kernels.
 [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by Geoffrey_Arndt on 2018-01-15
If these dual-OS's are installed to separate external usb v3 ssd devices (e.g., SanDisk Extreme 500) [https://www.sandisk.com/home/ssd/extreme-500-ssd](https://www.sandisk.com/home/ssd/extreme-500-ssd) does that negate need for multiple efi partitions on the internal hdd/ssd drive?   I know on legacy bios  - - - grub can be targeted to install to those external ssd's, but if the external ssd is pre-formated with an "efi-root-swap" basic partition layout, will that work via use of the boot-time uefi-boot menu (via F12 at bootup for example)??   

OR - if NOT booting windows 8x-10x, the user can change the uefi to legacy bios mode (and still use gpt versus mbr) and then use grub as noted above?   In other words, use Win 7 only, or not use Windows dual-boot at all?

To summarize, is the standard dual-boot setup on one internal disk equal in stability to internal & external dual-boot scenarios as discussed above.??

---

### Post by oldfred on 2018-01-15
@Geoffrey_Arndt 
With UEFI you have to manually partition the external device and include an ESP. 
Whether external is for UEFI or BIOS boot, you can use gpt. I have used gpt on all new drives & larger flash drives since 2010 or before UEFI on PCs.

But full Ubuntu install on external drive in UEFI mode, installs grub into ESP on drive seen as sda, usually internal drive. You then have to copy /EFI/ubuntu twice to ESP on external drive, once to /EFI/ubuntu and once to /EFI/Boot. In /EFI/Boot rename shimx64.efi to bootx64.efi. That is because UEFI only boots external devices from /EFI/Boot/bootx64.efi.

---

### Post by Geoffrey_Arndt on 2018-01-15
Thanks much OldFred for the specifics on the uefi install!   I appreciate it and I'll post this thread into my CherryTree database for future reference.  

IF I still needed Windows, and didn't want to run it inside Ubuntu via VirtualBox (as my low-end laptop (Acer Travelmate B117 has just 4 GiB ram)), then those instructions will come in super-handy.   

But even for the _Original Poster,_ doing this type of dual-boot seems worth the effort because it eliminates the damage Windows updates can do to a dual-boot with Linux on the same drive.   In other words, I would simply remove the external ssd before booting back into Windows.  Seems safer and cleaner - - no more Windows overwriting grub.

---

### Post by jonatanlv on 2018-01-16
Hi Oldfred:

Thank you very much. I will try this afternoon (in a few moments).

> **oldfred said:**
> Did you create a second ESP and reinstall grub?
No, I didn't made sda6 and I don't remember to have 3 windows recovery environment partitions.

---

### Post by jonatanlv on 2018-01-23
Hi all,

It didn't work. I tried the following:
1. Enter with the boot-repair usb.
2. Using gParted, remove the flag: boot from sda6
3. Launch boot-repair (with the purge GRUB option). This is the result: [http://paste.ubuntu.com/26445664/](http://paste.ubuntu.com/26445664/)
4. Reboot the computer and it enters windows directly
5. Enter boot-repair again and perform Recommended repair. This is the result: [http://paste.ubuntu.com/26445731/](http://paste.ubuntu.com/26445731/)

It enters windows as before. Anything else to try?

---

### Post by oldfred on 2018-01-23
If you press f12, can you then boot the ubuntu entry?

You may want to houseclean out the many Boot-Repair logs & boot-sav logs in the ESP.
I might keep an old one and latest or back up all of ESP and then delete the logs.

 [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 

You also should houseclean out old kernels.
       #Current kernel:
uname -a 
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

      I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by jonatanlv on 2018-01-24
> If you press f12, can you then boot the ubuntu entry?
No, I get a menu in which I can select between USB, HDD or ODD. When I select HDD it goes straight to windows.

> [COLOR=Navy]For more info on UEFI boot install & repair - Regularly Updated :[/COLOR]
I will check on it as soon as I can. For the moment, still not working.

> Please use Thread Tools above first post to change to [Solved] when/if answered completely.
Sure!!

Any other idea?

By the way, it seems that the computer model may be relevant, just in case, mine is a Toshiba Satellite P50-B-11L

---

### Post by oldfred on 2018-01-24
The last two are my signature, which may or may not apply.

Menu should be showing Windows Boot Manager & ubuntu as boot options.
Is there a sub menu somewhere?

You can try the work around that Boot-Repair has at the end of the report.
That is using Windows BCD editor to add an Ubuntu boot entry.
Then you start to boot into Windows and Windows will use UEFI's one time reboot to boot into Ubuntu.

You can also try adding a hard drive boot entry to use /EFI/Boot/bootx64.efi. Similar to this:
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not any other entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)
Boot-Repair should have already done the copy. We can add another UEFI boot entry:

From live installer:

 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2 as your ESP

   sudo efibootmgr -c  -l *EFI*ubuntu/shimx64.efi -L "UEFI hard drive" -d /dev/sda -p 2 
See also:
man efibootmgr

But that description may not pass either.
Many vendors now are modifying UEFI to use description as part of boot. That specifically is NOT allowed per UEFI standard.
And only valid description is "Windows Boot Manager".

---

### Post by jonatanlv on 2018-01-27
Hi again:

Finally, the only thing that worked was this one:

> You can also try adding a hard drive boot entry to use /EFI/Boot/bootx64.efi. Similar to this:
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not any other entry
[http://ubuntuforums.org/showthread.p...0#post12884470]("http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470")

For the record:
[LIST]
[*]There was no submenus when hitting F12
[*]The efibootmgr command you told me didn't seem to work
[*]The bcdedit commad didn't work neither
[/LIST]

Now I have the grub menu back (yahoo!!!).

Thank you for your time/patience/expertise...

---

