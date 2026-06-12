---
title: "Grub not recognizing the Windows partition"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by stri8ed on 2013-01-02
I recently installed ubuntu alongside windows 7. During the installation, i choose to manually partition the disk using gparted, and somewhere along that process I mistakenly deleted my windows partition. Using TestDisk I was able to restore the windows partition, however now the grub bootloader does not recognize my windows partition.

Here is the paste I got from running boot-repair:
[http://paste.ubuntu.com/1489320/](http://paste.ubuntu.com/1489320/)

and here is a screenshot of my gparted:
[http://i46.tinypic.com/3464xhk.png](http://i46.tinypic.com/3464xhk.png)

Something strange is going on here, but I am really lost as how to fix this. Any help is appreciated.

---

### Post by COMECON on 2013-01-02
Have you tried updating grub?
```
 $ sudo update-grub2 
```

Catbuntu

---

### Post by stri8ed on 2013-01-02
> **COMECON said:**
> Have you tried updating grub?
```
 $ sudo update-grub2 
```

Catbuntu

Yes. It does not seem to fix the problem. Here is what it returns:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done

```

---

### Post by COMECON on 2013-01-02
Well, you can try unmounting (if already mounted) and mounting again your Windows partition. Then try to update grub again.
Hope it works.

Catbuntu

---

### Post by stri8ed on 2013-01-02
> **COMECON said:**
> Well, you can try unmounting (if already mounted) and mounting again your Windows partition. Then try to update grub again.
Hope it works.

Catbuntu

Tried that. Unfortunately it does not do anything.

---

### Post by COMECON on 2013-01-02
> **stri8ed said:**
> Tried that. Unfortunately it does not do anything.

Oh, I'm sorry... I can't imagine any other solution, perhaps somebody will be able to help you :)

Catbuntu

---

### Post by oldfred on 2013-01-02
Windows has a hidden (in Windows) 100MB NTFS partition with the boot flag as the first partition. You are still missing that partition. It has two essential boot files and the recovery console in it. Windows made it a separate partition so you could encrypt you main install, but Vista did not have it separate.

Also Windows has to be in a primary partition to boot. You could use a Windows repairCD to add the missing boot files to your main install, but sda5 has to be converted to a primary partition.

       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You also have the 4 primary partition limit, so you cannot just convert back. You can delete swap, convert Windows back to a primary, then create a new swap in a new extended partition. You will then have to update fstab with new UUID.

Or you can reinstall Windows. But will still have to reorganize partitions.

 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by YannBuntu on 2013-01-02
/bootmgr /Boot/BCD are missing, which means either an erased Windows boot partition, or an erased ESP. This lost partition was 211MB, and was located at the start of the disk, as we can see in the log:

```
Number  Start  End    Size    Type      File system     Flags
1      211MB  202GB  202GB   extended                  boot
```

Solution:
1) use a Windows disc this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you get direct access to Windows
2) then use Boot-Repair to recover the GRUB menu. If Windows is UEFI, Boot-Repair will ask you to install Ubuntu 64bit instead of your current Ubuntu32bit.

---

### Post by stri8ed on 2013-01-02
Wow. Thanks so much oldfred and YannBuntu. You made my day. Using both your advice I was able to fix this. Here is what I ended up doing:

1. Using "fixparts" I converted my windows partition (sda5) into a primary partition.

2. Using Gparted, I formatted the 200MB unallocated space seen at the beginning of my drive to NTSF, and set the flag to boot.

3. I Downloaded the windows 7 repair ISO [from here]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"), and extracted the ISO files into the partition described above.

4. I ran "update-grub2", which now found my windows partition. I restarted the computer, booted into the windows option, and from there it prompted me to fix my broken startup. I selected ok, it restarted, and boom my windows is back and working.

---

