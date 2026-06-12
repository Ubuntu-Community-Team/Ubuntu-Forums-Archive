---
title: "No Grub: Boots Ubuntu"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by seeker.k3 on 2011-12-20
Hi, I've just started using Linux. My HP computer has Win7 (64-bit) installed, and I made space for Ubuntu. Ubuntu (32-bit) is now installed and running. Great! The problem is I can't boot into Windows now. When the computer starts, it boots directly to Ubuntu: I don't have a choice. I don't get a start menu, and holding down the shift key at start up doesn't help. 
I will attach the results.txt from the Boot_Info_Script. I don't know if that's helpful or not. It's not helpful to me.
Any help would be appreciated. Thank you.

---

### Post by emmomalick on 2011-12-20
> **seeker.k3 said:**
> Hi, I've just started using Linux. My HP computer has Win7 (64-bit) installed, and I made space for Ubuntu. Ubuntu (32-bit) is now installed and running. Great! The problem is I can't boot into Windows now. When the computer starts, it boots directly to Ubuntu: I don't have a choice. I don't get a start menu, and holding down the shift key at start up doesn't help. 
I will attach the results.txt from the Boot_Info_Script. I don't know if that's helpful or not. It's not helpful to me.
Any help would be appreciated. Thank you.
I think you have to reinstall your grub to show Windows at startup screen. See Here 

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

---

### Post by Quackers on 2011-12-20
Have you run ```
sudo update-grub
``` in a terminal? What output is given?

---

### Post by MartijnNL on 2011-12-20
Normally when Ubuntu is installed last, it should recognize Windows during the installation and there would be no need to reinstall GRUB. I just noticed [another thread]("http://ubuntuforums.org/showthread.php?p=11551718") with a similar problem. Perhaps there's something wrong with the os-prober in GRUB?

---

### Post by Quackers on 2011-12-20
The OP could have a look in synaptic package manager and make sure that os-prober is installed.

---

### Post by seeker.k3 on 2011-12-20
> **Quackers said:**
> Have you run ```
sudo update-grub
``` in a terminal? What output is given?
Thanks for looking at this.
The output:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3
done

Does this indicate anything?

---

### Post by pakopako on 2011-12-20
> **seeker.k3 said:**
> Does this indicate anything?
I don't meant to horn in, but it *looks* like everything is fine.
> Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic -- Your current up-to-date Linux

> Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic-- Your previous version before some upgrades (which you can search this forum how to remove)

> Found memtest86+ image: /boot/memtest86+.bin-- Memory test option

> [B]Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3[/B]-- This indicates Windows 7 (and recovery mode) should be available at GRUB.

When you restart your computer (after running *update-grub* as you already have) should look something like [this]("http://www.elfnet.org/wp-content/uploads/2010/10/GRUB.jpg") 
(with "Windows 7" instead of NT/2000/XP at the bottom)

Does your bootloader still look like [this]("http://en.wikipedia.org/wiki/File:GRUB_screenshot.png")?

---

### Post by seeker.k3 on 2011-12-21
Thanks all. 
No, there's no bootloader at all. (I didn't even know what it looked like until you showed me.)
Actually, the situation has changed--bad to worse. I followed the directions to re-install the Grub (the tuxgarage site kindly suggested by emmomalick), but it didn't work. In fact, not even Ubuntu boots now. When I start the computer, blank.
Oh Man, what have I done?
Check this out:

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I actually wonder if I installed Ubuntu properly. There were options for the boot device, I think, weren't there? I left it at the default, which was /dev/sda. Other options included Win7 (loader) and Ubuntu (loader), I think, from memory---my memory.

Should I have choosen Ubuntu (loader)?
Grateful for the help.

---

### Post by Quackers on 2011-12-21
The output of the update-grub command looks to have found the Windows system. On reboot you should have got a grub menu giving you the choice of which OS to boot. Did that happen, or did you just re-install grub? Which version of grub did you install? By what method?
Please re-run the boot script and post the contents of the new Results.txt file (probably named Results1.txt

---

### Post by seeker.k3 on 2011-12-22
> **Quackers said:**
> The output of the update-grub command looks to have found the Windows system. On reboot you should have got a grub menu giving you the choice of which OS to boot. Did that happen, or did you just re-install grub? Which version of grub did you install? By what method?
Please re-run the boot script and post the contents of the new Results.txt file (probably named Results1.txt

I have never seen a grub menu giving me the choice of OS to boot. (Should it appear automatically, or do I press shift to see it? I might have dumbed out at that point.)
I eventually did re-install the grub. (Not first choice.) 

You asked about the version & method. 

sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Does something look wrong here? 
Results.txt attached. (I can't boot either OS on the HD, I'm running Ubuntu from CD, so it's not results1)

BTW Should I install Ubuntu differently? I can't remember the options now, but there was something about the boot device. One of the options was Win7 (loader), and another was Linux (loader).

Thanks for your patience.

---

### Post by hussy786 on 2011-12-22
thanks for sharing

---

### Post by seeker.k3 on 2011-12-22
Here are the results

---

### Post by sikander3786 on 2011-12-22
Hello. Just when *Quackers* is away, I would jump in for the time being. :)

You don't need to re-install Ubuntu. And there is no guarantee that re-installing Ubuntu would let you dual-boot Windows successfully as the initial problem wasn't with Ubuntu rather it was Windows.

So, you are unable to boot either Windows or Ubuntu successfully for now, right?

If you follow everything mentioned here, step-by-step, I can assure you that you would be able to successfully boot Ubuntu and Windows however the whole practice might need some time.

We can try to repair Windows 7 boot at first and then re-install Grub for dual-booting but that has a 50 % chance of being successful as Windows 7's extra Boot partition is known to cause some boot problems with Grub. So what we are going to do here:

1. Purge and re-install Grub from an Ubuntu Live CD/USB and make sure you are able to successfully boot Ubuntu.
2. Delete the Windows boot partition and attempt to repair Windows 7 boot. When successfully done, you would only be able to boot Windows 7 for the time being and not Ubuntu.
3. Re-install Grub and successfully dual boot Windows 7 and Ubuntu.

Make sure you didn't add another HDD, CD-ROM or even switch the IDE/Sata cables of your HDD after posting the above bootinfoscript output. These commands are based on your output and might not be successful if the drive paths have changed in the meantime.

So, first of all, you need to purge and re-install Grub. Boot an Ubuntu Live CD/USB and get to a Terminal. Your commands would be:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sda6 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

At this point, you should test your connectivity and proceed only in-case the following command is successful:

```
apt-get update
```

If there weren't any errors, continue:

```
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
```

When Grub packages are being installed, you would be presented to choose your intended disk where you want to install Grub. In your case, it is 'sda'. Use <Space> to mark 'sda' as the target and use <Tab> and <Enter> to make the choice. DONOT select a partition like 'sda**6**' or whatever. Simply choose 'sda' without an integer.

Continue:

```
update-grub
```

```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
for i in /dev/pts /dev /proc /sys /boot; do sudo umount /mnt/temp$i ; done
```

The above commands were taken from **drs305's** guide and modified accordingly:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Now reboot your PC and see if are able to boot Ubuntu successfully. Hopefully, you are. Also see if you can boot Windows successfully. I am not sure but if successful, you obviously don't need to follow what is mentioned below.

If still not able to boot Windows 7 successfully, you need to do some more work. Get to Ubuntu's Terminal and install GParted:

```
sudo apt-get install gparted
```

Once installed, press the <Super> key and search the Dash for GParted and open it. Right click the 'sda1' partition and DELETE it.

Now right click you 'sda2' partition which actually holds the Windows 7 install and go to 'Manage Flags'. Tick the checkbox for 'boot'. Click close and click 'Apply' button in the top toolbar.

Now boot your Windows 7 install/repair disc and repair the startup as mentioned in the link below. You'd need to perform this repair 3 times at least. Once you've attempted to repair the startup 3 times, you should be able to boot Windows 7 by then, but not Ubuntu. The link is here:

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

So once you are able to successfully boot Windows 7, you now need to re-install Grub. At this point, 2 things are very important. First, you were successfully able to boot Ubuntu when we performed the purge/re-install Grub commands and second, you are successfully able to boot Windows after repairing the startup. If the answer to both of these is yes, boot the Ubuntu Live CD/USB once again and from a Terminal:

I am not sure about this one. As we've deleted the Windows 7 boot partition 'sda1', I guess your Ubuntu partition would now become 'sda5' instead of 'sda6' as is shown in your bootinfoscript output. You can figure it out by taking a look a the output of:

```
sudo fdisk -l
```

If you can't figure it out, post the output at this point so we can take a look.

Replace 'sda**X**' with whatever your Ubuntu partition is, in the command below:

```
sudo mount /dev/sda**X** /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and hopefully both Windows 7 and Ubuntu would be bootable, successfully. If you still can't see Windows 7, boot Ubuntu from the HDD and from its Terminal:

```
sudo update-grub
```

That should do it.

And you might also want to wait for **Quackers** to come online and take a look at my post and see if there is something I missed, or there is some other easier approach to solve your issue.

---

### Post by MartijnNL on 2011-12-22
I don't think reinstalling Ubuntu is necessary.

Are you using a live CD from the same Ubuntu version as you have installed?

When you re-installed GRUB did you follow the instructions exactly? So you did 'fdisk - l' first, then the mount command with 'dev/sdaX' where X is a number (did you choose the right number?) and then the grub-install command using '/dev/sda' **without** the number?

And yes to get to the GRUB menu you have to press and **hold** shift (not just a short press) right after the screen turns black during the boot. So after the screen(s) from you hardware/bios (like a logo for example). If you press shift right from the start it might not work.

If you have access to another pc where you can burn a disk, you could also try running [SuperGrub2 disk]("http://http://www.supergrubdisk.org/super-grub2-disk/"). This should get you into your own Ubuntu installation (not a live CD system).

You can then run 'sudo grub-install /dev/sda' in a terminal inside your Ubuntu. Do not use the mount command and such in that case, just this command. And you might want to run 'sudo update-grub' as well.

By the way: running 'sudo update-grub' in a LiveCD won't do you much good.

Edit: sikander3786 posted his answer while I was typing as well. His suggestion might be a better one, depending on the cause of your problem. Expecially  if there's some windows specific issue here. Mine (Supergrubdisk) might be bit quicker, and won't hurt. Just might not work though.

---

### Post by mastablasta on 2011-12-22
> **MartijnNL said:**
>  
And yes to get to the GRUB menu you have to press and **hold** shift (not just a short press) right after the screen turns black during the boot. So after the screen(s) from you hardware/bios (like a logo for example). If you press shift right from the start it might not work.

 
do this first.
 
because it might be simply that your boot grub menu timer is set to 0.
 
in this case grub menu will be skipped and default OS (first in line) will be booted (in your case first one is Ubuntu so that one will boot). this can easilly be solved and set to for example 5sec which will give you enough time to switch the os if necessary.

---

### Post by seeker.k3 on 2011-12-22
Thanks so much for your generous help. I've read all these posts closely, and I sincerely appreciate all your comments (tips on shift key, etc.). I followed sikander3786's instructions to purge and re-install Grub, but unfortunately, it didn't change a thing. The instructions were perfectly clear and easy to follow, and it seemed to go well, but still no boot. Against advice, I staggered onwards and deleted the Win7 boot partition. I ran the Windows' startup repair over and over, but it didn't work. (I have to wonder if this is more than a software issue.)
 
I don't think I can fix it now. And it's wasting your time and mine. I'll lieave this open for a few days (if someone wants to comment), and then stop it. In a few days I'll do a clean install--probably Ubuntu--and come back to dual boot when I've got more skills.
 
I've learnt lots and lots of stuff and picked up lots of resources (from the links), and in that sense it's been a very valuable experience for me.
Thanks for the goodwill.

---

### Post by sikander3786 on 2011-12-23
If you could please post the output of bootinfoscript once more, we might eventually be able to lock down the issue for you.

Thanks.

---

### Post by kansasnoob on 2011-12-23
> **sikander3786 said:**
> If you could please post the output of bootinfoscript once more, we might eventually be able to lock down the issue for you.

Thanks.

You probably noticed that the BIS now lacks some needed info:

> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

I opened a discussion regarding that here:

[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

Bottom line either the "git" version:

[http://ubuntuforums.org/showpost.php?p=11552634&postcount=7](http://ubuntuforums.org/showpost.php?p=11552634&postcount=7)

Or this test version:

[http://ubuntuforums.org/showpost.php?p=11554689&postcount=26](http://ubuntuforums.org/showpost.php?p=11554689&postcount=26)

Should work better for troubleshooting Oneiric and newer versions of grub 2 :)

---

### Post by sikander3786 on 2011-12-23
> **kansasnoob said:**
> You probably noticed that the BIS now lacks some needed info:



I opened a discussion regarding that here:

[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)

Bottom line either the "git" version:

[http://ubuntuforums.org/showpost.php?p=11552634&postcount=7](http://ubuntuforums.org/showpost.php?p=11552634&postcount=7)

Or this test version:

[http://ubuntuforums.org/showpost.php?p=11554689&postcount=26](http://ubuntuforums.org/showpost.php?p=11554689&postcount=26)

Should work better for troubleshooting Oneiric and newer versions of grub 2 :)
Yeah noticed that already and did a Web search on that earlier but couldn't find much. Thanks for the links and also for the pointers. :)

---

### Post by seeker.k3 on 2011-12-25
OK. I'm surprised, but here it is. I had to use version 0.60, because I couldn't sort out the links, without help. I did extract file bootinfoscripttest, but then I didn't know what to do with it. How do I run it? Anyway, here's my results.txt. If I need to use a different program, (i.e. bootinfoscripttest), tell me; and I might need some absolute beginner instructions. 
Thanks.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *        206,911   478,095,359   477,888,449   7 NTFS / exFAT / HPFS
/dev/sda3         953,677,824   976,771,071    23,093,248   7 NTFS / exFAT / HPFS
/dev/sda4         478,097,406   953,677,823   475,580,418   5 Extended
/dev/sda5         950,011,904   953,677,823     3,665,920  82 Linux swap / Solaris
/dev/sda6         478,097,408   946,343,935   468,246,528  83 Linux
/dev/sda7         946,345,984   950,003,711     3,657,728  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        B818E2EE18E2AA98                       ntfs       OS
/dev/sda3        2E301AF3301AC1AF                       ntfs       HP_RECOVERY
/dev/sda5        60d05540-e56d-41d4-adf8-d36b207c28b4   swap       
/dev/sda6        beb719ed-b8fc-426e-bf10-d54f8afeef99   ext4       
/dev/sda7        befc137c-1ac0-496c-b47b-ad80cf885e73   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=beb719ed-b8fc-426e-bf10-d54f8afeef99 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=beb719ed-b8fc-426e-bf10-d54f8afeef99 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=beb719ed-b8fc-426e-bf10-d54f8afeef99 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=beb719ed-b8fc-426e-bf10-d54f8afeef99 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root beb719ed-b8fc-426e-bf10-d54f8afeef99
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 54A4745EA4744510
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 2E301AF3301AC1AF
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=beb719ed-b8fc-426e-bf10-d54f8afeef99 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=60d05540-e56d-41d4-adf8-d36b207c28b4 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=befc137c-1ac0-496c-b47b-ad80cf885e73 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by saneearth on 2011-12-25
If you have just installed Ubuntu and not put too much work into it a fresh install might be your best bet to fix everything. Early in the installation you should be shown that Grub will be installed on sda by default and this is correct. I would use the third option for install and that is to do something else other that install along side, or upgrade ubuntu, which will likely be your first two choices. You will be give the option to choose where to put things. If you have only one disc you will see all of your partitions. Choose the same location as your windows partition to boot DO NOT CHECK the format box. You should see two other partitions (or three) which are your linux partitions. You can keep these partitions for the install. Just select to change each and select extension 4. On the larger partition select /home and check the partition box. On the next largest partition (likely around 15 GB, select / (which is root and check the format box. The third partition will be smallest and just select swap unless it is already designated as such. This will just put linux exactly where it was before. Though this seems like a lot of work it really isn't that much. It is also better to start fresh and right than to try repairs, especially when not having great experience with said repairs. I have used Ubuntu since 2006 and several other distributions, but I always go back to a fresh install of Ubuntu. If I do anything other than a fresh install, I only keep /home and even then I delete all my configuration files and keep only my data and the configurations for programs such as my web browsers, email readers and pan. Don't give up.

---

### Post by oldfred on 2011-12-25
Your sda1 is missing and with Windows 7 it normally creates a (hidden in Windows) boot/repair NTFS partition of 100MB. That contains two of the three files needed to boot.
Boot files:        /bootmgr /boot/bcd

You have the same files in the recovery partition but the BCD will be different and would then need repair. You are also then missing the repair files so pressing f8 to get to repair probably will not work. You might be able to copy the boot files and download EasyBCD to fix BCD but I have not used EasyBCD.

You may be able to get sda1 back as it looks like the space is still at the front of the drive before sda2. If you have changed partitions several times testdisk may show all the alternatives, but you cannot restore overlapping partitions. You just want to restore the one at the beginning of the drive.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Learning Linux 2011 on 2011-12-26
Being a new computer, could this have something to do with the new **Unified Extensible Firmware Interface** (**UEFI**)?

I've heard you need a special EFI version of GRUB if that is the case.

---

### Post by oldfred on 2011-12-26
New computers seem to have both BIOS & UEFI and do not have settings to use either. They seem to rely on the hard drive. If the first partition is efi (and gpt) then it is UEFI. 

Drive is MBR(msdos) and has no first partition, but since it is MBR, the missing first partition is the 100MB Windows boot partition. Unless of course it was converted from gpt somehow & the efi partition was deleted.

---

### Post by arjunrj405 on 2011-12-26
I've been having the same problem. My teacher told me that windows does not want people to run linux with their system so they provide such problems to which are difficult. 

Remember under this code given in the site;
sudo grub-install --root-directory=/mnt /dev/sda

under this was written the comment:-[I]
"Note, for the second command it is just sda without an integer."[/I]
i.e i suppose it must be :-
sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda6

though i must confess it dint work for me...  sigh!:roll:

---

### Post by oldfred on 2011-12-26
@arjunrj405 You posted a version with the integer or partition number not just the drive.

> sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt [COLOR=Red]/dev/sda6[/COLOR]Should be just sda, so it installs to the MBR of the drive not to a partition like sda6.

Should be this from liveCD of the same version of Ubuntu :
sudo fdisk -l
 sudo mount /dev/sda6 /mnt
 sudo grub-install --root-directory=/mnt [COLOR=Red]/dev/sda[/COLOR]

And with grub 1.99 boot not root preferred although above should work.

#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses [COLOR=Red]boot not root.[/COLOR]
sudo grub-install --[COLOR=Red]boot[/COLOR]-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

