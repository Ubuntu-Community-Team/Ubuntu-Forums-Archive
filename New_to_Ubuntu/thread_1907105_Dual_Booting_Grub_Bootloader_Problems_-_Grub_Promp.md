---
title: "Dual Booting Grub Bootloader Problems - Grub Prompt"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by misterdan on 2012-01-10
Hello, I have problems dual booting ubuntu 11.10 and Windows 7

After install instead of booting to the options, Grub displays the prompt and nothing else, (I used to get a grub partition error)

I used the boot-rescue and the first pastebin is here [http://paste.ubuntu.com/799853/](http://paste.ubuntu.com/799853/) , the second pastebin is here [http://paste.ubuntu.com/799868/](http://paste.ubuntu.com/799868/)

Nothing changed. I then went into windows 7 and fixed boot and mbr. Currently, I have easyBCD manage Boot, option 1 is windows 7, option 2 is ubuntu, but if I click on ubuntu I get sent to grub prompt.

Any help would be appreciated. Thanks

---

### Post by idoitprone on 2012-01-10
>  Grub2 (v1.99) is installed in the** MBR of /dev/sda and looks at sector 1** of      the same hard drive for core.img. core.img is at this location and looks      for  on this drive.
**sda1**: __________________________________________________________________________
 File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /bootmgr /Boot/BCD
**sda6**: __________________________________________________________________________
 File system:       ext4     Boot sector type:  Grub2 (v1.99)     Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6                         and looks at sector 613690512 of the same hard drive                         for core.img. core.img is at this location and looks                         for  on this drive.     Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
this looks problematic. It seems that you have to reinstall the grub2 bootloader by chroot.

It searching for the host os on the first partition instead of the 6th

get ubuntu live cd
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

```
sudo mount /dev/sda6 /mnt
sudo chroot /mnt
sudo grub-install /dev/sda
sudo umount /mnt
```tehn reboot

---

### Post by wolfen69 on 2012-01-10
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by Kniveau600s on 2012-01-10
How about unistalling Grub? Try using console :popcorn:

```
apt-get remove grub
```

---

### Post by oldfred on 2012-01-10
Your pastebin's show grub2's boot loader in the MBR & the PBR of sda6. Did you update the grub in the PBR of sda6 or just the copy in the MBR.

Understand having grub2's boot loader in the PBR is not recommended.

However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

But there are a few Windows apps with DRM that can interfere with grub2's boot loader and in those cases you may have to use EasyBCD. Otherwise it is better to use grub2 as it will also boot Windows.

---

### Post by misterdan on 2012-01-10
Thanks for your responses. I'm currently booting off a live CD and then going to terminal

@idoitprone, I tried that and after "sudo grub-install /dev/sda" I received

"
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
"

@wolfen69 , I then closed terminal, reopened it, tried to install and got some odd errors. maybe due to above. Rebooted and tried boot repair. installed but I got 4 GtK warning's that it was unable to locate theme engine in module path pixmap (exactly the same thing happened before). I checked the OS to boot by default is sda6, checked separate /boot partition in sda2 and placed grub into sda. Applied. Installed the pastebinit packages. Got the copy URL. Then to the terminal I got two new Gtk warnings about attempting to store changes but failing and failing to set permissions...

...pixmap",./glade2script.py:2032: GotWarning: Attempting to store changes into '/root/.local/share/recently-used.xbel;, but failed: Failed to create file '/root/.local/share/recently-used ....

the pastbin link is: [http://paste.ubuntu.com/800045/](http://paste.ubuntu.com/800045/) Also, I used Ubuntu's mechanism for original partitioning, not sure if that is related.

On Boot I now have GRUB, but windows 7 is the only one that comes up. I select Windows 7 and then I get Windows Boot manager, if I select Windows I go to windows. If I select Ubuntu, I go back to GRUB.

@Kniveau600s , I did not try completely removing grub because I'm not sure what the next steps would be.

@Oldfred, when I originally used bootloader I put it in two locations. But this is the first time I saw GRUB and Windows Boot Loader.

Any help from here appreciated...

---

### Post by oldfred on 2012-01-11
A Windows /boot and Ubuntu /boot are not the same or similar partitions in BIOS/MBR. With the new UEFI systems a /efi partition will be used by everyone.

You have parts of grub in the Windows partition, sda2 and they should be in the Ubuntu partition. Delete from Windows. 

> Boot files:        [COLOR=Red]/grub/grub.cfg [/COLOR]/Windows/System32/winload.exe 
                       [COLOR=Red]/grub/core.img[/COLOR]
Sometimes doing this even prevents Windows from booting. Your grub is booting if you can boot from the grub menu to Ubuntu.

This command only works from inside your working system (not liveCd) to install grub to a MBR.
 sudo grub-install /dev/sda

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by misterdan on 2012-01-11
@oldfred, ah, yeah, I see a grub folder in the windows partition. How would I remove that? Just deleting the folder seems to be a bad idea, and I'm not really sure which options on the boot repair program to use, if at all. Can I just remove grub with "apt-get remove grub" and then install via "sudo grub-install /dev/sda"?

---

### Post by oldfred on 2012-01-11
If worried about deleting the /grub in Windows, rename it or back it up first. It should not be a problem. Some have created a /boot/grub folder in the Windows boot partition that conflicts with /Boot in Windows that also has the BCD file. In that case you do have to be careful not to delete the BCD or other Windows files.

You should be able to reinstall grub with the boot-repair program. Usually the easiest way, just do not specify a separate /boot unless you really have one.

Again if manually using a liveCD you cannot just install grub. You have to mount the partition first then install grub.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by misterdan on 2012-01-11
Thanks. I deleted grub from windows partition, instead of using boot-repair I ran the commands. without a reboot, I ran "sudo update-grub" and got an error that it could not find a device for / (is /dev mounted?). I'm assuming I have to reboot into my drive version of ubuntu.

On a restart, I'm now booting straight into grub, and I get the prompt, no windows or ubuntu.

---

### Post by oldfred on 2012-01-11
Assuming you can reboot, then you run the sudo update-grub. It does not work from a liveCD unless you chroot into your system.

Something still not correct then.

Is it grub> or system rescue?

Manual boot your install was in sda6 in the results.txt:
# is comment do not type or copy
grub rescue:
ls # Do you see (hd0), (hd0,6) ? If so, run the next command. If you see (hd0,6), use that instead 
configfile (hd0,6)/boot/grub/grub.cfg

#Or if configfile does not work:
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot

---

### Post by misterdan on 2012-01-11
I do get a partition not in order message on the LiveCD and in the pastebin results.

grub rescue

I tried just typing configfile, got unknown command. if I type "set" I get

prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6

I typed in the first two commands, but when I type in the linux line I get an "unkonwn command 'linux'" and back at grub rescue. I also entered in just "initrd" and got an unknown command. left it at that

---

### Post by drs305 on 2012-01-11
> **misterdan said:**
> I do get a partition not in order message on the LiveCD and in the pastebin results.

grub rescue

I tried just typing configfile, got unknown command. if I type "set" I get

prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6

I typed in the first two commands, but when I type in the linux line I get an unknown command, and back at grub rescue. left it at that

After confirming the same prefix and root above, try loading the 'normal' mod (best case) or 'linux' mod and then trying the rest of the commands you were given earlier.

```
insmod (hd0,6)/boot/grub/normal.mod
insmod (hd0,6)/boot/grub/linux.mod
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot 
```

If the normal module loads, you may be presented with your Grub 2 menu. Otherwise, see if loading the linux module before loading the kernel eliminates the 'unknown command' error.

---

### Post by misterdan on 2012-01-11
insmod is a recognized command, I get "error: no module specified" if I just type it.

But if I type 

```
insmod (hd0,6)/boot/grub/normal.mod
```

I get "error: no such partition"

---

### Post by Cavsfan on 2012-01-11
You are in good hands with **drs305** and **oldfred**. When you get it all sorted out maybe you'll want to check out the How To in my sig.

Makes for a nice dual boot Grub2 menu and I posted my latest screen a couple of days ago as the last post.

Good luck! :D

---

### Post by oldfred on 2012-01-11
I do not know what EasyBCD does, but it should not interfere with grub2's boot loader. The install of grub2's boot loader to the partition sda6 or PBR, should be ignored for now, but if you want to use EasyBCD you will have to fix it.

But you have tried Boot-Repair & manual reinstall of grub2's boot loader to the MBR. Unless you typed something wrong (and that should give an error) the reinstall should work if system is otherwise ok. Are you typing commands or copy & paste into terminal from liveCD?

So you can either chroot into your system and uninstall & reinstall grub2, and do other updates, or do a full reinstall.

drs305 has chroot & uninstall grub & grub2 instructions. You may not have grub legacy to uninstall but otherwise those instructions should work.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by misterdan on 2012-01-11
At this point, I'm just going to reformat the entire disk. Both installations were new so it's easier to do that. This time I'll partition in windows.

Thanks for everyone's help

---

### Post by oldfred on 2012-01-11
Only partition in Windows for Windows partitions. If you try to create more than 4 partitions Windows converts from basic to dynamic with does not work with Linux (and from reports some Windows tools). 

Use gparted for adding Linux partitions.

---

