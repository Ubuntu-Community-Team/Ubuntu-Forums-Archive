---
title: "Boot problems"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by toner77 on 2012-10-08
Hello all,

I had some problems booting up Unbuntu 12.04 today,

I placed the installation disk in and loaded up the boot repair, 

Unfortunately now when I try to boot up it says there is no operating installed,

Any ideas ?

---

### Post by twipley on 2012-10-08
Maybe I am overusing this solution, but if it were happening to me,

I would boot from the LiveCD, chmod -R 777 all of my files, back them up to somewhere else, then install Ubuntu afresh.

After that, do not mess with other operating systems than Ubuntu unless being ready to fiddle up from the GRUB level.

Sounds like a good-enough solution? (Even though it is not meant to be the fastest one.)

---

### Post by DuckHook on 2012-10-09
Things are probably not all that bad. It is likely that your OS is still intact and you just have a corrupted bootloader or somehow nuked GRUB. However, your description of your problem does not give us anything to go on:

1. What was the initial problem that caused you to resort to boot repair? Using boot repair is serious stuff and must be done with knowledge and with care. It is all too easy to hose your bootloader if you don't know what you are doing.
2. What steps did you take in boot repair?
3. If you boot up with the live CD, can you see your HD? If so, can you see your file systems?

To get meaningful help, you must provide detailed and complete descriptions. It is not possible to provide help just knowing that something doesn't work.

---

### Post by varunendra on 2012-10-09
Welcome to the forums toner77 !

> **DuckHook said:**
> Using boot repair is serious stuff and must be done with knowledge and with care. It is all too easy to hose your bootloader if you don't know what you are doing.
Actually, using Boot-Repair (in its simple mode) is quite easy and is recommended as a "First-Aid" before trying anything serious. It 'may' go wrong only if you blindly try the 'Advance' options without any knowledge of what you are doing.

*@toner77,*
Please use the "Create BootInfo Summary" button in Boot-Repair and post back the pastebin link it creates for you.

---

### Post by NikTh on 2012-10-09
> **varunendra said:**
> 
*@toner77,*
Please use the "Create BootInfo Summary" button in Boot-Repair and post back the pastebin link it creates for you.

+1 

it would be helpful as we can see what really is going on. 

Thanks

---

### Post by toner77 on 2012-10-09
Thanks for the replies,

when I originally booted up I had a couple of options can't remember the exact wording but there was four or five options, memtest was included (did that passed),

So my next step was to load up the CD and run "try ubuntu" and then i installed "boot repair" a ran the fix common errors, it saved a file under filesystem/root/bootinfo but when I reloaded the Cd it wont let me access the file system, any suggestions would be welcome,

the operating system seems to be there but obviously I have corrupted the boot somehow,

Do I need to reload the bootrepair and when its finished post ?

---

### Post by NikTh on 2012-10-09
> **toner77 said:**
> 

Do I need to reload the bootrepair and when its finished post ?

Yes 
and give here the link.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225315&d=1349797017[/IMG]

Thanks

---

### Post by toner77 on 2012-10-09
attached boot info file

---

### Post by NikTh on 2012-10-09
[quote="boot-info"] 

sda1:
File system:       ext4
     Boot sector type:  -
     Boot sector info: 
     Mounting failed:   mount: **wrong fs type, bad option, bad superblock on /dev/sda1,**
        missing codepage or helper program, or other error
        In some cases useful info is found in syslog - try
        dmesg | tail  or so[/quote]
Your problem located at bold marked. 
You have an ext4 corrupted file-system. We can attempt to fix this , but **involves risks of Data-LOSS. **

If you want to attempt then follow this. 

Boot from LiveCd/Usb and open a terminal (Ctrl+Alt+t).
Give bellow commands 
```
sudo mke2fs -n /dev/sda1
```From the results , look at the end and you will see the numbers of **Superblock backups stored on blocks:**

Here is the attempt with fsck to fix the errors. 

```
sudo e2fsck -y -b **block_location** /dev/sda1
```where **block_location** you will replace it with one of the numbers from **Superblock backups stored on blocks**

**After the fsck's fix** , _run again the boot-repair _to install grub in /dev/sda. Click on [Recommended Repair] and at the end , reboot you Pc. 

Thanks and Good Luck.

---

### Post by toner77 on 2012-10-09
Problem solved with no data loss

Thank you very much for you help

---

### Post by DuckHook on 2012-10-09
Further recommend that you backup all data immediately and then run regular backups. In my experience, once a disk starts misbehaving, its reliability is greatly compromised. Don't want to alarm you, but if you purchase a cheap USB drive and perform regular backups, it could save you a world of trouble if the HD dies.

---

